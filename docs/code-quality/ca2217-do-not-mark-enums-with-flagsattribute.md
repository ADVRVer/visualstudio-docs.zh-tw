---
title: "CA2217： 不要不以 FlagsAttribute 標記列舉 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 10b3667a8147b0eea77f79735fca465401f7c436
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217：不要以 FlagsAttribute 標記列舉
|||  
|-|-|  
|TypeName|DoNotMarkEnumsWithFlags|  
|CheckId|CA2217|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 外部可見的列舉型別會標示<xref:System.FlagsAttribute>和的一個或多個值不是乘冪的兩個或其他組合列舉上定義值。  
  
## <a name="rule-description"></a>規則描述  
 列舉型別應該具有<xref:System.FlagsAttribute>呈現只有定義在列舉中的每個值的乘冪，或組合的定義值。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請移除<xref:System.FlagsAttribute>列舉型別。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例會示範列舉型別，[色彩] 包含 3 這個值，都不、 二的乘冪，也不是組合任何定義的值。 不應該用標記色彩列舉<xref:System.FlagsAttribute>。  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
 [!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例示範的列舉，天，符合的需求與 System.FlagsAttribute 標示。  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
 [!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>請參閱  
 <xref:System.FlagsAttribute?displayProperty=fullName>