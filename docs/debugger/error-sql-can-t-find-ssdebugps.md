---
title: "錯誤： SQL 可以 &#39; t 尋找不到 SSDEBUGPS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0e45c70d8186a178bafe6544bf83dcec1ed35d9d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="error-sql-can39t-find-ssdebugps"></a>錯誤： SQL 可以 &#39; t 尋找不到 SSDEBUGPS
SSDEBUGPS.dll 是 SQL Server 偵錯主機元件。  
  
 當您嘗試啟動偵錯時會發生這個錯誤，並表示指定的檔案不在 [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] 電腦上。 可能的原因是從未執行遠端偵錯 (Remote Debugging) 安裝程式，或者已刪除這個檔案。  
  
 若要解決此錯誤的兩種方法： 重新執行遠端偵錯安裝程式，並複製到檔案[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]機器。  
  
 若要重新執行遠端偵錯安裝程式，請遵循指示[遠端偵錯](../debugger/remote-debugging.md)。  
  
 如果找得到 ssdebugps.dll 的複本，您可以將它拖曳至複製[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]機器。 如果有這個檔案，會在 \Program Files\ Common Files\Microsoft Shared\SQL Debugging 目錄中。 您可能會發現它在另一台[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]電腦，或已在機器上[!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)]安裝。  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>若要將 SSDEBUGPS.dll 複製至 SQL Server 2005 電腦  
  
1.  將檔案複製到具有相同名稱和路徑的目錄中，在[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]機器。  
  
2.  註冊開啟**命令提示字元**，然後執行下列命令：  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```