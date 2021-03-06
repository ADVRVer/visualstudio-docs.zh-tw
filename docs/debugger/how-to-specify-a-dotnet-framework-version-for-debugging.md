---
title: "如何： 指定的.NET Framework 版本進行偵錯 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 69fa33ac76f39f7f37cc9aa84d61fd3cf7b0fe45
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>如何：指定偵錯的 .NET Framework 版本
[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 偵錯工具支援偵錯舊版 Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 以及最新的版本。 如果您從 Visual Studio 啟動應用程式，偵錯工具可以一定能辨識的正確版本[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]您正在偵錯應用程式。 如果已在執行應用程式，並使用**附加至**，偵錯工具可能不一定能夠識別舊版[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 如果發生這種情況，就會出現錯誤訊息：  
  
 偵錯工具對於應用程式所要使用的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本做了不正確的假設。  
  
 在這些不常見的情況中，您可以設定登錄機碼指示偵錯工具要使用的版本。  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>若要指定偵錯的 .NET Framework 版本  
  
1.  查詢目錄 Windows\Microsoft.NET\Framework 以尋找電腦上已安裝的 .NET Framework 版本。 版本號碼看起來如下所示：  
  
     `V1.1.4322`  
  
     識別正確的版本編號然後記下來。  
  
2.  啟動**登錄編輯程式**(regedit)。  
  
3.  在**登錄編輯程式**，開啟 HKEY_LOCAL_MACHINE 資料夾。  
  
4.  瀏覽至： HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     如果索引鍵不存在，以滑鼠右鍵按一下 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine，然後按一下**新金鑰**。 將新的機碼命名`{449EC4CC-30D2-4032-9256-EE18EB41B62B}`。  
  
5.  巡覽至 {449EC4CC-30D2-4032-9256-EE18EB41B62B} 之後, 查看**名稱**欄位然後尋找 clrversionfordebugging 機碼。  
  
    1.  如果索引鍵不存在，以滑鼠右鍵按一下 {449EC4CC-30D2-4032-9256-EE18EB41B62B}，然後按一下**新字串值**。 以滑鼠右鍵按一下新的字串值，請按一下**重新命名**，然後輸入`CLRVersionForDebugging`。  
  
6.  按兩下**CLRVersionForDebugging**。  
  
7.  在**編輯字串**方塊中，輸入中的.NET Framework 版本號碼**值**方塊。 例如：V1.1.4322。  
  
8.  按一下 [確定 **Deploying Office Solutions**]。  
  
9. 關閉**登錄編輯程式**。  
  
     如果在開始偵錯時仍然出現錯誤訊息，請確認已經在登錄中正確輸入版本編號。 同時確認是使用 Visual Studio 支援的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。 偵錯工具與 .NET Framework 的最新版本和舊版相容，但是不一定與未來的版本相容。  
  
## <a name="see-also"></a>請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)