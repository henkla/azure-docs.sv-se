---
title: Vad är nytt i ansikts service?
titleSuffix: Azure Cognitive Services
description: Viktig information för ansikts tjänsten innehåller en historik över publicerings ändringar för olika versioner.
services: cognitive-services
author: PatrickFarley
manager: nitinme
ms.service: cognitive-services
ms.subservice: face-api
ms.topic: conceptual
ms.date: 12/11/2020
ms.author: pafarley
ms.openlocfilehash: 8a409d66065a7ccd2b34365bd565202f207ac0e8
ms.sourcegitcommit: 77ab078e255034bd1a8db499eec6fe9b093a8e4f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/16/2020
ms.locfileid: "97560754"
---
# <a name="whats-new-in-face-service"></a>Vad är nytt i ansikts service?

Azure Face service uppdateras regelbundet. Använd den här artikeln för att hålla dig uppdaterad med funktions förbättringar, korrigeringar och dokumentations uppdateringar.

## <a name="november-2020"></a>November 2020
* Publicerat en exempel-app för ansikts registrering för att demonstrera bästa praxis för att skapa ett meningsfullt godkännande och skapa högpresterande ansikts igenkännings system med hjälp av hög kvalitets registrering. Exemplet med öppen källkod finns i [skapa en app](build-enrollment-app.md) -guide för registrering och på [GitHub](https://github.com/Azure-Samples/cognitive-services-FaceAPIEnrollmentSample), redo för utvecklare att distribuera eller anpassa.  

## <a name="june-2019"></a>Juni 2019

* Lade till en ny ansikts identifierings modell med förbättrad noggrannhet för små, sido visning, Occluded och suddiga ansikten. Använd IT [-detektering](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395236), [FaceList – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395250), [LargeFaceList – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/5a158c10d2de3616c086f2d3), [PersonGroup person – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f3039523b) och [LargePersonGroup person – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/599adf2a3a7b9412a4d53f42) genom att ange det nya namnet på ansikts identifierings modellen `detection_02` i `detectionModel` parametern. Mer information om [hur du anger en identifierings modell](Face-API-How-to-Topics/specify-detection-model.md).

## <a name="april-2019"></a>April 2019

* Bättre övergripande precision för- `age` och- `headPose` attribut. `headPose`Attributet uppdateras också med `pitch` värdet aktiverat nu. Använd de här attributen genom att ange dem i `returnFaceAttributes` parametern för [Face-detect-](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395236) `returnFaceAttributes` parameter. 

* Förbättrad hastighet för [ansikts igenkänning](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395236), [FaceList – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395250), [LargeFaceList – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/5a158c10d2de3616c086f2d3), [PersonGroup person – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f3039523b) och [LargePersonGroup person – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/599adf2a3a7b9412a4d53f42).

## <a name="march-2019"></a>Mars 2019

* Lade till en ny ansikts igenkännings modell med förbättrad noggrannhet. Använd den genom [ansikts-detect](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395236), [FaceList-Create](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f3039524b), [LargeFaceList-Create](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/5a157b68d2de3616c086f2cc), [PersonGroup-Create](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395244) och [LargePersonGroup-Create](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/599acdee6ac60f11b48b5a9d) genom att ange det nya namnet på ansikts igenkännings modellen `recognition_02` i `recognitionModel` parametern. Mer information finns i [så här anger du en igenkännings modell](Face-API-How-to-Topics/specify-recognition-model.md).

## <a name="january-2019"></a>Januari 2019

* Ögonblicks bild funktionen har lagts till för att stödja datamigrering över prenumerationer: [ögonblicks bild](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/snapshot-get) Mer information om [hur du migrerar dina ansikts data till en annan ansikts prenumeration](Face-API-How-to-Topics/how-to-migrate-face-data.md).

## <a name="october-2018"></a>Oktober 2018

* Förfinad Beskrivning av `status` , `createdDateTime` , `lastActionDateTime` , och `lastSuccessfulTrainingDateTime` i [PersonGroup – Hämta utbildnings status](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395247), [LargePersonGroup – Hämta utbildnings](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/599ae32c6ac60f11b48b5aa5)status och [LargeFaceList-Hämta utbildnings status](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/5a1582f8d2de3616c086f2cf).

## <a name="may-2018"></a>Maj 2018

* Förbättrat `gender` attribut är avsevärt och även förbättrat,,, `age` `glasses` `facialHair` `hair` och `makeup` attribut. Använd dem med hjälp av parametern [ansikts igenkänning](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395236) `returnFaceAttributes` . 

* Öka storleks gränsen för indata-bildfiler från 4 MB till 6 MB i [ansikts-detect](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395236), [FaceList ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395250), [LargeFaceList – Lägg till](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/5a158c10d2de3616c086f2d3)ansikte, [PersonGroup person – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f3039523b) och [LargePersonGroup person – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/599adf2a3a7b9412a4d53f42).

## <a name="march-2018"></a>Mars 2018

* Lade till Million-Scale behållare: [LargeFaceList](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/5a157b68d2de3616c086f2cc) och [LargePersonGroup](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/599acdee6ac60f11b48b5a9d). Mer information om [hur du använder funktionen för storskalig skalning](Face-API-How-to-Topics/how-to-use-large-scale.md).

* En ökat [ansikts identifierad](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395239) `maxNumOfCandidatesReturned` parameter från [1, 5] till [1, 100] och standardvärdet är 10.

## <a name="may-2017"></a>Maj 2017

* Attributen,,,, och har lagts till `hair` `makeup` `accessory` `occlusion` `blur` `exposure` `noise` i parametern [Face-detect](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395236) `returnFaceAttributes` .

* 10 000 personer som stöds i en PersonGroup och [identifierar ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395239).

* Sid brytning som stöds i [PersonGroup person-lista](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395241) med valfria parametrar: `start` och `top` .

* Samtidighet som stöds vid tillägg/borttagning av ansikten mot olika FaceLists och olika personer i PersonGroup.

## <a name="march-2017"></a>Mars 2017
* Attribut har lagts till `emotion` i [Face-detect-](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395236) `returnFaceAttributes` parametern.

* Det gick inte att identifiera sidan igen med den rektangel som returnerades från [ansikts igenkänning](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395236) som `targetFace` i [FaceList – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395250) och [PersonGroup person – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f3039523b).

* Fast den identifierbara ansikts storleken för att se till att det är strikt mellan 36x36 och 4096x4096 bild punkter.

## <a name="november-2016"></a>November 2016
* Lade till Ansiktslagring standard prenumeration för lagring av ytterligare beständiga ansikten när du använder [PersonGroup person – Lägg](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f3039523b) till ansikte eller [FaceList – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395250) för identifiering eller likhets matchning. De lagrade bilderna debiteras med USD 0:50 per 1000 ansikten och priset justeras proportionerligt på daglig basis. Prenumerationer på den kostnads fria nivån fortsätter att vara begränsade till totalt 1 000 personer.

## <a name="october-2016"></a>Oktober 2016
* Ett fel meddelande om fler än en ansikte i targetFace har ändrats från det finns fler än ett ansikte i bilden till det finns fler än ett ansikte i bilden i [FaceList – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395250) och [PersonGroup person – Lägg till ansikte](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f3039523b).

## <a name="july-2016"></a>Juli 2016
* Ansikte som stöds för person objekts autentisering i [FACET-verify](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f3039523a).

* Valfri parameter har lagts till `mode` för val av två arbets lägen: `matchPerson` och `matchFace` i [FACET-identifiera liknande](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395237) och standard är `matchPerson` .

* Valfri parameter har lagts till `confidenceThreshold` för att användaren ska kunna ange tröskeln för om ett ansikte tillhör ett person objekt i [ansikts-identifiera](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395239).

* Valfria och parametrar har lagts till `start` `top` i [PersonGroup-listan](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395248) för att användaren ska kunna ange start punkten och det totala antalet PersonGroups som ska visas.

## <a name="v10-changes-from-v0"></a>V 1.0 ändras från v0

* Uppdaterade tjänstens rot slut punkt från ```https://westus.api.cognitive.microsoft.com/face/v0/``` till ```https://westus.api.cognitive.microsoft.com/face/v1.0/``` . Ändringarna tillämpas på: [ansikts-detect](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395236), [ansikte-Identify](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395239), [ansikte – hitta liknande](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395237) och [ansikts grupp](https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395238).

* Uppdaterade storleken på den minimala identifierade ytan till 36x36 bild punkter. Ansikten som är mindre än 36x36 pixlar kommer inte att identifieras.

* Föråldrade PersonGroup och person uppgifter i ansikts v0. Dessa data kan inte nås med Face V 1.0-tjänsten.

* Föråldrad v0-slutpunkt för Ansikts-API den 30 juni 2016.
