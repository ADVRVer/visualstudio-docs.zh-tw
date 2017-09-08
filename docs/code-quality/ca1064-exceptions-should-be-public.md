---
title: 'CA1064: Exceptions should be public | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
manager: wpickett
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 3fd8a83eabc89bd44d60d470422f00849da87e87
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Exceptions should be public
|||  
|-|-|  
|TypeName|ExceptionsShouldBePublic|  
|CheckId|CA1064|  
|Category|Microsoft.Design|  
|Breaking Change|Non Breaking|  
  
## <a name="cause"></a>Cause  
 A non-public exception derives directly from <xref:System.Exception>, <xref:System.SystemException>, or <xref:System.ApplicationException>.  
  
## <a name="rule-description"></a>Rule Description  
 An internal exception is only visible inside its own internal scope. After the exception falls outside the internal scope, only the base exception can be used to catch the exception. If the internal exception is inherited from <xref:System.Exception>, <xref:System.SystemException>, or <xref:System.ApplicationException>, the external code will not have sufficient information to know what to do with the exception.  
  
 But, if the code has a public exception that later is used as the base for a internal exception, it is reasonable to assume the code further out will be able to do something intelligent with the base exception. The public exception will have more information than what is provided by T:System.Exception, T:System.SystemException, or T:System.ApplicationException.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 Make the exception public, or derive the internal exception from a public exception that is not <xref:System.Exception>, <xref:System.SystemException>, or <xref:System.ApplicationException>.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Suppress a message from this rule if you are sure in all cases that the private exception will be caught within its own internal scope.  
  
## <a name="example"></a>Example  
 This rule fires on the first example method, FirstCustomException because the exception class derives directly from Exception and is internal. The rule does not fire on the SecondCustomException class because although the class also derives directly from Exception, the class is declared public. The third class also does not fire the rule because it does not derive directly from <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, or <xref:System.ApplicationException?displayProperty=fullName>.  
  
 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]