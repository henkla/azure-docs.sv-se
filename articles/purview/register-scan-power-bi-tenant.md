---
title: Registrera och skanna en Power BI klient (förhands granskning)
description: Lär dig hur du använder Azure avdelningens kontroll-portalen för att registrera och skanna en Power BI klient.
author: chanuengg
ms.author: csugunan
ms.service: purview
ms.subservice: purview-data-catalog
ms.topic: how-to
ms.date: 11/19/2020
ms.openlocfilehash: 3370215e9a69e62596f214ba4330fc4914a2837f
ms.sourcegitcommit: fc23b4c625f0b26d14a5a6433e8b7b6fb42d868b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2021
ms.locfileid: "98539695"
---
# <a name="register-and-scan-a-power-bi-tenant-preview"></a>Registrera och skanna en Power BI klient (förhands granskning)

Den här artikeln visar hur du använder Azure avdelningens kontroll-portalen för att registrera och skanna en Power BI klient.

> [!Note]
> Om avdelningens kontroll-instansen och Power BI klienten finns i samma Azure-klient kan du bara använda autentisering med hanterad identitet (MSI) för att konfigurera en genomsökning av en Power BI klient. 

## <a name="create-a-security-group-for-permissions"></a>Skapa en säkerhets grupp för behörigheter

Om du vill konfigurera autentisering skapar du en säkerhets grupp och lägger till katalogens hanterade identitet i den.

1. Sök efter **Azure Active Directory** i [Azure Portal](https://portal.azure.com).
1. Skapa en ny säkerhets grupp i Azure Active Directory genom att följa [skapa en grundläggande grupp och lägga till medlemmar med Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal).

    > [!Tip]
    > Du kan hoppa över det här steget om du redan har en säkerhets grupp som du vill använda.

1. Välj **säkerhet** som **grupptyp**.

    :::image type="content" source="./media/setup-power-bi-scan-PowerShell/security-group.png" alt-text="Typ av säkerhets grupp":::

1. Lägg till din katalogs hanterade identitet i den här säkerhets gruppen. Välj **medlemmar** och välj sedan **+ Lägg till medlemmar**.

    :::image type="content" source="./media/setup-power-bi-scan-PowerShell/add-group-member.png" alt-text="Lägg till katalogens hanterade instans i gruppen.":::

1. Sök efter din katalog och markera den.

    :::image type="content" source="./media/setup-power-bi-scan-PowerShell/add-catalog-to-group-by-search.png" alt-text="Lägg till katalog genom att söka efter den":::

    Du bör se ett meddelande som visar att det har lagts till.

    :::image type="content" source="./media/setup-power-bi-scan-PowerShell/success-add-catalog-msi.png" alt-text="Tillägget av katalog-MSI lyckades":::

## <a name="associate-the-security-group-with-the-tenant"></a>Associera säkerhets gruppen med klienten

1. Logga in på [Power BI admin-portalen](https://app.powerbi.com/admin-portal/tenantSettings).
1. Välj sidan **klient inställningar** .

    > [!Important]
    > Du måste vara Power BI administratör för att se sidan klient inställningar.

1. Välj **admin API**  >  **-Inställningar Tillåt att tjänstens huvud namn använder skrivskyddade Power BI administrations-API: er (för hands version)**.
1. Välj **vissa säkerhets grupper**.

    :::image type="content" source="./media/setup-power-bi-scan-PowerShell/allow-service-principals-power-bi-admin.png" alt-text="Bild som visar hur du tillåter tjänstens huvud namn för att få skrivskyddade Power BI administrations-API-behörigheter":::

    > [!Caution]
    > När du tillåter säkerhets gruppen som du skapade (som har din hanterade identitet för data katalogen som medlem) att använda skrivskyddade Power BI administrations-API: er kan du också få åtkomst till metadata (t. ex. instrument panel och rapport namn, ägare, beskrivningar osv.) för alla dina Power BI artefakter i den här klienten. När metadata har hämtats till Azure-avdelningens kontroll, avdelningens kontroll-behörigheter, inte Power BI behörigheter, avgör vem som kan se dessa metadata.

    > [!Note]
    > Du kan ta bort säkerhets gruppen från dina inställningar för utvecklare, men de metadata som tidigare extraheras tas inte bort från avdelningens kontroll-kontot. Du kan ta bort den separat, om du vill.

## <a name="register-your-power-bi-and-set-up-a-scan"></a>Registrera din Power BI och konfigurera en sökning

Nu när du har gett katalog behörighet att ansluta till administrations-API: t för din Power BI-klient kan du konfigurera din genomsökning från katalog portalen.

Lägg först till en särskild funktions flagga till din avdelningens kontroll-URL 

1. Välj ikonen för **hanterings Center** .

    :::image type="content" source="media/setup-power-bi-scan-catalog-portal/management-center.png" alt-text="Ikonen för hanterings Center.":::

1. Välj sedan **+ ny** på **data källor**.

    :::image type="content" source="media/setup-power-bi-scan-catalog-portal/data-sources.png" alt-text="Bild av knappen ny data Källa":::

    Välj **Power BI** som data källa.

    :::image type="content" source="media/setup-power-bi-scan-catalog-portal/select-power-bi-data-source.png" alt-text="Bild som visar en lista över data källor som kan väljas":::

1. Ge Power BI instansen ett eget namn.

    :::image type="content" source="media/setup-power-bi-scan-catalog-portal/power-bi-friendly-name.png" alt-text="Bild som visar Power BI data källa – eget namn":::

    Namnet måste vara mellan 3-63 tecken långt och får bara innehålla bokstäver, siffror, under streck och bindestreck.  Blank steg är inte tillåtna.

    Som standard hittar systemet Power BI klient som finns i samma Azure-prenumeration.

    :::image type="content" source="media/setup-power-bi-scan-catalog-portal/power-bi-datasource-registered.png" alt-text="Power BI data källa registrerad":::

1. Ge skanningen ett namn. Observera att den enda autentiseringsmetoden som stöds är **hanterad identitet**.

    :::image type="content" source="media/setup-power-bi-scan-catalog-portal/power-bi-scan-setup.png" alt-text="Bild som visar Power BI skannings konfiguration":::

    Skannings namnet måste innehålla mellan 3-63 tecken och får bara innehålla bokstäver, siffror, under streck och bindestreck.  Blank steg är inte tillåtna.

1. Konfigurera en genomsöknings utlösare. Dina alternativ är **en gång**, **var sjunde dag** och **var 30: e dag**.

    :::image type="content" source="media/setup-power-bi-scan-catalog-portal/scan-trigger.png" alt-text="Skanna utlösare avbildning":::

1. Vid **Granska ny genomsökning** väljer du **Spara och kör** för att starta din sökning.

    :::image type="content" source="media/setup-power-bi-scan-catalog-portal/save-run-power-bi-scan.png" alt-text="Spara och kör Power BI skärm bild":::

## <a name="next-steps"></a>Nästa steg

- [Bläddra i Azure avdelningens kontroll Data Catalog](how-to-browse-catalog.md)
- [Sök i Azure avdelningens kontroll-Data Catalog](how-to-search-catalog.md)