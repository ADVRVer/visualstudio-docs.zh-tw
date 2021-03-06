---
title: "Ca1505： 應避免撰寫無法維護的程式碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5abaaba67d3390e36c4ad792d7b95bf41be80c2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505：應避免撰寫無法維護的程式碼
|||  
|-|-|  
|TypeName|AvoidUnmantainableCode|  
|CheckId|CA1505|  
|分類|Microsoft.Maintainability|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 類型或方法的維護性指標值很低。  
  
## <a name="rule-description"></a>規則描述  
 可維護性指數計算方式是使用下列度量： 程式碼，程式的磁碟區和循環複雜度的線條。 程式的磁碟區是了解類型或方法為基礎的運算子和程式碼中的運算元數目的困難度的量值。 循環複雜度是複雜度的量值的結構類型或方法。 您可以進一步了解在程式碼度量[測量複雜度和維護性 Managed 程式碼的](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)。  
  
 低的可維護性指數表示的類型或方法很可能難以維護，因此會重新設計的不錯候選者。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正這種違規，重新設計的類型或方法，嘗試將它分割成較小且更受關注的型別或方法。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 當類型或方法仍視為可維護性，儘管其大小太大，或無法分割類型或方法時，請排除這個警告。  
  
## <a name="see-also"></a>請參閱  
 [維護性警告](../code-quality/maintainability-warnings.md)   
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)