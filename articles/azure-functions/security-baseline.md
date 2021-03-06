---
title: Azures säkerhets bas linje för Azure Functions
description: Azures säkerhets bas linje för Azure Functions
author: msmbaldwin
ms.service: security
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: mbaldwin
ms.custom: subject-security-benchmark
ms.openlocfilehash: 5b38da5539cb80110b2a769a219213a5c74e1506
ms.sourcegitcommit: 2bd0a039be8126c969a795cea3b60ce8e4ce64fc
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98198563"
---
# <a name="azure-security-baseline-for-azure-functions"></a>Azures säkerhets bas linje för Azure Functions

Azures säkerhets bas linje för Azure Functions innehåller rekommendationer som hjälper dig att förbättra säkerhets position för din distribution.

Bas linjen för den här tjänsten hämtas från [Azures prestandatest version 1,0](../security/benchmarks/overview.md), som ger rekommendationer om hur du kan skydda dina moln lösningar i Azure med våra bästa praxis rikt linjer.

Mer information finns i [Översikt över Azure Security-bas linjer](../security/benchmarks/security-baselines-overview.md).

## <a name="network-security"></a>Nätverkssäkerhet

*Mer information finns i [säkerhets kontroll: nätverks säkerhet](../security/benchmarks/security-control-network-security.md).*

### <a name="11-protect-resources-using-network-security-groups-or-azure-firewall-on-your-virtual-network"></a>1,1: skydda resurser med hjälp av nätverks säkerhets grupper eller Azure-brandvägg på din Virtual Network

**Vägledning**: integrera dina Azure Functions-appar med ett virtuellt Azure-nätverk. Function-appar som körs i Premium-planen har samma värd funktioner som webbappar i Azure App Service, vilket omfattar funktionen "VNet-integration".  Med virtuella Azure-nätverk kan du placera många av dina Azure-resurser, till exempel Azure Functions, i ett dirigerbart nätverk som inte är från Internet.

- [Så här integrerar du funktioner med ett Azure-Virtual Network](./functions-create-vnet.md)

- [Förstå VNet-integrering för Azure Functions och Azure App Service](../app-service/web-sites-integrate-with-vnet.md)

**Azure Security Center-övervakning**: Inte tillgänglig för tillfället

**Ansvar**: Kund

### <a name="12-monitor-and-log-the-configuration-and-traffic-of-vnets-subnets-and-nics"></a>1,2: övervaka och logga konfigurationen och trafiken för virtuella nätverk, undernät och nätverkskort

**Vägledning**: Använd Azure Security Center och följ rekommendationer för nätverks skydd för att skydda nätverks resurser och nätverkskonfigurationer som är relaterade till dina Azure Functions appar.

Om du använder nätverks säkerhets grupper (NSG: er) med Azure Functions implementering aktiverar du NSG Flow-loggar och skickar loggar till ett Azure Storage konto för trafik granskningar. Du kan också skicka NSG Flow-loggar till en Log Analytics arbets yta och använda Trafikanalys för att ge insikter i trafikflöde i Azure-molnet. Några av fördelarna med Trafikanalys är möjligheten att visualisera nätverks aktivitet och identifiera aktiva punkter, identifiera säkerhetshot, förstå trafikflödes mönster och hitta nätverks problem.

- [Förstå nätverks säkerhet som tillhandahålls av Azure Security Center](../security-center/security-center-network-recommendations.md)

- [Så här aktiverar du NSG Flow-loggar](../network-watcher/network-watcher-nsg-flow-logging-portal.md)

