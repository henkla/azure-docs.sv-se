---
title: Loggnings fel och undantag i MSAL.NET
titleSuffix: Microsoft identity platform
description: Lär dig hur du loggar fel och undantag i MSAL.NET
services: active-directory
author: mmacy
manager: CelesteDG
ms.service: active-directory
ms.subservice: develop
ms.topic: conceptual
ms.workload: identity
ms.date: 01/25/2021
ms.author: marsma
ms.reviewer: saeeda, jmprieur
ms.custom: aaddev
ms.openlocfilehash: 47576265c9b1a20f801231abe2fb37a929d5a27c
ms.sourcegitcommit: 3c3ec8cd21f2b0671bcd2230fc22e4b4adb11ce7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2021
ms.locfileid: "98763535"
---
# <a name="logging-in-msalnet"></a>Loggning i MSAL.NET

[!INCLUDE [MSAL logging introduction](../../../includes/active-directory-develop-error-logging-introduction.md)]

## <a name="configure-logging-in-msalnet"></a>Konfigurera loggning i MSAL.NET

I MSAL 3. x anges loggning per program när appen skapas med hjälp av `.WithLogging` Builder-modifieraren. Den här metoden kräver valfria parametrar:

- `Level` gör att du kan bestämma vilken loggnings nivå du vill ha. Om du ställer in det på fel får du bara fel meddelanden
- `PiiLoggingEnabled` gör att du kan logga personliga och organisatoriska data om värdet är true. Som standard är detta inställt på falskt, så att programmet inte loggar personliga data.
- `LogCallback` har angetts till ett ombud som utför loggningen. Om `PiiLoggingEnabled` är sant får den här metoden meddelandena två gånger: När `containsPii` parametern är lika med falskt och meddelandet utan personliga data, och en andra gång med `containsPii` parametern lika med sant och meddelandet kan innehålla personliga data. I vissa fall (när meddelandet inte innehåller personliga data) är meddelandet samma.
- `DefaultLoggingEnabled` aktiverar standard loggning för plattformen. Som standard är det falskt. Om du anger värdet till sant används händelse spårning i Desktop/UWP-program, NSLog på iOS och logcat på Android.

```csharp
class Program
 {
  private static void Log(LogLevel level, string message, bool containsPii)
  {
     if (containsPii)
     {
        Console.ForegroundColor = ConsoleColor.Red;
     }
     Console.WriteLine($"{level} {message}");
     Console.ResetColor();
  }

  static void Main(string[] args)
  {
    var scopes = new string[] { "User.Read" };

    var application = PublicClientApplicationBuilder.Create("<clientID>")
                      .WithLogging(Log, LogLevel.Info, true)
                      .Build();

    AuthenticationResult result = application.AcquireTokenInteractive(scopes)
                                             .ExecuteAsync().Result;
  }
 }
 ```

> [!TIP]
 > Se [MSAL.net-wikin](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki) för exempel på MSAL.net-loggning med mera.

## <a name="next-steps"></a>Nästa steg

Fler kod exempel finns i [kod exempel för Microsoft Identity Platform](sample-v2-code.md).