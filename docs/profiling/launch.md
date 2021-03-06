---
title: Launch | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3b8a584e8e024416ec9c3feca63297eed4497624
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="launch"></a>啟動
**Launch** 選項會使用取樣方法來啟動分析工具，也會啟動指定的應用程式。  
  
 若要使用 **Launch** 選項，您必須在 **Start** 選項中指定 **Sample** 方法。  
  
## <a name="syntax"></a>語法  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### <a name="parameters"></a>參數  
 `AppName`  
 要啟動的應用程式名稱。 支援目前目錄中的完整和局部路徑。  
  
## <a name="valid-options"></a>有效選項  
 在單一命令列上，下列 VSPerfCmd 選項可以與 **Launch** 選項一起使用。  
  
 **Start:** `Method`  
 初始化命令列分析工具工作階段，並設定指定的分析方法。  
  
 **GlobalOn** 和 **GlobalOff**  
 繼續 (**GlobalOn**) 或暫停 (**GlobalOff**) 分析，但未結束分析工作階段。  
  
 **ProcessOn:** `PID` 和 **ProcessOff**:`PID`  
 繼續 (**ProcessOn**) 或暫停 (**ProcessOff**) 所指定處理序的分析。  
  
 **TargetCLR**  
 指定要在分析工作階段中載入多個版本時分析的 .NET Framework Common Language Runtime (CLR) 版本。 預設會分析第一個載入的版本。  
  
## <a name="exclusive-options"></a>專屬選項  
 下列選項只能與 **Launch** 選項搭配使用。  
  
 **Console**  
 在新視窗中啟動指定的命令列應用程式。  
  
 **Args:** `ArgList`  
 指定要傳遞至應用程式的引數清單。  
  
 **LineOff**  
 停用程式行層級分析資料的收集。  
  
## <a name="sampling-options"></a>取樣選項  
 下列其中一個取樣間隔選項可以指定於 **Launch** 命令列上。 預設取樣間隔為 10,000,000 個處理器時脈週期。  
  
 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:**`Events`]**Counter**[**:**`Name`,`Reload`,`FriendlyName`]**GC**[:**allocation**&#124;**lifetime**]  
 指定取樣間隔的數目和類型。  
  
-   **Timer** - 每 `Cycles` 個未暫止處理器時脈週期取樣一次。 如果未指定 `Cycles`，會使用 10,000,000 個週期。  
  
-   **PF** - 每 `Events` 個分頁錯誤取樣一次。 如果未指定 `Events`，則會使用 10 個分頁錯誤。  
  
-   **Sys** - 對作業系統每呼叫 `Events` 次取樣一次。 如果未指定 `Events`，則會使用 10 次系統呼叫。  
  
-   **Counter** - `Name` 所指定的 CPU 效能計數器每 `Reload` 個數目就取樣一次。 選擇性，`FriendlyName` 可以指定要作為分析工具報表中資料行標頭的字串。  
  
-   **GC** - 收集 .NET 記憶體資料。 根據預設 (**配置**)，系統會在每個記憶體配置事件發生時收集資料。 指定 **lifetime** 參數時，也會在每個記憶體回收事件發生時收集資料。  
  
## <a name="example"></a>範例  
 此範例示範如何使用 **Launch** 來啟動應用程式。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)