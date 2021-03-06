---
title: "CA2220： 完成項應該呼叫基底類別完成項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 46427cffe64c6c81e0f262520a61c1b1ea01fff8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220：完成項應該呼叫基底類別完成項
|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 覆寫的型別<xref:System.Object.Finalize%2A?displayProperty=fullName>不會呼叫<xref:System.Object.Finalize%2A>其基底類別中的方法。  
  
## <a name="rule-description"></a>規則描述  
 最終化必須透過繼承階層架構 (Inheritance Hierarchy) 進行傳播。 若要確保這種情況，類型必須呼叫其基底類別<xref:System.Object.Finalize%2A>方法從其本身內<xref:System.Object.Finalize%2A>方法。 C# 編譯器會自動新增呼叫基底類別完成項。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，呼叫基底型別<xref:System.Object.Finalize%2A>方法，從您<xref:System.Object.Finalize%2A>方法。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 某些以 common language runtime 為目標的編譯器插入的 Microsoft intermediate language (MSIL) 中呼叫基底類型完成項。 如果此規則的警告報告時，編譯器不會插入該呼叫，您必須將它加入您的程式碼。  
  
## <a name="example"></a>範例  
 下列 Visual Basic 範例顯示型別`TypeB`正確呼叫<xref:System.Object.Finalize%2A>其基底類別中的方法。  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## <a name="see-also"></a>請參閱  
 [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)