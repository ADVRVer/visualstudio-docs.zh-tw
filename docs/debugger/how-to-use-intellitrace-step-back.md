---
title: "檢視快照集使用 IntelliTrace 步驟後-Visual Studio |Microsoft 文件"
ms.custom: 
ms.date: 12/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9ee45132e4acf45bccffd3e05808defd3c7ced6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="view-snapshots-using-intellitrace-step-back"></a>使用 IntelliTrace 步驟後的檢視快照集
IntelliTrace 步驟後會自動帶您在每個中斷點和偵錯工具的應用程式的快照集步驟的事件。 記錄的快照集可讓您回溯到先前的中斷點或步驟，以檢視應用程式過去的狀態。 如果您想要查看先前的應用程式狀態，但不想要重新啟動偵錯或重新建立所需的應用程式狀態，IntelliTrace 回溯可節省您的時間。

IntelliTrace 步驟後就可用以啟動 Visual Studio Enterprise 2017 版本 15.5 及更新版本，而您需要 Windows 10 年度更新或更新版本。 目前支援偵錯 ASP.NET、 WinForms、 WPF、 受管理的主控台應用程式，與受管理的類別庫的功能。 目前不支援偵錯 ASP.NET Core、.NET Core 或 UWP 應用程式。 
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>啟用 IntelliTrace 事件和快照集模式 
若要啟用此功能，請移至**工具 > 選項 > IntelliTrace**設定，然後選取選項**IntelliTrace 事件和快照集**。 

![啟用 IntelliTrace 事件和快照集模式](../debugger/media/intellitrace-enable-snapshots.png "啟用 IntelliTrace 事件和快照集模式")

IntelliTrace 快照的應用程式的程序在每個偵錯工具步驟與中斷點的事件。 這些事件會記錄在**事件**索引標籤中**診斷工具**視窗中的，連同其他 IntelliTrace 事件。 若要開啟此視窗，請選擇**偵錯 / Windows / 顯示診斷工具**。

相機圖示旁邊的快照集是可用的事件。 

![事件索引標籤上，使用快照集](../debugger/media/intellitrace-events-tab-with-snapshots.png "中斷點和執行步驟的快照集的事件 索引標籤")

基於效能考量，在非常快速地逐步執行時，不會採用快照集。 如果沒有相機圖示出現之步驟旁，請嘗試逐步執行速度更慢。

## <a name="navigate-and-view-snapshots"></a>瀏覽和檢視的快照集

您可以使用事件之間瀏覽**步驟回溯 （Alt + [）**和**向前步驟 (Alt +])**中偵錯 工具列按鈕。 這些按鈕瀏覽中顯示的事件**事件**索引標籤中**診斷工具視窗**。 逐步返回或前進至某個事件會自動啟動所選事件的歷程偵錯。

![向後和向前按鈕](../debugger/media/intellitrace-step-back-icons-description.png "步驟向後和向前步驟按鈕")

當您逐步執行後或逐步往前時，Visual Studio 就會進入歷程偵錯模式。 在此模式中，偵錯工具的內容會切換到所選的事件錄製時的時間。 Visual Studio 也會將指標移至對應來源視窗中的程式碼行。 

從這個檢視中，您可以檢查中的值**呼叫堆疊**，**區域變數**，**自動變數**，和**監看式**windows。 您也可以停留來檢視資料提示方塊以及執行中的運算式評估的變數**即時運算**視窗。 您所看到的資料是從應用程式的程序時在該點間取得的快照集。

所以舉例來說，如果您叫用中斷點，並採取步驟 (**F10**)、**步驟回溯**按鈕將 Visual Studio 在程式碼對應至中斷點的行的歷程記錄模式。 

![使用快照集的事件上啟用歷程記錄模式](../debugger/media/intellitrace-historical-mode-with-snapshot.png "啟用快照集的事件的歷程記錄模式")

若要返回即時執行，請選擇**繼續 (F5)**或按一下**返回即時偵錯**資訊列中的連結。 

您也可以檢視從快照集**事件** 索引標籤。選取的事件，該快照集，然後按一下**啟用歷程偵錯**。 您也可以按一下 [相機] 圖示以啟動歷程偵錯。

