---
title: inkludera fil
description: inkludera fil
services: storage
author: tamram
ms.service: storage
ms.topic: include
ms.date: 11/26/2019
ms.author: tamram
ms.custom: include
ms.openlocfilehash: de79ea50d12ab322d1e28d0ad650df30ecc0c222
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/09/2020
ms.locfileid: "74806598"
---
## <a name="install-client-library-packages"></a>Installera klient biblioteks paket

> [!NOTE]
> Exemplen som visas här använder Azure Storage klient bibliotek version 12. Version 12-klient biblioteket är en del av Azure SDK. Mer information om Azure SDK finns i Azure SDK-lagringsplatsen på [GitHub](https://github.com/Azure/azure-sdk).

Installera Blob Storage-paketet genom att köra följande kommando från NuGet Package Manager-konsolen:

```powershell
Install-Package Azure.Storage.Blobs
```

Exemplen som visas här använder också den senaste versionen av [klient biblioteket för Azure Identity för .net](https://www.nuget.org/packages/Azure.Identity/) för att autentisera med Azure AD-autentiseringsuppgifter. Installera paketet genom att köra följande kommando från NuGet Package Manager-konsolen:

```powershell
Install-Package Azure.Identity
```