- [Så här aktiverar och använder du Trafikanalys](../network-watcher/traffic-analytics.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="13-protect-critical-web-applications"></a>1,3: skydda viktiga webb program

**Vägledning**: om du vill skydda dina Azure Functions-slutpunkter i produktion bör du överväga att implementera en av följande funktioner på App-nivå:
- Aktivera App Service autentisering/auktorisering för din Function-app
- Använd Azure API Management (APIM) för att autentisera begär Anden eller
- Distribuera din Function-app till en Azure App Service-miljön.

Se också till att fjärrfelsökning har inaktiverats för produktions Azure Functions. Dessutom bör resurs delning mellan ursprung (CORS) inte tillåta alla domäner att komma åt din Function-app i Azure. Tillåt endast domäner som krävs för att interagera med din Function-app.

Överväg att distribuera Azure Web Application Firewall (WAF) som en del av nätverks konfigurationen för ytterligare inspektion av inkommande trafik. Aktivera diagnostikinställningar för WAF och mata in loggar till ett lagrings konto, en Event Hub-eller Log Analytics-arbetsyta. 

- [Så här säkrar du Azure Functions-slutpunkter i produktion](./functions-bindings-http-webhook-trigger.md?tabs=csharp#secure-an-http-endpoint-in-production)

- [Så här distribuerar du Azure-WAF](../web-application-firewall/ag/create-waf-policy-ag.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="14-deny-communications-with-known-malicious-ip-addresses"></a>1,4: neka kommunikation med kända skadliga IP-adresser

**Vägledning**: Aktivera DDoS Protection standard på de virtuella nätverk som är kopplade till dina Functions-appar för att skydda dig mot DDoS-attacker. Använd Azure Security Center integrerad Hot information för att neka kommunikation med kända skadliga eller oanvända offentliga IP-adresser.
Dessutom kan du konfigurera en frontend-Gateway, till exempel Azure Web Application-brandvägg, för att autentisera alla inkommande begär Anden och filtrera bort skadlig trafik. Azure Web Application-brandväggen kan hjälpa dig att skydda din Function-app genom att inspektera inkommande webb trafik för att blockera SQL-injektering, skript körning över flera webbplatser, överföringar av skadlig kod och DDoS-attacker. Introduktionen av en WAF kräver antingen en App Service-miljön eller användning av privata slut punkter (för hands version). Se till att privata slut punkter inte längre är i (för hands version) innan du använder dem med produktions arbets belastningar.

- [Nätverksalternativ för Azure Functions](./functions-networking-options.md)

- [Azure Functions Premium-plan](./functions-premium-plan.md)

- [Introduktion till Azure App Service-miljöer](../app-service/environment/intro.md)

- [Nätverksöverväganden för en App Service-miljö](../app-service/environment/network-info.md)

- [Så här konfigurerar du DDoS-skydd](../ddos-protection/manage-ddos-protection.md)

- [Så här distribuerar du Azure-brandvägg](../firewall/tutorial-firewall-deploy-portal.md)

- [Förstå Azure Security Center integrerad Hot information](../security-center/azure-defender.md)

- [Förstå Azure Security Center anpassad nätverks härdning](../security-center/security-center-adaptive-network-hardening.md)

- [Förstå Azure Security Center just-in-Time-nätverk Access Control](../security-center/security-center-just-in-time.md)

- [Använda privata slut punkter för Azure Functions](../app-service/networking/private-endpoint.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="15-record-network-packets-and-flow-logs"></a>1,5: registrera nätverks paket och flödes loggar

**Vägledning**: om du använder nätverks säkerhets grupper (NSG: er) med Azure Functions implementering, aktiverar du flödes loggar för nätverks säkerhets grupper och skickar loggar till ett lagrings konto för trafik granskning. Du kan också skicka flödes loggar till en Log Analytics arbets yta och använda Trafikanalys för att ge insikter i trafikflödet i Azure-molnet. Några av fördelarna med Trafikanalys är möjligheten att visualisera nätverks aktivitet och identifiera aktiva punkter, identifiera säkerhetshot, förstå trafikflödes mönster och hitta nätverks problem.

- [Så här aktiverar du NSG Flow-loggar](../network-watcher/network-watcher-nsg-flow-logging-portal.md)

- [Så här aktiverar och använder du Trafikanalys](../network-watcher/traffic-analytics.md)

- [Så här aktiverar du Network Watcher](../network-watcher/network-watcher-create.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="16-deploy-network-based-intrusion-detectionintrusion-prevention-systems-idsips"></a>1,6: Distribuera Network-baserad intrångs identifiering/intrångs skydd system (ID/IP-adresser)

**Vägledning**: Konfigurera en frontend-Gateway, till exempel brand väggen för Azure Web Application för att autentisera alla inkommande förfrågningar och filtrera bort skadlig trafik. Azure Web Application-brandväggen kan hjälpa dig att skydda dina funktions program genom att inspektera inkommande webb trafik för att blockera SQL-injektering, skript körning över flera webbplatser, överföringar av skadlig kod och DDoS-attacker. Introduktionen av en WAF kräver antingen en App Service-miljön eller användning av privata slut punkter (för hands version). Se till att privata slut punkter inte längre är i (för hands version) innan du använder dem med produktions arbets belastningar.

Alternativt finns det flera Marketplace-alternativ som Barracuda-WAF för Azure som är tillgängliga på Azure Marketplace, som omfattar funktioner för ID/IP-adresser.

- [Nätverksalternativ för Azure Functions](./functions-networking-options.md)

- [Azure Functions Premium-plan](./functions-premium-plan.md)

- [Introduktion till Azure App Service-miljöer](../app-service/environment/intro.md)

- [Nätverksöverväganden för en App Service-miljö](../app-service/environment/network-info.md)

- [Förstå brand väggen för Azure-webbprogram](../web-application-firewall/index.yml)

- [Använda privata slut punkter för Azure Functions](../app-service/networking/private-endpoint.md)

- [Förstå moln tjänsten Barracuda WAF](../app-service/environment/app-service-app-service-environment-web-application-firewall.md#configuring-your-barracuda-waf-cloud-service)

**Azure Security Center-övervakning**: Inte tillgänglig för tillfället

**Ansvar**: Kund

### <a name="17-manage-traffic-to-web-applications"></a>1,7: hantera trafik till webb program

**Vägledning**: Konfigurera en frontend-Gateway för nätverket, till exempel en brand vägg för Azure-webbprogram med hjälp av TLS-kryptering från slut punkt till slut punkt. Introduktionen av en WAF kräver antingen en App Service-miljön eller användning av privata slut punkter (för hands version). Se till att privata slut punkter inte längre är i (för hands version) innan du använder dem med produktions arbets belastningar.

- [Nätverksalternativ för Azure Functions](./functions-networking-options.md)

- [Azure Functions Premium-plan](./functions-premium-plan.md)

- [Introduktion till Azure App Service-miljöer](../app-service/environment/intro.md)

- [Nätverksöverväganden för en App Service-miljö](../app-service/environment/network-info.md)

- [Förstå brand väggen för Azure-webbprogram](../web-application-firewall/index.yml)

- [Så här konfigurerar du end-to-end-TLS genom att använda Application Gateway med portalen](../application-gateway/end-to-end-ssl-portal.md)

- [Använda privata slut punkter för Azure Functions](../app-service/networking/private-endpoint.md)

**Azure Security Center-övervakning**: Inte tillgänglig för tillfället

**Ansvar**: Kund

### <a name="18-minimize-complexity-and-administrative-overhead-of-network-security-rules"></a>1,8: minimera komplexitet och administrativa kostnader för nätverks säkerhets regler

**Vägledning**: Använd Virtual Network Service-taggar för att definiera nätverks åtkomst kontroller i nätverks säkerhets grupper eller Azure-brandvägg. Du kan använda tjänsttaggar i stället för specifika IP-adresser när du skapar säkerhetsregler. Genom att ange service tag-namnet (t. ex. AzureAppService) i lämpligt käll-eller mål fält för en regel kan du tillåta eller neka trafiken för motsvarande tjänst. Microsoft hanterar de adressprefix som omfattas av tjänst tag gen och uppdaterar automatiskt tjänst tag gen när adresser ändras.

- [Mer information om att använda service märken](../virtual-network/service-tags-overview.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="19-maintain-standard-security-configurations-for-network-devices"></a>1,9: underhåll standardkonfigurationer för nätverks enheter

**Vägledning**: definiera och implementera standardinställda säkerhetskonfigurationer för nätverks inställningar som är relaterade till din Azure Functions. Använd Azure Policy alias i namn områdena "Microsoft. Web" och "Microsoft. Network" om du vill skapa anpassade principer för granskning eller tillämpa nätverks konfigurationen för din Azure Functions. Du kan också använda inbyggda princip definitioner för Azure Functions, till exempel:
- CORS bör inte tillåta alla resurser att komma åt dina funktions program
- Function-appen bör endast vara tillgänglig via HTTPS
- Den senaste TLS-versionen ska användas i din Function-app

Du kan också använda Azure-ritningar för att förenkla storskaliga Azure-distributioner genom att paketera viktiga miljö artefakter, till exempel Azure Resource Manager mallar, rollbaserad åtkomst kontroll i Azure (Azure RBAC) och principer i en enda skiss definition. Du kan enkelt använda skissen för nya prenumerationer, miljöer och finjustera kontroll och hantering genom versions hantering.

- [Konfigurera och hantera Azure Policy](../governance/policy/tutorials/create-and-manage.md)

- [Så här skapar du en Azure Blueprint](../governance/blueprints/create-blueprint-portal.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="110-document-traffic-configuration-rules"></a>1,10: dokumentera trafik konfigurations regler

**Vägledning**: om du använder nätverks säkerhets grupper (NSG: er) med din Azure Functions implementering, använder du taggar för NSG: er och andra resurser som är relaterade till nätverks säkerhets-och trafikflödet. För enskilda NSG-regler använder du fältet Beskrivning för att ange affärs behov och/eller varaktighet (osv.) för alla regler som tillåter trafik till/från ett nätverk.

Använd någon av de inbyggda definitioner av Azure-principer som är relaterade till taggning, till exempel "Kräv tagg och dess värde" för att säkerställa att alla resurser skapas med taggar och meddela dig om befintliga otaggade resurser.

Du kan använda Azure PowerShell eller Azure CLI för att söka efter eller utföra åtgärder på resurser baserat på deras taggar.

- [Skapa och använda Taggar](../azure-resource-manager/management/tag-resources.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="111-use-automated-tools-to-monitor-network-resource-configurations-and-detect-changes"></a>1,11: Använd automatiserade verktyg för att övervaka konfigurationer för nätverks resurser och identifiera ändringar

**Vägledning**: Använd Azure aktivitets logg för att övervaka konfigurationer av nätverks resurser och identifiera ändringar för nätverks inställningar och resurser som är relaterade till dina Azure Functions-distributioner. Skapa aviseringar inom Azure Monitor som ska utlösas när ändringar av kritiska nätverks inställningar eller resurser äger rum. 

- [Visa och hämta Azure aktivitets logg händelser](../azure-monitor/platform/activity-log.md#view-the-activity-log)

- [Så här skapar du aviseringar i Azure Monitor](../azure-monitor/platform/alerts-activity-log.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

## <a name="logging-and-monitoring"></a>Loggning och övervakning

*Mer information finns i [säkerhets kontroll: loggning och övervakning](../security/benchmarks/security-control-logging-monitoring.md).*

### <a name="21-use-approved-time-synchronization-sources"></a>2,1: Använd godkända tids källor för synkronisering

**Vägledning**: Microsoft hanterar den tids källa som används för Azure-resurser, till exempel Azure Functions för tidsstämplar i loggarna.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Microsoft

### <a name="22-configure-central-security-log-management"></a>2,2: Konfigurera central hantering av säkerhets loggar

**Vägledning**: för gransknings loggning i kontroll plan aktiverar du Azure aktivitets logg diagnostikinställningar och skickar loggarna till en Log Analytics arbets yta, Azure Event Hub eller Azure Storage-konto för arkivering. Med hjälp av Azures aktivitets logg data kan du avgöra vad, vem och när som helst för Skriv åtgärder (skicka, skicka och ta bort) på kontroll Plans nivån för dina Azure-resurser.

Azure Functions erbjuder även inbyggd integrering med Azure Application insikter för att övervaka funktioner. Application Insights samlar in logg-, prestanda-och fel data. Den identifierar automatiskt prestanda avvikelser och innehåller kraftfulla analys verktyg som hjälper dig att diagnostisera problem och förstå hur dina funktioner används.

Om du har inbyggd anpassad säkerhets-/gransknings loggning i din Function-app aktiverar du diagnostikinställningar "FunctionAppLogs" och skickar loggarna till en Log Analytics arbets yta, Azure Event Hub eller Azure Storage-konto för arkivering. 

Alternativt kan du aktivera och fordonsbaserad information till Azure Sentinel eller en SIEM från tredje part. 

- [Så här aktiverar du diagnostikinställningar för Azure aktivitets logg](../azure-monitor/platform/activity-log.md)

- [Så här konfigurerar du Azure Functions med Azure Application Insights](./functions-monitoring.md)

- [Så här aktiverar du diagnostikinställningar (användarspecifika loggar) för Azure Functions](./functions-monitor-log-analytics.md)

- [Publicera Azure Sentinel](../sentinel/quickstart-onboard.md)

**Azure Security Center-övervakning**: Inte tillgänglig för tillfället

**Ansvar**: Kund

### <a name="23-enable-audit-logging-for-azure-resources"></a>2,3: Aktivera gransknings loggning för Azure-resurser

**Vägledning**: för gransknings loggning i kontroll plan aktiverar du Azure aktivitets logg diagnostikinställningar och skickar loggarna till en Log Analytics arbets yta, Azure Event Hub eller Azure Storage-konto för arkivering. Med hjälp av Azures aktivitets logg data kan du avgöra vad, vem och när som helst för Skriv åtgärder (skicka, skicka och ta bort) på kontroll Plans nivån för dina Azure-resurser.

Om du har inbyggd anpassad säkerhets-/gransknings loggning i din Function-app aktiverar du diagnostikinställningar "FunctionAppLogs" och skickar loggarna till en Log Analytics arbets yta, Azure Event Hub eller Azure Storage-konto för arkivering. 

- [Så här aktiverar du diagnostikinställningar för Azure aktivitets logg](../azure-monitor/platform/activity-log.md)

- [Så här aktiverar du diagnostikinställningar (användarspecifika loggar) för Azure Functions](./functions-monitor-log-analytics.md)

**Azure Security Center-övervakning**: Inte tillgänglig för tillfället

**Ansvar**: Kund

### <a name="24-collect-security-logs-from-operating-systems"></a>2,4: samla in säkerhets loggar från operativ system

**Vägledning**: ej tillämpligt; den här rikt linjen är avsedd för IaaS beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="25-configure-security-log-storage-retention"></a>2,5: Konfigurera säkerhets logg lagrings kvarhållning

**Vägledning**: i Azure Monitor anger du logg kvarhållningsperiod för Log Analytics arbets ytor som är associerade med dina funktions program enligt organisationens regler för efterlevnad.

- [Ange parametrar för logg bevarande](../azure-monitor/platform/manage-cost-storage.md#change-the-data-retention-period)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="26-monitor-and-review-logs"></a>2,6: övervaka och granska loggar

**Vägledning**: Aktivera Azure Activity Log-diagnostikinställningar samt diagnostikinställningar för din Function-app och skicka loggarna till en Log Analytics-arbetsyta. Utför frågor i Log Analytics för att söka efter termer, identifiera trender, analysera mönster och tillhandahålla många andra insikter baserat på insamlade data.

Aktivera Application Insights för dina funktions program för att samla in logg-, prestanda-och fel data. Du kan visa telemetri-data som samlas in av Application Insights i Azure Portal.

Om du har inbyggd anpassad säkerhets-/gransknings loggning i din Function-app aktiverar du diagnostikinställningar "FunctionAppLogs" och skickar loggarna till en Log Analytics arbets yta, Azure Event Hub eller Azure Storage-konto för arkivering. 

Alternativt kan du aktivera och fordonsbaserad information till Azure Sentinel eller en SIEM från tredje part. 

- [Så här aktiverar du diagnostikinställningar för Azure aktivitets logg](../azure-monitor/platform/activity-log.md)

- [Så här aktiverar du diagnostikinställningar för Azure Functions](./functions-monitor-log-analytics.md)

- [Konfigurera Azure Functions med Azure Application insikter och Visa telemetridata](./functions-monitoring.md)

- [Publicera Azure Sentinel](../sentinel/quickstart-onboard.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="27-enable-alerts-for-anomalous-activity"></a>2,7: aktivera aviseringar för avvikande aktivitet

**Vägledning**: Aktivera Azure Activity Log-diagnostikinställningar samt diagnostikinställningar för din Function-app och skicka loggarna till en Log Analytics-arbetsyta. Utför frågor i Log Analytics för att söka efter termer, identifiera trender, analysera mönster och tillhandahålla många andra insikter baserat på insamlade data. Du kan skapa aviseringar baserat på Log Analytics arbets ytans frågor.

Aktivera Application Insights för dina funktions program för att samla in logg-, prestanda-och fel data. Du kan visa telemetri-data som samlas in av Application Insights och skapa aviseringar inom Azure Portal.

Alternativt kan du aktivera och fordonsbaserad information till Azure Sentinel eller en SIEM från tredje part. 

- [Så här aktiverar du diagnostikinställningar för Azure aktivitets logg](../azure-monitor/platform/activity-log.md)

- [Så här aktiverar du diagnostikinställningar för Azure Functions](./functions-monitor-log-analytics.md)

- [Så här aktiverar du Application Insights för Azure Functions](./configure-monitoring.md#enable-application-insights-integration)

- [Så här skapar du aviseringar i Azure](../azure-monitor/learn/tutorial-response.md)

- [Publicera Azure Sentinel](../sentinel/quickstart-onboard.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="28-centralize-anti-malware-logging"></a>2,8: centralisera loggning mot skadlig kod

**Vägledning**: ej tillämpligt; Functions-appar bearbetar eller skapar inte relaterade loggar mot skadlig kod.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="29-enable-dns-query-logging"></a>2,9: Aktivera loggning av DNS-frågor

**Vägledning**: ej tillämpligt; Functions-appar bearbetar eller skapar inte tillgängliga DNS-relaterade loggar för användare.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="210-enable-command-line-audit-logging"></a>2,10: Aktivera loggning av kommando rads granskning

**Vägledning**: ej tillämpligt; den här rikt linjen är avsedd för IaaS beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

## <a name="identity-and-access-control"></a>Identitets- och åtkomstkontroll

*Mer information finns i [säkerhets kontroll: identitets-och åtkomst kontroll](../security/benchmarks/security-control-identity-access-control.md).*

### <a name="31-maintain-an-inventory-of-administrative-accounts"></a>3,1: underhåll en inventering av administrativa konton

**Vägledning**: Azure Active Directory (AD) har inbyggda roller som måste tilldelas explicit och som kan frågas. Använd Azure AD PowerShell-modulen för att utföra ad hoc-frågor för att identifiera konton som är medlemmar i administrativa grupper. 

- [Så här hämtar du en katalog roll i Azure AD med PowerShell](/powershell/module/azuread/get-azureaddirectoryrole?view=azureadps-2.0)

- [Så här hämtar du medlemmar i en katalog roll i Azure AD med PowerShell](/powershell/module/azuread/get-azureaddirectoryrolemember?view=azureadps-2.0)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="32-change-default-passwords-where-applicable"></a>3,2: ändra standard lösen ord där tillämpligt

**Vägledning**: kontroll Plans åtkomst till Azure Functions styrs via Azure Active Directory (AD). Azure AD har inte begreppet standard lösen ord.

Åtkomst till data planet kan styras via flera olika sätt, inklusive auktoriseringsregler, nätverks begränsningar och verifiering av en Azure AD-identitet. Auktoriseringsregler används av klienterna som ansluter till din Azure Functions HTTP-slutpunkter och kan återskapas när som helst. Nycklarna genereras för nya HTTP-slutpunkter som standard.

Det finns flera distributions metoder för att Function-appar, varav vissa kan använda en uppsättning genererade autentiseringsuppgifter. Granska de distributions metoder som ska användas för ditt program.

- [Skydda en HTTP-slutpunkt](./functions-bindings-http-webhook-trigger.md?tabs=csharp#secure-an-http-endpoint-in-production)

- [Hämta och återskapa auktoriseringsregler](./functions-bindings-http-webhook-trigger.md?tabs=csharp#obtaining-keys)

- [Distributions tekniker i Azure Functions](./functions-deployment-technologies.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="33-use-dedicated-administrative-accounts"></a>3,3: Använd dedikerade administrativa konton

**Vägledning**: skapa standard procedurer för användning av dedikerade administrativa konton. Använd Azure Security Center identitets-och åtkomst hantering för att övervaka antalet administrativa konton.

För att hjälpa dig att hålla koll på dedikerade administrativa konton kan du dessutom använda rekommendationer från Azure Security Center eller inbyggda Azure-principer, t. ex.: det bör finnas fler än en ägare som tilldelats prenumerations föråldrade konton med ägar behörighet bör tas bort från din prenumerations externa konton med ägar behörigheter bör tas bort från din prenumeration

- [Använda Azure Security Center för att övervaka identitet och åtkomst (för hands version)](../security-center/security-center-identity-access.md)

- [Använda Azure Policy](../governance/policy/tutorials/create-and-manage.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="34-use-single-sign-on-sso-with-azure-active-directory"></a>3,4: Använd enkel inloggning (SSO) med Azure Active Directory

**Vägledning**: var som helst, Använd Azure Active Directory SSO i stället för att konfigurera enskilda fristående autentiseringsuppgifter för data åtkomst till din Function-app. Använd rekommendationer för Azure Security Center identitets-och åtkomst hantering. Implementera enkel inloggning för dina funktions appar med hjälp av funktionen App Service autentisering/auktorisering.

- [Förstå autentisering och auktorisering i Azure Functions](../app-service/overview-authentication-authorization.md#identity-providers)

- [Förstå SSO med Azure AD](../active-directory/manage-apps/what-is-single-sign-on.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="35-use-multi-factor-authentication-for-all-azure-active-directory-based-access"></a>3,5: Använd Multi-Factor Authentication för all Azure Active Directory baserad åtkomst

**Vägledning**: Aktivera Azure Active Directory (AD) Multi-Factor Authentication (MFA) och följ rekommendationer för Azure Security Center identitets-och åtkomst hantering.

- [Aktivera MFA i Azure](../active-directory/authentication/howto-mfa-getstarted.md)

- [Övervaka identitet och åtkomst i Azure Security Center](../security-center/security-center-identity-access.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="36-use-dedicated-machines-privileged-access-workstations-for-all-administrative-tasks"></a>3,6: Använd dedikerade datorer (arbets stationer med privilegie rad åtkomst) för alla administrativa uppgifter

**Vägledning**: Använd Paw (Privileged Access Workstation) med Multi-Factor Authentication (MFA) konfigurerat för att logga in på och konfigurera Azure-resurser.

- [Lär dig mer om arbets stationer med privilegie rad åtkomst](https://4sysops.com/archives/understand-the-microsoft-privileged-access-workstation-paw-security-model/)

- [Aktivera MFA i Azure](../active-directory/authentication/howto-mfa-getstarted.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="37-log-and-alert-on-suspicious-activity-from-administrative-accounts"></a>3,7: Logga och Avisera om misstänkt aktivitet från administrativa konton

**Vägledning**: Använd Azure Active Directory (AD) PRIVILEGED Identity Management (PIM) för att skapa loggar och varningar när misstänkt eller osäker aktivitet inträffar i miljön.

Dessutom kan du använda Azure AD-farlighets identifiering för att visa aviseringar och rapporter om riskfyllda användar beteenden.

- [Distribuera Privileged Identity Management (PIM)](../active-directory/privileged-identity-management/pim-deployment-plan.md)

- [Förstå identifieringar av Azure AD-risker](../active-directory/identity-protection/overview-identity-protection.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="38-manage-azure-resources-from-only-approved-locations"></a>3,8: hantera endast Azure-resurser från godkända platser

**Vägledning**: Använd villkorlig åtkomst med namngivna platser för att tillåta åtkomst till Azure Portal från enbart vissa logiska grupperingar av IP-adressintervall eller länder/regioner.

- [Så här konfigurerar du namngivna platser i Azure](../active-directory/reports-monitoring/quickstart-configure-named-locations.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="39-use-azure-active-directory"></a>3,9: Använd Azure Active Directory

**Vägledning**: Använd Azure Active Directory (AD) som central-autentiserings-och auktoriserings system för dina funktions appar. Azure AD skyddar data med stark kryptering för data i vila och under överföring. Azure AD innehåller även salter, hash-värden och lagrar användarautentiseringsuppgifter på ett säkert sätt.

- [Så här konfigurerar du att din Function-app använder Azure AD-inloggning](../app-service/configure-authentication-provider-aad.md)

- [Skapa och konfigurera en Azure AD-instans](../active-directory/fundamentals/active-directory-access-create-new-tenant.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="310-regularly-review-and-reconcile-user-access"></a>3,10: granska och stäm regelbundet av användar åtkomst

**Vägledning**: Azure Active Directory (AD) innehåller loggar för att hjälpa dig att identifiera inaktuella konton. Dessutom kan du använda Azure Identity Access-granskningar för att effektivt hantera grupp medlemskap, åtkomst till företags program och roll tilldelningar. Användar åtkomst kan granskas regelbundet för att se till att endast rätt användare har fortsatt åtkomst. 

- [Förstå Azure AD repor ting](../active-directory/reports-monitoring/index.yml)

- [Så här använder du granskningar av Azure Identity Access](../active-directory/governance/access-reviews-overview.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="311-monitor-attempts-to-access-deactivated-accounts"></a>3,11: övervaka försök att komma åt inaktiverade konton

**Vägledning**: Använd Azure Active Directory (AD) som central-autentiserings-och auktoriserings system för dina funktions appar. Azure AD skyddar data med stark kryptering för data i vila och under överföring. Azure AD innehåller även salter, hash-värden och lagrar användarautentiseringsuppgifter på ett säkert sätt.

Du har åtkomst till Azure AD-inloggning, gransknings-och risk händelse logg källor, som gör att du kan integrera med Azure Sentinel eller en SIEM från tredje part.

Du kan effektivisera den här processen genom att skapa diagnostikinställningar för Azure AD-användarkonton och skicka gransknings loggar och inloggnings loggar till en Log Analytics-arbetsyta. Du kan konfigurera önskade logg aviseringar i Log Analytics.

- [Så här konfigurerar du att din Function-app använder Azure AD-inloggning](../app-service/configure-authentication-provider-aad.md)

- [Så här integrerar du Azures aktivitetsloggar i Azure Monitor](../active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics.md)

- [Aktivera Azure-kontroll på kort](../sentinel/quickstart-onboard.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="312-alert-on-account-login-behavior-deviation"></a>3,12: avisering om beteende för beteende för konto inloggning

**Vägledning**: Använd Azure Active Directory (AD) som central-autentiserings-och auktoriserings system för dina funktions appar. Använd Azure Active Directory (AD) identitets skydd och identifierings funktioner för att konfigurera automatiserade svar på identifierade misstänkta åtgärder relaterade till användar identiteter för konto inloggnings beteende avvikelse i kontroll planet (Azure Portal). Du kan också mata in data i Azure Sentinel för ytterligare undersökning.

- [Så visar du riskfyllda inloggningar för Azure AD](../active-directory/identity-protection/overview-identity-protection.md)

- [Så här konfigurerar och aktiverar du risk principer för identitets skydd](../active-directory/identity-protection/howto-identity-protection-configure-risk-policies.md)

- [Publicera Azure Sentinel](../sentinel/quickstart-onboard.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="313-provide-microsoft-with-access-to-relevant-customer-data-during-support-scenarios"></a>3,13: ge Microsoft åtkomst till relevant kund information under support scenarier

**Vägledning**: inte tillgänglig för närvarande. Customer Lockbox stöds för närvarande inte för Azure Functions.

- [Lista över Customer Lockbox tjänster som stöds](../security/fundamentals/customer-lockbox-overview.md#supported-services-and-scenarios-in-general-availability)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

## <a name="data-protection"></a>Dataskydd

*Mer information finns i [säkerhets kontroll: data skydd](../security/benchmarks/security-control-data-protection.md).*

### <a name="41-maintain-an-inventory-of-sensitive-information"></a>4,1: underhåll en inventering av känslig information

**Vägledning**: Använd taggar för att spåra Azure-resurser som lagrar eller bearbetar känslig information.

- [Skapa och använda Taggar](../azure-resource-manager/management/tag-resources.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="42-isolate-systems-storing-or-processing-sensitive-information"></a>4,2: isolera system som lagrar eller bearbetar känslig information

**Vägledning**: implementera separata prenumerationer och/eller hanterings grupper för utveckling, testning och produktion. function-appar ska åtskiljas av Virtual Network (VNet)/Subnet och taggas på lämpligt sätt.

Du kan också använda privata slut punkter för att utföra nätverks isolering. En privat Azure-slutpunkt är ett nätverks gränssnitt som ansluter privat och säkert till en tjänst (t. ex. en funktion app HTTPs-slutpunkt) som drivs av en privat Azure-länk. Den privata slutpunkten använder en privat IP-adress från ditt VNet, vilket effektivt tar tjänsten till ditt VNet. Privata slut punkter är i (för hands version) för Function-appar som körs i Premium-planen. Se till att privata slut punkter inte längre är i (för hands version) innan du använder dem med produktions arbets belastningar.

- [Så här skapar du ytterligare Azure-prenumerationer](../cost-management-billing/manage/create-subscription.md)

- [Så här skapar du Hanteringsgrupper](../governance/management-groups/create-management-group-portal.md)

- [Skapa och använda Taggar](../azure-resource-manager/management/tag-resources.md)

- [Nätverksalternativ för Azure Functions](./functions-networking-options.md)

- [Azure Functions Premium-plan](./functions-premium-plan.md)

- [Förstå privat slut punkt](../private-link/private-endpoint-overview.md)

- [Använda privata slut punkter för Azure Functions](../app-service/networking/private-endpoint.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="43-monitor-and-block-unauthorized-transfer-of-sensitive-information"></a>4,3: övervaka och blockera obehörig överföring av känslig information

**Vägledning**: Distribuera ett automatiserat verktyg på nätverks-perimeter som övervakar för obehörig överföring av känslig information och blockerar sådana överföringar vid avisering av information säkerhets tekniker. 

Microsoft hanterar den underliggande infrastrukturen för Azure Functions och har implementerat strikta kontroller för att förhindra förlust eller exponering av kund information.

- [Förstå skydd av kunddata i Azure](../security/fundamentals/protection-customer-data.md)

**Azure Security Center-övervakning**: Inte tillgänglig för tillfället

**Ansvars område**: inte tillämpligt

### <a name="44-encrypt-all-sensitive-information-in-transit"></a>4,4: kryptera all känslig information under överföring

**Vägledning**: i Azure Portal för dina funktions program, under "plattforms funktioner: nätverk: SSL", aktiverar du inställningen "endast https" och ställer in den lägsta TLS-versionen på 1,2.

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="45-use-an-active-discovery-tool-to-identify-sensitive-data"></a>4,5: Använd ett aktivt identifierings verktyg för att identifiera känsliga data

**Vägledning**: inte tillgänglig för närvarande. funktionerna för data identifiering, klassificering och förlust av förlust är inte tillgängliga för Azure Functions. Tagga funktions program som kan bearbeta känslig information som sådan och implementera en lösning från tredje part om det krävs för efterlevnad.

För den underliggande plattform som hanteras av Microsoft behandlar Microsoft allt kund innehåll som känsligt och går till fantastiska längder för att skydda mot kund data förlust och exponering. För att säkerställa att kunddata i Azure förblir skyddade har Microsoft implementerat och underhåller en svit med robusta data skydds kontroller och-funktioner.

- [Förstå skydd av kunddata i Azure](../security/fundamentals/protection-customer-data.md)

**Azure Security Center-övervakning**: Inte tillgänglig för tillfället

**Ansvar**: Kund

### <a name="46-use-azure-rbac-to-control-access-to-resources"></a>4,6: Använd Azure RBAC för att kontrol lera åtkomsten till resurser

**Vägledning**: Använd rollbaserad åtkomst kontroll i Azure (Azure RBAC) för att styra åtkomsten till funktionen app Control plan (Azure Portal). 

- [Så här konfigurerar du Azure RBAC](../role-based-access-control/role-assignments-portal.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="47-use-host-based-data-loss-prevention-to-enforce-access-control"></a>4,7: Använd värdbaserade data förlust skydd för att genomdriva åtkomst kontroll

**Vägledning**: ej tillämpligt; den här rekommendationen är avsedd för IaaS-beräknings resurser.

Microsoft hanterar den underliggande infrastrukturen för Azure Functions och har implementerat strikta kontroller för att förhindra förlust eller exponering av kund information.

- [Förstå skydd av kunddata i Azure](../security/fundamentals/protection-customer-data.md)

**Azure Security Center-övervakning**: Inte tillgänglig för tillfället

**Ansvar**: Kund

### <a name="48-encrypt-sensitive-information-at-rest"></a>4,8: kryptera känslig information i vila

**Vägledning**: när du skapar en Function-app måste du skapa eller länka till ett allmänt Azure Storage-konto som stöder BLOB-, Queue-och table-lagring. Detta beror på att funktioner förlitar sig på Azure Storage för åtgärder som att hantera utlösare och loggning av funktions körningar. Azure Storage krypterar alla data i ett lagrings konto i vila. Som standard krypteras data med Microsoft-hanterade nycklar. Om du vill ha ytterligare kontroll över krypterings nycklar kan du ange Kundhanterade nycklar för kryptering av BLOB-och fildata. Dessa nycklar måste finnas i Azure Key Vault för att Function-appen ska kunna komma åt lagrings kontot.

- [Förstå lagrings överväganden för Azure Functions](./storage-considerations.md)

- [Förstå Azure Storage-kryptering för vilande data](../storage/common/storage-service-encryption.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Delad

### <a name="49-log-and-alert-on-changes-to-critical-azure-resources"></a>4,9: logg och varning vid ändringar av kritiska Azure-resurser

**Vägledning**: Använd Azure monitor med Azure aktivitets loggen för att skapa aviseringar för när ändringar sker i appar för produktions funktioner samt andra kritiska eller relaterade resurser.

- [Så här skapar du aviseringar för Azure aktivitets logg händelser](../azure-monitor/platform/alerts-activity-log.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

## <a name="vulnerability-management"></a>Sårbarhetshantering

*Mer information finns i [säkerhets kontroll: sårbarhets hantering](../security/benchmarks/security-control-vulnerability-management.md).*

### <a name="51-run-automated-vulnerability-scanning-tools"></a>5,1: köra automatiserade sårbarhets skannings verktyg

**Vägledning**: anta en DevSecOps-metod för att se till att dina funktions program är säkra och förblir så säkra som möjligt under hela livs cykeln. DevSecOps införlivar din organisations säkerhets team och deras funktioner i din DevOps-praxis, vilket ger säkerhets ansvars områden för alla i teamet.

Följ dessutom rekommendationer från Azure Security Center för att skydda dina funktions program.

- [Så här lägger du till kontinuerlig säkerhets validering till din CI/CD-pipeline](/azure/devops/migrate/security-validation-cicd-pipeline?view=azure-devops)

- [Så här implementerar du rekommendationer för Azure Security Center sårbarhets bedömning](../security-center/deploy-vulnerability-assessment-vm.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="52-deploy-an-automated-operating-system-patch-management-solution"></a>5,2: Distribuera en automatiserad hanterings lösning för operativ system

**Vägledning**: ej tillämpligt; den här rekommendationen är avsedd för IaaS-beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="53-deploy-automated-third-party-software-patch-management-solution"></a>5,3: Distribuera automatisk hanterings lösning för program uppdatering från tredje part

**Vägledning**: ej tillämpligt; den här rekommendationen är avsedd för IaaS-beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="54-compare-back-to-back-vulnerability-scans"></a>5,4: jämför sökningar efter säkerhets risker

**Vägledning**: ej tillämpligt; den här rekommendationen är avsedd för IaaS-beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="55-use-a-risk-rating-process-to-prioritize-the-remediation-of-discovered-vulnerabilities"></a>5,5: Använd en risk klassificerings process för att prioritera reparation av identifierade säkerhets risker

**Vägledning**: Microsoft utför sårbarhets hantering på de underliggande systemen som har stöd för Azure Functions, men du kan använda rekommendationernas allvarlighets grad i Azure Security Center samt säkra Poäng för att mäta risker i din miljö. Dina säkra Poäng baseras på hur många Security Center rekommendationer som du har begränsat. För att prioritera rekommendationerna för att lösa det första, bör du tänka igenom allvarlighets graden för var och en.

- [Referens guide för säkerhets rekommendationer](../security-center/recommendations-reference.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Delad

## <a name="inventory-and-asset-management"></a>Inventerings- och tillgångshantering

*Mer information finns i [säkerhets kontroll: inventering och till gångs hantering](../security/benchmarks/security-control-inventory-asset-management.md).*

### <a name="61-use-azure-asset-discovery"></a>6,1: Använd Azure Asset Discovery

**Vägledning**: Använd Azure Resource Graph för att fråga/identifiera alla resurser (t. ex. data bearbetning, lagring, nätverk, portar och protokoll osv.) i din prenumeration (er).  Se till att du har rätt (Läs) behörigheter i din klient organisation och räkna upp alla Azure-prenumerationer samt resurser i dina prenumerationer.

Även om klassiska Azure-resurser kan identifieras via resurs diagram, rekommenderar vi starkt att du skapar och använder Azure Resource Manager resurser som går framåt.

- [Så här skapar du frågor med Azure Resource Graph](../governance/resource-graph/first-query-portal.md)

- [Så här visar du dina Azure-prenumerationer](/powershell/module/az.accounts/get-azsubscription?view=azps-3.0.0)

- [Förstå Azure RBAC](../role-based-access-control/overview.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="62-maintain-asset-metadata"></a>6,2: underhåll till gångens metadata

**Vägledning**: Använd taggar till Azure-resurser som ger metadata till att logiskt organisera dem i en taxonomi.

- [Skapa och använda Taggar](../azure-resource-manager/management/tag-resources.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="63-delete-unauthorized-azure-resources"></a>6,3: ta bort obehöriga Azure-resurser

**Vägledning**: Använd taggning, hanterings grupper och separata prenumerationer om det behövs för att organisera och spåra Azure-resurser. Stäm av inventering regelbundet och se till att obehöriga resurser tas bort från prenumerationen inom rimlig tid.

Använd dessutom Azure policy för att ange begränsningar för den typ av resurser som kan skapas i kund prenumerationer med hjälp av följande inbyggda princip definitioner: ej tillåtna resurs typer tillåtna resurs typer

- [Så här skapar du ytterligare Azure-prenumerationer](../cost-management-billing/manage/create-subscription.md)

- [Så här skapar du Hanteringsgrupper](../governance/management-groups/create-management-group-portal.md)

- [Skapa och använda Taggar](../azure-resource-manager/management/tag-resources.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="64-maintain-an-inventory-of-approved-azure-resources-and-software-titles"></a>6,4: underhåll en inventering av godkända Azure-resurser och program varu titlar

**Vägledning**: definiera godkända Azure-resurser och godkänd program vara för beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="65-monitor-for-unapproved-azure-resources"></a>6,5: övervaka för ej godkända Azure-resurser

**Vägledning**: Använd Azure policy för att ange begränsningar för den typ av resurser som kan skapas i dina prenumerationer. 

Använd Azure Resource Graph för att fråga/identifiera resurser i sina prenumerationer.  Se till att alla Azure-resurser som finns i miljön är godkända. 

- [Konfigurera och hantera Azure Policy](../governance/policy/tutorials/create-and-manage.md)

- [Så här skapar du frågor med Azure Graph](../governance/resource-graph/first-query-portal.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="66-monitor-for-unapproved-software-applications-within-compute-resources"></a>6,6: övervaka för program som inte godkänts i beräknings resurser

**Vägledning**: ej tillämpligt; den här rekommendationen är avsedd för IaaS-beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="67-remove-unapproved-azure-resources-and-software-applications"></a>6,7: ta bort icke godkända Azure-resurser och program

**Vägledning**: ej tillämpligt; den här rekommendationen är avsedd för IaaS-beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="68-use-only-approved-applications"></a>6,8: Använd endast godkända program

**Vägledning**: ej tillämpligt; den här rekommendationen är avsedd för IaaS-beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="69-use-only-approved-azure-services"></a>6,9: Använd endast godkända Azure-tjänster

**Vägledning**: Använd Azure policy för att ange begränsningar för den typ av resurser som kan skapas i kund prenumerationer med hjälp av följande inbyggda princip definitioner: ej tillåtna resurs typer tillåtna resurs typer

- [Konfigurera och hantera Azure Policy](../governance/policy/tutorials/create-and-manage.md)

- [Så här nekar du en speciell resurs typ med Azure Policy](../governance/policy/samples/index.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="610-implement-approved-application-list"></a>6,10: implementera lista över godkända program

**Vägledning**: ej tillämpligt; den här rekommendationen är avsedd för IaaS-beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="611-limit-users-ability-to-interact-with-azure-resources-manager-via-scripts"></a>6,11: begränsa användarnas möjlighet att interagera med Azures resurs hanterare via skript

**Vägledning**: Konfigurera villkorlig åtkomst i Azure för att begränsa användarnas möjlighet att interagera med Azure Resource Manager genom att konfigurera "blockera åtkomst" för appen "Microsoft Azure hantering".

- [Så här konfigurerar du villkorlig åtkomst för att blockera åtkomst till Azure Resource Manager](../role-based-access-control/conditional-access-azure-management.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="612-limit-users-ability-to-execute-scripts-within-compute-resources"></a>6,12: begränsa användarnas möjlighet att köra skript i beräknings resurser

**Vägledning**: ej tillämpligt; den här rekommendationen är avsedd för IaaS-beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="613-physically-or-logically-segregate-high-risk-applications"></a>6,13: fysiskt eller logiskt särskiljande program med hög risk

**Vägledning**: för känsliga eller hög risk funktioner kan du implementera separata prenumerationer och/eller hanterings grupper för att tillhandahålla isolering.

Distribuera program med hög risk funktion till sina egna Virtual Network (VNet). Perimeter-säkerhet för Function-appar uppnås via virtuella nätverk. Funktioner som körs i Premium-planen eller App Service-miljön (ASE) kan integreras med virtuella nätverk. Välj den bästa arkitekturen för ditt användnings fall.

- [Nätverksalternativ för Azure Functions](./functions-networking-options.md)

- [Azure Functions Premium-plan](./functions-premium-plan.md)

- [Nätverksöverväganden för en App Service-miljö](../app-service/environment/network-info.md)

- [Så här skapar du en extern ASE](../app-service/environment/create-external-ase.md)

Så här skapar du en intern ASE:

- [https://docs.microsoft.com/azure/app-service/environment/create-ilb-as](../virtual-network/quick-create-portal.md)

- [Så här skapar du en NSG med en säkerhets konfiguration](../virtual-network/tutorial-filter-network-traffic.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

## <a name="secure-configuration"></a>Säker konfiguration

*Mer information finns i [säkerhets kontroll: säker konfiguration](../security/benchmarks/security-control-secure-configuration.md).*

### <a name="71-establish-secure-configurations-for-all-azure-resources"></a>7,1: upprätta säkra konfigurationer för alla Azure-resurser

**Vägledning**: definiera och implementera standardkonfigurationer för din Function-app med Azure policy. Använd Azure Policy alias i namn området "Microsoft. Web" för att skapa anpassade principer för att granska eller tillämpa konfigurationen för dina funktions program. Du kan också använda inbyggda princip definitioner som:
- Hanterad identitet ska användas i din Function-app
- Fjärrfelsökning bör inaktive ras för Function-appar
- Function-appen bör endast vara tillgänglig via HTTPS

- [Visa tillgängliga Azure Policy alias](/powershell/module/az.resources/get-azpolicyalias?view=azps-3.3.0)

- [Konfigurera och hantera Azure Policy](../governance/policy/tutorials/create-and-manage.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="72-establish-secure-operating-system-configurations"></a>7,2: upprätta säkra konfigurationer för operativ system

**Vägledning**: ej tillämpligt; den här rikt linjen är avsedd för IaaS beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="73-maintain-secure-azure-resource-configurations"></a>7,3: underhåll säker Azure-resurs-konfigurationer

**Vägledning**: Använd Azure policy [Deny] och [distribuera om det inte finns] för att genomdriva säkra inställningar i dina Azure-resurser.

- [Konfigurera och hantera Azure Policy](../governance/policy/tutorials/create-and-manage.md)

- [Förstå Azure Policys effekter](../governance/policy/concepts/effects.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="74-maintain-secure-operating-system-configurations"></a>7,4: underhåll säkra konfigurationer för operativ system

**Vägledning**: ej tillämpligt; även om det är möjligt att distribuera lokala funktioner, är den här rikt linjen avsedd för IaaS beräknings resurser. När du distribuerar lokala funktioner ansvarar du för den säkra konfigurationen för din miljö.

- [Förstå lokala funktioner](./functions-runtime-install.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="75-securely-store-configuration-of-azure-resources"></a>7,5: Spara konfigurationen av Azure-resurser på ett säkert sätt

**Vägledning**: lagra och hantera arm-mallar och anpassade Azure policy-definitioner på ett säkert sätt i käll kontroll.

- [Vad är infrastruktur som kod](/azure/devops/learn/what-is-infrastructure-as-code)

- [Design princip som kod arbets flöden](../governance/policy/concepts/policy-as-code.md)

- [Så här lagrar du kod i Azure DevOps](/azure/devops/repos/git/gitworkflow?view=azure-devops)

- [Dokumentation om Azure databaser](/azure/devops/repos/index?view=azure-devops)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="76-securely-store-custom-operating-system-images"></a>7,6: lagra anpassade operativ Systems avbildningar på ett säkert sätt

**Vägledning**: ej tillämpligt; den här rikt linjen är avsedd för IaaS beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="77-deploy-system-configuration-management-tools"></a>7,7: Distribuera hanterings verktyg för system konfiguration

**Vägledning**: använd inbyggda Azure policy definitioner samt Azure policy alias i namn området "Microsoft. Web" för att skapa anpassade principer för att varna, granska och genomdriva system konfigurationer. Dessutom kan du utveckla en process och pipeline för att hantera princip undantag.

- [Konfigurera och hantera Azure Policy](../governance/policy/tutorials/create-and-manage.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="78-deploy-system-configuration-management-tools-for-operating-systems"></a>7,8: distribuera system konfigurations hanterings verktyg för operativ system

**Vägledning**: ej tillämpligt; den här rikt linjen är avsedd för IaaS beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="79-implement-automated-configuration-monitoring-for-azure-services"></a>7,9: implementera automatisk konfigurations övervakning för Azure-tjänster

**Vägledning**: använd inbyggda Azure policy definitioner samt Azure policy alias i namn området "Microsoft. Web" för att skapa anpassade principer för att varna, granska och genomdriva system konfigurationer. Använd Azure-princip [granskning], [neka] och [distribuera om det inte finns] för att automatiskt tillämpa konfigurationer för dina Azure-resurser.

- [Konfigurera och hantera Azure Policy](../governance/policy/tutorials/create-and-manage.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="710-implement-automated-configuration-monitoring-for-operating-systems"></a>7,10: implementera automatisk konfigurations övervakning för operativ system

**Vägledning**: ej tillämpligt; den här rikt linjen är avsedd för IaaS beräknings resurser.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="711-manage-azure-secrets-securely"></a>7,11: Hantera Azure-hemligheter på ett säkert sätt

**Vägledning**: Använd hanterade identiteter tillsammans med Azure Key Vault för att förenkla och skydda hemlig hantering för dina moln program. Med hanterade identiteter kan din Function-app autentisera till alla tjänster som stöder Azure AD-autentisering, inklusive Key Vault, utan några autentiseringsuppgifter i koden.

- [Så här skapar du en Key Vault](../key-vault/secrets/quick-create-portal.md)

- [Använda hanterade identiteter för App Service och Azure Functions](../app-service/overview-managed-identity.md)

* [Så här autentiserar du till Key Vault](../key-vault/general/authentication.md)

* [Så här tilldelar du en Key Vault åtkomst princip](../key-vault/general/assign-access-policy-portal.md)

- [Använd Key Vault referenser för App Service och Azure Functions](../app-service/app-service-key-vault-references.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="712-manage-identities-securely-and-automatically"></a>7,12: hantera identiteter säkert och automatiskt

**Vägledning**: Använd hanterade identiteter för att tillhandahålla din Function-app med en automatiskt hanterad identitet i Azure AD. Med hanterade identiteter kan du autentisera till vilken tjänst som helst som stöder Azure AD-autentisering, inklusive Key Vault utan autentiseringsuppgifter i din kod.

- [Använda hanterade identiteter för App Service och Azure Functions](../app-service/overview-managed-identity.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="713-eliminate-unintended-credential-exposure"></a>7,13: eliminera oavsiktlig exponering för autentiseringsuppgifter

**Vägledning**: implementera autentiseringsuppgifterna för inloggning för att identifiera autentiseringsuppgifter inom koden. Credential Scanner uppmanar också till att flytta identifierade autentiseringsuppgifter till en säkrare plats som Azure Key Vault. 

- [Konfigurera inloggnings skannern](https://secdevtools.azurewebsites.net/helpcredscan.html)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

## <a name="malware-defense"></a>Skydd mot skadlig kod

*Mer information finns i [säkerhets kontroll: försvar mot skadlig kod](../security/benchmarks/security-control-malware-defense.md).*

### <a name="81-use-centrally-managed-anti-malware-software"></a>8,1: Använd centralt hanterat program mot skadlig kod

**Vägledning**: ej tillämpligt; den här rikt linjen är avsedd för IaaS beräknings resurser.

Microsofts program mot skadlig kod har Aktiver ATS på den underliggande värden som har stöd för Azure-tjänster (till exempel Azure Functions), men det körs inte på kund innehållet.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Microsoft

### <a name="82-pre-scan-files-to-be-uploaded-to-non-compute-azure-resources"></a>8,2: för skanning av filer som ska laddas upp till Azure-resurser som inte är Compute

**Vägledning**: ej tillämpligt; den här rekommendationen är avsedd för icke-Compute-resurser som är utformade för att lagra data.


**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

### <a name="83-ensure-anti-malware-software-and-signatures-are-updated"></a>8,3: se till att program vara och signaturer för skadlig program vara uppdateras

**Vägledning**: ej tillämpligt; den här rekommendationen är avsedd för icke-Compute-resurser som är utformade för att lagra data.

Microsofts program mot skadlig kod har Aktiver ATS på den underliggande värden som har stöd för Azure-tjänster (till exempel Azure Functions), men det körs inte på kund innehållet.

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvars område**: inte tillämpligt

## <a name="data-recovery"></a>Dataåterställning

*Mer information finns i [säkerhets kontroll: Data återställning](../security/benchmarks/security-control-data-recovery.md).*

### <a name="91-ensure-regular-automated-back-ups"></a>9,1: se till att vanlig automatisk säkerhets kopiering UPS

**Vägledning**: Använd funktionen säkerhets kopiering och återställning för att schemalägga regelbundna säkerhets kopieringar av din app. Function-appar som körs i Premium-planen har samma värd funktioner som webbappar i Azure App Service, vilket innefattar funktionen säkerhets kopiering och återställning.

Du kan också använda en lösning för käll kontroll som Azure databaser och Azure DevOps för att lagra och hantera din kod på ett säkert sätt. Azure DevOps Services utnyttjar många av funktionerna i Azure Storage för att säkerställa att data är tillgängliga i händelse av maskinvaruproblem, avbrott i tjänsten eller haveri. Azure DevOps-teamet följer dessutom procedurer för att skydda data från oavsiktlig eller skadlig borttagning.

- [Säkerhetskopiera din app i Azure](../app-service/manage-backup.md)

- [Förstå data tillgänglighet i Azure DevOps](/azure/devops/organizations/security/data-protection?view=azure-devops#data-availability)

- [Så här lagrar du kod i Azure DevOps](/azure/devops/repos/git/gitworkflow?view=azure-devops)

- [Dokumentation om Azure databaser](/azure/devops/repos/index?view=azure-devops)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="92-perform-complete-system-backups-and-backup-any-customer-managed-keys"></a>9,2: Utför fullständig säkerhets kopiering av systemet och säkerhetskopiera alla Kundhanterade nycklar

**Vägledning**: Använd funktionen säkerhets kopiering och återställning för att schemalägga regelbundna säkerhets kopieringar av din app. Function-appar som körs i Premium-planen har samma värd funktioner som webbappar i Azure App Service, vilket innefattar funktionen säkerhets kopiering och återställning. Säkerhetskopiera kund hanterade nycklar inom Azure Key Vault.

Du kan också använda en lösning för käll kontroll som Azure databaser och Azure DevOps för att lagra och hantera din kod på ett säkert sätt. Azure DevOps Services utnyttjar många av funktionerna i Azure Storage för att säkerställa att data är tillgängliga i händelse av maskinvaruproblem, avbrott i tjänsten eller haveri. Azure DevOps-teamet följer dessutom procedurer för att skydda data från oavsiktlig eller skadlig borttagning.

- [Säkerhetskopiera din app i Azure](../app-service/manage-backup.md)

- [Så här säkerhetskopierar du nyckel valv nycklar i Azure](/powershell/module/azurerm.keyvault/backup-azurekeyvaultkey)

- [Förstå data tillgänglighet i Azure DevOps](/azure/devops/organizations/security/data-protection?view=azure-devops#data-availability)

- [Så här lagrar du kod i Azure DevOps](/azure/devops/repos/git/gitworkflow?view=azure-devops)

- [Dokumentation om Azure databaser](/azure/devops/repos/index?view=azure-devops)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="93-validate-all-backups-including-customer-managed-keys"></a>9,3: validera alla säkerhets kopior inklusive Kundhanterade nycklar

**Vägledning**: Säkerställ att du regelbundet kan utföra återställning från säkerhets kopierings-och återställnings funktionen. Om du använder en annan plats offline för att säkerhetskopiera din kod, så kan du regelbundet se till att slutföra fullständiga återställningar. Testa återställning av säkerhetskopierade nycklar som hanteras av kunden.

- [Återställa en app i Azure från en säkerhets kopia](../app-service/web-sites-restore.md)

- [Återställa en app i Azure från en ögonblicks bild](../app-service/app-service-web-restore-snapshots.md)

- [Återställa Key Vault-nycklar i Azure](/powershell/module/azurerm.keyvault/restore-azurekeyvaultkey?view=azurermps-6.13.0)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="94-ensure-protection-of-backups-and-customer-managed-keys"></a>9,4: se till att skydda säkerhets kopior och Kundhanterade nycklar

**Vägledning**: säkerhets kopieringar från funktionen säkerhets kopiering och återställning använder ett Azure Storage konto i din prenumeration. Azure Storage krypterar alla data i ett lagrings konto i vila. Som standard krypteras data med Microsoft-hanterade nycklar. Om du vill ha ytterligare kontroll över krypterings nycklar kan du ange Kundhanterade nycklar för kryptering av lagrings data.

Om du använder Kundhanterade nycklar kontrollerar du att Soft-Delete i Key Vault är aktiverat för att skydda nycklar mot oavsiktlig eller skadlig borttagning.

- [Azure Storage-kryptering i vila](../storage/common/storage-service-encryption.md)

- [Så här aktiverar du Soft-Delete i Key Vault](../storage/blobs/soft-delete-blob-overview.md?tabs=azure-portal)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Delad

## <a name="incident-response"></a>Incidenthantering

*Mer information finns i [säkerhets kontroll: incident svar](../security/benchmarks/security-control-incident-response.md).*

### <a name="101-create-an-incident-response-guide"></a>10,1: skapa en incident svars guide

**Vägledning**: Skapa en guide till incidentsvar för organisationen. Se till att det finns skriftliga planer för incidentsvar som definierar alla personalroller och faser i incidenthanteringen, från identifiering till granskning efter incidenten.

- [Konfigurera automatisering av arbets flöden i Azure Security Center](../security-center/security-center-planning-and-operations-guide.md)

- [Vägledning om hur du skapar en egen svars process för säkerhets incidenter](https://msrc-blog.microsoft.com/2019/07/01/inside-the-msrc-building-your-own-security-incident-response-process/)

- [Microsoft Security Response Centers Beskrivning av en incident](https://msrc-blog.microsoft.com/2019/07/01/inside-the-msrc-building-your-own-security-incident-response-process/)

- [Kunden kan också utnyttja NISTs hanterings guide för dator säkerhet för att hjälpa till med att skapa egna incident svars planer](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="102-create-an-incident-scoring-and-prioritization-procedure"></a>10,2: skapa en incident bedömnings-och prioriterings procedur

**Vägledning**: Security Center tilldelar en allvarlighets grad till varje avisering för att hjälpa dig att prioritera vilka aviseringar som bör undersökas först. Allvarlighets graden baseras på hur tillförlitlig Security Center befinner sig i att söka efter eller det analytiska som används för att utfärda aviseringen samt vilken konfidensnivå som det fanns skadlig avsikt bakom den aktivitet som ledde till aviseringen.

Dessutom är det tydligt att markera prenumerationer (t. ex. produktion, icke-Prod) och skapa ett namngivnings system för att tydligt identifiera och kategorisera Azure-resurser.

**Azure Security Center-övervakning**: Ja

**Ansvar**: Delad

### <a name="103-test-security-response-procedures"></a>10,3: testa säkerhets svars procedurer

**Vägledning**: utföra övningar för att testa dina Systems incident svars funktioner på en vanlig takt. Identifiera svaga punkter och luckor, och ändra planen efter behov.

- [Se NIST: guide för test, utbildning och övnings program för IT-planer och funktioner](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-84.pdf)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="104-provide-security-incident-contact-details-and-configure-alert-notifications-for-security-incidents"></a>10,4: Ange kontakt information för säkerhets incidenter och konfigurera aviseringar för säkerhets incidenter

**Vägledning**: kontakt information om säkerhets incidenter kommer att användas av Microsoft för att kontakta dig om Microsoft Security Response Center (MSRC) upptäcker att kundens data har öppnats av en olaglig eller obehörig part.  Granska incidenter när du är säker på att problemen är lösta.

- [Så här ställer du in Azure Security Center säkerhets kontakt](../security-center/security-center-provide-security-contact-details.md)

**Azure Security Center-övervakning**: Ja

**Ansvar**: Kund

### <a name="105-incorporate-security-alerts-into-your-incident-response-system"></a>10,5: införliva säkerhets aviseringar i ditt incident svars system

**Vägledning**: exportera Azure Security Center aviseringar och rekommendationer med hjälp av funktionen för kontinuerlig export. Med kontinuerlig export kan du exportera aviseringar och rekommendationer antingen manuellt eller i löpande miljö. Du kan använda Azure Security Center Data Connector för att strömma aviseringarna till Azure Sentinel.

- [Så här konfigurerar du kontinuerlig export](../security-center/continuous-export.md)

- [Så här strömmar du aviseringar till Azure Sentinel](../sentinel/connect-azure-security-center.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

### <a name="106-automate-the-response-to-security-alerts"></a>10,6: automatisera svaret på säkerhets aviseringar

**Vägledning**: Använd funktionen för automatisering av arbets flöden i Azure Security Center för att automatiskt utlösa svar på säkerhets aviseringar och rekommendationer med Logic Apps.

- [Konfigurera automatisering av arbets flöden och Logic Apps](../security-center/workflow-automation.md)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Kund

## <a name="penetration-tests-and-red-team-exercises"></a>Penetrationstester och Red Team-tester

*Mer information finns i [säkerhets kontroll: inträngande tester och röda team övningar](../security/benchmarks/security-control-penetration-tests-red-team-exercises.md).*

### <a name="111-conduct-regular-penetration-testing-of-your-azure-resources-and-ensure-remediation-of-all-critical-security-findings"></a>11,1: utför regelbundna inträngande tester av dina Azure-resurser och se till att åtgärda alla viktiga säkerhets brister

**Vägledning**: Följ Microsofts regler för engagemang för att se till att dina inträngande tester inte strider mot Microsofts principer. Använd Microsofts strategi och körning av röda team indelning och inträngande av direktsända webbplatser mot Microsoft-hanterad moln infrastruktur, tjänster och program.

- [Regler för intrångstester](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1)

- [”Red team”-aktiviteter i Microsoft Cloud](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Övervakning i Azure Security Center**: Ej tillämpligt

**Ansvar**: Delad

## <a name="next-steps"></a>Nästa steg

- Se [Azures säkerhets benchmark](../security/benchmarks/overview.md)
- Läs mer om [säkerhetsbaslinjer för Azure](../security/benchmarks/security-baselines-overview.md)
