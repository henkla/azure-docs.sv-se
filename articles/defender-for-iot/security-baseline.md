---
title: Azures säkerhets bas linje för Azure Defender för IoT
description: Säkerhets bas linjen för Azure Defender för IoT ger procedur vägledning och resurser för att implementera de säkerhets rekommendationer som anges i Azures säkerhets benchmark.
author: msmbaldwin
ms.service: defender-for-iot
ms.topic: conceptual
ms.date: 11/19/2020
ms.author: mbaldwin
ms.custom: subject-security-benchmark
ms.openlocfilehash: 6fbd70c1de99818e2baf73d15ed365db3a54e43d
ms.sourcegitcommit: 08458f722d77b273fbb6b24a0a7476a5ac8b22e0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2021
ms.locfileid: "98246731"
---
# <a name="azure-security-baseline-for-azure-defender-for-iot"></a>Azures säkerhets bas linje för Azure Defender för IoT

Den här säkerhets bas linjen använder vägledning från [Azures säkerhets benchmark-version 2,0](../security/benchmarks/overview.md) till Microsoft Azure Defender för IoT. Azure Security Benchmark ger rekommendationer om hur du kan skydda dina molnlösningar i Azure. Innehållet grupperas efter **säkerhets kontrollerna** som definieras av Azures säkerhets benchmark och relaterade rikt linjer som gäller för Azure Defender för IoT. **Kontroller** som inte är tillämpliga på Azure Defender för IoT har uteslutits.

Om du vill se hur Azure Defender för IoT fullständigt mappar till Azures säkerhets benchmark, se den [fullständiga mappnings filen för Azure Defender för IoT-säkerhet](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines).

## <a name="identity-management"></a>Identitetshantering

*Mer information finns i [Azure Security Benchmark: Identitetshantering](../security/benchmarks/security-controls-v2-identity-management.md).*

### <a name="im-1-standardize-azure-active-directory-as-the-central-identity-and-authentication-system"></a>IM-1: Standardisera Azure Active Directory som centralt system för identiteter och autentisering

**Vägledning**: Azure Defender för IoT är integrerat med Azure Active Directory (Azure AD), Azures standard tjänst för identitets-och åtkomst hantering. Du bör standardisera Azure AD för att styra organisationens identitets-och åtkomst hantering i:

- Microsoft Cloud resurser, till exempel Azure Portal, Azure Storage, virtuell Azure-dator (Linux och Windows), Azure Key Vault, PaaS och SaaS program.

- Organisationens resurser, till exempel program i Azure eller företagets nätverksresurser.

Skyddet av Azure AD bör ha hög prioritet i organisationens säkerhetspraxis för molnet. Azure AD ger dig en identitetsskyddspoäng som hjälper dig att utvärdera identiteternas säkerhet i relation till Microsofts rekommendationer kring regelverk. Använd poängen till att mäta hur nära konfigurationen matchar rekommendationerna kring regelverk och förbättra säkerhetsläget.

Azure AD stöder extern identitet som gör det möjligt för användare utan Microsoft-konto att logga in på sina program och resurser med sin externa identitet.

- [Klientorganisation i Azure Active Directory](../active-directory/develop/single-and-multi-tenant-apps.md) 

- [Skapa och konfigurera en Azure AD-instans](../active-directory/fundamentals/active-directory-access-create-new-tenant.md) 

- [Använda en extern identitetsprovider för appar](../active-directory/external-identities/identity-providers.md) 

