---
author: ggailey777
ms.service: azure-functions
ms.topic: include
ms.date: 03/18/2020
ms.author: glenga
ms.openlocfilehash: 179ae760f146a5ac3041a54065ae12147f3f9bf0
ms.sourcegitcommit: 44844a49afe8ed824a6812346f5bad8bc5455030
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/23/2020
ms.locfileid: "97739828"
---
Eftersom archetype också skapar en uppsättning tester måste du uppdatera de här testerna för att hantera den nya `msg` parametern i `run` Metodsignaturen.  

Bläddra till platsen för test koden under _src/test/java_, öppna filen *Function. java* -projekt och ersätt kodraden under `//Invoke` med följande kod.

:::code language="java" source="~/functions-quickstart-java/functions-add-output-binding-storage-queue/src/test/java/com/function/FunctionTest.java" range="48-50":::
