---
title: Vad är Azure Digital Twins?
titleSuffix: Azure Digital Twins
description: Översikt över vad som kan göras med Azure Digital-dubbla.
author: baanders
ms.author: baanders
ms.date: 3/12/2020
ms.topic: overview
ms.service: digital-twins
ms.openlocfilehash: 91915f204a68d59a603b8bdea383b497a5b33d34
ms.sourcegitcommit: 52e3d220565c4059176742fcacc17e857c9cdd02
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/21/2021
ms.locfileid: "98664035"
---
# <a name="what-is-azure-digital-twins"></a>Vad är Azure Digital Twins?

**Azure Digitals** är ett PaaS-erbjudande (Platform as a Service) som gör det möjligt att skapa kunskaps grafer baserade på digitala modeller av hela miljöer. De här miljöerna kan vara byggnader, fabriker, anläggningar, energi nät, järnvägar, stadium med mera, även hela städer. Dessa digitala modeller kan användas för att få insikter om bättre produkter, optimerade åtgärder, lägre kostnader och revolutionerande kund upplevelser.

Utnyttja dina domän expert kunskaper ovanpå Azure Digitals, för att bygga anpassade, anslutna lösningar som:
* Modellera valfri miljö och få digitala längder på ett skalbart och säkert sätt
* Ansluta till gångar som IoT-enheter och befintliga företags system
* Använd ett robust händelse system för att bygga dynamisk affärs logik och data bearbetning
* Integrera med Azure data-, Analytics-och AI-tjänster som hjälper dig att spåra den senaste och Förutsäg sedan framtiden

## <a name="azure-digital-twins-capabilities"></a>Azure Digitals dubbla funktioner

Här är en sammanfattning av de funktioner som tillhandahålls av Azure Digitals flätas.

### <a name="open-modeling-language"></a>Öppna modellerings språk

I Azure Digitals, definierar du de digitala entiteter som representerar personer, platser och saker i din fysiska miljö med anpassade dubbla typer som kallas [**modeller**](concepts-models.md). 

Du kan tänka på dessa modell definitioner som en specialiserad vokabulär för att beskriva ditt företag. För att skapa en hanterings lösning kan du till exempel definiera modeller som "byggnad", "golv" och "hiss". Du kan sedan skapa **digitala dubbla** nätverk baserat på dessa modeller för att representera din speciella miljö.

[!INCLUDE [digital-twins-versus-device-twins](../../includes/digital-twins-versus-device-twins.md)]

