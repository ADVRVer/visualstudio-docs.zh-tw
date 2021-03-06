---
title: "如何：收集 CPU 計數器資料 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 13bba809b77286cd4a6eea4efa41b69c317d23d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-collect-cpu-counter-data"></a>如何：收集 CPU 計數器資料
CPU 事件計數器可用來收集硬體特定的效能資料。 本主題說明當您使用檢測分析方法時要如何收集事件計數器資料。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 有兩種類型的 CPU 計數器事件會發生︰  
  
-   Portable Events - 不論特定 CPU 的可收集 CPU 事件。  
  
-   Platform Events - 結合到特定 CPU 的 CPU 事件。  
  
 Portable Events 包含一般事件，例如停用的指令、未暫止時脈週期、CPU 緩衝區事件、分支事件及 L2 快取事件。 可用的 Portable Events 計數器是由處理器製造商決定。  
  
 Portable 和 Platform 計數器之間可共用的事件類別。 例如，下列類別的資料是經常通用於這兩種類型︰  
  
-   記憶體事件。  
  
-   前端事件。  
  
-   分支事件。  
  
 在程式碼剖析工具中，收集效能計數器資料的方式有兩種︰  
  
-   透過檢測分析時，從一或多個計數器收集資料。  
  
-   透過取樣分析時，將計數器事件指定為取樣間隔。 如需詳細資訊，請參閱[如何：選擇取樣事件](../profiling/how-to-choose-sampling-events.md)。  
  
### <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>透過檢測分析時收集 CPU 效能計數器資料  
  
1.  在效能工作階段 [屬性頁] 上，按一下 [CPU 計數器]。  
  
2.  選取 [收集 CPU 計數器] 核取方塊。  
  
3.  展開 [可用的效能計數器] 樹狀結構，直到您找到想要收集的取樣事件為止。  
  
4.  針對每個您想收集的事件，選取事件，然後按一下向右鍵以將事件加入至 [選取的計數器] 清單。  
  
    > [!NOTE]
    >  只有在您選取 [收集 CPU 計數器] 核取方塊時，才會啟用 [可用的效能計數器]。  
  
## <a name="see-also"></a>請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [效能工作階段屬性](../profiling/performance-session-properties.md)   
 [CPU 和 Windows 計數器](../profiling/cpu-and-windows-counters.md)   
 [如何：選擇取樣事件](../profiling/how-to-choose-sampling-events.md)