---
title: Program utveckling – Azure Database for MySQL
description: Introducerar design överväganden som en utvecklare bör följa när program koden skrivs för att ansluta till Azure Database for MySQL
author: savjani
ms.author: pariks
ms.service: mysql
ms.topic: conceptual
ms.date: 3/18/2020
ms.openlocfilehash: 20c6841bb596c7f4a32ef689423515a8da59a945
ms.sourcegitcommit: 6ab718e1be2767db2605eeebe974ee9e2c07022b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94541563"
---
# <a name="application-development-overview-for-azure-database-for-mysql"></a>Översikt över program utveckling för Azure Database for MySQL 
Den här artikeln beskriver design överväganden som en utvecklare bör följa när de skriver program kod för att ansluta till Azure Database for MySQL. 

> [!TIP]
> En själv studie kurs som visar hur du skapar en server, skapar en serverbaserad brand vägg, visar Server egenskaper, skapar databas och ansluter och frågar med hjälp av Workbench och mysql.exe finns i [utforma din första Azure Database for MySQL databasen](tutorial-design-database-using-portal.md)

## <a name="language-and-platform"></a>Språk och plattform
Det finns kodexempel för olika programmeringsspråk och plattformar. Du kan hitta länkar till kod exempel på: [anslutnings bibliotek som används för att ansluta till Azure Database for MySQL](concepts-connection-libraries.md)

## <a name="tools"></a>Verktyg
Azure Database for MySQL använder MySQL community-versionen som är kompatibel med MySQLs vanliga hanterings verktyg som Workbench eller MySQL-verktyg som mysql.exe, [phpMyAdmin](https://www.phpmyadmin.net/), [Navicat](https://www.navicat.com/products/navicat-for-mysql)och andra. Du kan också använda Azure Portal, Azure CLI och REST-API: er för att interagera med databas tjänsten.

## <a name="resource-limitations"></a>Resursbegränsningar
Azure Database for MySQL hanterar resurserna som är tillgängliga för en server med hjälp av två olika metoder: 
- Resurser styrning.
- Tillämpning av gränser.

## <a name="security"></a>Säkerhet
Azure Database for MySQL ger resurser för att begränsa åtkomst, skydda data, konfigurera användare och roller och övervaka aktiviteter på en MySQL-databas.

## <a name="authentication"></a>Autentisering
Azure Database for MySQL stöder serverautentisering för användare och inloggningar.

## <a name="resiliency"></a>Återhämtning
När ett tillfälligt fel uppstår vid anslutning till en MySQL-databas, bör din kod försöka anropa igen. Vi rekommenderar att logiken för omprövning använder en annan logik så att den inte överbelastar SQL-databasen med flera klienter och försöker igen samtidigt.

- Kod exempel: för kod exempel som illustrerar logik för omprövning, se exempel för det språk som du väljer på: [anslutnings bibliotek som används för att ansluta till Azure Database for MySQL](concepts-connection-libraries.md)

## <a name="managing-connections"></a>Hantera anslutningar
Databas anslutningar är en begränsad resurs, så vi rekommenderar lämpliga användning av anslutningar vid åtkomst till MySQL-databasen för att uppnå bättre prestanda.
- Få åtkomst till databasen med hjälp av anslutningspoolen eller permanenta anslutningar.
- Få åtkomst till databasen med hjälp av kort tids längd för anslutning. 
- Använd logiken för omprövning i programmet vid tidpunkten för anslutnings försöket för att fånga fel som uppstår till följd av samtidiga anslutningar har nått det högsta tillåtna antalet. I logiken för omförsök anger du en kort fördröjning och väntar sedan en slumpmässig tid innan ytterligare anslutnings försök görs.