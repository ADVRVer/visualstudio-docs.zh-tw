---
title: "CA1702： 複合字應該使用的大小寫正確 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d410f3796cdb30a620f0e0260f8cd529a4428831
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702：複合字應該使用正確的大小寫
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|分類|Microsoft.Naming|  
|中斷變更|組件中斷時引發。<br /><br /> 非-中斷-引發時於型別參數。|  
  
## <a name="cause"></a>原因  
 識別項名稱包含多個單字而其中至少一個單字是大小寫不正確的複合字。  
  
## <a name="rule-description"></a>規則描述  
 識別項的名稱會分成根據其大小寫的單字。 每個連續的兩個字組合會檢查 Microsoft 拼字檢查程式庫。 如果辨識出它是，識別項會產生規則違規。 造成違規的複合字的範例是"CheckSum"和"MultiPart"，這應該大小寫慣例為"Checksum"和"Multipart"，分別。 前一個常見的用法，因為許多例外狀況所內建規則，以及數個單字會加上旗標，例如"Toolbar"和"Filename"時，所應該使用大小寫視為兩個不同的單字 （在此情況下，在"ToolBar"和"FileName"）。  
  
 命名慣例提供共同的外觀文件庫目標通用語言執行平台。 這會減少需要新的軟體程式庫，而增加文件庫由具備專業知識在開發 managed 程式碼開發的客戶信心的學習曲線。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 變更名稱，是正確的大小寫。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果拼字檢查字典所辨識的複合字的兩個部分，且其目的是要使用兩個字。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1701：資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>請參閱  
 [命名方針](/dotnet/standard/design-guidelines/naming-guidelines)   
 [大小寫慣例](/dotnet/standard/design-guidelines/capitalization-conventions)