---
title: Azure Resource Manager-mallexempel – Event Grid | Microsoft Docs
description: Den här artikeln innehåller en lista över Azure Resource Manager mal sampel för Azure Event Grid på GitHub.
ms.topic: sample
ms.date: 07/07/2020
ms.openlocfilehash: 910012adf2dc930e6f1a26f1a7fc41f5ed0580c9
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/09/2020
ms.locfileid: "86119063"
---
# <a name="azure-resource-manager-templates-for-event-grid"></a>Azure Resource Manager-mallar för Event Grid

JSON-syntaxen och egenskaperna som ska användas i en mall finns på sidan med [Microsoft.EventGrid-resurstyper](/azure/templates/microsoft.eventgrid/allversions). Följande tabell innehåller länkar till Azure Resource Manager-mallar för Event Grid.

## <a name="event-grid-subscriptions"></a>Event Grid prenumerationer
- [Anpassat ämne och prenumeration med webhook-slutpunkt](https://github.com/Azure/azure-quickstart-templates/tree/master/101-event-grid) – distribuerar ett event Grid anpassat ämne. Skapar en prenumeration på detta anpassade ämne som använder en WebHook-slutpunkt. 
- [Anpassad ämnes prenumeration med EventHub-slutpunkt](https://github.com/Azure/azure-quickstart-templates/tree/master/101-event-grid-event-hubs-handler) – skapar en Event Grid-prenumeration för ett anpassat ämne. Prenumerationen använder en EventHub för slutpunkten. 
- [Azure-prenumeration eller resurs grupp prenumeration](https://github.com/Azure/azure-quickstart-templates/tree/master/101-event-grid-resource-events-to-webhook) – prenumererar på händelser för en resurs grupp eller en Azure-prenumeration. Den resursgrupp som du anger som mål under distributionen är källan för händelser. Prenumerationen använder en WebHook för slutpunkten. 
- [Blob Storage-konto och-prenumeration](https://github.com/Azure/azure-quickstart-templates/tree/master/101-event-grid-subscription-and-storage) – distribuerar ett Azure Blob Storage-konto och prenumererar på händelser för det lagrings kontot. 

## <a name="next-steps"></a>Nästa steg
Se följande exempel:

- [PowerShell-exempel](powershell-samples.md)
- [CLI-exempel](cli-samples.md)
