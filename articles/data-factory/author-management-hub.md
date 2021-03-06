---
title: Hanteringshubb
description: Hantera anslutningar, konfiguration av käll kontroll och globala redigerings egenskaper i Azure Data Factory Management Hub
services: data-factory
ms.service: data-factory
ms.workload: data-services
ms.topic: conceptual
author: dcstwh
ms.author: weetok
manager: anandsub
ms.date: 06/02/2020
ms.openlocfilehash: aa1246a65dc6971107abe35f4a418b0bbb05641b
ms.sourcegitcommit: d60976768dec91724d94430fb6fc9498fdc1db37
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96486139"
---
# <a name="management-hub-in-azure-data-factory"></a>Hanterings hubb i Azure Data Factory

[!INCLUDE[appliesto-adf-xxx-md](includes/appliesto-adf-xxx-md.md)]

Hanterings hubben, som nås via fliken *Hantera* i Azure Data Factory UX, är en portal som är värd för globala hanterings åtgärder för din data fabrik. Här kan du hantera dina anslutningar till data lager och externa beräkningar, käll kontroll konfiguration och utlösnings inställningar.

## <a name="manage-connections"></a>Hantera anslutningar

### <a name="linked-services"></a>Länkade tjänster

Länkade tjänster definierar anslutnings informationen för Azure Data Factory för att ansluta till externa data lager och beräknings miljöer. Mer information finns i [begrepp för länkade tjänster](concepts-linked-services.md). Det går att skapa, redigera och ta bort länkade tjänster i hanterings hubben.

![Hantera länkade tjänster](media/author-management-hub/management-hub-linked-services.png)

### <a name="integration-runtimes"></a>Integrerings körningar

En integration runtime är en beräknings infrastruktur som används av Azure Data Factory för att tillhandahålla funktioner för data integrering i olika nätverks miljöer. Mer information finns i [integration runtime-koncept](concepts-integration-runtime.md). I hanterings hubben kan du skapa, ta bort och övervaka dina integrerings körningar.

![Hantera integrerings körningar](media/author-management-hub/management-hub-integration-runtime.png)

## <a name="manage-source-control"></a>Hantera käll kontroll

### <a name="git-configuration"></a>Git-konfiguration

Visa och redigera dina konfigurerade git-serverinställningar i hanterings hubben. Mer information finns [i käll kontroll i Azure Data Factory](source-control.md).

![Hantera git-lagrings platsen](media/author-management-hub/management-hub-git.png)

### <a name="parameterization-template"></a>Parameterisering-mall

Om du vill åsidosätta de genererade parametrarna för Resource Manager-mallen när du publicerar från samarbets grenen, kan du generera eller redigera en fil med anpassade parametrar. Mer information finns [i använda anpassade parametrar i Resource Manager-mallen](continuous-integration-deployment.md#use-custom-parameters-with-the-resource-manager-template). Parameterisering-mallen är bara tillgänglig när du arbetar i en git-lagringsplats. Om *arm-template-parameters-definition.jsi* filen inte finns i arbets grenen kommer den att generera den genom att redigera standard mal len.

![Hantera anpassade parametrar](media/author-management-hub/management-hub-custom-parameters.png)

## <a name="manage-authoring"></a>Hantera redigering

### <a name="triggers"></a>Utlösare

Utlösare fastställer när en pipeline-körning ska startas. För närvarande kan utlösare finnas på ett klock schema för en vägg, använda ett periodiskt intervall eller vara beroende av en händelse. Mer information finns i om [utlösarens körning](concepts-pipeline-execution-triggers.md#trigger-execution). I hanterings hubben kan du skapa, redigera, ta bort eller Visa det aktuella läget för en utlösare.

![Skärm bild som visar var du kan skapa, redigera, ta bort och visa aktuell status för en utlösare.](media/author-management-hub/management-hub-triggers.png)

### <a name="global-parameters"></a>Globala parametrar

Globala parametrar är konstanter över en data fabrik som kan användas av en pipeline i valfritt uttryck. Mer information finns i [globala parametrar](author-global-parameters.md).

![Skapa globala parametrar](media/author-global-parameters/create-global-parameter-3.png)

## <a name="next-steps"></a>Nästa steg

Lär dig hur du [konfigurerar en git-lagringsplats](source-control.md) till din ADF


