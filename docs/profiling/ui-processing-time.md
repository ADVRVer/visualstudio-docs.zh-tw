---
title: "UI 處理時間 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.uiprocessing
helpviewer_keywords: Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8171fa96848aa53fb151ed4d4701268308e4ad1c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ui-processing-time"></a>UI 處理時間
時間軸中的這些區段與歸類為 UI 處理的封鎖時間建立關聯。 這表示執行緒會提取 Windows 訊息或執行其他使用者介面 (UI) 工作。 在這段期間內，會在並行視覺化檢視當作 UI 處理計數的 API 中封鎖執行緒。 `GetMessage()` 和 `MsgWaitForMultipleObjects()` 這類 API 屬於這個群組。  
  
 如果識別不到任何預先定義的封鎖 API，請檢閱呼叫堆疊並分析報表來判斷延遲的基本原因。  
  
 [UI 處理] 分類對於了解 GUI 應用程式回應性而言十分重要，並且適用於與 UI 回應性相依的應用程式。 例如，如果應用程式中的 UI 執行緒達到 100% 的 UI 處理時間，則可能極具回應性。 不過，如果 UI 執行緒將大量時間花在其他分類中，請尋找根本原因，並考慮用於減少執行緒上非 UI 分類的選項。  
  
## <a name="see-also"></a>請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)