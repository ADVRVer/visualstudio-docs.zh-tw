---
title: "如何： 使用階層連結巡覽 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 95e79ab384c6311aa17f2592b514d62b899b8b6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-breadcrumb-navigation"></a>HOW TO：使用階層連結巡覽
有三種主要方式可用來變更顯示在 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 中的活動集合：  
  
1.  按兩下來向內切入子活動。  
  
2.  按一下階層連結列上的按鈕來巡覽至祖系活動。  
  
3.  就地展開或摺疊活動。  
  
### <a name="using-breadcrumb-navigation"></a>使用階層連結巡覽  
  
1.  按兩下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 活動，從根活動變更為按下後的活動。 按下後的活動就會完全於根目錄展開，而且其祖系會顯示於階層連結列。 有時，這會稱為向內切入或向外切出活動。  
  
2.  若要巡覽至目前根活動的祖系，請按一下階層連結列上的活動。  
  
### <a name="expanding-or-collapsing-an-activity-in-place"></a>就地展開或摺疊活動  
  
1.  按一下活動上的＞形箭號，即可就地展開或摺疊活動。  
  
2.  按一下按鈕而變更展開狀態時，展開的新狀態會儲存於 XAML。  
  
    > [!WARNING]
    >  並非所有活動都可就地展開。 無法就地展開活動的情況有兩種：父活動不允許就地展開子活動，(例如，流程圖中的活動無法就地展開)，或活動設計工具不允許將本身就地展開。 雖然包含於 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 的活動設計工具都不會發生後者的情況，但是某些自訂活動也許會有這種情況。  
  
### <a name="expanding-all-or-collapsing-all-activities"></a>全部展開或全部摺疊活動  
  
1.  使用**全部展開**和**全部摺疊**展開或摺疊目前階層連結根目錄下的所有活動的使用者介面中的按鈕。 請注意，全部展開和全部摺疊都是全域狀態。 這表示，當您變更根活動使用階層連結巡覽，全部展開或摺疊的所有狀態一直保存，直到您按一下**還原**。  
  
2.  套用全部展開或摺疊的所有狀態之後，您可以按一下**還原**按鈕，以返回查看先前套用至每個活動的狀態。  
  
    > [!WARNING]
    >  如果某個活動，例如<xref:System.Activities.Statements.Flowchart>，已選擇不就地展開，功能與相關聯**全部展開**和**全部摺疊**上已停用按鈕**流程圖**設計工具。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]**流程圖**設計工具，請參閱[流程圖](../workflow-designer/flowchart-activity-designer.md)主題。  
  
    > [!WARNING]
    >  全部展開中也有特殊效果**交換器**和**TryCatch**活動設計工具。 當您按一下**全部展開**，顯示的切換案例與所有的 try/catch/finally 區塊。 按一下**還原**或**全部摺疊**返回這些設計工具恢復預設狀態，您可從中按一下個別的案例/區塊來檢視其內容。