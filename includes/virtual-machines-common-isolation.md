---
title: ta med fil
description: ta med fil
services: virtual-machines
author: styli365
ms.service: virtual-machines
ms.topic: include
ms.date: 11/05/2020
ms.author: sttsinar
ms.custom: include file
ms.openlocfilehash: bd31152c6742271658cf4fd7ac2a5e2957651c84
ms.sourcegitcommit: 6a350f39e2f04500ecb7235f5d88682eb4910ae8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96476781"
---
Azure Compute erbjuder storlekar för virtuella datorer som är isolerade till en viss maskin varu typ och som är dedikerad till en enda kund. De isolerade storlekarna är aktiva och fungerar på en speciell maskin varu generation och kommer att bli föråldrade när maskin varu genereringen dras tillbaka.

Isolerade storlekar på virtuella datorer lämpar sig bäst för arbets belastningar som kräver en hög grad av isolering från andra kunders arbets belastningar av skäl som innehåller krav på efterlevnad och regler.  Användning av en isolerad storlek garanterar att den virtuella datorn är den enda som körs på den aktuella Server instansen. 


Dessutom kan kunderna välja att dela upp resurserna för de virtuella datorerna med hjälp av [Azure-stöd för kapslade virtuella datorer](https://azure.microsoft.com/blog/nested-virtualization-in-azure/)eftersom de isolerade virtuella datorerna är stora.

De aktuella isolerade virtuella dator erbjudandena är:
* Standard_E64is_v3
* Standard_E64i_v3
* Standard_E80ids_v4
* Standard_E80is_v4
* Standard_M128ms
* Standard_GS5
* Standard_G5
* Standard_F72s_v2


> [!NOTE]
> Isolerade VM-storlekar har en maskinvaru begränsad livs längd. Mer information finns nedan.

## <a name="deprecation-of-isolated-vm-sizes"></a>Utfasning av isolerade VM-storlekar

Eftersom isolerade VM-storlekar är maskin varans bindnings storlekar ger Azure påminnelser 12 månader före den officiella utfasningen av storlekarna.  Azure kommer också att erbjuda en uppdaterad isolerad storlek på vår nästa maskin varu version som kunden kan överväga att flytta sin arbets belastning till.

| Storlek | Datum för isolerings Pension | 
| --- | --- |
| Standard_DS15_v2<sup>1</sup> | 15 maj, 2020 |
| Standard_D15_v2<sup>1</sup>  | 15 maj, 2020 |

<sup>1</sup>  mer information om Standard_DS15_v2 och Standard_D15_v2 isolerings program för isolering finns i vanliga frågor och svar


## <a name="faq"></a>VANLIGA FRÅGOR OCH SVAR
### <a name="q-is-the-size-going-to-get-retired-or-only-isolation-feature-is"></a>F: är storleken på att få en inaktive rad eller enda isolerings funktion?
**A**: om den virtuella datorns storlek inte har under skriptet "i", kommer bara funktionen isoleras att dras tillbaka. Om isolering inte behövs, finns det ingen åtgärd som kan vidtas och den virtuella datorn fortsätter att fungera som förväntat. Exempel på detta är Standard_DS15_v2, Standard_D15_v2, Standard_M128ms osv. Om den virtuella datorns storlek innehåller "i"-under skript, kommer storleken att bli tillbakadragen.

### <a name="q-is-there-a-downtime-when-my-vm-lands-on-a-non-isolated-hardware"></a>F: finns det en nedtid när min virtuella dator hamnar på en icke isolerad maskin vara?
**A**: om det inte finns något behov av isolering behövs ingen åtgärd och det kommer inte att finnas något avbrott.

### <a name="q-is-there-any-cost-delta-for-moving-to-a-non-isolated-virtual-machine"></a>F: kostar det någon kostnad delta för att flytta till en icke-isolerad virtuell dator?
**A**: Nej

### <a name="q-when-are-the-other-isolated-sizes-going-to-retire"></a>F: När är de andra isolerade storlekarna som ska tas ur bruk?
S **: vi** kommer att tillhandahålla påminnelser 12 månader före den officiella utfasningen av den isolerade storleken.

### <a name="q-im-an-azure-service-fabric-customer-relying-on-the-silver-or-gold-durability-tiers-does-this-change-impact-me"></a>F: Jag är en Azure Service Fabric-kund som förlitar sig på silver-eller Gold-nivåerna. Påverkar den här ändringen mig?
**A**: Nej. De garantier som tillhandahålls av Service Fabrics [hållbarhets nivåer](../articles/service-fabric/service-fabric-cluster-capacity.md#durability-characteristics-of-the-cluster) kommer att fortsätta att fungera även efter den här ändringen. Om du behöver en fysisk maskin varu isolering av andra orsaker kan du fortfarande behöva vidta en av de åtgärder som beskrivs ovan. 
 
### <a name="q-what-are-the-milestones-for-d15_v2-or-ds15_v2-isolation-retirement"></a>F: vilka är mil stolparna för D15_v2 eller DS15_v2 isoleringen? 
**A**: 
 
| Datum | Åtgärd |
|---|---| 
| Den 18 november 2019 | Tillgänglighet för D/DS15i_v2 (PAYG, 1 – år, RI) | 
| 14 maj, 2020 | Senaste dagen för att köpa D/DS15i_v2 1 års RI | 
| 15 maj, 2020 | D/DS15_v2 isolerings garanti borttagen | 
| 15 maj, 2021 | Dra tillbaka D/DS15i_v2 (alla kunder, förutom de som köpt 3-års RI-D/DS15_v2 före 18 november 2019)| 
| 17 november 2022 | Dra tillbaka D/DS15i_v2 när 3 års RIs har slutförts (för kunder som köpte 3-års RI för D/DS15_v2 före 18 november 2019) |

## <a name="next-steps"></a>Nästa steg

Kunder kan också välja att ytterligare dela upp resurserna i de isolerade virtuella datorerna med hjälp av [Azure-stöd för kapslade virtuella datorer](https://azure.microsoft.com/blog/nested-virtualization-in-azure/).
