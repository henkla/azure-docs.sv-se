---
title: Lägg till anpassade attribut till självbetjänings registrerings flöden – Azure AD
description: Läs om hur du anpassar attributen för dina självbetjänings registrerings användar flöden.
services: active-directory
author: msmimart
manager: celestedg
ms.service: active-directory
ms.subservice: B2B
ms.topic: how-to
ms.date: 06/16/2020
ms.author: mimart
ms.custom: it-pro
ms.collection: M365-identity-device-management
ms.openlocfilehash: e64ab70fed13d4ca907b2bfb3aa448acdedc39e9
ms.sourcegitcommit: 9b8425300745ffe8d9b7fbe3c04199550d30e003
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/23/2020
ms.locfileid: "92441461"
---
# <a name="define-custom-attributes-for-user-flows-preview"></a>Definiera anpassade attribut för användar flöden (förhands granskning)

> [!NOTE]
> Funktionen för anpassade användarattribut är en offentlig förhands gransknings funktion i Azure Active Directory. Mer information om för hands versionerna finns i kompletterande användnings [villkor för Microsoft Azure för hands](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)versionerna.

För varje program kan du ha olika krav för den information som du vill samla in under registreringen. Azure AD levereras med en inbyggd uppsättning information som lagras i attribut, till exempel namn, efter namn, stad och post nummer. Med Azure AD kan du utöka uppsättningen med attribut som lagras på ett gäst konto när den externa användaren loggar in via ett användar flöde.

Du kan skapa anpassade attribut i Azure Portal och använda dem i dina användar flöden för självbetjänings registrering. Du kan också läsa och skriva attributen med hjälp av [Microsoft Graph-API: et](../../active-directory-b2c/manage-user-accounts-graph-api.md). Microsoft Graph API har stöd för att skapa och uppdatera en användare med attribut för tillägg. Attribut för tillägg i Graph API namnges med hjälp av konventionen `extension_<extensions-app-id>_attributename` . Exempel:

```JSON
"extension_831374b3bd5041bfaa54263ec9e050fc_loyaltyNumber": "212342"
```

`<extensions-app-id>`Är unik för din klient. Du hittar den här identifieraren genom att gå till Azure Active Directory > Appregistreringar > alla program. Sök efter appen som börjar med "AAD-Extensions-app" och markera den. Notera program-ID (klient) på appens översikts sida.

## <a name="create-a-custom-attribute"></a>Skapa ett anpassat attribut

1. Logga in till [Azure-portalen](https://portal.azure.com) som Azure AD-administratör.
2. Under **Azure-tjänster**väljer du **Azure Active Directory**.
3. På den vänstra menyn väljer du **externa identiteter**.
4. Välj **anpassade användarattribut (förhands granskning)**. De tillgängliga användarattribut visas.

   ![Välj användarattribut för registrering](media/user-flow-add-custom-attributes/user-attributes.png)

5. Välj **Lägg**till om du vill lägga till ett attribut.
6. Ange följande värden i fönstret **Lägg till ett attribut** :

   - **Namn** – ange ett namn för det anpassade attributet (till exempel "Shoesize").
   - **Datatyp** – Välj en datatyp (**sträng**, **boolesk**eller **int**).
   - **Beskrivning** – alternativt anger du en beskrivning av det anpassade attributet för intern användning. Den här beskrivningen visas inte för användaren.

   ![Lägg till ett attribut](media/user-flow-add-custom-attributes/add-an-attribute.png)

7. Välj **Skapa**.

Det anpassade attributet är nu tillgängligt i listan över användarattribut och för användning i dina användar flöden. Ett anpassat attribut skapas bara första gången det används i alla användar flöden och inte när du lägger till det i listan med användarattribut.

När du har skapat en ny användare med ett användar flöde som använder det nya anpassade attributet, kan du frågas om objektet i [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer). Nu bör du se **ShoeSize** i listan över attribut som samlats in under registreringen av användaren på användarobjektet. Du kan anropa Graph API från ditt program för att hämta data från det här attributet när det har lagts till i objektet User.

## <a name="next-steps"></a>Nästa steg

[Lägga till ett användar flöde för självbetjänings registrering i en app](self-service-sign-up-user-flow.md)