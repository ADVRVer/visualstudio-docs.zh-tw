---
title: "CA1713： 事件不應有 before 或 after 前置字元 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 18e6e5d712e538c67abb6e8946df581c38cb9876
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713：事件不應有 before 或 after 前置字元
|||  
|-|-|  
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|  
|CheckId|CA1713|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 事件的名稱啟動與 'Before' 或 'After'。  
  
## <a name="rule-description"></a>規則描述  
 事件名稱應該要引發事件的動作描述。 若要命名在特定序列 (Sequence) 中引發的相關事件，請使用現在式或過去式表示動作序列相對的位置。 例如，當命名的一組事件引發時關閉資源時，您可能會為它命名 '關閉' 和 'Closed'，而不是 'BeforeClose' 和 'AfterClose'。  
  
 命名慣例提供共同的外觀文件庫目標通用語言執行平台。 這會減少需要新的軟體程式庫，而增加文件庫由具備專業知識在開發 managed 程式碼開發的客戶信心的學習曲線。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 事件名稱，從移除前置字元，請考慮變更要使用現在式或過去式動詞命令的名稱。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。