---
title: Delat ansvar i Cloud-Microsoft Azure
description: Förstå den delade ansvars modellen och vilka säkerhets aktiviteter som hanteras av moln leverantören och vilka aktiviteter som hanteras av dig.
services: security
documentationcenter: na
author: TerryLanfear
manager: rkarlin
editor: na
ms.assetid: ''
ms.service: security
ms.subservice: security-fundamentals
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/16/2019
ms.author: terrylan
ms.openlocfilehash: 8f16105d6bda1798828bc423ec8a158d49e0cf2b
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/09/2020
ms.locfileid: "72518374"
---
# <a name="shared-responsibility-in-the-cloud"></a>Delat ansvar i molnet

När du bedömer och utvärderar offentliga moln tjänster är det viktigt att förstå den delade ansvars modellen och vilka säkerhets aktiviteter som hanteras av moln leverantören och vilka aktiviteter som hanteras av dig. Arbets Belastningens ansvar varierar beroende på om arbets belastningen finns på program vara som en tjänst (SaaS), plattform som en tjänst (PaaS), infrastruktur som en tjänst (IaaS) eller i ett lokalt Data Center

## <a name="division-of-responsibility"></a>Ansvars Division
I ett lokalt Data Center äger du hela stacken. När du flyttar till molnet kan du överföra vissa ansvars områden till Microsoft. I följande diagram illustreras ansvars områdena mellan dig och Microsoft, enligt vilken typ av stack du har.

![Ansvars zoner](./media/shared-responsibility/shared-responsibility.png)

Du äger dina data och identiteter oavsett typen av molndistribution. Du ansvarar för att skydda säkerheten för dina data och identiteter, lokala resurser och de moln komponenter som du styr (beroende på tjänst typ).

Oavsett typ av distribution behålls alltid följande ansvar:

- Data
- Slutpunkter
- Konto
- Åtkomsthantering

## <a name="cloud-security-advantages"></a>Fördelar med moln säkerhet
Molnet erbjuder avsevärda fördelar för att lösa långa ständiga data säkerhets utmaningar. I en lokal miljö har organisationer troligen ouppfyllda ansvar och begränsade resurser som är tillgängliga för att investera i säkerhet, vilket skapar en miljö där angripare kan utnyttja sårbarheter på alla nivåer.

Följande diagram visar en traditionell metod där många säkerhets ansvars områden ouppfyllda på grund av begränsade resurser. I den molnbaserade metoden kan du byta dag till dagens säkerhets ansvars områden för din moln leverantör och omallokera dina resurser.

![Säkerhets fördelarna med moln era](./media/shared-responsibility/cloud-enabled-security.png)

I den molnbaserade metoden kan du också utnyttja molnbaserade säkerhetsfunktioner för att öka effektiviteten och använda Cloud Intelligence för att förbättra din hot identifiering och svars tid. Genom att ändra ansvars områden till moln leverantören kan organisationer få mer säkerhets täckning, vilket gör att de kan allokera om säkerhets resurser och budget till andra affärs prioriteringar.

## <a name="next-steps"></a>Nästa steg
Mer information om ansvars fördelningen mellan dig och Microsoft i en SaaS-, PaaS-och IaaS-distribution finns i [delade ansvars områden för molnbaserad data behandling](https://gallery.technet.microsoft.com/Shared-Responsibilities-81d0ff91).
