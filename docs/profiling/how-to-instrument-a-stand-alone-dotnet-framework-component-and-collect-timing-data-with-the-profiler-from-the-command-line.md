---
title: "如何：從命令列使用程式碼剖析工具以檢測獨立的 .NET Framework 元件並收集計時資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：從命令列使用程式碼剖析工具以檢測獨立的 .NET Framework 元件並收集計時資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具來檢測 .NET Framework 元件 \(例如 .exe 或 .dll 檔案\)，以及收集詳細的執行時間資料。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增強安全性功能，需要在 Visual Studio 分析工具收集這些平台資料的方式上進行重大變更。  Windows 市集應用程式也需要新的收集技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
>   
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。  若要使用分析工具命令列工具，您必須將工具路徑加入至 \[命令提示字元\] 視窗的 PATH 環境變數，或將它加入至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
>   
>  有命令列程式碼剖析工具的特定程序才可將階層互動資料加入至程式碼剖析。  請參閱 [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)。  
  
 若要使用檢測方法來收集 .NET Framework 元件中詳細的時間資料，您可以使用 [VSInstr.exe](../profiling/vsinstr.md) 工具來產生已檢測後的元件，以及 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具來初始化程式碼剖析環境變數。  接著啟動程式碼剖析工具。  
  
 當執行檢測元件時，時間資料會自動收集至資料檔案。  您可以在程式碼剖析工作階段期間暫停和繼續資料收集。  
  
 若要結束程式碼剖析工作階段，請關閉目標應用程式，然後明確地關閉程式碼剖析工具。  在許多情況下，我們建議在工作階段結尾清除程式碼剖析環境變數。  
  
## 啟動程式碼剖析工作階段  
  
#### 若要使用檢測方法開始進行程式碼剖析  
  
1.  開啟 \[命令提示字元\] 視窗。  如有需要，請將程式碼剖析工具目錄加入至您的 PATH 環境變數。  安裝時不會新增路徑。  
  
2.  使用 **VSInstr** 工具產生目標應用程式的檢測版本。  
  
3.  初始化 .NET Framework 程式碼剖析的環境變數。  型別：  
  
     **VSPerfClrEnv \/traceon**  
  
4.  啟動程式碼剖析工具。  型別：  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) **:trace** 選項會初始化程式碼剖析工具。  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile` 選項必須搭配 **\/start** 使用。  `OutputFile` 指定程式碼剖析資料 \(.vsp\) 檔案的名稱和位置。  
  
     您可以使用下列任何一個選項搭配 **\/start:trace** 選項使用。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定擁有已進行程式碼剖析處理序之帳戶的網域和使用者名稱。  只有在處理序是以非登入使用者的身分執行時，才需要這個選項。  處理序擁有人列於 \[Windows 工作管理員\] 的 \[處理程序\] 索引標籤上的 \[使用者名稱\] 資料行。|  
    |[\/crosssession](../profiling/crosssession.md)|對其他工作階段中的處理序啟用程式碼剖析。  如果 ASP.NET 應用程式在不同的工作階段中執行，就必須有這個選項。  工作階段識別項列於 \[Windows 工作管理員\] 之 \[處理程序\] 索引標籤上的 \[工作階段 ID\] 資料行。  **\/CS** 可以當做 **\/crosssession** 的縮寫來指定。|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|在暫停資料收集的情況下，啟動程式碼剖析工具。  使用 [\/globalon](../profiling/globalon-and-globaloff.md) 繼續程式碼剖析。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|從 `Config` 中指定的處理器效能計數器收集資訊。  計數器資訊會加入至每個程式碼剖析事件收集的資料中。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|僅能與 **\/wincounter** 搭配使用。  指定 Windows 效能計數器收集事件之間的毫秒數。  預設為 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 \(ETW\) 事件。  ETW 事件是在不同的 \(.etl\) 檔案中收集的。|  
  
5.  從 \[命令提示字元\] 視窗啟動目標應用程式。  
  
## 控制資料收集  
 當目標應用程式正在執行時，您可以使用 **VSPerfCmd.exe** 選項，啟動及停止將資料寫入程式碼剖析工具資料檔案，以控制資料收集。  資料收集控制可讓您收集程式執行中特定組件的資料，例如應用程式的開始與結束。  
  
#### 若要啟動和停止資料收集  
  
-   下列選項配對會啟動和停止資料收集。  在不同的命令列上指定每個選項。  您可以多次開啟或關閉資料收集。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|啟動 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有處理序的資料收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|啟動 \(**\/processon**\) 或停止 \(**\/processoff**\) 對處理序 ID \(`PID`\) 所指定的處理序進行資料收集。|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|啟動 \(**\/threadon**\) 或停止 \(**\/threadoff**\) 對執行緒 ID \(`TID`\) 所指定的執行緒進行資料收集。|  
  
## 結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，請關閉正在執行已檢測元件的應用程式。  呼叫 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 選項，關閉分析工具並關閉程式碼剖析資料檔案。  **VSPerfClrEnv \/off** 命令會清除程式碼剖析環境變數。  
  
#### 若要結束程式碼剖析工作階段  
  
1.  關閉目標應用程式。  
  
2.  關閉程式碼剖析工具。  型別：  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(選擇項\) 清除程式碼剖析環境變數。  型別：  
  
     **VSPerfClrEnv \/off**  
  
## 請參閱  
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)