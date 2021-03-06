---
title: "動態指令碼分析概觀 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9413e8b6e6db0c81eb1853c24506d20c8d06f3e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-profiling-overview"></a>動態指令碼分析概觀
[動態指令碼分析工具介面](../winscript/reference/active-script-profiler-interfaces.md)可啟用指令碼引擎的分析。 動態指令碼分析包含下列各部分：  
  
-   語言引擎  
  
-   主機  
  
-   程式碼剖析工具  
  
## <a name="language-engine"></a>語言引擎  
 語言引擎會執行指令碼。 它提供的方法可啟用指令碼在執行時的分析。 啟用分析時，語言引擎可接受分析工具 COM 物件的類別識別碼 (CLSID) 作為引數。 它會建立分析工具 COM 物件的執行個體，然後在發生各種事件時呼叫分析工具。  
  
 語言引擎會實作 [IActiveScriptProfilerControl 介面](../winscript/reference/iactivescriptprofilercontrol-interface.md)。  
  
> [!NOTE]
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 語言執行階段會在建立時檢查 JS_PROFILER 環境變數，判斷是否應該啟用分析。 如果此變數設定為分析工具的 CLSID，則語言執行階段會建立分析工具 COM 物件執行個體，並使用變數的值來判斷要建立的分析工具。  
  
## <a name="host"></a>主機  
 主機會建立語言引擎，並提供具有要執行之指令碼的語言引擎。 智慧主機也提供偵錯工具或分析工具可使用的文件內容，以在您偵錯或分析時提供更好的資訊。  
  
## <a name="profiler"></a>程式碼剖析工具  
 分析工具會在發生各種事件時收到來自語言引擎的呼叫。 分析工具必須註冊為 COM 物件，並且必須實作 [IActiveScriptProfilerCallback 介面](../winscript/reference/iactivescriptprofilercallback-interface.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼分析工具介面](../winscript/reference/active-script-profiler-interfaces.md)