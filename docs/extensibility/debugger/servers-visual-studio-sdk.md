---
title: "伺服器 (Visual Studio SDK) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 404048e37f0a95ac1425250cfdcd098c4eb7f59d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="servers-visual-studio-sdk"></a>伺服器 (Visual Studio SDK)
偵錯工具就架構而言，**伺服器**:  
  
-   為連接埠和通訊埠供應商的容器，用來與工作階段的偵錯管理員 (SDM) 通訊連接埠和通訊埠供應商和偵錯引擎。  
  
-   可以依名稱、 識別自己，並列舉其連接埠和通訊埠供應商。  
  
-   由[IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)介面，只藉由 Visual Studio （Visual Studio 執行的每個執行個體的伺服器一個執行個體）。  
  
## <a name="see-also"></a>請參閱  
 [連接埠](../../extensibility/debugger/ports.md)   
 [連接埠供應商](../../extensibility/debugger/port-suppliers.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)