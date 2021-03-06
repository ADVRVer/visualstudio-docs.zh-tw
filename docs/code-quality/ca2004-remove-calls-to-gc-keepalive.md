---
title: "Ca2004： 必須移除 gc。KeepAlive |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dd6cc8b51ddd8f9e8813229cf66b9facb52e4668
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004：必須移除對 GC.KeepAlive 的呼叫
|||  
|-|-|  
|TypeName|RemoveCallsToGCKeepAlive|  
|CheckId|CA2004|  
|分類|Microsoft.Reliability|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 類別會使用`SafeHandle`但仍包含呼叫`GC.KeepAlive`。  
  
## <a name="rule-description"></a>規則描述  
 如果您要將它轉換成`SafeHandle`使用方式，移除所有對`GC.KeepAlive`（物件）。 在此情況下，類別應該不需要呼叫`GC.KeepAlive`，假設它們沒有完成項，但依賴`SafeHandle`完成作業系統控制代碼。  雖然離開中呼叫成本`GC.KeepAlive`可能是微不足道測量效能，相比，呼叫`GC.KeepAlive`是必要或不足以解決可能不再存在的問題，讓程式碼更難的存留期維護。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 移除呼叫`GC.KeepAlive`。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 您可以隱藏這個警告，只有不是技術上正確將轉換成`SafeHandle`您類別中的使用方式。