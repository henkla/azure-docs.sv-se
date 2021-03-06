---
title: Snabb start – skapa och hantera resurser i Azure Communication Services
titleSuffix: An Azure Communication Services quickstart
description: I den här snabb starten får du lära dig hur du skapar och hanterar din första Azure Communication Services-resurs.
author: mikben
manager: jken
services: azure-communication-services
ms.author: mikben
ms.date: 09/30/2020
ms.topic: overview
ms.service: azure-communication-services
zone_pivot_groups: acs-plat-azp-net
ms.openlocfilehash: a93ac3b5d988be33c0f27726a75b1006f990d1da
ms.sourcegitcommit: 230d5656b525a2c6a6717525b68a10135c568d67
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94886125"
---
# <a name="quickstart-create-and-manage-communication-services-resources"></a>Snabb start: skapa och hantera kommunikations tjänst resurser

[!INCLUDE [Public Preview Notice](../includes/public-preview-include.md)]

Kom igång med Azure Communication Services genom att tillhandahålla din första kommunikations tjänst resurs. Kommunikations tjänst resurser kan tillhandahållas via Azure Portal eller med klient biblioteket för .NET-hantering. Med hanterings klient biblioteket kan du skapa, konfigurera, uppdatera och ta bort dina resurser och gränssnitt med [Azure Resource Manager](../../azure-resource-manager/management/overview.md), Azures distributions-och hanterings tjänst. Alla funktioner i klient biblioteken är tillgängliga i Azure Portal. 

> [!WARNING]
> Observera att tillgänglighet för kommunikations tjänster är begränsat till amerikanska geografi under den offentliga för hands versionen. Observera också att kommunikations resurser inte kan överföras till en annan prenumeration under den offentliga för hands versionen.

::: zone pivot="platform-azp"
[!INCLUDE [Azure portal](./includes/create-resource-azp.md)]
::: zone-end

::: zone pivot="platform-net"
[!INCLUDE [.NET](./includes/create-resource-net.md)]
::: zone-end

## <a name="access-your-connection-strings-and-service-endpoints"></a>Åtkomst till anslutnings strängar och tjänst slut punkter

Anslutnings strängar gör att klient biblioteken för kommunikations tjänster kan ansluta och autentisera till Azure. Du kan komma åt anslutnings tjänst anslutnings strängar och tjänst slut punkter från Azure Portal eller program mässigt med Azure Resource Manager-API: er. 

När du har navigerat till kommunikations tjänst resursen väljer du **nycklar** i navigerings menyn och kopierar **anslutnings strängen** eller **slut punkts** värden för användning av klient biblioteken för kommunikations tjänster. Observera att du har åtkomst till primära och sekundära nycklar. Detta kan vara användbart i scenarier där du vill ge tillfällig åtkomst till dina kommunikations tjänst resurser till en tredje part eller en utvecklings miljö.

:::image type="content" source="./media/key.png" alt-text="Skärm bild av nyckel sidan för kommunikations tjänster.":::

## <a name="store-your-connection-string"></a>Lagra anslutnings strängen

Klient bibliotek för kommunikations tjänster använder anslutnings strängar för att auktorisera begär Anden som görs till kommunikations tjänster. Du har flera alternativ för att lagra anslutnings strängen:

* Ett program som körs på Skriv bordet eller på en enhet kan lagra anslutnings strängen i en **app.config** eller **web.config** fil. Lägg till anslutnings strängen i avsnittet **appSettings** i de här filerna.
* Ett program som körs i en Azure App Service kan lagra anslutnings strängen i [app service program inställningar](../../app-service/configure-common.md). Lägg till anslutnings strängen i avsnittet **anslutnings strängar** på fliken program inställningar i portalen.
* Du kan lagra anslutnings strängen i [Azure Key Vault](../../data-factory/store-credentials-in-key-vault.md).
* Om du kör programmet lokalt kanske du vill lagra anslutnings strängen i en miljö variabel.

### <a name="store-your-connection-string-in-an-environment-variable"></a>Lagra anslutnings strängen i en miljö variabel

Om du vill konfigurera en miljö variabel öppnar du ett konsol fönster och väljer ditt operativ system på flikarna nedan. Ersätt `<yourconnectionstring>` med den faktiska anslutnings strängen.

#### <a name="windows"></a>[Windows](#tab/windows)

Öppna ett konsol fönster och ange följande kommando:

```console
setx COMMUNICATION_SERVICES_CONNECTION_STRING "<yourconnectionstring>"
```

När du har lagt till miljövariabeln kan du behöva starta om alla program som körs och som behöver läsa in miljövariabeln, däribland konsolfönstret. Om du till exempel använder Visual Studio som redigerings program måste du starta om Visual Studio innan du kör exemplet.

#### <a name="macos"></a>[macOS](#tab/unix)

Redigera din **. zshrc** och Lägg till miljövariabeln:

```bash
export COMMUNICATION_SERVICES_CONNECTION_STRING="<yourconnectionstring>"
```

När du har lagt till miljövariabeln så kör `source ~/.zshrc` från konsolfönstret så att ändringarna träder i kraft. Om du har skapat miljövariabeln med din IDE öppen, kan du behöva stänga och öppna redigeraren, IDE eller Shell igen för att få åtkomst till variabeln.

#### <a name="linux"></a>[Linux](#tab/linux)

Redigera **.bash_profile** och Lägg till miljövariabeln:

```bash
export COMMUNICATION_SERVICES_CONNECTION_STRING="<yourconnectionstring>"
```

När du har lagt till miljövariabeln så kör `source ~/.bash_profile` från konsolfönstret så att ändringarna träder i kraft. Om du har skapat miljövariabeln med din IDE öppen, kan du behöva stänga och öppna redigeraren, IDE eller Shell igen för att få åtkomst till variabeln.

---

## <a name="clean-up-resources"></a>Rensa resurser

Om du vill rensa och ta bort en kommunikations tjänst prenumeration kan du ta bort resursen eller resurs gruppen. Om du tar bort resurs gruppen raderas även andra resurser som är kopplade till den.

Om du har ett telefonnummer som är tilldelat till resursen när resursen tas bort, släpps telefonnumret från din resurs automatiskt på samma gång. 

## <a name="next-steps"></a>Nästa steg

I den här snabb starten har du lärt dig att:

> [!div class="checklist"]
> * Skapa en Communication Services-resurs
> * Konfigurera geografi och taggar för resurs
> * Åtkomst till nycklarna för den resursen
> * Ta bort resursen

> [!div class="nextstepaction"]
> [Skapa dina första åtkomsttoken för användare](access-tokens.md)