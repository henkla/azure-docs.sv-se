---
title: Flytta ett nyckel valv till en annan region – Azure Key Vault | Microsoft Docs
description: Den här artikeln ger vägledning om hur du flyttar ett nyckel valv till en annan region.
services: key-vault
author: ShaneBala-keyvault
manager: ravijan
tags: azure-resource-manager
ms.service: key-vault
ms.subservice: general
ms.topic: how-to
ms.date: 04/24/2020
ms.author: sudbalas
Customer intent: As a key vault administrator, I want to move my vault to another region.
ms.openlocfilehash: 54a1894c88d12cfac1a2d8062425de9549c4292e
ms.sourcegitcommit: 7863fcea618b0342b7c91ae345aa099114205b03
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93285203"
---
# <a name="move-an-azure-key-vault-across-regions"></a>Flytta ett Azure Key Vault över regioner

Azure Key Vault stöder inte en resurs flyttnings åtgärd som tillåter att ett nyckel valv flyttas från en region till en annan. Den här artikeln beskriver lösningar för organisationer som har ett företag som behöver flytta ett nyckel valv till en annan region. Varje lösnings alternativ har begränsningar. Det är viktigt att förstå konsekvenserna av dessa lösningar innan du försöker tillämpa dem i en produktions miljö.

Om du vill flytta ett nyckel valv till en annan region skapar du ett nyckel valv i den andra regionen och kopierar sedan manuellt varje enskild hemlighet från det befintliga nyckel valvet till det nya nyckel valvet. Du kan göra detta med något av följande två alternativ.

## <a name="design-considerations"></a>Designöverväganden

Kom ihåg följande koncept innan du börjar:

* Nyckel valvs namn är globalt unika. Du kan inte återanvända ett valv namn.
* Du måste konfigurera om dina åtkomst principer och nätverks konfigurations inställningar i det nya nyckel valvet.
* Du måste konfigurera om mjuk borttagnings-och rensnings skyddet i det nya nyckel valvet.
* Säkerhets kopierings-och återställnings åtgärden bevarar inte inställningarna för autorotation. Du kan behöva konfigurera om inställningarna.

## <a name="option-1-use-the-key-vault-backup-and-restore-commands"></a>Alternativ 1: Använd säkerhets kopierings-och återställnings kommandona i Key Vault

Du kan säkerhetskopiera varje enskild hemlighet, nyckel och certifikat i valvet genom att använda säkerhets kopierings kommandot. Dina hemligheter laddas ned som en krypterad blob. Du kan sedan återställa blobben till det nya nyckel valvet. En lista över kommandon finns i [Azure Key Vault-kommandon](/powershell/module/azurerm.keyvault/?view=azurermps-6.13.0#key_vault).

Att använda säkerhets kopierings-och återställnings kommandon har två begränsningar:

* Du kan inte säkerhetskopiera ett nyckel valv i en geografi och återställa det till ett annat geografiskt område. Mer information finns i avsnittet om [Azure-geografiska](https://azure.microsoft.com/global-infrastructure/geographies/)områden.

* Säkerhetskopieringskommandot säkerhetskopierar alla versioner av varje hemlighet. Om du har en hemlighet med ett stort antal tidigare versioner (fler än 10) kanske storleken på begäran överskrider maxgränsen och åtgärden misslyckas.

## <a name="option-2-manually-download-and-upload-the-key-vault-secrets"></a>Alternativ 2: Hämta och ladda ned nyckel valv hemligheter manuellt

Du kan ladda ned vissa hemliga typer manuellt. Du kan till exempel Ladda ned certifikat som en PFX-fil. Med det här alternativet elimineras de geografiska begränsningarna för vissa typer av hemliga typer, t. ex. certifikat. Du kan ladda upp PFX-filerna till alla nyckel valv i vilken region som helst. Hemligheterna laddas ned i ett format som inte är lösenordsskyddade. Du ansvarar för att skydda dina hemligheter under flytten.