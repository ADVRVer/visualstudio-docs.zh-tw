---
title: "DA0501：進行程式碼剖析之處理序所需的平均 CPU 使用量。 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2269ea4c58703cf5f2c4d8516e14cb40b342c958

---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501：進行程式碼剖析之處理序所需的平均 CPU 使用量。
|||  
|-|-|  
|規則 ID|DA501|  
|分類|資源監視|  
|程式碼剖析方法|全部|  
|訊息|所分析之處理序的平均 CPU 消耗。|  
|規則型別|資訊|  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。  
  
## <a name="rule-description"></a>規則描述  
 此訊息報告處理器忙於執行應用程式指令的時間百分比。 報告的值是所分析的處理序作用中之所有測量間隔的平均。 在有多個處理器的電腦上，值可以大於 100%。  
  
## <a name="how-to-use-rule-data"></a>如何使用規則資料  
 使用規則值可比較程式不同版本或組建的效能，或了解不同測試情節中的應用程式效能。


<!--HONumber=Feb17_HO4-->


