---
title: Byten och återbetalning för Azure-reservationer via självbetjäning
description: Lär dig hur du kan byta eller återbetala Azure-reservationer. Du måste ha ägaråtkomst till reservationsbeställningen för att kunna byta eller återbetala reservationer.
author: yashesvi
ms.service: cost-management-billing
ms.subservice: reservations
ms.topic: how-to
ms.date: 12/15/2020
ms.author: banders
ms.openlocfilehash: 045ab35a35aa4caefb1e1bcbbf7bf78b726c09f7
ms.sourcegitcommit: fc401c220eaa40f6b3c8344db84b801aa9ff7185
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98601457"
---
# <a name="self-service-exchanges-and-refunds-for-azure-reservations"></a>Byten och återbetalning för Azure-reservationer via självbetjäning

Azure-reservationer ger flexibilitet för att tillgodose dina föränderliga behov. Du kan byta en reservation mot en annan reservation av samma typ. Du kan till exempel byta en reservation för virtuell dator och köpa en annan reservation för någon annan storlek eller region för virtuella datorer. På samma sätt kan du byta en SQL PaaS Database-reservation och köpa en annan reservation för valfri typ eller region för SQL PaaS Database. Du kan också återbetala reservationer, men summan av alla avbrutna reservationsåtaganden i faktureringsomfånget (till exempel EA, Microsoft-kundavtal eller Microsoft-partneravtal) får inte överstiga 50 000 USD under en rullande period på 12 månader. Reserverad kapacitet för Azure Databricks, Azure VMware solution by CloudSimple-reservation, Azure Red Hat Open Shift-reservation, Red Hat-avtal och SUSE Linux-planer är inte berättigade till återbetalningar.

Byte eller annullering av kapacitet via självbetjäning är inte tillgängligt för US Government-kunder med Enterprise-avtal. Andra typer av US Government-prenumerationer, inklusive Pay-As-You-Go (betala per användning) och CSP (molnlösningsleverantör) stöds.