- [Vad är identitetsskyddspoängen i Azure Active Directory](../active-directory/fundamentals/identity-secure-score.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="im-3-use-azure-ad-single-sign-on-sso-for-application-access"></a>IM-3: Använd enkel inloggning i Azure AD (SSO) för åtkomst till appar

**Vägledning**: Azure Defender för IoT använder Azure Active Directory för att tillhandahålla identitets-och åtkomst hantering för Azure-resurser, moln program och lokala program. I det här ingår företagsidentiteter som anställda samt externa identiteter som partner, och leverantörer. På så sätt kan enkel inloggning (SSO) hantera och skydda åtkomsten till organisationens data och resurser både lokalt och i molnet. Anslut alla användare, appar och enheter till Azure AD för en smidig och säker åtkomst samt bättre insyn och kontroll.

- [Förstå SSO för appar i Azure AD](../active-directory/manage-apps/what-is-single-sign-on.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="im-4-use-strong-authentication-controls-for-all-azure-active-directory-based-access"></a>IM-4: Använd kraftfulla verifieringskontroller för all Azure Active Directory-baserad åtkomst

**Vägledning**: Azure Defender för IoT använder Azure Active Directory som stöder starka verifierings kontroller med Multi-Factor Authentication (MFA), och starka metoder för lösen ords kryptering.

- Multifaktorautentisering – aktivera MFA i Azure AD och följ rekommendationerna kring hantering av identiteter och åtkomst i Azure Security Center så att du använder de bästa regelverken i din MFA-konfiguration. MFA kan tillämpas för alla användare, vissa användare eller på användarnivå baserat på inloggningsförhållanden och riskfaktorer.
- Lösen ords kryptering – tre alternativ för lösen ords kryptering är tillgängliga: Windows Hello för företag, Microsoft Authenticator app och lokala autentiseringsmetoder som smartkort.

För administratörer och privilegierade användare bör du se till att den högsta nivån för metoden stark autentisering används, följt av lämplig princip för stark autentisering för andra användare.

- [Aktivera MFA i Azure](../active-directory/authentication/howto-mfa-getstarted.md) 

- [Introduktion till alternativ för lösenordsfri autentisering för Azure Active Directory](../active-directory/authentication/concept-authentication-passwordless.md) 

- [Standardprincip för lösenord för Azure AD](../active-directory/authentication/concept-sspr-policy.md#password-policies-that-only-apply-to-cloud-user-accounts)

- [Eliminera felaktiga lösen ord med Azure AD-lösenordsskydd](../active-directory/authentication/concept-password-ban-bad.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="im-5-monitor-and-alert-on-account-anomalies"></a>IM-5: Övervaka och skicka aviseringar vid kontoavvikelser

**Vägledning**: Azure Defender för IoT är integrerat med Azure Active Directory som tillhandahåller följande data Källor:

Inloggningsaktiviteter – Rapporten för inloggningsaktiviteter ger information om användningen av hanterade program och användares inloggningsaktiviteter.

Granskningsloggar – Ger spårbarhet via loggar för alla ändringar som gjorts via olika funktioner i Azure AD. Exempel på granskningsloggar är de resursändringar som görs i Azure AD, som att lägga till eller ta bort användare, appar, grupper, roller och principer.

Riskfyllda inloggningar – En riskfylld inloggning indikerar ett potentiellt inloggningsförsök av någon annan än användarkontots ägare.

Användare som har flaggats för risk – En användare som har flaggats för risk indikerar att ett användarkonto kan ha komprometterats.

Dessa data källor kan integreras med Azure Monitor, Azure Sentinel eller SIEM system från tredje part.

Azure Security Center kan också avisera om vissa misstänkta aktiviteter, till exempel ett högt antal misslyckade autentiseringsförsök eller föråldrade konton i prenumerationen.

Azure Advanced Threat Protection (ATP) är en säkerhetslösning som kan använda Active Directory-signaler för att identifiera, upptäcka och undersöka avancerade hot, komprometterade identiteter och skadliga Insider-åtgärder.

- [Granska aktivitets rapporter i Azure AD](../active-directory/reports-monitoring/concept-audit-logs.md) 

- [Så visar du riskfyllda inloggningar för Azure AD](../active-directory/identity-protection/overview-identity-protection.md) 

- [Så här identifierar du Azure AD-användare som har flaggats för riskfylld aktivitet](../active-directory/identity-protection/overview-identity-protection.md) 

- [Så här övervakar du användarnas identitets- och åtkomstrelaterade aktiviteter i Azure Security Center](../security-center/security-center-identity-access.md) 

- [Aviseringar i skyddsmodulen för hotinformation i Azure Security Center](../security-center/alerts-reference.md) 

- [Så här integrerar du Azures aktivitetsloggar i Azure Monitor](../active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

## <a name="privileged-access"></a>Privilegierad åtkomst

*Mer information finns i [Azure Security Benchmark: Privilegierad åtkomst](../security/benchmarks/security-controls-v2-privileged-access.md).*

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2: Begränsa administrativ åtkomst till affärskritiska system

**Vägledning**: Azure Defender för IoT använder Azure RBAC för att isolera åtkomst till affärs kritiska system genom att begränsa vilka konton som har privilegie rad åtkomst till de prenumerationer och hanterings grupper som de finns i.

Se till att du också begränsar åtkomsten till hanterings-, identitets-och säkerhets system som har administrativ åtkomst till din affärs kritiska åtkomst, till exempel Active Directory-domän controllers (DCs), säkerhets verktyg och system hanterings verktyg med agenter som är installerade på affärs kritiska system. Angripare som angriper dessa hanterings-och säkerhets system kan omedelbart weaponize dem för att kompromettera affärs kritiska till gångar.

Alla typer av åtkomst kontroller bör justeras mot din strategi för företags segmentering för att säkerställa en konsekvent åtkomst kontroll.

- [Azure-komponenter och referens modell](/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151) 

- [Åtkomst till hanterings grupp](../governance/management-groups/overview.md#management-group-access) 

- [Administratörer för Azure-prenumeration](../cost-management-billing/manage/add-change-subscription-administrator.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="pa-4-set-up-emergency-access-in-azure-ad"></a>PA-4: Konfigurera nödåtkomst i Azure AD

**Vägledning**: Azure Defender för IoT är integrerat med Azure Active Directory för att hantera sina resurser. För att förhindra oavsiktligt låst av din Azure AD-organisation konfigurerar du ett konto för nöd åtkomst för åtkomst när normala administrativa konton inte kan användas. Konton för nödåtkomst har ofta hög behörighet och bör inte tilldelas till specifika individer. Konton för nödåtkomst är begränsade till nödsituationer där du inte kan använda normala administratörskonton.

Du bör se till att autentiseringsuppgifterna (som lösenord, certifikat eller smartkort) för nödåtkomstkonton är skyddade och bara kända av personer som har behörighet att använda dem i nödfall.

- [Hantera konton för nödåtkomst i Azure AD](../active-directory/roles/security-emergency-access.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="pa-5-automate-entitlement-management"></a>PA-5: automatisera rättighets hantering 

**Vägledning**: Azure Defender för IoT är integrerat med Azure Active Directory för att hantera sina resurser. Använd funktioner för hantering av Azure AD-rättighet för att automatisera åtkomst till begär ande arbets flöden, inklusive åtkomst tilldelningar, recensioner och förfallo datum. Det finns också stöd för godkännande med dubbla eller flera steg.

- [Vad är åtkomst granskningar för Azure AD](../active-directory/governance/access-reviews-overview.md) 

- [Vad är hantering av Azure AD-berättigande](../active-directory/governance/entitlement-management-overview.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="pa-7-follow-just-enough-administration-least-privilege-principle"></a>PA-7: Följ JEA (Just Enough Administration, precis tillräcklig administration) (principen om minsta behörighet) 

**Vägledning**: Azure Defender för IoT är integrerat med rollbaserad åtkomst kontroll (RBAC) i Azure för att hantera dess resurser. Med Azure RBAC kan du hantera åtkomst till Azure-resurser via rolltilldelningar. Du kan tilldela dessa roller till användare, grupper tjänstens huvud namn och hanterade identiteter. Det finns fördefinierade inbyggda roller för vissa resurser och dessa roller kan inventeras eller frågas via verktyg som Azure CLI, Azure PowerShell eller Azure-portalen. De behörigheter som du tilldelar resurser via Azure RBAC bör alltid vara begränsade till vad som krävs av rollerna. Det här är ett komplement till JIT-metoden (just in time) för Azure AD Privileged Identity Management (PIM) och bör granskas regelbundet.

Använd inbyggda roller för att allokera behörighet och skapa bara en anpassad roll vid behov.

- [Vad är Azure rollbaserad åtkomst kontroll (Azure RBAC)](../role-based-access-control/overview.md) 

- [Så här konfigurerar du RBAC i Azure](../role-based-access-control/role-assignments-portal.md) 

- [Så här använder du identitets- och åtkomstgranskningar i Azure AD](../active-directory/governance/access-reviews-overview.md)

**Azure Security Center-övervakning**: Inte tillämpligt

**Ansvar**: Kund

## <a name="data-protection"></a>Dataskydd

*Mer information finns i [Azure Security Benchmark: Dataskydd](../security/benchmarks/security-controls-v2-data-protection.md).*

### <a name="dp-1-discovery-classify-and-label-sensitive-data"></a>DP-1: Identifiera, klassificera och märk upp känsliga data

**Vägledning**: identifiera, klassificera och märk känsliga data så att du kan utforma lämpliga kontroller för att se till att känslig information lagras, bearbetas och överförs säkert av organisationens teknik system. 

Använd Azure Information Protection (och dess associerade skanningsverktyg) för känslig information i Office-dokument på Azure, lokalt, i Office 365 och på andra platser. 

Du kan använda Azure SQL-Information Protection för att hjälpa till med klassificering och märkning av information som lagras i Azure SQL-databaser.

- [Tagga känslig information med Azure Information Protection](/azure/information-protection/what-is-information-protection) 

- [Så här implementerar du identifiering av Azure SQL-data](../azure-sql/database/data-discovery-and-classification-overview.md)

**Azure Security Center-övervakning**: Inte tillämpligt

**Ansvar**: Kund

### <a name="dp-2-protect-sensitive-data"></a>DP-2: Skydda känsliga data

**Vägledning**: skydda känsliga data genom att begränsa åtkomsten med hjälp av Azure Role-baserad Access Control (Azure RBAC), nätverksbaserade åtkomst kontroller och vissa kontroller i Azure-tjänster (till exempel kryptering i SQL och andra databaser). 

För att säkerställa konsekvent åtkomstkontroll bör alla typer av åtkomstkontroll justeras mot din strategi för företagssegmentering. Strategin för företagssegmentering bör också informeras om platsen för känsliga eller affärskritiska data och system.

När det gäller den underliggande plattformen, som hanteras av Microsoft, behandlar Microsoft allt kundinnehåll som känsligt och skyddar det mot förlust och exponering av kunddata. För att säkerställa att kunddata i Azure alltid är skyddade har Microsoft implementerat vissa standardkontroller och funktioner för dataskydd.

- [Rollbaserad åtkomstkontroll (RBAC) i Azure](../role-based-access-control/overview.md)

- [Förstå skydd av kunddata i Azure](../security/fundamentals/protection-customer-data.md)

**Azure Security Center-övervakning**: Inte tillämpligt

**Ansvar**: Kund

### <a name="dp-4-encrypt-sensitive-information-in-transit"></a>DP-4: Kryptera känslig information under överföring

**Vägledning**: för att komplettera åtkomst kontroller bör data i överföring skyddas mot "out of band"-attacker (t. ex. trafik insamling) som använder kryptering för att säkerställa att angripare inte kan läsa eller ändra data. 

Även om det är valfritt för trafik i privata nätverk, är detta avgörande för trafik på externa och offentliga nätverk. För HTTP-trafik ser du till att alla klienter som ansluter till dina Azure-resurser kan förhandla TLS v 1.2 eller senare. För fjärrhantering använder du SSH (för Linux) eller RDP/TLS (för Windows) i stället för ett okrypterat protokoll. Inaktuella SSL-, TLS-och SSH-versioner och-protokoll och svaga chiffer bör inaktive ras.  

Som standard tillhandahåller Azure kryptering för data i överföring mellan Azures Data Center. 

- [Förstå kryptering i överföring med Azure](../security/fundamentals/encryption-overview.md#encryption-of-data-in-transit)

- [Information om TLS-säkerhet](/security/engineering/solving-tls1-problem)

- [Double Encryption för Azure-data under överföring](../security/fundamentals/double-encryption.md#data-in-transit)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

## <a name="asset-management"></a>Tillgångshantering

*Mer information finns i [Azure Security Benchmark: Tillgångshantering](../security/benchmarks/security-controls-v2-asset-management.md).*

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1: Se till att säkerhetsteamet har insyn i risker för tillgångar

**Riktlinjer**: Se till att säkerhetsteamen beviljas behörigheter för säkerhetsläsare i din Azure-klient och prenumerationer som gör att de kan övervaka säkerhetsrisker med hjälp av Azure Security Center. 

Beroende på hur säkerhetsteamets ansvarsområden är strukturerade kan ansvaret för övervakning av säkerhetsrisker ligga hos en central säkerhetsgrupp eller ett lokalt team. Detta innebär att säkerhetsinsikter och -risker alltid måste samlas centralt inom en organisation. 

Behörigheter för säkerhetsläsare kan tillämpas brett över en hel klientorganisation (rothanteringsgrupp) eller omfattas av hanteringsgrupper eller specifika prenumerationer. 

Ytterligare behörigheter kan krävas för att få insyn i arbets belastningar och tjänster. 

- [Översikt över säkerhetsläsarrollen](../role-based-access-control/built-in-roles.md#security-reader)

- [Översikt över Azure-hanteringsgrupper](../governance/management-groups/overview.md)

**Azure Security Center-övervakning**: Inte tillgänglig för tillfället

**Ansvar**: Kund

### <a name="am-3-use-only-approved-azure-services"></a>AM-3: Använd bara godkända Azure-tjänster

**Vägledning**: Använd Azure policy för att granska och begränsa vilka tjänster som användare kan etablera i din miljö. Använd Azure Resource Graph till att fråga efter och identifiera resurser i prenumerationerna. Du kan också använda Azure Monitor till att skapa regler för att utlösa aviseringar när en icke-godkänd tjänst upptäcks.

- [Konfigurera och hantera Azure Policy](../governance/policy/tutorials/create-and-manage.md)

- [Så här nekar du en speciell resurs typ med Azure Policy](../governance/policy/samples/built-in-policies.md#general)

- [Skapa frågor med Azure Resource Graph Explorer](../governance/resource-graph/first-query-portal.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="am-4-ensure-security-of-asset-lifecycle-management"></a>AM-4: Garantera säker livscykelhantering för tillgångar

**Riktlinjer**: Upprätta eller uppdatera säkerhetsprinciper som kan användas för att hantera processer för livscykelhantering för ändringar med potentiellt stora konsekvenser. Sådana ändringar kan till exempel avse: identitetsleverantörer och åtkomst, datakänslighet, nätverkskonfiguration och tilldelning av administrativa privilegier.

Ta bort Azure-resurser när de inte längre behövs.

- [Ta bort Azure-resursgrupp och resurs](../azure-resource-manager/management/delete-resource-group.md)

**Azure Security Center-övervakning**: Inte tillämpligt

**Ansvar**: Kund

### <a name="am-5-limit-users-ability-to-interact-with-azure-resource-manager"></a>AM-5: begränsa användarnas möjlighet att interagera med Azure Resource Manager

**Vägledning**: Använd villkorlig åtkomst i Azure AD för att begränsa användarnas möjlighet att interagera med Azure Resource Manager genom att konfigurera "blockera åtkomst" för appen "Microsoft Azure hantering".

- [Så här konfigurerar du villkorlig åtkomst för att blockera åtkomst till Azures resurs hanterare](../role-based-access-control/conditional-access-azure-management.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

## <a name="incident-response"></a>Incidenthantering

*Mer information finns i [Azure Security Benchmark: Incidentsvar](../security/benchmarks/security-controls-v2-incident-response.md).*

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1: Förberedelse – uppdatera processen för svar på incidenter i Azure

**Vägledning**: Se till att organisationen har processer för svar på säkerhetsincidenter, att processerna är uppdaterade för Azure och att de tränas regelbundet för att säkerställa beredskapen.

- [Implementera säkerhet i hela företagsmiljön](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Referensguide för incidentsvar](/microsoft-365/downloads/IR-Reference-Guide.pdf)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2: Förberedelse – konfigurera aviseringar vid incidenter

**Vägledning**: Konfigurera kontaktinformation vid säkerhetsincidenter i Azure Security Center. Microsoft använder de här kontaktuppgifterna till att kontakta dig om Microsoft Security Response Center (MSRC) upptäcker obehörig åtkomst till dina data. Det finns även alternativ för att anpassa aviseringar och meddelanden vid incidenter i olika Azure-tjänster baserat på åtgärdsbehovet. 

- [Så här ställer du in säkerhetskontakt i Azure Security Center](../security-center/security-center-provide-security-contact-details.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3: identifiering och analys – skapa incidenter baserat på aviseringar med hög kvalitet 

**Vägledning**: Se till att du har en process för att skapa aviseringar av hög kvalitet och mäta aviseringskvaliteten. På så sätt kan du lära dig av tidigare incidenter och prioritera aviseringar till analytiker så att de inte slösar tid på falska positiva identifieringar. 

Du kan basera aviseringar av hög kvalitet på erfarenheter från tidigare incidenter, validerade community-källor och verktyg som utformats för att skapa och rensa aviseringar genom att sammanfoga och korrelera olika signalkällor. 

Azure Security Center ger aviseringar med hög kvalitet över flera Azure-tillgångar. Du kan använda anslutningsprogrammet för ASC-data för att strömma aviseringarna till Azure Sentinel. Med Azure Sentinel kan du skapa avancerade aviseringsregler för att generera incidenter automatiskt för en undersökning. 

Exportera dina Azure Security Center-aviseringar och -rekommendationer med hjälp av exportfunktionen för att identifiera risker med Azure-resurser. Exportera aviseringar och rekommendationer antingen manuellt eller löpande.

- [Så här konfigurerar du export](../security-center/continuous-export.md)

- [Så här strömmar du aviseringar till Azure Sentinel](../sentinel/connect-azure-security-center.md)

**Azure Security Center-övervakning**: Inte tillgänglig för tillfället

**Ansvar**: Kund

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4: Identifiering och analys – undersöka en incident

**Riktlinjer**: Se till att analytiker kan fråga och använda olika datakällor när de undersöker potentiella incidenter, så att de kan skapa en fullständig överblick över vad som hände. Diverse loggar bör samlas in för att spåra en potentiell angripares aktiviteter över hela händelsekedjan för att undvika att blinda fläckar.  Du bör också se till att insikter och kunskaper fångas upp för andra analytiker och för framtida historiska referenser.  

Datakällorna för undersökningen innehåller de centraliserade loggningskällor som redan har samlats in från tjänster som omfattas och system som körs, men kan även innehålla:

- Nätverksdata – Använd nätverkssäkerhetsgruppers flödesloggar, Azure Network Watcher och Azure Monitor för att avbilda nätverksflödesloggar och annan analysinformation. 

- Ögonblicksbilder av system som körs: 

    - Använd funktionen för ögonblicksbilder på den virtuella Azure-datorn för att skapa en ögonblicksbild av det aktiva systemets disk. 

    - Använd operativsystemets interna minnesdumpningsfunktion för att skapa en ögonblicksbild av det aktiva systemets minne.

    - Använd funktionen för ögonblicksbilder i Azure-tjänsterna eller din programvaras egna funktion för att skapa ögonblicksbilder av de system som körs.

Azure Sentinel tillhandahåller omfattande dataanalyser i praktiskt taget alla loggkällor och en ärendehanteringsportal för att hantera hela livscykeln för incidenter. Affärsinformation under en undersökning kan associeras med en incident för spårning och rapportering. 

- [Ögonblicksbild av en Windows-dators disk](../virtual-machines/windows/snapshot-copy-managed-disk.md)

- [Ögonblicksbild av en Linux-dators disk](../virtual-machines/linux/snapshot-copy-managed-disk.md)

- [Microsoft Azure har stöd för diagnostikinformation och insamling av minnesdumpar](https://azure.microsoft.com/support/legal/support-diagnostic-information-collection/) 

- [Undersöka incidenter med Azure Sentinel](../sentinel/tutorial-investigate-cases.md)

**Azure Security Center-övervakning**: Inte tillämpligt

**Ansvar**: Kund

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5: Identifiering och analys – prioritera incidenter

**Riktlinjer**: Tillhandahålla en kontext till analytiker om vilka incidenter att fokusera på först baserat på aviseringens allvarlighetsgrad och tillgångens känslighet. 

Azure Security Center tilldelar en allvarlighetsgrad till varje avisering för att hjälpa dig att prioritera vilka aviseringar som bör undersökas först. Allvarlighets graden baseras på hur tillförlitlig Security Center befinner sig vid sökning eller analys som används för att utfärda aviseringen, samt den konfidensnivå som det fanns skadlig avsikt bakom den aktivitet som ledde till aviseringen.

Markera även resurser med taggar och skapa ett namngivningssystem för att identifiera och kategorisera Azure-resurser, i synnerhet sådana som används för bearbetning av känsliga data.  Det är ditt ansvar att prioritera åtgärdandet av aviseringar baserat på allvarlighetsgraden för de Azure-resurser och den miljö där incidenten inträffade.

- [Säkerhetsaviseringar i Azure Security Center](../security-center/security-center-alerts-overview.md)

- [Använda taggar för att organisera dina Azure-resurser](../azure-resource-manager/management/tag-resources.md)

**Azure Security Center-övervakning**: Inte tillgänglig för tillfället

**Ansvar**: Kund

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6: Inneslutning, utrotning och återställning – automatisera hanteringen av incidenter

**Vägledning**: Automatisera manuella återkommande uppgifter för att korta ned svarstiderna och underlätta för analytikerna. Det tar längre tid att köra uppgifter manuellt, så att varje incident tar längre tid att hantera och analytikerna hinner med färre incidenter. Manuella uppgifter gör dessutom analytikern mer utmattad, vilket ökar risken för mänskliga fel som i sin tur orsakar fördröjningar, samt minskar analytikernas förmåga att fokusera på komplexa uppgifter på ett effektivt sätt. Använd automatiseringsfunktioner för arbetsflöde i Azure Security Center och Azure Sentinel för att automatiskt utlösa åtgärder eller köra en spelbok för att svara på inkommande säkerhetsaviseringar. Spelboken vidtar åtgärder som att skicka meddelanden, inaktivera konton och isolera problematiska nätverk. 

- [Konfigurera arbetsflödesautomation i Security Center](../security-center/workflow-automation.md)

- [Konfigurera automatiska svar på hot i Azure Security Center](../security-center/tutorial-security-incident.md#triage-security-alerts)

- [Konfigurera automatiska svar på hot i Azure Sentinel](../sentinel/tutorial-respond-threats-playbook.md)

**Azure Security Center-övervakning**: Inte tillgänglig för tillfället

**Ansvar**: Kund

## <a name="posture-and-vulnerability-management"></a>Hantering av säkerhetsposition och säkerhetsrisker

*Mer information finns i [Azure Security Benchmark: Hantering av säkerhetsposition och säkerhetsrisker](../security/benchmarks/security-controls-v2-posture-vulnerability-management.md).*

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8: Utför regelbundna angreppssimuleringar

**Vägledning**: Utför intrångstester och ”red team”-aktiviteter för dina Azure-resurser och åtgärda alla kritiska säkerhetsbrister som upptäcks.
Se till att följa reglerna för intrångstester i Microsoft Cloud så att dina tester inte strider mot Microsofts policyer. Använd Microsofts strategi och utförande av ”red team”-aktiviteter och intrångstester live mot molninfrastruktur, tjänster och appar som hanteras av Microsoft.

- [Intrångstester i Azure](../security/fundamentals/pen-testing.md)

- [Regler för intrångstester](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1) 

- [”Red team”-aktiviteter i Microsoft Cloud](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Delad

## <a name="governance-and-strategy"></a>Styrning och strategi

*Mer information finns i [Azure Security Benchmark: Styrning och strategi](../security/benchmarks/security-controls-v2-governance-strategy.md).*

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1: Definiera en strategi för tillgångshantering och dataskydd 

**Vägledning**: Se till att dokumentera och förmedla en tydlig strategi för kontinuerlig övervakning och skydd av system och data. Prioritera identifiering, utvärdering, skydd och övervakning av affärskritiska data och system. 

Strategin bör omfatta dokumenterad vägledning, policyer och standarder för följande element: 

-   En standard för dataklassificering i enlighet med affärsrisker

-   Säkerhetsorganisationens insyn i risker och tillgångsinventering 

-   Säkerhetsorganisationens godkännande av de Azure-tjänster som används 

-   Tillgångars säkerhet genom hela livscykeln

-   Nödvändig strategi för åtkomstkontroll i enlighet med organisationens dataklassificering

-   Användning av dataskyddsfunktioner i Azure och från tredje part

-   Krav på datakryptering både under överföring och i vila

-   Lämpliga kryptografiska standarder

Läs mer i följande referenser:
- [Rekommendationer för en säkerhetsarkitektur i Azure – lagring, data och kryptering](/azure/architecture/framework/security/storage-data-encryption?bc=%2fsecurity%2fcompass%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fcompass%2ftoc.json)

- [Grundläggande Azure-säkerhet – säkerhet, kryptering och lagring av data i Azure](../security/fundamentals/encryption-overview.md)

- [Cloud Adoption Framework – regelverk kring datasäkerhet och kryptering i Azure](../security/fundamentals/data-encryption-best-practices.md?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json)

- [Azure Security Benchmark – hantering av tillgångar](../security/benchmarks/security-controls-v2-asset-management.md)

- [Azure Security Benchmark – dataskydd](../security/benchmarks/security-controls-v2-data-protection.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2: Definiera företagets segmenteringsstrategi 

**Vägledning**: Upprätta en strategi för hela företaget gällande att segmentera åtkomsten till tillgångar utifrån en kombination av identiteter, nätverk, program, prenumerationer, hanteringsgrupper och andra kontroller.

Du måste noga avväga behovet av separationsskyddet med behovet att underlätta den dagliga driften av de system som måste kommunicera med varandra och komma åt data.

Se till att segmenteringsstrategin implementeras konsekvent för olika kontrolltyper som nätverkssäkerhet, modeller för identiteter och åtkomst, modeller för appbehörighet och appåtkomst samt kontroller för mänskliga processer.

- [Vägledning om segmenteringsstrategi i Azure (video)](/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151)

- [Vägledning om segmenteringsstrategi i Azure (dokument)](/security/compass/governance#enterprise-segmentation-strategy)

- [Justera nätverkssegmenteringen efter företagets segmenteringsstrategi](/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3: Definiera en strategi för hantering av säkerhetspositionen

**Vägledning**: Mät och minimera risker gällande enskilda tillgångar och miljöerna där de finns regelbundet. Prioritera värdefulla tillgångar och attackytor med stor exponering, som publicerade appar, in- och utgångar i nätverket och slutpunkter för användare och administratörer.

- [Azure Security Benchmark – hantering av säkerhetspositionen och säkerhetsrisker](../security/benchmarks/security-controls-v2-posture-vulnerability-management.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4: Justera organisationens roller och ansvarsområden

**Vägledning**: Dokumentera och förmedla en tydlig strategi gällande säkerhetsorganisationens roller och ansvarsområden. Prioritera att delegera ett tydligt ansvar för olika säkerhetsbeslut och utbilda alla kring modellen med gemensamt ansvar, och ge de tekniska teamen den utbildning som behövs kring tekniken för att skydda molnet.

- [Regelverk för Azure-säkerhet 1 – personal: utbilda teamen om molnsäkerhetsresan](/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey)

- [Regelverk för Azure-säkerhet 2 – personal: utbilda teamen om molnsäkerhetstekniken](/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology)

- [Regelverk för Azure-säkerhet 3 – personal: tilldela ansvar för molnsäkerhetsbeslut](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="gs-5-define-network-security-strategy"></a>GS-5: Definiera en strategi för nätverkssäkerhet

**Vägledning**: Upprätta en strategi för nätverkssäkerhet i Azure inom ramen för organisationens övergripande strategi för åtkomstkontroll.  

Strategin bör omfatta dokumenterad vägledning, policyer och standarder för följande element: 

-   Centraliserade ansvarsområden kring nätverkshantering och säkerhet

-   Modell för segmentering av virtuella nätverk anpassad efter företagets segmenteringsstrategi

-   Åtgärdsstrategi för olika hot- och angreppsscenarier

-   Strategi för kantenheter på internet samt in- och utgångar

-   Strategi för hybridmoln och lokala anslutningar

-   Aktuella nätverkssäkerhetsartefakter (som nätverksdiagram och referensnätverksarkitekturer)

Läs mer i följande referenser:
- [Regelverk för Azure-säkerhet 11 – arkitektur. En enhetlig säkerhetsstrategi](/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Azure Security Benchmark – nätverkssäkerhet](../security/benchmarks/security-controls-v2-network-security.md)

- [Översikt över nätverkssäkerhet i Azure](../security/fundamentals/network-overview.md)

- [En strategi för företagets nätverksarkitektur](/azure/cloud-adoption-framework/ready/enterprise-scale/architecture)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6: Definiera en strategi för identiteter och privilegierad åtkomst

**Vägledning**: Upprätta en strategi för identiteter och privilegierad åtkomst i Azure inom ramen för organisationens övergripande strategi för åtkomstkontroll.  

Strategin bör omfatta dokumenterad vägledning, policyer och standarder för följande element: 

-   Ett centraliserat system för identiteter och autentisering och dess anslutningar till andra interna och externa identitetssystem

-   Starka autentiseringsmetoder i olika användningsfall och scenarier

-   Skydda och användare med hög behörighet

-   Övervaka och hantera avvikande användaraktiviteter  

-   Process för att granska och stämma av identiteter och åtkomstbehörighet

Läs mer i följande referenser:

- [Azure Security Benchmark – hantering av identiteter](../security/benchmarks/security-controls-v2-identity-management.md)

- [Azure Security Benchmark – privilegierad åtkomst](../security/benchmarks/security-controls-v2-privileged-access.md)

- [Regelverk för Azure-säkerhet 11 – arkitektur. En enhetlig säkerhetsstrategi](/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Översikt över säker identitetshantering i Azure](../security/fundamentals/identity-management-overview.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7: Definiera en strategi för loggning och hotåtgärder

**Vägledning**: Upprätta en strategi för loggning och hotåtgärder så att du snabbt kan identifiera och åtgärda hot och samtidigt uppfylla efterlevnadskraven. Prioritera att ge analytiker tillgång till aviseringar av hög kvalitet och en användarvänlig miljö så att de kan fokusera på hoten snarare än integrering och manuella steg. 

Strategin bör omfatta dokumenterad vägledning, policyer och standarder för följande element: 

-   Säkerhetsorganisationens roller och ansvarsområden 

-   En väldefinierad process för incidentsvar anpassad efter NIST eller något annat branschramverk 

-   Insamling och kvarhållning av loggar som stöd till hotidentifiering, incidentsvar och efterlevnadskrav

-   Central insyn i och korrelerande information om olika hot med hjälp av SIEM, interna Azure-funktioner och andra källor 

-   Plan för kommunikation med kunder, leverantörer och offentliga intressenter

-   Användning av plattformar för incidenthantering i Azure och från tredje part, till exempel för loggning och hotidentifiering, datautredning och motverkande åtgärder

-   Processer för hantering av incidenter och efterföljande aktiviteter som hantering av lärdomar och bevis

Läs mer i följande referenser:

- [Azure Security Benchmark – loggning och hotidentifiering](../security/benchmarks/security-controls-v2-logging-threat-detection.md)

- [Azure Security Benchmark – svar på incidenter](../security/benchmarks/security-controls-v2-incident-response.md)

- [Regelverk för Azure-säkerhet 4 – process: uppdatera processer kring incidentsvar för molnet](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Azure Adoption Framework, guide till beslut om loggning och rapporter](/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Hantering och övervakning i företagsskala i Azure](/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

## <a name="next-steps"></a>Nästa steg

- Läs mer i [Översikten över Azure Security Benchmark V2](../security/benchmarks/overview.md)
- Läs mer om [säkerhetsbaslinjer för Azure](../security/benchmarks/security-baselines-overview.md)