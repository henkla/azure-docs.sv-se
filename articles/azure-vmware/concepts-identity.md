---
title: Koncept – identitet och åtkomst
description: Lär dig mer om identitets-och åtkomst koncepten i Azure VMware-lösningen
ms.topic: conceptual
ms.date: 11/11/2020
ms.openlocfilehash: e9c0d62968d94e2b018186f67072b6ae7078db02
ms.sourcegitcommit: 6ab718e1be2767db2605eeebe974ee9e2c07022b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94536106"
---
# <a name="azure-vmware-solution-identity-concepts"></a>Identitets koncept för Azure VMware-lösning

Privata moln i Azure VMware-lösningen är etablerade med vCenter Server och NSX-T Manager. Du använder vCenter för att hantera arbets belastningar för virtuella datorer (VM). Du kan använda NSX-T-hanteraren för att utöka det privata molnet.

Åtkomst-och identitets hantering använder CloudAdmin grupp behörigheter för vCenter-och begränsade administratörs rättigheter för NSX-T Manager. Det garanterar att din privata moln plattform uppgraderas automatiskt med de senaste funktionerna och korrigeringarna.  Mer information finns i [artikeln om uppgraderingar av privata moln][concepts-upgrades].

## <a name="vcenter-access-and-identity"></a>vCenter-åtkomst och identitet

CloudAdmin-gruppen ger behörighet i vCenter. Du hanterar gruppen lokalt i vCenter. Ett annat alternativ är genom integrering av enkel inloggning med vCenter LDAP med Azure Active Directory. Du aktiverar den integrationen när du har distribuerat ditt privata moln. 

Tabellen visar **CloudAdmin** -och **CloudGlobalAdmin** -privilegier.

|  Privilegie rad uppsättning           | CloudAdmin | CloudGlobalAdmin | Kommentar |
| :---                     |    :---:   |       :---:      |   :--:  |
|  Larm                  | En CloudAdmin-användare har alla larm privilegier för larm i Compute-ResourcePool och virtuella datorer.     |          --        |  -- |
|  Automatisk distribution             |  --  |        --        |  Microsoft hanterar värd hantering.  |
|  Certifikat            |  --  |        --       |  Microsoft certifikat hantering.  |
|  Innehållsbibliotek         | En CloudAdmin-användare har behörighet att skapa och använda filer i ett innehålls bibliotek.    |         Aktive rad med SSO.         |  Microsoft distribuerar filer i innehålls biblioteket till ESXi-värdar.  |
|  Datacenter              |  --  |        --          |  Microsoft utför alla data Center åtgärder.  |
|  Datalager               | Data lager. AllocateSpace, data lager. browse, Datastore.Config, data lager. DeleteFile, data lager. FileManagement, data lager. UpdateVirtualMachineMetadata     |    --    |   -- |
|  ESX Agent Manager       |  --  |         --       |  Microsoft utför alla åtgärder.  |
|  Mapp                  |  En CloudAdmin-användare har alla mappbehörigheter.     |  --  |  --  |
|  Global                  |  Global. CancelTask, global. GlobalTag, global. Health, global. LogEvent, global. ManageCustomFields, global. ServiceManagers, global. SetCustomField, Global.SystemTag         |                  |    |
|  Värd                    |  Host. HBR. HbrManagement      |        --          |  Microsoft utför alla andra värd åtgärder.  |
|  InventoryService        |  InventoryService. taggning      |        --          |  --  |
|  Nätverk                 |  Nätverk. tilldela    |                  |  Microsoft utför alla andra nätverks åtgärder.  |
|  Behörigheter             |  --  |        --       |  Microsoft gör alla behörigheter-åtgärder.  |
|  Profil driven lagring  |  --  |        --       |  Microsoft utför alla profil åtgärder.  |
|  Resurs                |  En CloudAdmin-användare har alla resurs behörigheter.        |      --       | --   |
|  Schemalagd aktivitet          |  En CloudAdmin-användare har alla ScheduleTask-behörigheter.   |   --   | -- |
|  Sessioner                |  Sessions. GlobalMessage, sessions. ValidateSession      |   --   |  Microsoft gör alla andra åtgärder i sessioner.  |
|  Lagringspooler           |  StorageViews. View   |        --          |  Microsoft gör alla andra lagrings visnings åtgärder (konfigurera tjänsten).  |
|  Aktiviteter                   |  --  |  --   |  Microsoft hanterar tillägg som hanterar aktiviteter.  |
|  vApp                    |  En CloudAdmin-användare har alla vApp-behörigheter.  |  --  |  --  |
|  Virtuell dator         |  En CloudAdmin-användare har alla VirtualMachine-behörigheter.  |  --  |  --  |
|  vService                |  En CloudAdmin-användare har alla vService-behörigheter.  |  --  |  --  |

## <a name="nsx-t-manager-access-and-identity"></a>NSX-T-hanterarens åtkomst och identitet

Använd kontot "administratör" för att få åtkomst till NSX-T Manager. Den har fullständig behörighet och låter dig skapa och hantera T1-routrar, logiska växlar och alla tjänster. Behörigheten ger dig åtkomst till NSX-T t0-routern. En ändring i t0-routern kan resultera i försämrade nätverks prestanda eller ingen åtkomst till privata moln. Öppna en supportbegäran i Azure Portal för att begära ändringar i din NSX-T t0-router.
  
## <a name="next-steps"></a>Nästa steg

Nästa steg är att lära dig om [metoder för uppgradering av privata moln][concepts-upgrades].

<!-- LINKS - external -->

<!-- LINKS - internal -->
[concepts-upgrades]: ./concepts-upgrades.md