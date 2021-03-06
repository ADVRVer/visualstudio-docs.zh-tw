---
title: "在偵錯工具外執行我的程式時，如何偵錯存取違規？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0af98932a940126c8f7288d7b5c830bb40f270fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>在偵錯工具外執行我的程式時，如何偵錯存取違規？
## <a name="problem-description"></a>問題說明  
 我的程式在 Visual Studio 環境裡執行正常，但是當我以 Windows 作業系統獨立執行它時，它會產生存取違規。 我該如何偵錯這個問題？  
  
## <a name="solution"></a>方案  
 設定[時間恰好偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)選項，然後執行獨立程式，直到發生存取違規。 然後，在**存取違規**對話方塊中，您可以按一下**取消**啟動偵錯工具。  
  
 請參閱知識庫 (Knowledge Base) 文件 Q133174「How to Locate Where a General Protection (GP) Fault Occurs」。 您可以在 MSDN Library CD 上，或藉由搜尋找到知識庫文章[http://support.microsoft.com/](http://support.microsoft.com/)。  
  
## <a name="see-also"></a>請參閱  
 [機器碼偵錯 Faq](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)