---
title: Problem med att skapa ett program för programproxy | Microsoft Docs
description: Så här felsöker du problem med att skapa Application Proxy-program i Azure AD admin-portalen
services: active-directory
documentationcenter: ''
author: kenwith
manager: celestedg
ms.assetid: ''
ms.service: active-directory
ms.subservice: app-mgmt
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: troubleshooting
ms.date: 05/21/2018
ms.author: kenwith
ms.reviewer: asteen
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2593f80db4c271d6ae4773f324cc9777e5400550
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/09/2020
ms.locfileid: "84764969"
---
# <a name="problem-creating-an-application-proxy-application"></a>Problem med att skapa ett program för programproxy 

Nedan visas några vanliga problem när man skapar ett nytt program för programproxy.

## <a name="recommended-documents"></a>Rekommenderade dokument 

Mer information om hur du skapar ett program-proxy-program via administrations portalen finns i [Publicera program med hjälp av Azure AD-programproxy](application-proxy-add-on-premises-application.md).

Om du följer stegen i dokumentet och får ett fel när du skapar programmet, kan du läsa mer i fel informationen och förslag på hur du kan åtgärda programmet. De flesta fel meddelanden innehåller en föreslagen korrigering. 

## <a name="specific-things-to-check"></a>Vissa saker att kontrol lera

För att undvika vanliga fel, verifiera:

-   Du är administratör med behörighet att skapa ett program för programproxy

-   Den interna URL: en är unik

-   Den externa URL: en är unik

-   URL: erna börjar med http eller https och slutar med "/"

-   URL: en måste vara ett domän namn och inte en IP-adress

Fel meddelandet bör visas i det övre högra hörnet när du skapar programmet. Du kan också välja meddelande ikonen för att se fel meddelandena.

   ![Meddelande prompt](./media/application-proxy-config-problem/error-message.png)

## <a name="next-steps"></a>Nästa steg
[Aktivera Application Proxy på Azure-portalen](application-proxy-add-on-premises-application.md)
