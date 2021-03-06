---
title: Azure snabb start – ange och hämta en nyckel från Key Vault med Azure Portal | Microsoft Docs
description: Snabb start visar hur du ställer in och hämtar en nyckel från Azure Key Vault med hjälp av Azure Portal
services: key-vault
author: msmbaldwin
manager: rkarlin
tags: azure-resource-manager
ms.service: key-vault
ms.subservice: keys
ms.topic: quickstart
ms.custom: mvc
ms.date: 03/24/2020
ms.author: mbaldwin
ms.openlocfilehash: 419fe72d400177ce9fa3d9811d7dfa06e74c0810
ms.sourcegitcommit: 2aa52d30e7b733616d6d92633436e499fbe8b069
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2021
ms.locfileid: "97935061"
---
# <a name="quickstart-set-and-retrieve-a-key-from-azure-key-vault-using-the-azure-portal"></a>Snabb start: Ange och hämta en nyckel från Azure Key Vault med hjälp av Azure Portal

Azure Key Vault är en molntjänst som tillhandahåller ett säkert lager för hemligheter. Du kan på ett säkert sätt lagra nycklar, lösenord, certifikat och andra hemligheter. Du kan skapa och hantera Azure-nyckelvalv via Azure Portal. I den här snabb starten skapar du ett nyckel valv och använder det för att lagra en nyckel. Mer information om nyckelvalv finns i [översikten](../general/overview.md).

Om du inte har någon Azure-prenumeration kan du skapa ett [kostnadsfritt konto](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) innan du börjar.

## <a name="sign-in-to-azure"></a>Logga in på Azure

Logga in på Azure Portal på https://portal.azure.com.

## <a name="create-a-vault"></a>Skapa ett valv

1. På Azure Portal-menyn eller på **Start** sidan väljer du **skapa en resurs**.
2. I rutan Sök anger du **Key Vault**.
3. Välj **Key Vault** i listan med resultat.
4. Välj **Skapa** i avsnittet Key Vault.
5. Ange följande information i avsnittet **Skapa nyckelvalv** avsnittet Ange följande information:
    - **Namn**: Ett unikt namn krävs. I den här snabb starten använder vi **exempel-valv**. 
    - **Prenumeration**: Välj en prenumeration.
    - Under **resurs grupp** väljer du **Skapa ny** och anger ett resurs grupp namn.
    - Välj en plats i listrutan **Plats**.
    - Lämna standardvärdena för de andra alternativen.
6. När du har angett den här informationen väljer du **Skapa**.

Anteckna de två egenskaperna som visas nedan:

* **Valv namn**: i exemplet är detta **exempel-valv**. Du kommer att använda det här namnet i senare steg.
* **Valvets URI**: I det här exemplet är det https://example-vault.vault.azure.net/. Program som använder ditt valv via dess REST-API måste använda denna URI.

Nu är ditt Azure-konto det enda kontot med behörighet att utföra åtgärder i det nya valvet.

![Utdata när nyckelvalvet har skapats](../media/keys/quick-create-portal/vault-properties.png)

## <a name="add-a-key-to-key-vault"></a>Lägg till en nyckel i Key Vault

Om du vill lägga till en nyckel i valvet behöver du bara göra några ytterligare steg. I det här fallet lägger vi till en nyckel som kan användas av ett program. Nyckeln kallas **ExampleKey**.

1. På sidan Key Vault egenskaper väljer du **nycklar**.
2. Klicka på **Generera/importera**.
3. På skärmen **skapa en nyckel** väljer du följande värden:
    - **Alternativ**: skapa.
    - **Namn**: ExampleKey.
    - Lämna standardvärdena för de andra alternativen. Klicka på **Skapa**.

När du har fått ett meddelande om att nyckeln har skapats kan du klicka på den i listan. Du ser då vissa av egenskaperna. Om du klickar på den aktuella versionen så kan du se värdet du angav i föregående steg.

![Nyckelegenskaper](../media/keys/quick-create-portal/current-version-hidden.png)


## <a name="clean-up-resources"></a>Rensa resurser

Andra snabbstarter och självstudier om Key Vault bygger på den här snabbstarten. Om du planerar att fortsätta med efterföljande snabbstarter och självstudier kan du lämna kvar de här resurserna.
När du inte behöver resursgruppen längre så tar du bort den. Då tas även nyckelvalvet och relaterade resurser bort. Så här tar du bort resursgruppen via portalen:

1. Skriv namnet på resursgruppen i rutan Sök längst upp i portalen. När du ser resursgruppen du använde i den här snabbstarten bland sökresultaten väljer du den.
2. Välj **Ta bort resursgrupp**.
3. I rutan **SKRIV RESURSGRUPPSNAMNET:** skriver du namnet på resursgruppen och väljer **Ta bort**.


## <a name="next-steps"></a>Nästa steg

I den här snabb starten skapade du en Key Vault och sparade en nyckel i den. Om du vill veta mer om Key Vault och hur du integrerar den med dina program, Fortsätt till artiklarna nedan.

- Läs en [Översikt över Azure Key Vault](../general/overview.md)
- Se [Azure Key Vault Developer ' s guide](../general/developers-guide.md)
- Granska [Key Vault säkerhets översikt](../general/security-overview.md)