---
title: "CA1704： 識別項應該使用正確的拼字 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 63b10dd1d1037ee90156505f2e73105be7a9ee63
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704：識別項應該使用正確的拼字
|||  
|-|-|  
|TypeName|IdentifiersShouldBeSpelledCorrectly|  
|CheckId|CA1704|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 識別項名稱包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。 此規則不會不檢查建構函式或特殊名為的成員，例如 get 和 set 屬性存取子。  
  
## <a name="rule-description"></a>規則描述  
 此規則會識別項剖析成語彙基元，並檢查每個語彙基元的拼字。 剖析的演算法會執行下列轉換：  
  
-   大寫字母開始新的權杖。 例如，MyNameIsJoe 會 token 化以"My"、"Name"、"Is"、"Joe"。  
  
-   多個大寫字母，最後一個大寫字母會啟動新的權杖。 例如，GUIEditor 會 token 化以 「 GUI"，"Editor"。  
  
-   會移除開頭和尾端所有格符號。 例如，'sender' 會語彙基元化為"sender"。  
  
-   表示語彙基元的結尾底線，而且會移除。 例如，Hello_world 會語彙基元化為"Hello"，"world"。  
  
-   會移除內嵌的連字號。 例如，for&mat 會語彙基元化為 "format"。  
  
 根據預設，會使用拼字檢查程式的英文 (en) 版。 目前使用任何其他語言的字典不。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，更正單字的拼字，或將該字加入至名為 CustomDictionary.xml 自訂字典。 安裝目錄中的工具，專案目錄，或在 「 工具 」 的使用者設定檔相關聯的目錄中，將字典 (%USERPROFILE%\Application 資料\\...)。若要了解如何將自訂字典中的專案至[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，請參閱[How to： 自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
-   新增應該不會造成違反字典/單字/Recognized 路徑下的單字。  
  
-   新增應該會造成無法辨識字典/字路徑下的違規的單字。  
  
-   新增應該標示的文字，為已過時字典/字路徑下已過時。 請參閱相關的規則主題[ca1726 建議： 使用慣用的詞彙](../code-quality/ca1726-use-preferred-terms.md)如需詳細資訊。  
  
-   加入至字典/首字母縮略字/CasingExceptions 路徑的縮略字大小寫規則的例外狀況。  
  
 以下是結構的自訂字典檔案的範例。  
  
```  
<Dictionary>  
   <Words>  
      <Unrecognized>  
         <Word>cb</Word>  
      </Unrecognized>  
      <Recognized>  
         <Word>stylesheet</Word>  
         <Word>GotDotNet</Word>  
      </Recognized>  
      <Deprecated>  
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>  
      </Deprecated>  
   </Words>  
   <Acronyms>  
      <CasingExceptions>  
         <Acronym>CJK</Acronym>  
         <Acronym>Pi</Acronym>  
      </CasingExceptions>  
   </Acronyms>  
</Dictionary>  
```  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 如果刻意拼錯字則 word 會套用到一組有限的文件庫，隱藏此規則的警告。 正確拼寫正確的單字會降低所需的新軟體程式庫的學習曲線。  
  
## <a name="related-rules"></a>相關的規則  
 [CA2204：常值必須使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703：資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707：識別項名稱不應該包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726：建議使用慣用詞彙](../code-quality/ca1726-use-preferred-terms.md)  
  
## <a name="see-also"></a>請參閱  
 [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
