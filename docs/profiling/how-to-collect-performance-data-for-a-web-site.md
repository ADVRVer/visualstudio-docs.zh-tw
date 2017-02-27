---
title: "如何：使用效能精靈對網站或 Web 應用程式進行程式碼剖析 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vsperf.url.url"
  - "vsperf.chooseurl"
  - "vs.performance.wizard.asppage"
  - "vsperf.url.ok"
  - "vsperf.url.cancel"
helpviewer_keywords: 
  - "程式碼剖析工具，程式碼剖析 ASP.NET"
  - "網站，效能分析"
  - "ASP.NET，效能分析"
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 33
---
# 如何：使用效能精靈對網站或 Web 應用程式進行程式碼剖析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 \[效能精靈\] 收集 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式的效能資料。 您可以對 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中開啟之 Web 應用程式進行程式碼剖析，也可以對位於本機電腦上但在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 中未開啟之 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 網站進行程式碼剖析。  
  
> [!NOTE]
>  \[效能精靈\] 可讓您將階層互動 \(TIP\) 資料及\/或 JScript 效能資料新增至收集的程式碼剖析資料。 TIP 選項會從伺服器端處理序收集資料。 JScript 程式碼剖析會從本機或遠端網站上執行的指令碼收集資料。 在大部分情況下，您應該只選擇其中一個選項。  
  
 依據系統管理員提供的使用者存取權限設定，個別使用者不一定具有安全性權限可以在裝載 ASP.NET 處理序的電腦上建立分析工具工作階段。 下列範例説明各使用者之間可能存在的差異：  
  
-   當系統管理員設定了要啟動的驅動程式和服務時，某些使用者可以存取進階的程式碼剖析功能。  
  
-   網域使用者只能存取取樣程式碼剖析。  
  
-   某些使用者可以拒絕其他所有使用者存取程式碼剖析。  
  
 如需詳細資訊，請參閱 [分析和 Windows Vista 安全性](../profiling/profiling-and-windows-vista-security.md)，以及 [VSPerfCmd](../profiling/vsperfcmd.md) 中的 ADMIN 選項。  
  
### 對網站專案進行程式碼剖析  
  
1.  在 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] 或 [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] 中，開啟 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 專案。  
  
2.  按一下 \[分析\] 功能表上的 \[啟動效能精靈\]。  
  
3.  在精靈的第一個頁面上，選取程式碼剖析方法，然後按一下 \[下一步\]。 如需程式碼剖析方法的詳細資訊，請參閱 [認識程式碼剖析方法](../profiling/understanding-performance-collection-methods.md)。 請注意，並行視覺化檢視程式碼剖析方法不適用於 Web 應用程式。  
  
4.  在 \[您要以哪一個應用程式作為分析的目標?\] 下拉式清單中，確認已選取目前的專案，然後按一下 \[下一步\]。  
  
5.  在精靈的第三個頁面上，您可以選擇是否要新增階層互動分析 \(TIP\) 資料及\/或網頁中執行之 JavaScript 的資料。  
  
    -   若要收集階層互動，請選取 \[啟用階層互動分析\] 核取方塊。  
  
    -   若要從網頁中執行的 JavaScript 收集資料，請選取 \[分析 JavaScript\] 核取方塊。  
  
6.  按 \[**下一步**\]。  
  
7.  在精靈的第四個頁面上，按一下 \[完成\]。  
  
8.  隨即為 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式建立效能工作階段，並在瀏覽器中啟動網站。 執行您要進行程式碼剖析的功能，然後關閉瀏覽器。  
  
     分析工具隨即產生資料檔案，並在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 主視窗中顯示資料的 \[摘要\] 檢視。  
  
### 對網站進行程式碼剖析，但不在 Visual Studio 中開啟專案  
  
1.  開啟 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] 或 [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)]。  
  
2.  按一下 \[分析\] 功能表上的 \[啟動效能精靈\]。  
  
3.  在精靈的第一個頁面上，選取程式碼剖析方法，然後按一下 \[下一步\]。 如需詳細資訊，請參閱[認識程式碼剖析方法](../profiling/understanding-performance-collection-methods.md)。  
  
4.  在精靈的第二個頁面上，選取 \[為 ASP.NET 或 JavaScript 應用程式進行程式碼剖析\] 選項，然後按一下 \[下一步\]。  
  
5.  在精靈第三個頁面的 \[您要使用哪個 URL 或路徑執行 Web 應用程式\] 方塊中，輸入應用程式首頁的 URL，然後按一下 \[下一步\]。  
  
    -   若是伺服器 \(IIS\) 架構的網站，請輸入如 **http:\/\/localhost\/MySite\/default.aspx** 之類的 URL。 這會對本機電腦上位於 MySite 之應用程式根目錄的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式進行程式碼剖析，然後 Internet Explorer 會啟動該網站的 default.aspx 頁面以開始工作階段。  
  
    -   針對檔案架構的網站，請輸入如檔案\/\/\/**c:\\WebSites\\MySite\\default.aspx** 之類的路徑。 這會對位於 c:\\webSites\\MySite 的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式進行程式碼剖析，然後 Internet Explorer 會啟動 http:\/\/localhost:nnnn\/MySite\/default.aspx 頁面以開始工作階段。  
  
    -   針對您想要收集 JavaScript 資料的外部網站，請輸入如 http:\/\/www.contoso.com 之類的 URL。  
  
     如需詳細資訊，請檢視 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 目標二進位檔的屬性頁。  
  
6.  在精靈的第三個頁面上，您可以選擇是否要新增階層互動分析 \(TIP\) 資料及\/或網頁中執行之 JavaScript 的資料。  
  
    -   若要收集階層互動，請選取 \[啟用階層互動分析\] 核取方塊。  
  
    -   若要從網頁中執行的 JavaScript 收集資料，請選取 \[分析 JavaScript\] 核取方塊。  
  
7.  按 \[**下一步**\]。  
  
8.  在精靈的第四個頁面上，按一下 \[完成\]。  
  
9. 隨即為 ASP.NET 應用程式建立效能工作階段，並在瀏覽器中啟動網站。 執行您要進行程式碼剖析的功能，然後關閉瀏覽器。  
  
     分析工具隨即產生資料檔案，並在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 主視窗中顯示資料的 \[摘要\] 檢視。  
  
## 請參閱  
 [概觀](../profiling/overviews-performance-tools.md)   
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [認識檢測資料值](../profiling/understanding-instrumentation-data-values.md)   
 [認識取樣資料值](../profiling/understanding-sampling-data-values.md)