> [!NOTE]
> - **Du måste ha ägaråtkomst till reservationsbeställningen för att byta eller återbetala en befintlig reservation.** Du kan [Lägga till eller ändra användare som kan hantera en reservation](./manage-reserved-vm-instance.md#who-can-manage-a-reservation-by-default).
> - Microsoft debiterar för närvarande inte avgifter för tidig uppsägning för återbetalningar av reservationer. Vi kan komma att debitera avgifterna för återbetalningar som görs i framtiden. Vi har för närvarande inget datum för när den här avgiften skulle införas.

## <a name="how-to-exchange-or-refund-an-existing-reservation"></a>Så här byter eller återbetalar du en befintlig reservation

Du kan byta din reservation i [Azure-portalen](https://portal.azure.com/#blade/Microsoft_Azure_Reservations/ReservationsBrowseBlade).

1. Välj de reservationer som du vill få återbetalda och klicka på **Byt**.  
    [![Exempelbild som visar reservationer som ska returneras](./media/exchange-and-refund-azure-reservations/exchange-refund-return.png)](./media/exchange-and-refund-azure-reservations/exchange-refund-return.png#lightbox)
1. Välj den VM-produkt som du vill köpa och ange antal. Se till att den nya inköpssumman är högre än retursumman. [Fastställ rätt storlek innan du köper](../../virtual-machines/prepay-reserved-vm-instances.md#determine-the-right-vm-size-before-you-buy).  
    [![Exempelbild som visar den VM-produkt som ska köpas med ett byte](./media/exchange-and-refund-azure-reservations/exchange-refund-select-purchase.png)](./media/exchange-and-refund-azure-reservations/exchange-refund-select-purchase.png#lightbox)
1. Granska och slutför transaktionen.  
    [![Exempelbild som visar den VM-produkt som ska köpas med ett byte, slutförande av returen](./media/exchange-and-refund-azure-reservations/exchange-refund-confirm-exchange.png)](./media/exchange-and-refund-azure-reservations/exchange-refund-confirm-exchange.png#lightbox)

Om du vill få en reservation återbetald går du till **Reservationsinformation** och väljer **Återbetalning**.

## <a name="exchange-non-premium-storage-for-premium-storage"></a>Byta icke-Premium-lagring mot Premium-lagring

Du kan byta en reservation som köpts för en VM-storlek som inte stöder Premium-lagring till en motsvarande VM-storlek som gör det. Det kan till exempel gälla byte av _F1_ mot en _F1s_. Om du vill göra bytet går du till Reservationsinformation och väljer **Byt**. Bytet återställer inte perioden för den reserverade instansens och skapar inte någon ny transaktion. 

## <a name="how-transactions-are-processed"></a>Så bearbetas transaktioner

Först avbryter Microsoft den befintliga reservationen och återbetalar det proportionella beloppet för den reservationen. Om det finns ett byte bearbetas det nya köpet. Microsoft bearbetar återbetalningar med någon av följande metoder, beroende på din kontotyp och betalningsmetod:

### <a name="enterprise-agreement-customers"></a>Enterprise-avtalskunder

Pengar läggs till i Azure-förskottsbetalningen (kallades tidigare ekonomiskt åtagande) för byten och återbetalningar om det ursprungliga köpet gjordes med ett sådant. Om den period för Azure-förskottsbetalning som använder den köpta reservationen inte längre är aktiv läggs krediten till i din aktuella period för Azure-förskottsbetalning med Enterprise-avtal. Krediten är giltig i 90 dagar från och med återbetalningsdagen. Oanvänd kredit upphör att gälla efter 90 dagar.

Om det ursprungliga köpet gjordes som överförbrukning kommer den ursprungliga fakturan där reservationen köptes och alla senare fakturor att öppnas på nytt och ändras. Microsoft utfärdar en kreditnota för återbetalningarna.

### <a name="pay-as-you-go-invoice-payments-and-csp-program"></a>Betala per användning-fakturabetalningar och CSP-program

Den ursprungliga fakturan för reservationsköp annulleras och en ny faktura skapas för återbetalningen. För byten visar den nya fakturan återbetalningen och det nya köpet. Återbetalningsbeloppet justeras mot köpet. Om du bara återbetalade en reservation stannar det proportionella beloppet hos Microsoft och justeras mot ett framtida reservationsköp. Om du har köpt en reservation till Betala per användning-priser och senare går över till CSP, kan reservationen returneras och köpas på nytt utan tilläggsavgift.

### <a name="pay-as-you-go-credit-card-customers"></a>Kunder med Betala per användning-kreditkort

Den ursprungliga fakturan annulleras och en ny faktura skapas. Pengarna återbetalas till det kreditkort som användes för det ursprungliga köpet. Om du har ändrat kortet [kontaktar du supporten](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest).

## <a name="cancel-exchange-and-refund-policies"></a>Principer för att avbryta, byta och återbetala

Azure har följande principer för att avbryta, byta och återbetala.

**Principer för byte**

- Du kan returnera flera befintliga reservationer för att köpa en enskild ny reservation av samma typ. Du kan inte byta reservationer av en typ mot en annan. Till exempel kan du inte returnera en VM-reservation för att köpa en SQL-reservation. Du kan ändra alla reservationsegenskaper såsom familj, serie, version, SKU, region, kvantitet och period med ett byte.
- Endast reservationsägare kan bearbeta ett byte. [Lär dig hur du lägger till eller ändrar användare som kan hantera en reservation](manage-reserved-vm-instance.md#who-can-manage-a-reservation-by-default).
- Ett byte bearbetas som en återbetalning och ett omköp – olika transaktioner skapas för annulleringen och det nya reservationsköpet. Det proportionella reservationsbeloppet återbetalas för de reservationer som byts ut. Du debiteras helt för det nya köpet. Det proportionella reservationsbeloppet är det dagliga proportionella restvärdet för den reservation som returneras.
- Du kan byta eller återbetala reservationer även om det Enterprise-avtal som användes för att köpa reservationen har upphört att gälla och förnyats som ett nytt avtal.
- Den nya reservationens livslängdsåtagande ska vara lika med eller större än den returnerade reservationens återstående åtagande. Exempel: för en tre års reservation på 100 USD per månad som byts ut efter den 18:e betalningen ska den nya reservationens livslängdsåtagande vara 1 800 USD eller mer (betalat per månad eller i förskott).
- Den nya reservationen som köpts som en del av bytet har en ny period som börjar vid tiden för bytet.
- Det finns ingen tilläggsavgift eller årliga gränser för byten.

**Principer för återbetalning**

- För närvarande utgår det ingen avgift för tidig uppsägnings, men en avgift på 12 % för tidig uppsägning för annulleringar kan bli aktuell längre fram.
- Det totala annullerade åtagandet får inte överstiga 50 000 USD under en rullande period på 12 månader för en faktureringsprofil eller enskild registrering. För en treårig reservation på 100 USD per månad som återbetalas den 18:e månaden är det annullerade åtagandet 1 800 USD. Efter återbetalningen blir din nya tillgängliga gräns för återbetalning 48 200 USD. 365 dagar efter den här återbetalningen höjs gränsen på 48 200 USD med 1 800 USD och din nya pool blir då 50 000 USD. Eventuella andra reservationsannulleringar för samma faktureringsprofil eller EA-registrering dras från samma pool, och samma påfyllningslogik gäller för dem.
- Azure behandlar inga återbetalningar som överskrider gränsen på 50 000 USD under en period på 12 månader för en faktureringsprofil eller EA-registrering.
- Återbetalningar beräknas baserat på det lägsta priset – antingen ditt inköpspris eller det aktuella priset för reservationen.
- Endast reservationsbeställningsägare kan hantera en återbetalning. [Lär dig hur du lägger till eller ändrar användare som kan hantera en reservation](manage-reserved-vm-instance.md#who-can-manage-a-reservation-by-default).

## <a name="need-help-contact-us"></a>Behöver du hjälp? Kontakta oss.

Om du har frågor eller behöver hjälp kan du [skapa en supportbegäran](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest).

## <a name="next-steps"></a>Nästa steg

- Information om hur du hanterar en reservation finns i [Hantera Azure-reservationer](manage-reserved-vm-instance.md).
- Mer information om Azure-reservationer finns i följande artiklar:
    - [Vad är Azure-reservationer?](save-compute-costs-reservations.md)
    - [Hantera reservationer i Azure](manage-reserved-vm-instance.md)
    - [Förstå hur reservationsrabatten tillämpas](../manage/understand-vm-reservation-charges.md)
    - [Förstå reservationsanvändning för din Betala per användning-prenumeration](understand-reserved-instance-usage.md)
    - [Förstå reservationsanvändning för din Enterprise-registrering](understand-reserved-instance-usage-ea.md)
    - [Kostnader för Windows-programvara ingår inte i reservationer](reserved-instance-windows-software-costs.md)
    - [Azure-reservationer i CSP-programmet](/partner-center/azure-reservations)