Modeller definieras i ett JSON-liknande språk som kallas för [digitala DTDL (Endefinierat definitions språk)](https://github.com/Azure/opendigitaltwins-dtdl/blob/master/DTDL/v2/dtdlv2.md)och de beskriver vad de har för tillstånds egenskaper, telemetri, kommandon, komponenter och relationer.
* Modeller definierar semantiska **relationer** mellan dina entiteter så att du kan ansluta dina delar till ett kunskaps diagram som återspeglar deras interaktioner. Du kan tänka dig att modeller som Substantiv i en beskrivning av din värld och relationerna som verb.
* Du kan också specialisera dig på att använda modell arv. En modell kan ärva från en annan.

DTDL används för data modeller i andra Azure IoT-tjänster, inklusive [IoT plug and Play (PNP)](../iot-pnp/overview-iot-plug-and-play.md) och [Time Series Insights (TSD)](../time-series-insights/overview-what-is-tsi.md). Detta hjälper dig att hålla din Azure digital-lösning ansluten och kompatibel med andra delar av Azure-eko systemet.

### <a name="live-execution-environment"></a>Livekörningsmiljö

Digitala modeller i digitala Azure-sändningar är Live, uppdaterade representationer av den verkliga världen. Med hjälp av relationerna i dina anpassade DTDL-modeller kan du ansluta dubbla till en **levande graf** som representerar din miljö.

Du kan visa en visualisering av ditt Azure Digitals-diagram genom att använda ett exempel program, en [**Azure Digital-Utforskare**](/samples/azure-samples/digital-twins-explorer/digital-twins-explorer/).

Så här ser exempel visualiseringen ut:

:::image type="content" source="media/includes/azure-digital-twins-explorer.png" alt-text="Skärm bild av exempel programmet för Azure Digitals flätad Utforskare som visar ett diagram över noder som representerar digitala dubbla" lightbox="media/includes/azure-digital-twins-explorer.png":::

Azure Digitals dubbla är ett omfattande **händelse system** för att hålla diagrammet aktuellt med data behandling och affärs logik. Du kan ansluta externa beräknings resurser, till exempel [Azure Functions](../azure-functions/functions-overview.md), för att köra den här data bearbetningen på ett flexibelt och anpassat sätt.

Du kan också extrahera insikter från miljön för Live-körning med hjälp av Azure Digitals "kraftfulla **fråge-API**. Med API: et kan du fråga med omfattande Sök villkor, inklusive egenskaps värden, relationer, Relations egenskaper, modell information och mycket annat. Du kan också kombinera frågor, samla in en mängd olika insikter om din miljö och besvara anpassade frågor som är viktiga för dig.

### <a name="input-from-iot-and-business-systems"></a>Mata in från IoT och företags system

För att hålla den aktiva Azure-miljön i Azure Digital är uppdaterad med den verkliga världen, kan du använda [IoT Hub](../iot-hub/about-iot-hub.md) för att ansluta din lösning till IoT och IoT Edge enheter. Dessa nav-hanterade enheter visas som en del av ditt dubbla diagram och tillhandahåller de data som driver din modell.

Du kan skapa en ny IoT Hub för detta ändamål med Azure Digitals, eller ansluta ett befintligt IoT Hub tillsammans med de enheter som den redan hanterar.

Du kan också köra Azure Digitals-enheter från andra data källor med hjälp av REST API: er eller kopplingar till andra tjänster som [Logic Apps](../logic-apps/logic-apps-overview.md).

### <a name="output-to-tsi-storage-and-analytics"></a>Utdata till TSD, Storage och Analytics

Data i din Azure Digital-modell med dubbla modeller kan dirigeras till underordnade Azure-tjänster för ytterligare analys eller lagring. Detta tillhandahålls via **händelse vägar**, som använder [händelsehubben](../event-hubs/event-hubs-about.md), [Event Grid](../event-grid/overview.md)eller [Service Bus](../service-bus-messaging/service-bus-messaging-overview.md) för att driva dina önskade data flöden.

Några saker du kan göra med händelse vägar är:
* Lagra Azure Digital Twins-data i [Azure Data Lake](../storage/blobs/data-lake-storage-introduction.md)
* Analysera Azure Digital Twins-data med [Azure Synapse Analytics](../synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-what-is.md) eller andra Microsoft-verktyg för dataanalys
* Integrera större arbetsflöden med Logic Apps
* Att ansluta Azure Digitals dubbla steg till Time Series Insights för att spåra tids serie historiken för varje dubbla
* Anpassa en Time Series-modell i Time Series Insights med en källa i Azure Digital Twins

Det här är ett annat sätt att Azure Digitals, kan ansluta till en större lösning och stödja dina anpassade behov för att fortsätta arbeta med dessa insikter.

## <a name="azure-digital-twins-in-a-solution-context"></a>Azure Digitals dubbla i en lösnings kontext

Azure Digitals, används ofta i kombination med andra Azure-tjänster som en del av en större IoT-lösning. 

En komplett lösning som använder digitala Azure-dubbla, kan innehålla följande delar:
* Azure Digitals dubbla tjänst instans. Detta lagrar dina dubbla modeller och det dubbla diagrammet med sitt tillstånd och dirigerar händelse bearbetning.
* En eller flera klient program som driver den digitala Azure-instansen genom att konfigurera modeller, skapa topologi och extrahera insikter från den dubbla grafen.
* En eller flera externa beräknings resurser för att bearbeta händelser som genererats av digitala Azure-enheter eller anslutna data källor, t. ex. enheter. Ett vanligt sätt att tillhandahålla beräknings resurser är via [Azure Functions](../azure-functions/functions-overview.md).
* En IoT-hubb för att tillhandahålla funktioner för enhets hantering och IoT-dataströmmar.
* Underordnade tjänster för hantering av uppgifter, till exempel arbets flödes integrering (t. ex. [Logic Apps](../logic-apps/logic-apps-overview.md), kall lagring, tids serie integrering eller analys).

Följande diagram visar var Azure Digitals dubbla är i sammanhanget för en större Azure IoT-lösning.

:::image type="content" source="media/overview/solution-context.png" alt-text="Diagram över inmatnings källor, utgående tjänster och tvåvägs kommunikation med både klient-och externa beräknings resurser." border="false" lightbox="media/overview/solution-context.png":::

## <a name="service-limits"></a>Tjänstbegränsningar

En lista över gränser för digital Digitals dubbla gränser finns i [*referens: tjänst begränsningar*](reference-service-limits.md).

## <a name="next-steps"></a>Nästa steg

Om du har arbetat med den första för hands versionen av Azure Digitals (oktober 2018), lär du dig vad som har ändrats: [*Översikt: skillnader från den första versionen*](overview-differences.md).

Du kan också gå vidare och lära dig att arbeta med Azure Digitals dubbla med snabb start: [*snabb start: utforska ett exempel scenario*](quickstart-adt-explorer.md).