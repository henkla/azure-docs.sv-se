---
title: 'Justera prestanda: Hive, HDInsight & Azure Data Lake Storage Gen2 | Microsoft Docs'
description: Förstå justerings rikt linjer för I/O-intensiva frågor med Hive, HDInsight och Azure Data Lake Storage Gen2.
author: normesta
ms.subservice: data-lake-storage-gen2
ms.service: storage
ms.topic: how-to
ms.date: 11/18/2019
ms.author: normesta
ms.reviewer: stewu
ms.openlocfilehash: 4b1e5dd3c72122ade2fd4d4092bb18a7acf215f5
ms.sourcegitcommit: a43a59e44c14d349d597c3d2fd2bc779989c71d7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/25/2020
ms.locfileid: "95912951"
---
# <a name="tune-performance-hive-hdinsight--azure-data-lake-storage-gen2"></a>Justera prestanda: Hive, HDInsight & Azure Data Lake Storage Gen2

Standardinställningarna har ställts in för att ge bästa prestanda i många olika användnings fall.  För I/O-intensiva frågor kan Hive justeras för att få bättre prestanda med Azure Data Lake Storage Gen2.  

## <a name="prerequisites"></a>Förutsättningar

* **En Azure-prenumeration**. Se [Hämta en kostnadsfri utvärderingsversion av Azure](https://azure.microsoft.com/pricing/free-trial/).
* **Ett data Lake Storage Gen2 konto**. Anvisningar om hur du skapar ett finns i [snabb start: skapa ett Azure Data Lake Storage Gen2 lagrings konto](../common/storage-account-create.md)
* **Azure HDInsight-kluster** med åtkomst till ett data Lake Storage Gen2-konto. Se [använda Azure Data Lake Storage Gen2 med Azure HDInsight-kluster](../../hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2.md)
* **Kör Hive i HDInsight**.  Information om hur du kör Hive-jobb i HDInsight finns i [använda Hive i HDInsight](../../hdinsight/hadoop/hdinsight-use-hive.md)
* **Rikt linjer för prestanda justering på data Lake Storage Gen2**.  Allmänna prestanda koncept finns i [vägledning för data Lake Storage Gen2 prestanda justering](data-lake-storage-performance-tuning-guidance.md)

## <a name="parameters"></a>Parametrar

Här är de viktigaste inställningarna för att justera för förbättrade Data Lake Storage Gen2 prestanda:

* **Hive. Tez. container. size** – mängden minne som används av varje aktivitet

* **Tez. Grouping. min-size** – minsta storlek för varje mapper

* **Tez. Grouping. Max-size** – maximal storlek för varje mappning

* **hive.exec. reduce. byte. per.** dereducerare – storlek på varje minsknings man

**Hive. Tez. container. size** -container-storlek anger hur mycket minne som är tillgängligt för varje aktivitet.  Detta är den viktigaste indatan för styrning av samtidigheten i Hive.  

**Tez. Grouping. min-size** – med den här parametern kan du ange den minsta storleken för varje mapp.  Om antalet mappningar som Tez väljer är mindre än värdet för den här parametern kommer Tez att använda värdet som anges här.

**Tez. Grouping. Max-size** – parametern låter dig ange max storleken för varje mapp.  Om antalet mappningar som Tez väljer är större än värdet för den här parametern kommer Tez att använda värdet som anges här.

**hive.exec. Reducer. bytes. per. reduce** – den här parametern anger storleken på varje minskning.  Som standard är varje minskning 256 MB.  

## <a name="guidance"></a>Vägledning

**Ange hive.exec. dereducerare. bytes. per. reduce** – standardvärdet fungerar bra när data är okomprimerade.  För data som är komprimerade bör du minska storleken på minskningen.  

**Ange Hive. Tez. container. size** – i varje nod anges minnet av garn. nodemanager. Resource. Memory-MB och bör anges korrekt i HDI-kluster som standard.  Mer information om hur du ställer in rätt minne i garn finns i det här [inlägget](../../hdinsight/hdinsight-hadoop-hive-out-of-memory-error-oom.md).

I/O-intensiva arbets belastningar kan dra nytta av mer parallellitet genom att minska storleken på Tez-behållare. Detta ger användaren fler behållare vilket ökar samtidigheten.  Vissa Hive-frågor kräver dock en stor mängd minne (t. ex. MapJoin).  Om det inte finns tillräckligt med minne på den här aktiviteten får du ett slut på minnes undantag under körningen.  Om du får slut på minnes undantag bör du öka minnet.   

Antalet samtidiga aktiviteter som körs eller parallellitet kommer att begränsas av det totala garn minnet.  Antalet garn behållare kommer att diktera hur många samtidiga aktiviteter som kan köras.  För att hitta garn minnet per nod kan du gå till Ambari.  Navigera till garn och Visa fliken configs.  GARN minnet visas i det här fönstret.  

- Totalt garn minne = noder * garn minne per nod
- \# av garn behållare = total garn minne/Tez container storlek

Nyckeln för att förbättra prestanda med hjälp av Data Lake Storage Gen2 är att öka samtidigheten så mycket som möjligt.  Tez beräknar automatiskt antalet uppgifter som ska skapas så att du inte behöver ange den.   

## <a name="example-calculation"></a>Exempel beräkning

Anta att du har ett D14-kluster med 8 noder.  

- Totalt garn minne = noder * garn minne per nod
- Totalt garn minne = 8 noder * 96GB = 768GB
- \# av garn behållare = 768GB/3072MB = 256

## <a name="further-information-on-hive-tuning"></a>Mer information om Hive-justering

Här följer några Bloggar som kan hjälpa dig att justera dina Hive-frågor:
* [Optimera Hive-frågor för Hadoop i HDInsight](../../hdinsight/hdinsight-hadoop-optimize-hive-query.md)
* [Optimera Apache Hive-frågor i Azure HDInsight](../../hdinsight/hdinsight-hadoop-optimize-hive-query.md)
* [Tala om optimering av Hive i HDInsight](https://channel9.msdn.com/events/Machine-Learning-and-Data-Sciences-Conference/Data-Science-Summit-2016/MSDSS25)