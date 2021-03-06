---
title: Neka offentlig nätverks åtkomst – Azure Portal-Azure Database for MariaDB
description: Lär dig hur du konfigurerar neka offentlig nätverks åtkomst med Azure Portal för din Azure Database for MariaDB
author: mksuni
ms.author: sumuth
ms.service: jroth
ms.topic: how-to
ms.date: 03/10/2020
ms.openlocfilehash: 7925107f4334df7a844b3f3e029f3769eef51a9c
ms.sourcegitcommit: 52e3d220565c4059176742fcacc17e857c9cdd02
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/21/2021
ms.locfileid: "98665080"
---
# <a name="deny-public-network-access-in-azure-database-for-mariadb-using-azure-portal"></a>Neka offentlig nätverks åtkomst i Azure Database for MariaDB att använda Azure Portal

I den här artikeln beskrivs hur du kan konfigurera en Azure Database for MariaDB-Server för att neka alla offentliga konfigurationer och bara tillåta anslutningar via privata slut punkter för att ytterligare förbättra nätverks säkerheten.

## <a name="prerequisites"></a>Förutsättningar

För att slutföra den här instruktions guiden behöver du:

* En [Azure Database for MariaDB](quickstart-create-MariaDB-server-database-using-azure-portal.md)

## <a name="set-deny-public-network-access"></a>Ange neka offentlig nätverks åtkomst

Följ dessa steg om du vill ställa in MariaDB Server neka offentlig nätverks åtkomst:

1. I [Azure Portal](https://portal.azure.com/)väljer du din befintliga Azure Database for MariaDB-Server.

1. På sidan MariaDB Server under **Inställningar** klickar du på **anslutnings säkerhet** för att öppna sidan anslutnings säkerhets konfiguration.

1. I neka offentlig nätverks åtkomst väljer du **Ja** för att aktivera neka offentlig åtkomst för MariaDB-servern.

    ![Azure Database for MariaDB neka nätverks åtkomst](./media/howto-deny-public-network-access/deny-public-network-access.PNG)

1. Klicka på **Spara** för att spara ändringarna.

1. Ett meddelande bekräftar att anslutnings säkerhets inställningen har Aktiver ATS.

    ![Azure Database for MariaDB nekad nätverks åtkomst](./media/howto-deny-public-network-access/deny-public-network-access-success.png)

## <a name="next-steps"></a>Nästa steg

Lär dig mer om [hur du skapar aviseringar för mått](howto-alert-metric.md).