---
title: Självstudie – Distribuera Azure våren Cloud i ett virtuellt nätverk
description: Distribuera Azure våren Cloud i ett virtuellt nätverk (VNet-insprutning).
author: MikeDodaro
ms.author: brendm
ms.service: spring-cloud
ms.topic: tutorial
ms.date: 07/21/2020
ms.custom: devx-track-java
ms.openlocfilehash: 9d72d60bd3a1ef23b8122b2bc5ba4f0c5c701254
ms.sourcegitcommit: d2d1c90ec5218b93abb80b8f3ed49dcf4327f7f4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/16/2020
ms.locfileid: "97587731"
---
# <a name="tutorial-deploy-azure-spring-cloud-in-a-virtual-network"></a>Självstudie: Distribuera Azure våren Cloud i ett virtuellt nätverk

**Den här artikeln gäller för:** ✔️ Java ✔️ C #

I den här självstudien beskrivs hur du distribuerar en Azure våren Cloud-instans i det virtuella nätverket. Den här distributionen kallas ibland VNet-inmatning.

Distributionen gör det möjligt att:

* Isolering av Azure våren-molnappar och service runtime från Internet i företags nätverket.
* Azure våren Cloud-interaktion med system i lokala data Center eller Azure-tjänster i andra virtuella nätverk.
* Att kunderna ska kunna kontrol lera inkommande och utgående nätverkskommunikation för Azure våren Cloud.

## <a name="prerequisites"></a>Krav

