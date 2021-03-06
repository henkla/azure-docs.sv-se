---
title: 'Självstudie: Azure Active Directory enkel inloggning (SSO) med loop-flöde CRM | Microsoft Docs'
description: Lär dig hur du konfigurerar enkel inloggning mellan Azure Active Directory och loop-flöde i CRM.
services: active-directory
author: jeevansd
manager: CelesteDG
ms.reviewer: CelesteDG
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.topic: tutorial
ms.date: 09/24/2020
ms.author: jeedes
ms.openlocfilehash: eccc10cc50bac2eb2dde0bf9f77ab1ba656d5eb8
ms.sourcegitcommit: 9b8425300745ffe8d9b7fbe3c04199550d30e003
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/23/2020
ms.locfileid: "92458376"
---
# <a name="tutorial-azure-active-directory-single-sign-on-sso-integration-with-loop-flow-crm"></a>Självstudie: Azure Active Directory enkel inloggning (SSO) med loop-flöde CRM

I den här självstudien får du lära dig hur du integrerar loop-flöden i CRM med Azure Active Directory (Azure AD). När du integrerar loop-flödet CRM med Azure AD kan du:

* Kontroll i Azure AD som har åtkomst till loop-flöde CRM.
* Gör det möjligt för användarna att bli inloggade automatiskt så att de kan använda Azure AD-konton automatiskt.
* Hantera dina konton på en central plats – Azure Portal.

## <a name="prerequisites"></a>Förutsättningar

För att komma igång behöver du följande objekt:

