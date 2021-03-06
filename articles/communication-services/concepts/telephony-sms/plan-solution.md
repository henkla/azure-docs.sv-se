---
title: Planera din Azure Communication Services-telefoni och SMS-lösning
titleSuffix: An Azure Communication Services concept document
description: Lär dig att effektivt planera din användning av telefonnummer och telefoni.
author: prakulka
manager: nmurav
services: azure-communication-services
ms.author: prakulka
ms.date: 10/05/2020
ms.topic: overview
ms.custom: references_regions
ms.service: azure-communication-services
ms.openlocfilehash: 271d7ce38d50fd21975327eb1f21528aeacc485e
ms.sourcegitcommit: dea56e0dd919ad4250dde03c11d5406530c21c28
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96937244"
---
# <a name="plan-your-telephony-and-sms-solution"></a>Planera din telefoni- och SMS-lösning

[!INCLUDE [Public Preview Notice](../../includes/public-preview-include.md)]
[!INCLUDE [Regional Availability Notice](../../includes/regional-availability-include.md)]

Azure Communication Services gör att du kan använda telefonnummer för att ringa röst samtal och skicka SMS-meddelanden med det offentliga telefonnätet. I det här dokumentet granskar vi telefonnummer typer, konfigurations alternativ och regions tillgänglighet för att planera din telefoni-och SMS-lösning med hjälp av kommunikations tjänster.





## <a name="phone-number-types-in-azure-communication-services"></a>Telefonnummer typer i Azure Communication Services
 
Kommunikations tjänsterna erbjuder två typer av telefonnummer: **lokalt** och **avgiftsfritt**. 

### <a name="local-numbers"></a>Lokala nummer
Lokala (geografiska) nummer är 10-siffriga telefonnummer som består av de lokala rikt numren i USA. Är till exempel `+1 (206) XXX-XXXX` ett lokalt nummer med ett rikt nummer för `206` . Det här rikt numret tilldelas staden Seattle. Dessa telefonnummer används vanligt vis av enskilda personer och lokala företag. Azure Communication Services erbjuder lokala nummer i USA. Dessa siffror kan användas för att ringa telefonsamtal, men inte för att skicka SMS-meddelanden. 

### <a name="toll-free-numbers"></a>Avgiftsfritt nummer
Avgiftsfritt nummer är 10-siffriga telefonnummer med distinkta rikt nummer som kan anropas från ett telefonnummer kostnads fritt. Till exempel `+1 (800) XXX-XXXX` är ett avgiftsfritt nummer i Nordamerika regionen. Dessa telefonnummer används vanligt vis för kund tjänst. Azure Communication Services erbjuder avgiftsfria nummer i USA. De här numren kan användas för att ringa telefonsamtal och skicka SMS-meddelanden. Avgiftsfritt nummer kan inte användas av personer och kan bara tilldelas till program.

#### <a name="choosing-a-phone-number-type"></a>Välja en telefonnummer typ

Om ditt telefonnummer ska användas av ett program (till exempel för att ringa eller skicka meddelanden åt din tjänst), kan du välja ett avgiftsfritt eller lokalt (geografiskt) nummer. Du kan välja ett avgiftsfritt nummer om ditt program skickar SMS-meddelanden och/eller gör anrop.

Om ditt telefonnummer används av en person (till exempel en användare av ditt anrops program), måste det lokala (geografiska) telefonnumret användas. 

I tabellen nedan sammanfattas dessa telefonnummer typer: 

| Typ av telefonnummer | Exempel                              | Lands tillgänglighet    | Telefon funktion |Vanligt användnings fall                                                                                                     |
| ----------------- | ------------------------------------ | ----------------------- | ------------------------|------------------------------------------------------------------------------------------------------------------- |
| Lokalt (geografiskt)        | + 1 (lokalt rikt nummer) XXX XX XX  | USA                      | Anropar (utgående) | Tilldela telefonnummer till användare i dina program  |
| Toll-Free         | + 1 (avgiftsfrit rikt *nummer*) xxx xx xx | USA                      | Anrop (utgående), SMS (inkommande/utgående)| Tilldela telefonnummer till IVR-system/robotar-system (Interactive Voice Response), SMS-program                                        |


## <a name="phone-number-features-in-azure-communication-services"></a>Telefonnummer funktioner i Azure Communication Services 

[!INCLUDE [Emergency Calling Notice](../../includes/emergency-calling-notice-include.md)]

För de flesta telefonnummer ger vi dig möjlighet att konfigurera en "a la carte"-uppsättning funktioner. Dessa funktioner kan väljas när du lånar dina telefonnummer i Azure Communication Services.

Vilka funktioner som är tillgängliga beror på vilket land du arbetar i, ditt användnings fall och vilken typ av telefonnummer som du har valt. De här funktionerna varierar beroende på vilket land som är på grund av myndighets krav. Azure Communication Services erbjuder följande telefonnummer funktioner:

- **Envägs utgående SMS** Med det här alternativet kan du skicka SMS-meddelanden till dina användare. Detta kan vara användbart i meddelande-och tvåfaktorautentisering. 
- **Tvåvägs inkommande och utgående SMS** Med det här alternativet kan du skicka och ta emot meddelanden från dina användare med hjälp av telefonnummer. Detta kan vara användbart i kund tjänst scenarier.
- **Envägs utgående telefon samtal** Med det här alternativet kan du ringa till dina användare och konfigurera uppringnings-ID för utgående samtal som har placerats av tjänsten. Detta kan vara användbart i scenarier för kund tjänst och röst meddelanden.

## <a name="countryregion-availability"></a>Tillgänglighet för land/region

I följande tabell visas var du kan hämta olika typer av telefonnummer tillsammans med de inkommande och utgående anrops-och SMS-funktionerna som är kopplade till dessa telefonnummer typer.

|Siffer typ| Hämta nummer i | Gör anrop till                                        | Ta emot samtal från                                    |Skicka meddelanden till       | Ta emot meddelanden från |
|-----------| ------------------ | ---------------------------------------------------  |-------------------------------------------------------|-----------------------|--------|
| Lokalt (geografiskt)  | USA                 | USA, Kanada, Storbritannien, Tyskland, Frankrike. + Mer *| USA, Kanada, Storbritannien, Tyskland, Frankrike. + Mer * |Inte tillgänglig| Inte tillgänglig |
| Toll-Free | USA                 | USA                                                   | USA                                                    |USA                | USA |

* Mer information om samtals destinationer och priser finns på sidan med [priser](../pricing.md).

## <a name="azure-subscriptions-eligibility"></a>Azure-prenumerationer berättigar

För att skaffa ett telefonnummer måste du vara på en betald Azure-prenumeration. Det går inte att hämta telefonnummer för utvärderings konton eller kostnads fria Azure-krediter. 

För närvarande är telefonnumret för tillgänglighet begränsat till Azure-prenumerationer som har en fakturerings adress i USA.

## <a name="next-steps"></a>Nästa steg

### <a name="quickstarts"></a>Snabbstarter

- [Hämta ett telefonnummer](../../quickstarts/telephony-sms/get-phone-number.md)
- [Placera ett samtal](../../quickstarts/voice-video-calling/calling-client-samples.md)
- [Skicka ett SMS](../../quickstarts/telephony-sms/send.md)

### <a name="conceptual-documentation"></a>Konceptuell dokumentation

- [Begrepp inom röst- och videosamtal](../voice-video-calling/about-call-types.md)
- [Samtals flöden](../call-flows.md)
- [Prissättning](../pricing.md)
