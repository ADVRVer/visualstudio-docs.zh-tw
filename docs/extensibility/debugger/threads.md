---
title: "執行緒 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6faced71ba03bcf1c4bf1849515bdf7b4fe455f8
ms.lasthandoff: 02/22/2017

---
# <a name="threads"></a>執行緒
偵錯工具就架構而言，**執行緒**:  
  
-   是計算的基本單位。 執行緒循序執行，其內容中的單一呼叫堆疊，從一種程式碼內容移至下一步的指示。  
  
-   可以識別本身也程式正在執行中，並將它名為、 暫止，並繼續。 執行緒也可以列舉其相關聯的堆疊框架，而且在某些情況下可以移到另一個堆疊框架。 指定堆疊框架的內容，執行緒可以傳回其相關聯的邏輯執行緒，如果有的話。 執行緒都會有屬性，例如暫停次數，可以顯示在 IDE 的 [執行緒] 視窗中。  
  
-   由[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)介面，通常由偵錯引擎 (DE) 或由於執行程式的虛擬機器所建立。  
  
## <a name="see-also"></a>另請參閱  
 [程式](../../extensibility/debugger/programs.md)   
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [偵錯工具的概念](../../extensibility/debugger/debugger-concepts.md)   
 [偵錯的工作階段管理員](../../extensibility/debugger/session-debug-manager.md)
