---
title: Anslut squid-proxy-data till Azure Sentinel | Microsoft Docs
description: Lär dig hur du använder squid proxy data Connector för att hämta squid proxy-loggar till Azure Sentinel. Visa squid-proxy-data i arbets böcker, skapa aviseringar och förbättra undersökningen.
services: sentinel
documentationcenter: na
author: yelevin
manager: rkarlin
editor: ''
ms.service: azure-sentinel
ms.subservice: azure-sentinel
ms.devlang: na
ms.topic: how-to
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/17/2021
ms.author: yelevin
ms.openlocfilehash: b183abf8d42e6f4b1c43db2d87b2650721e0c2a9
ms.sourcegitcommit: ca215fa220b924f19f56513fc810c8c728dff420
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/19/2021
ms.locfileid: "98567993"
---
# <a name="connect-your-squid-proxy-to-azure-sentinel"></a>Anslut din squid-proxy till Azure Sentinel

> [!IMPORTANT]
> Squid proxy Connector är för närvarande en för **hands version**. Se [kompletterande användnings villkor för Microsoft Azure](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) för hands versioner av ytterligare juridiska villkor som gäller för Azure-funktioner som är i beta, för hands version eller på annat sätt ännu inte släppts till allmän tillgänglighet.

Den här artikeln förklarar hur du ansluter squid-proxyservern till Azure Sentinel. Med squid proxy data Connector kan du enkelt ansluta dina squid-loggar med Azure Sentinel, så att du kan visa data i arbets böcker, använda dem för att skapa anpassade aviseringar och införliva dem för att förbättra undersökningen. Integreringen mellan squid proxy och Azure Sentinel använder syslog.

> [!NOTE]
> Data lagras på den geografiska platsen för den arbets yta där du kör Azure Sentinel.

## <a name="prerequisites"></a>Krav

- Du måste ha läs-och Skriv behörighet på Azure Sentinel-arbetsytan.

## <a name="forward-squid-proxy-logs-to-the-syslog-agent"></a>Vidarebefordra squid proxy-loggar till syslog-agenten  

Konfigurera squid proxy för att vidarebefordra syslog-meddelanden till Azure-arbetsytan via syslog-agenten.

1. I navigerings menyn i Azure Sentinel väljer du **data kopplingar**.

1. I galleriet **data anslutningar** väljer du **squid proxy (för hands version)** och öppnar sedan **kopplings sidan**.

1. Följ instruktionerna på sidan **squid proxy** Connector:

    1. Installera och publicera agenten för Linux

        - Välj en virtuell Azure Linux-dator eller en icke-Azure Linux-dator (fysisk eller virtuell).

    1. Konfigurera loggarna som ska samlas in

        - I avancerade inställningar för arbets ytan lägger du till en anpassad loggtyp, laddar upp en exempel fil och konfigurerar den enligt anvisningarna.

## <a name="find-your-data"></a>Hitta dina data

När en lyckad anslutning har upprättats visas data i **loggarna** under **anpassade loggar** i `SquidProxy_CL` tabellen.

Se **Nästa steg** -fliken på kopplings sidan för några användbara exempel frågor.

## <a name="validate-connectivity"></a>Verifiera anslutning

Det kan ta upp till 20 minuter innan loggarna börjar visas i Log Analytics. 

## <a name="next-steps"></a>Nästa steg

I det här dokumentet har du lärt dig hur du ansluter squid proxy till Azure Sentinel. Mer information om Azure Sentinel finns i följande artiklar:

- Lär dig hur du [får insyn i dina data och potentiella hot](quickstart-get-visibility.md).
- Kom igång [med att identifiera hot med Azure Sentinel](tutorial-detect-threats-built-in.md).
- [Använd arbets böcker](tutorial-monitor-your-data.md) för att övervaka dina data.
