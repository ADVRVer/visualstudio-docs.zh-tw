---
title: "CA2104： 不要宣告唯讀的可變動參考類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bbd12d09c95f1ec93c7232901270cfbece311693
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104：不要宣告唯讀的可變動參考類型
|||  
|-|-|  
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|分類|Microsoft.Security|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 外部可見類型包含了可變動參考類型的外部可見唯讀欄位。  
  
## <a name="rule-description"></a>規則描述  
 可變動類型是可以修改執行個體資料的類型。 <xref:System.Text.StringBuilder?displayProperty=fullName>類別是可變動參考類型的範例。 它包含的成員可以變更類別的執行個體的值。 不可變的參考類型的範例是<xref:System.String?displayProperty=fullName>類別。 已執行個體化之後，可以永遠不會變更其值。  
  
 唯讀的修飾詞 ([readonly](/dotnet/csharp/language-reference/keywords/readonly)在 C# 中， [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，和[const](/cpp/cpp/const-cpp) c + + 中) 上的參考類型欄位 （c + + 中的指標） 會防止欄位取代為參考類型的不同執行個體。 不過，修飾詞不會阻止執行個體資料的欄位正在修改透過參考類型。  
  
 唯讀陣列欄位免套用此規則，但改為導致違反[CA2105： 陣列欄位不應該為唯讀](../code-quality/ca2105-array-fields-should-not-be-read-only.md)規則。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請移除唯讀修飾詞，或如果可接受的重大變更，請使用不可變的類型取代欄位。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果欄位類型是不變。  
  
## <a name="example"></a>範例  
 下列範例顯示會導致違反此規則的欄位宣告。  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]