---
title: "在 Visual Studio 中測量 Python 程式碼的效能 | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2723d4d0-89c8-4279-bfc2-27c0834a997e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 2511f1076450848dfc75584edc97950fd4279c7b
ms.lasthandoff: 03/10/2017

---

# <a name="profiling-python-code"></a>分析 Python 程式碼

Visual Studio 支援在使用 CPython 型解譯器時分析 Python 應用程式。

若要進行分析，請執行 [分析] > [啟動 Python 分析] 功能表命令，這將會開啟設定對話方塊：

![分析設定對話方塊](media/profiling-start.png)

當您選取 [確定] 時，分析工具會執行並開啟效能報告，您可以透過該報告探索應用程式中的執行時間：

![分析效能報告](media/profiling-results.png)

如需概觀說明，請參閱下列內容

如需逐步解說示範，請觀看[使用適用於 Visual Studio 的 Python 工具進行分析 (英文)](http://www.youtube.com/watch?v=K-KqkFkp55k) 影片 (8 分&52; 秒)。

> [!VIDEO https://www.youtube.com/embed/K-KqkFkp55k]

## <a name="profiling-for-ironpython"></a>針對 IronPython 的分析

由於 IronPython 並非 CPython 型解譯器，上述分析功能將無法運作。

請改為直接將 `ipy.exe` 作為目標應用程式啟動來使用 Visual Studio .NET 分析工具，並使用適當的引數來啟動您的啟動指令碼。 將 `-X:Debug` 包含在命令列上，以將您的所有 Python 程式碼強制設定為可偵錯且可分析。 這會產生包含在 IronPython 執行階段及您程式碼上所花費時間的效能報告。 您的程式碼是以損害名稱來識別。

此外，IronPython 本身也有一些內建的分析功能，但它目前並沒有良好的視覺化檢視。 請參閱 [IronPython 分析工具 (英文)](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (MSDN 部落格) 來查看可用內容。
