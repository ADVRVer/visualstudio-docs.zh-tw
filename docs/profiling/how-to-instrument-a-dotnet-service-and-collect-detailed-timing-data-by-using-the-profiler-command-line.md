---
title: "如何：使用分析工具命令列檢測 .NET 服務並收集詳細計時資料 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f73593a-69a7-41b7-a21c-81d3ab0eb8fe
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 1e56c0b64b0ccd508d7a879d8270af8ffed5c807
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>如何：使用程式碼剖析工具命令列以檢測 .NET 服務並收集詳細計時資料
本主題描述如何使用 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] 分析工具命令列工具來檢測 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 服務，並收集詳細的計時資料。  
  
> [!NOTE]
>  如果某項服務無法在電腦啟動後重新啟動 (這類服務只會在作業系統啟動時啟動)，則無法使用檢測方法來分析服務。  
>   
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安裝目錄的 \Team Tools\Performance Tools 子目錄中。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。 如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
>   
>  若要將階層互動資料加入至程式碼剖析回合中，則需要使用命令列程式碼剖析工具的特定程序。 請參閱[收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)。  
  
 若要使用檢測方法從 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 服務收集詳細的計時資料，您可使用 [VSInstr.exe](../profiling/vsinstr.md) 工具產生已檢測的元件版本。 然後以檢測過的版本取代未經檢測的服務版本，確認服務設定為手動啟動。 使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具初始化全域分析環境變數，然後重新啟動主機電腦。 然後啟動分析工具。  
  
 啟動服務後，計時資料會自動收集到資料檔案。 程式碼剖析工作階段期間，您可以暫停和繼續資料收集。  
  
 若要結束分析工作階段，請關閉服務，然後明確關閉分析工具。 在大部分情況下，建議您在工作階段結束時清除程式碼剖析環境變數。  
  
## <a name="starting-the-application-with-the-profiler"></a>使用程式碼剖析工具啟動應用程式  
  
#### <a name="to-start-profiling-a-net-framework-service"></a>開始分析 .NET Framework 服務  
  
1.  開啟 [命令提示字元] 視窗。  
  
2.  使用 [VSInstr] 工具產生服務二進位檔的已檢測版本。  
  
3.  以檢測過的版本取代原始二進位檔。 在 Windows 服務控制管理員中，確定服務的啟動類型設定為 [手動]。  
  
4.  初始化 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 分析環境變數。 類型：  
  
     **VSPerfClrEnv /globaltraceon**  
  
5.  重新啟動電腦。  
  
6.  開啟 [命令提示字元] 視窗。  
  
7.  啟動分析工具。 類型：  
  
     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  
  
    -   [/start](../profiling/start.md)**:trace** 選項會初始化程式碼剖析工具。  
  
    -   [/output](../profiling/output.md)**:**`OutputFile` 選項必須搭配 **/start** 使用。 `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。  
  
     您可以使用下列任一選項搭配 **/start:trace** 選項。  
  
    > [!NOTE]
    >  **/user** 和 **/crosssession** 選項通常是分析服務的必要選項。  
  
    |選項|描述|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|指定擁有程式碼剖析處理序之帳戶的網域和使用者名稱。 只有在以登入的使用者之外的使用者身分執行處理序時，才需要這個選項。 處理序擁有者會列在 [Windows 工作管理員] 的 [處理程序] 索引標籤上的 [使用者名稱] 欄。|  
    |[/crosssession](../profiling/crosssession.md)|在其他工作階段啟用處理序程式碼剖析。 如果應用程式在不同的工作階段中執行，則需要這個選項。 工作階段識別碼會列在 [Windows 工作管理員] 的 [處理程序] 索引標籤上的 [工作階段識別碼] 欄。 **/crosssession** 可縮寫成 **/CS**。|  
    |[/waitstart](../profiling/waitstart.md)[**:**`Interval`]|指定在分析工具傳回錯誤之前，等候它初始化的秒數。 如果未指定 `Interval`，分析工具會無限期等候。 根據預設，**/start** 會立即傳回。|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|若要啟動暫停資料收集的程式碼剖析工具，請將 **/globaloff** 選項新增到 **/start** 命令列。 使用 **/globalon** 以繼續程式碼剖析。|  
    |[/counter](../profiling/counter.md) **:** `Config`|從 Config 中指定的處理器效能計數器收集資訊。計數器資訊會新增至在每個分析事件收集的資料。|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[/automark](../profiling/automark.md) **:** `Interval`|只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.etl) 檔案。|  
  
8.  從 Windows 服務控制管理員啟動服務。  
  
## <a name="controlling-data-collection"></a>控制資料收集  
 當服務執行時，您可以使用 **VSPerfCmd.exe** 選項開始和停止將資料寫入至分析工具資料檔案。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉服務) 的資料。  
  
#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集  
  
-   下列成對的 **VSPerfCmd** 選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。  
  
    |選項|描述|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|開始 (**/threadon**) 或停止 (**/threadoff**) 執行緒識別碼 (`TID`) 所指定執行緒的資料收集。|  
  
## <a name="ending-the-profiling-session"></a>結束程式碼剖析工作階段  
 若要結束分析工作階段，請停止正在執行已檢測元件的服務，然後呼叫 **VSPerfCmd** [/shutdown](../profiling/shutdown.md) 選項以關閉分析工具，並關閉分析資料檔案。 **VSPerfClrEnv /globaloff** 命令會清除分析環境變數。  
  
 您必須重新啟動電腦才能套用新的環境設定。  
  
#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段  
  
1.  從服務控制管理員停止服務。  
  
2.  關閉分析工具。 類型：  
  
     **VSPerfCmd /shutdown**  
  
3.  當您完成所有分析時，請清除分析環境變數。 類型：  
  
     **VSPerfClrEnv /globaloff**  
  
4.  以原始模組取代檢測過的模組。 如有必要，請重新設定服務的啟動類型。  
  
5.  重新啟動電腦。  
  
## <a name="see-also"></a>請參閱  
 [分析服務](../profiling/command-line-profiling-of-services.md)   
 [檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)