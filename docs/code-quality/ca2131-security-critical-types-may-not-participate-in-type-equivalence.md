---
title: "CA2131： 安全性關鍵類型可能未參與類型等價 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2b1ba8aa4584d0d0505c7916d05e7c9bd6f446da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131：安全性關鍵類型可能未參與類型等價
|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 類型會參與類型等價或類型本身，或標示的成員或欄位型別的<xref:System.Security.SecurityCriticalAttribute>屬性。  
  
## <a name="rule-description"></a>規則描述  
 此規則會引發任何關鍵的類型或包含參與類型等價之關鍵方法或欄位的類型。 當 CLR 偵測到這類類型時，它便無法載入它與<xref:System.TypeLoadException>在執行階段。 通常，只有在使用者手動實作類型等價，而不是依賴 tlbimp 和編譯器進行類型等價時，就會引發這項規則。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請移除 SecurityCritical 屬性。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例示範介面、 方法，並會導致引發此規則的欄位。  
  
 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [安全性透明的程式碼，層級 2](/dotnet/framework/misc/security-transparent-code-level-2)