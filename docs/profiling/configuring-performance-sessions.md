---
title: "設定效能工作階段 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: "36"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9fbcd3e98768ddda7cfb32070fc613e341fee0ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-performance-sessions"></a>設定效能工作階段
使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具，您可以收集大量應用程式類型的各種效能資料。 本節說明如何使用效能精靈，以及效能工作階段的屬性和目標二進位檔，來設定分析工具收集您感興趣的資料。 分析工具的組態屬性也可以用來控制要在分析執行中收集的資料量。 如需詳細資訊，請參閱[控制資料收集](../profiling/controlling-data-collection.md)。  
  
> [!NOTE]
>  在許多情況下，使用效能精靈的預設屬性是收集分析資料的有效方式。 如需詳細資訊，請參閱[效能分析的初級開發人員指南](../profiling/beginners-guide-to-performance-profiling.md)和[使用者入門](../profiling/getting-started-with-performance-tools.md)。  
  
## <a name="common-tasks"></a>一般工作  
  
|工作|相關內容|  
|----------|---------------------|  
|**設定基本分析選項︰**您應該設定 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 使用 Microsoft 符號伺服器。 如此可確保您可以存取目前 Windows 版本和其他 Microsoft 應用程式的符號，例如函式和參數名稱。 在分析工作階段開始之前，您也可以指定其他一般選項，例如分析工具的系統權限和分析資料檔案的名稱。|-   [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [如何：序列化符號資訊](../profiling/how-to-serialize-symbol-information.md)<br />-   [如何：設定目前的工作階段](../profiling/how-to-set-the-current-session.md)<br />-   [如何：設定權限](../profiling/how-to-set-permissions.md)<br />-   [如何：設定效能資料檔案名稱選項](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**指定您想要收集的資料︰**您用來設定分析工作階段的程序取決於您要分析的目標應用程式類型和您想要收集的效能資料類型。|-   [如何：選擇收集方法](../profiling/how-to-choose-collection-methods.md)<br />-   [使用取樣收集效能統計資料](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [如何：分析網頁中的 JavaScript 程式碼](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [收集執行緒和處理序並行資料](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [收集其他效能資料](../profiling/collecting-additional-performance-data.md)|  
|**設定進階設定選項：**當您分析載入多個通用語言執行平台 (CLR) 版本的 .NET Framework 應用程式時，可以指定要分析的版本。 當您的效能工作階段中有多個 .exe 檔案時，可以設定二進位檔的啟動順序。|-   [如何︰指定 .NET Framework 執行階段](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [如何：指定要啟動的二進位檔](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## <a name="related-sections"></a>相關章節  
 [控制資料收集](../profiling/controlling-data-collection.md)  
  
## <a name="see-also"></a>請參閱  
 [效能總管](../profiling/performance-explorer.md)