---
title: Ansluta ett Azure Purview-konto 
description: Anslut ett Azure avdelningens kontroll-konto till en Synapse-arbetsyta.
services: synapse-analytics
author: ArnoMicrosoft
ms.service: synapse-analytics
ms.topic: quickstart
ms.date: 12/16/2020
ms.author: acomet
ms.reviewer: jrasnick
ms.openlocfilehash: cb6a63e4ead45d7751d1d3442793478cfdcd71c0
ms.sourcegitcommit: b39cf769ce8e2eb7ea74cfdac6759a17a048b331
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/22/2021
ms.locfileid: "98676348"
---
# <a name="quickstartconnect-an-azure-purview-account-to-a-synapse-workspace"></a>Snabb start: ansluta ett Azure avdelningens kontroll-konto till en Synapse-arbetsyta 


I den här snabb starten registrerar du ett Azure avdelningens kontroll-konto på en Synapse-arbetsyta. Med den anslutningen kan du identifiera Azure avdelningens kontroll-tillgångar och interagera med dem via Synapse-funktioner. 

Du kan utföra följande uppgifter i Synapse: 
- Använd sökrutan längst upp för att hitta avdelningens kontroll-tillgångar baserat på nyckelord 
- Förstå data baserat på metadata, härkomst, anteckningar 
- Anslut dessa data till din arbets yta med länkade tjänster eller integrations data uppsättningar 
- Analysera dessa data uppsättningar med Synapse Apache Spark, Synapse SQL och data flöde 

## <a name="prerequisites"></a>Förutsättningar 
- [Azure avdelningens kontroll-konto](../../purview/create-catalog-portal.md) 
- [Synapse-arbetsyta](../quickstart-create-workspace.md) 

## <a name="signin-toa-synapse-workspace"></a>Logga in på en Synapse-arbetsyta 

Gå till  [https://web.azuresynapse.net](https://web.azuresynapse.net) och logga in på din arbets yta. 

## <a name="permissions-for-connecting-an-azure-purview-account"></a>Behörigheter för att ansluta ett Azure avdelningens kontroll-konto 

- Om du vill ansluta ett Azure avdelningens kontroll-konto till en Synapse-arbetsyta behöver du en **deltagar** roll i Synapse-arbetsytan från Azure Portal IAM och du behöver åtkomst till det Azure avdelningens kontroll-kontot.

## <a name="connect-an-azure-purview-account"></a>Ansluta ett Azure Purview-konto  

- I arbets ytan Synapse går du till **Hantera**  ->  **Azure avdelningens kontroll**. Välj **Anslut till ett avdelningens kontroll-konto**. 
- Du kan välja **från Azure-prenumerationen** eller **ange manuellt**. **Från Azure-prenumeration** kan du välja det konto som du har åtkomst till. 
- När du är ansluten bör du kunna se namnet på avdelningens kontroll-kontot på fliken **Azure avdelningens kontroll-konto**. 
- Du kan använda Sök fältet längst upp i mitten av Synapse-arbetsytan för att söka efter data. 

## <a name="nextsteps"></a>Nästa steg 

[Registrera och skanna Azure Synapse-tillgångar i Azure avdelningens kontroll](../../purview/register-scan-azure-synapse-analytics.md)

[Identifiera, ansluta och utforska data i Synapse med hjälp av Azure Purview](how-to-discover-connect-analyze-azure-purview.md)   
