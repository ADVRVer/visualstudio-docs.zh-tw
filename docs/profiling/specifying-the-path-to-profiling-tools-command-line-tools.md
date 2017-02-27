---
title: "指定程式碼剖析工具命令列工具的路徑 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 指定程式碼剖析工具命令列工具的路徑
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼分析工具命令列工具的路徑不會加入 PATH 環境變數中。  在 32 位元電腦上，這些工具會在一個目錄中。  在 64 位元電腦上，程式碼分析工具有 32 位元和 64 位元兩種版本。  
  
## 32 位元電腦  
 在 32 位元電腦上，預設的程式碼剖析工具目錄是 *磁碟機*\\Program Files\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools。  
  
## 64 位元電腦  
 在 64 位元電腦上，則會根據已進行程式碼剖析之應用程式的目標平台指定路徑。  
  
-   若是 32 位元應用程式，預設程式碼剖析工具目錄是：  
  
     *磁碟機*\\Program Files \(x86\)\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools  
  
-   若是 64 位元應用程式，預設程式碼剖析工具目錄是：  
  
     *磁碟機*\\Program Files \(x86\)\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools\\x64