![在事件上啟用 歷程偵錯](../debugger/media/intellitrace-activate-historical-debugging.png "啟用歷程偵錯的事件")

不同於**設定下一個陳述式**命令，檢視快照集不會重新執行您的程式碼; 它可讓您的應用程式狀態的靜態檢視點發生在過去的時間。

![IntelliTrace 步驟後的概觀](../debugger/media/intellitrace-step-back-overview.png "概觀的 IntelliTrace 步驟回")

## <a name="next-steps"></a>後續步驟  
 若要了解如何檢查 Visual Studio 中的變數，請參閱[偵錯工具功能的教學課程](../debugger/debugger-feature-tour.md)  
 如需歷程偵錯的概觀，請參閱[歷程偵錯](../debugger/historical-debugging.md)。  

## <a name="frequently-asked-questions"></a>常見問題集

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>如何與 IntelliTrace 步驟後不同 IntelliTrace 事件僅限模式？

事件模式中的 IntelliTrace 確實可讓您啟動偵錯工具的步驟和中斷點上的歷程記錄偵錯。 不過，IntelliTrace 只會擷取中的資料**區域變數**和**自動變數**windows 如果視窗已開啟，且只會擷取已展開的資料和檢視中。 事件模式，您通常沒有完整的變數和複雜的物件檢視。 此外，運算式評估及檢視資料中的**監看式**視窗不支援。 

在事件和快照集模式中，IntelliTrace 會擷取整個快照集的應用程式的程序，包括複雜的物件。 在一行程式碼中，您可以看到相同的資訊，如同您在中斷點處停止 （且不論是否您之前會展開資訊）。 檢視快照集時，也支援運算式評估。  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>這項功能的效能影響為何？ 

逐步執行的整體效能的影響取決於您的應用程式。 取得快照集的額外負荷是大約 30 毫秒。 當快照時，分叉應用程式的程序，而且分岔的複製已暫停。 當您檢視快照集時，Visual Studio 附加至處理程序的分岔副本。 每個快照，Visual Studio 複製頁面資料表，並將頁面設定為寫入時複製。 如果物件在堆積上的變更偵錯工具相關聯的快照集的步驟之間，個別頁面然後複製資料表，因而產生最少的記憶體成本。 如果 Visual Studio 偵測到沒有足夠的記憶體，以擷取快照時，它不會其中一個。
 
## <a name="known-issues"></a>已知問題  
* 如果您在比 Windows 10 年秋季建立者更新 (RS3)，舊的 Windows 版本上使用 IntelliTrace 事件和快照集模式，而且應用程式的偵錯平台目標設定為 x86，IntelliTrace 不會將快照集。

    因應措施：
    * 安裝或升級到 Windows 10 年秋季建立者更新 (RS3)。 
    * 或者： 
        1. 從 Visual Studio 安裝程式安裝適用於桌上型電腦 (x86、x64) 的 VC++ 2015.3 v140 工具組。
        2. 建置目標應用程式。
        3. 從命令列使用 editbin 工具來設定`Largeaddressaware`目標可執行檔的旗標。 例如，您可能會使用這個命令 （之後更新的路徑）:"C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe"/Largeaddressaware"C:\Path\To\Application\app.exe"。
        4. 若要開始偵錯，請按 **F5**。 現在，拍攝快照時，在偵錯工具的步驟和中斷點。

        > [!Note]
        > `Largeaddressaware`旗標必須設定每個可執行檔根據變更的時間。

* 當應用程式的程序的快照時的應用程式，使用持續性的記憶體對應檔案時，快照集的處理序持有獨佔鎖定於記憶體對應檔 （即使父處理序已釋放其鎖定）。 其他處理序的仍可讀取，但不是寫入至記憶體對應檔。

    因應措施：
    * 清除所有快照集結束偵錯工作階段。 

* 儲存的檔案時**偵錯 > IntelliTrace > 儲存 IntelliTrace 工作階段**在事件和快照集模式下，從快照集擷取的其他資料沒有.itrace 檔中。 中斷點和步驟的事件，您會看到相同的資訊，如同您有用於 IntelliTrace 事件僅限模式來儲存檔案。 
