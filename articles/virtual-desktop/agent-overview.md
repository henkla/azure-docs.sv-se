---
title: Kom igång med Windows Virtual Desktop-agenten
description: En översikt över Windows Virtual Desktop agent och uppdaterings processer.
author: Sefriend
ms.topic: conceptual
ms.date: 12/16/2020
ms.author: sefriend
manager: clarkn
ms.openlocfilehash: 325502255e84e38a39ca5b90ee4126354c0d425b
ms.sourcegitcommit: fc401c220eaa40f6b3c8344db84b801aa9ff7185
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98601235"
---
# <a name="get-started-with-the-windows-virtual-desktop-agent"></a>Kom igång med Windows Virtual Desktop-agenten

I Windows Virtual Desktop Service Framework finns tre huvud komponenter: fjärr skrivbords klienten, tjänsten och de virtuella datorerna. De här virtuella datorerna är aktiva i kund prenumerationen där Windows Virtual Desktop agent och agentens start program är installerade. Agenten fungerar som mellanliggande Communicator mellan tjänsten och de virtuella datorerna, vilket möjliggör anslutning. Om du har problem med Agent installationen, uppdateringen eller konfigurationen kan de virtuella datorerna därför inte ansluta till tjänsten. Agentens start program är den körbara fil som läser in agenten. 

Den här artikeln ger en kort översikt över Agent installationen och uppdaterings processerna.

>[!NOTE]
>Den här dokumentationen gäller inte för FSLogix-agenten eller klient agenten för fjärr skrivbord.


## <a name="initial-installation-process"></a>Inledande installations process

Windows-agenten för virtuella skriv bord installeras på ett av två sätt. Om du etablerar virtuella datorer i Azure Portal och Azure Marketplace installeras agenten och agentens start program automatiskt. Om du etablerar virtuella datorer med hjälp av PowerShell måste du manuellt hämta agent-och agentens start program. msi-filer när du [skapar en Windows-pool för virtuella skriv bord med PowerShell](create-host-pools-powershell.md#register-the-virtual-machines-to-the-windows-virtual-desktop-host-pool). När agenten installeras installeras även stack-och Genève Monitoring Agent på Windows Virtual Desktop samtidigt. Stack-komponenten sida vid sida krävs för att användare ska kunna upprätta omvänd server-till-klient-anslutningar på ett säkert sätt. Genèvekonventionen övervakar agentens hälso tillstånd. Alla dessa tre komponenter är nödvändiga för slut punkt till slut punkt för att användaren ska fungera korrekt.

>[!IMPORTANT]
>För att kunna installera Windows Virtual Desktop-agenten, sida-vid-sida-stack och Genève Monitoring Agent, måste du avblockera alla URL: er som anges i [listan över obligatoriska URL](safe-url-list.md#virtual-machines): er. Att avblockera dessa URL: er krävs för att använda tjänsten Windows Virtual Desktop.

## <a name="agent-update-process"></a>Process för agent uppdatering

Tjänsten Windows Virtual Desktop uppdaterar automatiskt agenten när en uppdatering blir tillgänglig. Agent uppdateringar kan innehålla nya funktioner eller åtgärda tidigare problem. När den ursprungliga versionen av Windows Virtual Desktop-agenten har installerats frågar agenten regelbundet efter Windows Virtual Desktop-tjänsten för att avgöra om det finns en nyare version av agenten och dess komponenter är tillgängliga. Om det finns en ny version hämtar agentens start program automatiskt den senaste versionen av agenten, stacken sida vid sida och Genèvekonventionen övervaknings agent.

>[!NOTE]
>- När Genève Monitoring Agent uppdaterar till den senaste versionen, finns den gamla GenevaTask-aktiviteten och inaktive rad innan du skapar en ny uppgift för den nya övervaknings agenten. Den tidigare versionen av övervaknings agenten tas inte bort om den senaste versionen av övervaknings agenten har ett problem som kräver återställning till den tidigare versionen för att åtgärda problemet. Om den senaste versionen har ett problem kommer den gamla övervaknings agenten att aktive ras igen för att fortsätta leverera övervaknings data. Alla versioner av övervakaren som är tidigare än den sista som du installerade innan uppdateringen tas bort från den virtuella datorn.
>- Den virtuella datorn behåller tre versioner av den sida-vid-sida-stacken i taget. Detta möjliggör snabb återställning om något går fel med uppdateringen. Den tidigaste versionen av stacken tas bort från den virtuella datorn när stacken uppdateras.

Den här uppdateringen varar vanligt vis 2-3 minuter på en ny virtuell dator och bör inte göra att den virtuella datorn förlorar anslutningen eller stängs av. Den här uppdaterings processen gäller för både Windows Virtual Desktop (klassisk) och den senaste versionen av Windows Virtual Desktop med Azure Resource Manager.

## <a name="next-steps"></a>Nästa steg

Nu när du har en bättre förståelse för Windows Virtual Desktop-agenten finns här några resurser som kan hjälpa dig att:

- Om du har problem med agent-eller anslutnings problem kan du titta närmare på [fel söknings guide för Windows Virtual Desktop agent](troubleshoot-agent.md).