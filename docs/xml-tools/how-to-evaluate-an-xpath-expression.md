---
title: "How to： 評估 XPath 運算式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8a0072df206fcdfc27966632e3801316bcfb7274
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-evaluate-an-xpath-expression"></a>HOW TO：評估 XPath 運算式
您可以評估 XPath 運算式與**快速監看式** 對話方塊。 根據 W3C XPath 1.0 版建議事項，XPath 運算式必須有效。 目前的 XSLT 內容 — 也就是`self::node()`中的節點**區域變數**視窗，提供 XPath 運算式的評估內容。  
  
 下列清單說明當評估 XPath 運算式時，支援哪些函式：  
  
-   支援內建 XPath 函式。  
  
-   不支援內建 XSLT 函式。  
  
-   不支援使用者定義函式。  
  
> [!NOTE]
>  下列程序會使用 belowAvg.xsl 及 books.xml 檔[逐步解說： 偵錯 XSLT 樣式表](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)主題。  
  
### <a name="to-evaluate-an-xpath-expression"></a>評估 XPath 運算式  
  
1.  在 `xsl:if` 開始標記處插入中斷點。  
  
2.  按一下**偵錯 XSL** XML 編輯器工具列上的按鈕。  
  
     偵錯工具會啟動，並在 `xsl:if` 標記處中斷。  
  
3.  以滑鼠右鍵按一下並選取**快速監看式**。  
  
     **快速監看式**對話方塊隨即出現。  
  
4.  輸入`./price/text()`中**運算式**欄位**快速監看式**對話方塊，按一下**重新評估**。  
  
     目前的書籍節點的價格會出現在**值**方塊。  
  
5.  將 XPath 運算式變更為`./price/text() < $bookAverage`按一下**重新評估**。  
  
     **值**方塊會顯示 XPath 運算式評估為`true`。  
  
## <a name="see-also"></a>請參閱  
 [偵錯 XSLT](../xml-tools/debugging-xslt.md)