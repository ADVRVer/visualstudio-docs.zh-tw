---
title: "運算式評估工具架構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "架構中，運算式評估工具"
  - "運算式評估工具架構"
  - "偵錯的 [偵錯 SDK]，運算式評估工具"
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 運算式評估工具架構
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 整合 Visual Studio 偵錯封裝的專用語言表示實作所需的運算式評估工具 \(EE\) 介面和呼叫的通用語言執行階段符號提供者 \(SP\) 和繫結器介面。 預存程序和繫結器物件，以及目前執行的位址，會進行評估運算式的內容。 這些介面產生及耗用的資訊代表 EE 架構中的重要概念。  
  
## 概觀  
  
### 剖析運算式  
 當您偵錯程式時，會將多個原因，但永遠 （由使用者用來放置中斷點或例外狀況所造成的其中一個） 的中斷點處停止偵錯程式評估運算式。 所表示的是 Visual Studio 時取得堆疊框架，此時 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 介面，從 \[偵錯引擎 \(DE\)。 Visual Studio 接著會呼叫 [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 取得 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 介面。 此介面上呈現的內容，在其中的運算式可以評估; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 是評估程序的進入點。 目前，所有介面的都實作方式 DE。  
  
 當 `IDebugExpressionContext2::ParseText` 是呼叫，DE 具現化語言的原始程式檔發生中斷點的位置相關聯的 EE （DE 也會具現化 SH 此時）。 EE 由 [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) 介面。 然後呼叫 DE [剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 若要剖析的運算式 （以文字形式） 的運算式，準備好進行評估。 剖析的運算式由 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 介面。 請注意，通常剖析並不會在此時評估運算式。  
  
 DE 會建立該物件會實作 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 介面，將 `IDebugParsedExpression` 物件插入 `IDebugExpression2` 物件，並傳回 `IDebugExpression2` 物件從 `IDebugExpressionContext2::ParseText`。  
  
### 評估運算式  
 Visual Studio 會呼叫 \[ [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 評估已剖析的運算式。 這兩種方法呼叫 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) \(`IDebugExpression2::EvaluateSync` 呼叫的方法，而 `IDebugExpression2::EvaluateAsync` 呼叫方法，透過背景執行緒\) 評估剖析的運算式，並傳回 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 介面，表示已剖析運算式的型別與值。`IDebugParsedExpression::EvaluateSync` 使用提供的 SH、 位址和繫結器將已剖析的運算式轉換成實際值，由 `IDebugProperty2` 介面。  
  
### 例如  
 在執行中的程式遇到中斷點之後，使用者選擇檢視中的變數 **快速監看式** 對話方塊。 這個對話方塊會顯示變數的名稱，其值，其型別。 使用者通常可以變更值。  
  
 當 **快速監看式** 而顯示對話方塊，正在檢查變數的名稱以文字格式來傳送 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)。 這會傳回 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 物件，代表剖析的運算式，在此案例中為變數。[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 然後呼叫以產生 `IDebugProperty2` 物件，表示變數的值和型別，以及它的名稱。 就會顯示此資訊。  
  
 如果使用者變更變數的值 [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) 呼叫新的值，變更在記憶體中變數的值，所以會使用該程式繼續執行時執行。  
  
 請參閱 [顯示 \[區域變數\]](../../extensibility/debugger/displaying-locals.md) 如需有關此程序顯示變數的值。 請參閱 [變更本機值](../../extensibility/debugger/changing-the-value-of-a-local.md) 如需有關如何變更變數的值。  
  
## 本章節內容  
 [評估內容](../../extensibility/debugger/evaluation-context.md)  
 提供當 DE 呼叫 EE 傳遞的引數。  
  
 [索引鍵運算式評估工具介面](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 說明撰寫 EE，以及評估內容時所需的重要介面。  
  
## 請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [顯示 \[區域變數\]](../../extensibility/debugger/displaying-locals.md)   
 [變更本機值](../../extensibility/debugger/changing-the-value-of-a-local.md)