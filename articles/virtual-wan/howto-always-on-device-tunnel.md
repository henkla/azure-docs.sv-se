---
title: Konfigurera en Always-On VPN-tunnel
titleSuffix: Azure Virtual WAN
description: Steg för att konfigurera Always on VPN-enhets tunnel för virtuellt WAN
services: virtual-wan
author: cherylmc
ms.service: virtual-wan
ms.topic: how-to
ms.date: 09/22/2020
ms.author: cherylmc
ms.openlocfilehash: e814487cb4dab9c8c19daab2ea3bb81391d4a98f
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/09/2020
ms.locfileid: "90983684"
---
# <a name="configure-an-always-on-vpn-device-tunnel-for-virtual-wan"></a>Konfigurera en tunnel för alltid på VPN-enheter för virtuellt WAN

[!INCLUDE [intro](../../includes/vpn-gateway-vwan-always-on-intro.md)]

## <a name="prerequisites"></a>Förutsättningar

Du måste skapa en punkt-till-plats-konfiguration och redigera den virtuella hubben. Anvisningar finns i följande avsnitt:

* [Skapa en P2S-konfiguration](virtual-wan-point-to-site-portal.md#p2sconfig)
* [Skapa hubb med P2S-Gateway](virtual-wan-point-to-site-portal.md#hub)

## <a name="configure-the-device-tunnel"></a>Konfigurera enhets tunneln

[!INCLUDE [device tunnel](../../includes/vpn-gateway-vwan-always-on-device.md)]

## <a name="to-remove-a-profile"></a>Ta bort en profil

Om du vill ta bort profilen kör du följande kommando:

![Skärm bild som visar ett PowerShell-fönster som kör kommandot Remove-VpnConnection-Name MachineCertTest.](./media/howto-always-on-device-tunnel/cleanup.png)

## <a name="next-steps"></a>Nästa steg

Mer information om virtuellt WAN finns i [vanliga frågor och svar](virtual-wan-faq.md).