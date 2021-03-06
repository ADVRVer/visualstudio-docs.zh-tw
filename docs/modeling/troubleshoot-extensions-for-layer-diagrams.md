---
title: "相依性圖表的擴充功能疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b9a13da8d987304831a3ce8e8311a9e7cf36b4e8
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>相依性圖表的擴充功能疑難排解
本主題說明當您建立圖層模型擴充功能時可能遇到的一些問題。  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>當我按下 F5 以偵錯 my 擴充功能時，我命令、 軌跡處理常式，驗證擴充功能或自訂屬性不會出現在實驗執行個體中的相依性圖表[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
1.  在實驗執行個體中開啟您的擴充功能方案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，然後在**建置**功能表上，按一下 **重建方案**。  
  
2.  按**F5**或**CTRL + F5**啟動實驗執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 開啟相依性圖表，並測試您的擴充功能。  
  
 如有必要，請繼續執行下一個程序。  
  
#### <a name="an-old-version-of-my-extension-runs"></a>執行的是舊版的擴充功能。  
  
1.  請確定沒有任何 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 實驗執行個體執行中。  
  
2.  刪除下列資料夾： %LocalAppData%\Microsoft\VisualStudio\\[version] \ComponentModelCache  
  
    > [!NOTE]
    >  %Localappdata%通常是*DriveName*: \Users\\*UserName*\AppData\Local。  
  
 如有必要，請繼續執行下一個程序。  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>出現的是舊版的驗證結果，或沒有呼叫我的驗證方法。  
  
1.  在實驗執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]上**建置**功能表上，按一下 **清除方案**。 這會清除上一次驗證分析的快取結果。  
  
2.  請確定模型中的圖層與程式碼項目相關聯，而且模型中至少有一個相依性連結。 如果沒有要驗證的項目，就不會叫用驗證。  
  
3.  一般的中斷點可能不會在驗證方法中運作，因為它是在不同的處理序中執行。 如果想要逐步執行您的方法，您必須插入對 `System.Diagnostics.Debugger.Launch()` 的呼叫。  
  
4.  在**source.extension.vsixmanifest**在圖層驗證專案中，確定您已經加入兩**MEF 元件**項目和**自訂延伸模組類型**項目底下**內容**。  
  
## <a name="see-also"></a>請參閱  
 [擴充相依性圖表](../modeling/extend-layer-diagrams.md)
