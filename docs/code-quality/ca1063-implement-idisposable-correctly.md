---
title: "Ca1063： 必須實作 IDisposable 正確 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 33c9b3d7b3cdcfc49c3fac14e5ba3a2dcfc2fc49
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063：必須正確實作 IDisposable
|||  
|-|-|  
|TypeName|ImplementIDisposableCorrectly|  
|CheckId|CA1063|  
|分類|Microsoft.Design|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 `IDisposable`未正確實作。 這個問題的一些原因如下：  
  
-   IDisposable 是重新實作在類別中。  
  
-   完成重新覆寫。  
  
-   會覆寫 dispose。  
  
-   Dispose （） 不是公用，密封，或已命名的處置。  
  
-   Dispose （bool） 不受保護、 虛擬或未密封。  
  
-   未密封的型別，在 dispose （） 必須呼叫 dispose （true）。  
  
-   對於未密封的型別，Finalize 實作不會呼叫其中一個或兩個 dispose （bool） 或案例類別完成項。  
  
 這些模式的其中任何一個違規將會觸發這個警告。  
  
 每個未密封的根 IDisposable 類型都必須提供自己受保護虛擬 void dispose （bool） 的方法。 Dispose （） 應該呼叫 Dipose(true) 和 Finalize 應該呼叫 dispose （false）。 如果您要建立未密封的根 IDisposable 類型，您必須定義 dispose （bool），並呼叫它。 如需詳細資訊，請參閱[清除 Unmanaged 資源上](/dotnet/standard/garbage-collection/unmanaged)中[Framework 設計方針](/dotnet/standard/design-guidelines/index)部分的.NET Framework 說明文件。  
  
## <a name="rule-description"></a>規則描述  
 所有的 IDisposable 類型都需正確地實作 Dispose 模式。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 檢查您的程式碼，並判斷哪些解決方案可以修正此違規。  
  
-   從由 {0} 實作且改為覆寫基底類別 Dispose 實作的介面清單中移除 IDisposable。  
  
-   移除型別 {0} 中的完成項、 覆寫 Dispose (bool disposing)，以及最終處理邏輯中的程式碼路徑其中 'disposing' 為 false。  
  
-   移除 {0}，覆寫 Dispose (bool disposing)，而且將處置邏輯放在程式碼路徑中 'disposing' 為 true。  
  
-   確定 {0} 已宣告為 public 和 sealed。  
  
-   重新命名為 'Dispose' {0}，並請確定它宣告為 public 和 sealed。  
  
-   請確定該 {0} 宣告為 protected、 virtual 和未密封。  
  
-   修改 {0}，讓它會呼叫 dispose （true），然後呼叫 GC。目前的物件執行個體上的 SuppressFinalize ('this' Me' 中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])，然後傳回。  
  
-   修改 {0}，讓它會呼叫 dispose （false），然後傳回。  
  
-   如果您正在撰寫的未密封的根 IDisposable 的類別，請確定實作 IDisposable 的遵循本節稍早描述的模式。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="pseudo-code-example"></a>虛擬程式碼範例  
 下列虛擬程式碼提供 dispose （bool） 應如何實作中使用受管理的類別和原生資源的一般的範例。  
  
```  
public class Resource : IDisposable   
{  
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);  
    private AnotherResource managedResource = new AnotherResource();  
  
// Dispose() calls Dispose(true)  
    public void Dispose()  
    {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
    // NOTE: Leave out the finalizer altogether if this class doesn't   
    // own unmanaged resources itself, but leave the other methods  
    // exactly as they are.   
    ~Resource()   
    {  
        // Finalizer calls Dispose(false)  
        Dispose(false);  
    }  
    // The bulk of the clean-up code is implemented in Dispose(bool)  
    protected virtual void Dispose(bool disposing)  
    {  
        if (disposing)   
        {  
            // free managed resources  
            if (managedResource != null)  
            {  
                managedResource.Dispose();  
                managedResource = null;  
            }  
        }  
        // free native resources if there are any.  
        if (nativeResource != IntPtr.Zero)   
        {  
            Marshal.FreeHGlobal(nativeResource);  
            nativeResource = IntPtr.Zero;  
        }  
    }  
}  
```