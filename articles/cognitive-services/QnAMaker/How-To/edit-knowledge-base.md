---
title: Redigera en kunskaps bas – QnA Maker
description: Med QnA Maker kan du hantera innehållet i kunskaps basen genom att tillhandahålla en användarvänlig redigerings upplevelse.
ms.service: cognitive-services
ms.subservice: qna-maker
ms.topic: conceptual
ms.date: 07/16/2020
ms.openlocfilehash: 9541320f65060a0b1f2b5c84a131c08e92554e9e
ms.sourcegitcommit: 9eda79ea41c60d58a4ceab63d424d6866b38b82d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96351715"
---
# <a name="edit-qna-pairs-in-your-knowledge-base"></a>Redigera QnA-par i kunskaps basen

Med QnA Maker kan du hantera innehållet i kunskaps basen genom att tillhandahålla en användarvänlig redigerings upplevelse.

QnA-par läggs till från en data källa, till exempel en fil eller URL, eller läggs till som en redaktionell källa. En redaktionell källa visar att QnA-paret lades till i QnA-portalen manuellt. Alla QnA-par är tillgängliga för redigering.

<a name="add-an-editorial-qna-set"></a>

## <a name="add-an-editorial-qna-pair"></a>Lägg till ett redigerings QnA-par

1. Logga in på [QNA-portalen](https://www.qnamaker.ai/)och välj sedan den kunskaps bas som QNA-paret ska läggas till i.
1. På sidan **Redigera** i kunskaps basen väljer du **Lägg till QNA-par** för att lägga till ett nytt QNA-par.

    > [!div class="mx-imgBorder"]
    > ![Lägg till QnA-par](../media/qnamaker-how-to-edit-kb/add-qnapair.png)

1. I den nya QnA pair-raden lägger du till obligatoriska frågor och svars fält. De andra fälten är valfria. Alla fält kan ändras när som helst.

1. Du kan också lägga till **[alternativa formuleringen](../Quickstarts/add-question-metadata-portal.md#add-additional-alternatively-phrased-questions)**. Alternativa formuleringen är en form av frågan som är mycket annorlunda från den ursprungliga frågan men som bör ge samma svar.

    När din kunskaps bas publiceras och du har aktiverat [aktiv inlärning](use-active-learning.md) , samlar QNA Maker in alternativa formuleringen-alternativ som du kan acceptera. Dessa val väljs för att öka förutsägelse noggrannheten.

1. Du kan också lägga till **[metadata](../Quickstarts/add-question-metadata-portal.md#add-metadata-to-filter-the-answers)**. Om du vill visa metadata väljer du **visnings alternativ** på snabb menyn. Metadata innehåller filter för de svar som klient programmet, till exempel en chatt-robot, tillhandahåller.

1. Du kan också lägga till **[uppföljnings](multiturn-conversation.md)** anvisningarna. Följ anvisningarna innehåller ytterligare konversations Sök vägar till klient programmet för att presentera för användaren.

1. Välj **Spara och träna** för att se förutsägelser, inklusive det nya QNA-paret.

## <a name="rich-text-editing-for-answer"></a>Omfattande text redigering för svar

Text redigering av svars texten ger dig markdown format från ett enkelt verktygsfält.

1. Välj text områden för ett svar, verktygsfältet RTF-redigerare visas på QnA-adresspar-raden.

    > [!div class="mx-imgBorder"]
    > ![Skärm bild av RTF-redigeraren med frågan och svaret på en QnA pair-rad.](../media/qnamaker-how-to-edit-kb/rich-text-control-qna-pair-row.png)

    Text som redan finns i svaret visas som den ska när användaren ser den från en robot.

1. Redigera texten. Välj formateringsfunktioner i verktygsfältet text redigering eller Använd växlings funktionen för att växla till markdown-syntax.

    > [!div class="mx-imgBorder"]
    > ![Använd Rich Text Editor för att skriva och formatera text och Spara som markdown.](../media/qnamaker-how-to-edit-kb/rich-text-display-image.png)

    |Funktioner i Rich-Text-redigeraren|Kortkommando|
    |--|--|
    |Växla mellan Rich-Text Editor och markdown. `</>`|CTRL+M|
    |Breda. **T**|Prod + LB|
    |Kursiv stil, visas med kursivt **_i_**|CTRL + I|
    |Osorterad lista||
    |Ordnad lista||
    |Stycke format||
    |Bild – Lägg till en avbildning som är tillgänglig från en offentlig URL.|CTRL + G|
    |Lägg till länk till offentligt tillgänglig URL.|CTRL + K|
    |Uttrycks symbol – Lägg till från ett urval av uttrycks symboler.|CTRL + E|
    |Avancerad meny – ångra|CTRL + Z|
    |Avancerad meny – gör om|CTRL + Y|

1. Lägg till en bild till svaret med hjälp av ikonen bild i verktygsfältet RTF. Den inbyggda redigeraren behöver den allmänt tillgängliga bild-URL: en och den alternativa texten för avbildningen.


    > [!div class="mx-imgBorder"]
    > ![Skärm bild som visar redigerings programmet på plats med den allmänt tillgängliga bild-URL: en och en alternativ text för den angivna bilden.](../media/qnamaker-how-to-edit-kb/add-image-url-alternate-text.png)

1. Lägg till en länk till en URL genom att antingen välja texten i svaret och sedan välja länk ikonen i verktygsfältet eller genom att välja länk ikonen i verktygsfältet och sedan ange ny text och URL: en.

    > [!div class="mx-imgBorder"]
    > ![Använd RTF-redigeraren för att lägga till en offentligt tillgänglig bild och dess alternativ text.](../media/qnamaker-how-to-edit-kb/add-link-to-answer-rich-text-editor.png)

## <a name="edit-a-qna-pair"></a>Redigera ett QnA-par

Alla fält i ett QnA-par kan redige ras, oavsett den ursprungliga data källan. Vissa fält kanske inte visas på grund av dina aktuella inställningar för **visnings alternativ** , som finns i kontext verktygsfältet.

## <a name="delete-a-qna-pair"></a>Ta bort ett QnA-par

Om du vill ta bort en QnA klickar du på ikonen **ta bort** längst till höger på raden QNA. Detta är en permanent åtgärd. Det går inte att återställa. Överväg att exportera dina KB från sidan **publicera** innan du tar bort par.

![Ta bort QnA-par](../media/qnamaker-how-to-edit-kb/delete-qnapair.png)

## <a name="find-the-qna-pair-id"></a>Hitta QnA par-ID

Om du behöver hitta QnA par-ID: t kan du hitta det på två platser:

* Hovra över borttagnings ikonen på QnA-värdeparet som du är intresse rad av. Hov rings texten innehåller QnA-parets ID.
* Exportera kunskaps basen. Varje QnA-par i kunskaps basen innehåller QnA-parets ID.

## <a name="add-alternate-questions"></a>Lägg till alternativa frågor

Lägg till alternativa frågor i ett befintligt QnA-par för att förbättra sannolikheten för en matchning till en användar fråga.

![Lägg till alternativa frågor](../media/qnamaker-how-to-edit-kb/add-alternate-question.png)

## <a name="linking-qna-pairs"></a>Länkar QnA-par

Länkar av QnA-par finns med [uppföljnings instruktioner](multiturn-conversation.md). Det här är en logisk anslutning mellan QnA-par som hanteras på kunskaps bas nivån. Du kan redigera uppföljnings anvisningarna i QnA Maker portalen.

Du kan inte länka QnA-par i svarets metadata.

## <a name="add-metadata"></a>Lägg till metadata

Lägg till metadata-par genom att först välja **visnings alternativ** och sedan välja **Visa metadata**. Kolumnen metadata visas. Sedan väljer du **+** tecknet för att lägga till ett metadata-par. Det här paret består av en nyckel och ett värde.

Läs mer om metadata i snabb starten för QnA Maker Portal för metadata:
* [Redigering – Lägg till metadata i QnA-paret](../quickstarts/add-question-metadata-portal.md#add-metadata-to-filter-the-answers)
* [Fråga förutsägelse – filtrera svar efter metadata](../quickstarts/get-answer-from-knowledge-base-using-url-tool.md)

## <a name="save-changes-to-the-qna-pairs"></a>Spara ändringar i QnA-par

Välj regelbundet **Spara och träna** efter att du har redigerat ändringarna för att undvika att förlora ändringar.

![Lägg till metadata](../media/qnamaker-how-to-edit-kb/add-metadata.png)

## <a name="when-to-use-rich-text-editing-versus-markdown"></a>När du ska använda Rich-Text-redigering jämfört med markdown

Med [text redigering](#add-an-editorial-qna-set) av svar kan du, som författare, använda verktygsfältet Formatering för att snabbt välja och formatera text.

[Markdown](../reference-markdown-format.md) är ett bättre verktyg när du behöver generera innehåll automatiskt för att skapa kunskaps banker som ska importeras som en del av en CI/CD-pipeline eller för [batch-testning](../index.yml).

## <a name="next-steps"></a>Nästa steg

> [!div class="nextstepaction"]
> [Samarbeta i en kunskapsbas](../index.yml)

* [Hantera Azure-resurser som används av QnA Maker](set-up-qnamaker-service-azure.md)