* En Azure AD-prenumeration. Om du inte har någon prenumeration kan du få ett [kostnads fritt konto](https://azure.microsoft.com/free/).
* Loopback Flow-prenumeration med enkel inloggning (SSO) i CRM.

## <a name="scenario-description"></a>Scenariobeskrivning

I den här självstudien konfigurerar och testar du Azure AD SSO i en test miljö.

* Loop-flöde CRM stöder **SP-och IDP** -INITIERAd SSO

## <a name="adding-loop-flow-crm-from-the-gallery"></a>Lägga till loop Flow CRM från galleriet

Om du vill konfigurera integreringen av loop-flödet i Azure AD måste du lägga till loop-flödet CRM från galleriet till listan över hanterade SaaS-appar.

1. Logga in på Azure Portal med antingen ett arbets-eller skol konto eller en personlig Microsoft-konto.
1. I det vänstra navigerings fönstret väljer du tjänsten **Azure Active Directory** .
1. Navigera till **företags program** och välj sedan **alla program**.
1. Välj **nytt program**om du vill lägga till ett nytt program.
1. I avsnittet **Lägg till från Galleri** skriver du **loop-flöde CRM** i rutan Sök.
1. Välj **loop-flöde CRM** från resultat panelen och Lägg sedan till appen. Vänta några sekunder medan appen läggs till i din klient organisation.


## <a name="configure-and-test-azure-ad-sso-for-loop-flow-crm"></a>Konfigurera och testa Azure AD SSO för loop-flöde CRM

Konfigurera och testa Azure AD SSO med loop-flöde CRM med en test användare som heter **B. Simon**. För att SSO ska fungera måste du upprätta en länk relation mellan en Azure AD-användare och den relaterade användaren i loop Flow CRM.

Utför följande steg för att konfigurera och testa Azure AD SSO med loop-flöde CRM:

1. **[Konfigurera Azure AD SSO](#configure-azure-ad-sso)** – så att användarna kan använda den här funktionen.
    1. **[Skapa en Azure AD-test](#create-an-azure-ad-test-user)** för att testa enkel inloggning med Azure AD med B. Simon.
    1. **[Tilldela Azure AD-testuser](#assign-the-azure-ad-test-user)** -för att aktivera B. Simon för att använda enkel inloggning med Azure AD.
1. **[Konfigurera loop-flöde CRM SSO](#configure-loop-flow-crm-sso)** – för att konfigurera inställningarna för enkel inloggning på program sidan.
    1. **[Skapa loop-flöde CRM-testanvändare](#create-loop-flow-crm-test-user)** – för att få en motsvarighet till B. Simon i loop-flöde CRM som är länkat till Azure AD-representation av användare.
1. **[Testa SSO](#test-sso)** – för att kontrol lera om konfigurationen fungerar.

## <a name="configure-azure-ad-sso"></a>Konfigurera Azure AD SSO

Följ de här stegen för att aktivera Azure AD SSO i Azure Portal.

1. I Azure Portal går du till sidan för körning av CRM-programintegration i **loopen** och letar upp avsnittet **Hantera** och väljer **enkel inloggning**.
1. På sidan **Välj metod för enkel inloggning** väljer du **SAML**.
1. På sidan **Konfigurera enkel inloggning med SAML** klickar du på ikonen Redigera/penna för **grundläggande SAML-konfiguration** för att redigera inställningarna.

   ![Redigera grundläggande SAML-konfiguration](common/edit-urls.png)

1. I avsnittet **grundläggande SAML-konfiguration** , om du vill konfigurera programmet i **IDP** initierat läge, anger du värdena för följande fält:

    a. I text rutan **identifierare** anger du en URL med hjälp av följande mönster: `https://<CUSTOMER_NAME>.loopworks.com`

    b. Skriv en URL i text rutan **svars-URL** med följande mönster: `https://<CUSTOMER_NAME>.loopworks.com/sso/consume/<CUSTOMER_NAME>`

1. Klicka på **Ange ytterligare URL:er** och gör följande om du vill konfigurera appen i **SP**-initierat läge:

    I text rutan **inloggnings-URL** skriver du en URL med följande mönster:  `https://<CUSTOMER_NAME>.loopworks.com/sso/<CUSTOMER_NAME>`

    > [!NOTE]
    > Dessa värden är inte verkliga. Uppdatera värdena med den faktiska identifieraren, svars-URL och inloggnings-URL. Kontakta [loopback Flow-support teamet för CRM-klienten](mailto:support@loopworks.com) för att hämta dessa värden. Du kan även se mönstren som visas i avsnittet **Grundläggande SAML-konfiguration** i Azure-portalen.

1. På sidan **Konfigurera enkel inloggning med SAML** , i avsnittet **SAML-signeringscertifikat** , klickar du på Kopiera för att kopiera **URL: en för appens Federations-metadata** och spara den på din dator.

    ![Länk för nedladdning av certifikatet](common/copy-metadataurl.png)
### <a name="create-an-azure-ad-test-user"></a>Skapa en Azure AD-testanvändare

I det här avsnittet ska du skapa en test användare i Azure Portal som kallas B. Simon.

1. I den vänstra rutan i Azure Portal väljer du **Azure Active Directory**, väljer **användare**och väljer sedan **alla användare**.
1. Välj **ny användare** överst på skärmen.
1. I **användar** egenskaperna följer du de här stegen:
   1. I **Namn**-fältet skriver du `B.Simon`.  
   1. I fältet **användar namn** anger du username@companydomain.extension . Till exempel `B.Simon@contoso.com`.
   1. Markera kryssrutan **Visa lösenord** och skriv sedan ned det värde som visas i rutan **Lösenord**.
   1. Klicka på **Skapa**.

### <a name="assign-the-azure-ad-test-user"></a>Tilldela Azure AD-testanvändaren

I det här avsnittet ska du aktivera B. Simon för att använda enkel inloggning med Azure genom att bevilja åtkomst till loop-flöde CRM.

1. I Azure Portal väljer du **företags program**och väljer sedan **alla program**.
1. I listan program väljer du **loop-flöde CRM**.
1. På sidan Översikt för appen letar du reda på avsnittet **Hantera** och väljer **användare och grupper**.
1. Välj **Lägg till användare**och välj sedan **användare och grupper** i dialog rutan **Lägg till tilldelning** .
1. I dialog rutan **användare och grupper** väljer du **B. Simon** från listan användare och klickar sedan på knappen **Välj** längst ned på skärmen.
1. Om du förväntar dig att en roll ska tilldelas användarna kan du välja den från List rutan **Välj en roll** . Om ingen roll har kon figurer ATS för den här appen ser du rollen "standard åtkomst" vald.
1. Klicka på knappen **tilldela** i dialog rutan **Lägg till tilldelning** .

## <a name="configure-loop-flow-crm-sso"></a>Konfigurera loop-flöde CRM SSO

Om du vill konfigurera enkel inloggning på **loopback Flow CRM** -sidan måste du skicka **URL: en för appens Federations-metadata** till [support teamet för loopback Flow](mailto:support@loopworks.com). De anger inställningen så att SAML SSO-anslutningen ställs in korrekt på båda sidorna.

### <a name="create-loop-flow-crm-test-user"></a>Skapa loop-flöde CRM-test användare

I det här avsnittet ska du skapa en användare med namnet Britta Simon i loop Flow CRM. Arbeta med [support teamet för loop Flow](mailto:support@loopworks.com) för att lägga till användare i slingan FLOWs CRM-plattformen. Användare måste skapas och aktiveras innan du använder enkel inloggning.

## <a name="test-sso"></a>Testa SSO 

I det här avsnittet ska du testa Azure AD-konfigurationen för enkel inloggning med följande alternativ. 

#### <a name="sp-initiated"></a>SP initierad:

* Klicka på **testa det här programmet** i Azure Portal. Detta omdirigeras till loopback Flow CRM-inloggnings-URL där du kan starta inloggnings flödet.  

* Gå till loopback Flow CRM-inloggnings-URL: en direkt och starta inloggnings flödet därifrån.

#### <a name="idp-initiated"></a>IDP initierad:

* Klicka på **testa det här programmet** i Azure Portal så bör du loggas in automatiskt till det loop-flöde som du ställer in SSO för. 

Du kan också använda Microsoft Access-panelen för att testa programmet i vilket läge som helst. När du klickar på panelen för loopback Flow-fönstret i åtkomst panelen, om det kon figurer ATS i SP-läge, kommer du att omdirigeras till programmets inloggnings sida för att initiera inloggnings flödet och om det kon figurer ATS i IDP-läge, bör du logga in automatiskt på det loop-flöde i CRM som du ställer in SSO för. Mer information om åtkomstpanelen finns i [introduktionen till åtkomstpanelen](../user-help/my-apps-portal-end-user-access.md).


## <a name="next-steps"></a>Nästa steg

När du har konfigurerat loop-flöde CRM kan du genomdriva session Control, som skyddar exfiltrering och intrånget för organisationens känsliga data i real tid. Kontroll av sessionen sträcker sig från villkorlig åtkomst. [Lär dig hur du tvingar fram en session med Microsoft Cloud App Security](/cloud-app-security/proxy-deployment-any-app).