Registrera Azure våren Cloud Resource Provider **Microsoft. AppPlatform** och **Microsoft. container service** enligt instruktionerna i [Registrera resurs leverantör på Azure Portal](../azure-resource-manager/management/resource-providers-and-types.md#azure-portal) eller genom att köra följande Azure CLI-kommando:

```azurecli
az provider register --namespace Microsoft.AppPlatform
az provider register --namespace Microsoft.ContainerService
```

## <a name="virtual-network-requirements"></a>Krav för virtuellt nätverk

Det virtuella nätverk som du distribuerar din Azure våren-moln instans till måste uppfylla följande krav:

* **Plats**: det virtuella nätverket måste finnas på samma plats som Azure våren Cloud-instansen.
* **Prenumeration**: det virtuella nätverket måste finnas i samma prenumeration som Azure våren Cloud-instansen.
* **Undernät**: det virtuella nätverket måste innehålla två undernät som är dedikerade till en Azure våren Cloud-instans:

    * En för tjänst körningen.
    * En för dina våren Boot-mikrotjänstprogram.
    * Det finns en 1-till-1-relation mellan dessa undernät och en Azure våren Cloud-instans. Använd ett nytt undernät för varje tjänst instans som du distribuerar. Varje undernät kan bara innehålla en enda tjänst instans.
* **Adress utrymme**: CIDR-block blockerar upp till */28* för både service runtime-undernätet och våren Boot Boot-programtjänstprogram.
* **Routningstabell**: under näten får inte ha någon befintlig routningstabell kopplad.

Följande procedurer beskriver hur du installerar det virtuella nätverket som innehåller instansen av Azure våren Cloud.

## <a name="create-a-virtual-network"></a>Skapa ett virtuellt nätverk

Om du redan har ett virtuellt nätverk som värd för en Azure våren-moln instans hoppar du över steg 1, 2 och 3. Du kan börja från steg 4 för att förbereda undernät för det virtuella nätverket.

1. I menyn i Azure-portalen väljer du **Skapa en resurs**. Välj **nätverk**  >  **virtuellt nätverk** från Azure Marketplace.

1. I dialog rutan **Skapa virtuellt nätverk** anger eller väljer du följande information:

    |Inställningen          |Värde                                             |
    |-----------------|--------------------------------------------------|
    |Prenumeration     |Välj din prenumeration.                         |
    |Resursgrupp   |Välj en resurs grupp eller skapa en ny.  |
    |Name             |Ange **Azure-våren-Cloud-VNet**.                 |
    |Plats         |Välj **USA, östra**.                               |

1. Välj **Nästa: IP-adresser**.

1. För IPv4-adress utrymmet anger du **10.1.0.0/16**.

1. Välj **Lägg till undernät**. Ange sedan **tjänst-runtime-Subnet** för **under nätets namn** och ange **10.1.0.0/28** för **under nätets adress intervall**. Välj **Lägg till**.

1. Välj **Lägg till undernät** igen och ange sedan **under nätets namn** och **under nätets adress intervall**. Ange till exempel **Apps-Subnet** och **10.1.1.0/28**. Välj **Lägg till**.

1. Välj **Granska + skapa**. Lämna resten som standard och välj **skapa**.

## <a name="grant-service-permission-to-the-virtual-network"></a>Bevilja tjänst behörighet till det virtuella nätverket

Välj det virtuella nätverket **Azure-våren-Cloud-VNet** som du skapade tidigare.

1. Välj **åtkomst kontroll (IAM)** och välj sedan **Lägg till**  >  **Lägg till roll tilldelning**.

    ![Skärm bild som visar skärmen för åtkomst kontroll.](./media/spring-cloud-v-net-injection/access-control.png)

1. I dialog rutan **Lägg till roll tilldelning** anger eller väljer du följande information:

    |Inställningen  |Värde                                             |
    |---------|--------------------------------------------------|
    |Roll     |Välj **ägare**.                                 |
    |Välj   |Ange **Azure våren Cloud Resource Provider**.   |

    Välj sedan **Azure våren Cloud Resource Provider** och välj **Spara**.

    ![Skärm bild som visar val av Azure våren Cloud Resource Provider.](./media/spring-cloud-v-net-injection/grant-azure-spring-cloud-resource-provider-to-vnet.png)

Du kan också göra detta steg genom att köra följande Azure CLI-kommando:

```azurecli
VIRTUAL_NETWORK_RESOURCE_ID=`az network vnet show \
    --name ${NAME_OF_VIRTUAL_NETWORK} \
    --resource-group ${RESOURCE_GROUP_OF_VIRTUAL_NETWORK} \
    --query "id" \
    --output tsv`

az role assignment create \
    --role "Owner" \
    --scope ${VIRTUAL_NETWORK_RESOURCE_ID} \
    --assignee e8de9221-a19c-4c81-b814-fd37c6caf9d2
```

## <a name="deploy-an-azure-spring-cloud-instance"></a>Distribuera en Azure våren Cloud-instans

Så här distribuerar du en Azure våren-moln instans i det virtuella nätverket:

1. Öppna [Azure-portalen](https://portal.azure.com).

1. Sök efter **Azure våren Cloud** i den översta sökrutan. Välj **Azure våren Cloud** från resultatet.

1. På sidan **Azure våren Cloud** väljer du **+ Lägg till**.

1. Fyll i formuläret på sidan Azure våren Cloud **create** .

1. Välj samma resurs grupp och region som det virtuella nätverket.

1. Som **namn** under **tjänst information** väljer du **Azure-våren-Cloud-VNet**.

1. Välj fliken **nätverk** och välj följande värden:

    |Inställningen                                |Värde                                             |
    |---------------------------------------|--------------------------------------------------|
    |Distribuera i ditt eget virtuella nätverk     |Välj **Ja**.                                   |
    |Virtuellt nätverk                        |Välj **Azure-våren-Cloud-VNet**.               |
    |Undernät för service runtime                 |Välj **service-runtime-Subnet**.                |
    |Subnet Boot mikroservice Apps-undernät   |Välj **appar-undernät**.                           |

    ![Skärm bild som visar fliken nätverk på sidan Azure våren Cloud Create.](./media/spring-cloud-v-net-injection/creation-blade-networking-tab.png)

1. Välj **Granska och skapa**.

1. Kontrol lera dina specifikationer och välj **skapa**.

    ![Skärm bild som visar verifierings anvisningar.](./media/spring-cloud-v-net-injection/verify-specifications.png)

Efter distributionen skapas två ytterligare resurs grupper i din prenumeration som värd för nätverks resurserna för Azure våren Cloud-instansen. Gå till **Start** och välj sedan **resurs grupper** från de översta meny alternativen för att hitta följande nya resurs grupper.

Resurs gruppen med namnet as **AP-SVC-RT_ {tjänst instans namn} _ {tjänst instans region}** innehåller nätverks resurser för tjänst körningens tjänst körning.

  ![Skärm bild som visar tjänst körningen.](./media/spring-cloud-v-net-injection/service-runtime-resource-group.png)

Resurs gruppen med namnet som **AP-app_ {tjänst instans namn} _ {tjänst instans region}** innehåller nätverks resurser för dina våren Boot-mikrotjänstprogram för tjänst instansen.

  ![Skärm bild som visar resurs gruppen appar.](./media/spring-cloud-v-net-injection/apps-resource-group.png)

Nätverks resurserna är anslutna till ditt virtuella nätverk som du skapade i föregående bild.

  ![Skärm bild som visar det virtuella nätverket med anslutna enheter.](./media/spring-cloud-v-net-injection/vnet-with-connected-device.png)

   > [!Important]
   > Resurs grupperna hanteras helt av moln tjänsten Azure våren. Ta *inte* bort eller ändra någon resurs i manuellt.

## <a name="limitations"></a>Begränsningar

Ett litet under näts intervall sparar IP-adresser, men det ger begränsningar för det maximala antalet App-instanser som Azure våren Cloud-instansen kan innehålla.

| App-undernät, CIDR | Totalt antal IP-adresser | Tillgängliga IP-adresser | Maximalt antal App-instanser                                        |
| --------------- | --------- | ------------- | ------------------------------------------------------------ |
| /28             | 16        | 8             | <p> App med 1 kärna: 96 <br/> App med 2 kärnor: 48<br/>  App med 3 kärnor: 32 <br/> App med 4 kärnor: 24 </p> |
| /27             | 32        | 24            | <p> App med 1 kärna: 228<br/> App med 2 kärnor: 144<br/>  App med 3 kärnor: 96 <br/>  App med 4 kärnor: 72</p> |
| /26             | 64        | 56            | <p> App med 1 kärna: 500<br/> App med 2 kärnor: 336<br/>  App med 3 kärnor: 224<br/>  App med 4 kärnor: 168</p> |
| /25             | 128       | 120           | <p> App med 1 kärna: 500<br> App med 2 kärnor: 500<br>  App med 3 kärnor: 480<br>  App med 4 kärnor: 360</p> |
| /24             | 256       | 248           | <p> App med 1 kärna: 500<br/> App med 2 kärnor: 500<br/>  App med 3 kärnor: 500<br/>  App med 4 kärnor: 500</p> |

För undernät är fem IP-adresser reserverade av Azure och minst fyra adresser krävs av Azure våren Cloud. Minst nio IP-adresser krävs, så/29 och/30 är inte drift.

För ett undernät för service runtime är den minsta storleken/28. Den här storleken har ingen betydelse för antalet App-instanser.

## <a name="next-steps"></a>Nästa steg

[Distribuera program till Azure våren Cloud i ditt VNet](https://github.com/microsoft/vnet-in-azure-spring-cloud/blob/master/02-deploy-application-to-azure-spring-cloud-in-your-vnet.md)

## <a name="see-also"></a>Se även

- [Felsöka Azure våren Cloud i VNET](https://github.com/microsoft/vnet-in-azure-spring-cloud/blob/master/05-troubleshooting-azure-spring-cloud-in-vnet.md)
- [Kund ansvar för att köra Azure våren Cloud i VNET](https://github.com/microsoft/vnet-in-azure-spring-cloud/blob/master/06-customer-responsibilities-for-running-azure-spring-cloud-in-vnet.md)
