---
title: "Visual Studio 協助工具祕訣和訣竅 | Microsoft Docs"
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4cfc07cb77e1db595d1b381b1097dcfcba0abdab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Visual Studio 協助工具祕訣和訣竅
> [!TIP]
> 若要深入了解最新的協助工具更新，請參閱 [Visual Studio 2017 15.3 版中的協助工具改善](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) \(英文\) 部落格文章。

Visual Studio 有與螢幕助讀程式和其他輔助技術相容的內建協助工具功能。 本主題列出的常見快速組合鍵，可用以執行只能使用鍵盤的工作，包括使用高對比佈景主題以改善可見性的相關資訊。 它也會向您示範如何使用註解顯示實用的程式碼資訊，以及如何設定組建和中斷點事件的音效提示。

## <a name="save-your-ide-settings"></a>儲存 IDE 設定  
 您可以儲存視窗配置、鍵盤對應配置和其他喜好設定，來自訂 IDE 體驗。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。  

## <a name="modify-your-ide-for-high-contrast-viewing"></a>修改您的 IDE 進行高對比檢視
對有些人而言，部分色彩十分難以辨識。 如果希望提高程式碼的對比，但不想使用一般的「高對比」佈景主題，我們現在提供「藍色 (超對比)」佈景主題。

  ![比較藍色佈景主題和藍色超對比佈景主題](media/blue-extra-contrast-theme.png "看到藍色佈景主題和藍色超對比佈景主題之間的差異")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>使用註釋顯示程式碼的實用資訊

Visual Studio 編輯器包含許多文字「裝飾」，讓您知道程式碼特定點的特性和功能，例如燈泡、錯誤和警告的「波浪線」、書籤等等。 您可以使用「顯示程式碼行註釋」命令集協助探索，然後巡覽這些裝飾。

  ![使用顯示程式碼行註釋命令集](media/show-line-annotations-command-set.png "示範如何設定顯示程式碼行註釋命令集")

## <a name="access-toolbars-by-using-shortcut-key-combinations"></a>使用快速鍵組合存取工具列
Visual Studio IDE 工具列的作用與許多工具視窗相同。 下列快速鍵組合可協助您進行存取。

|功能|描述|按鍵組合|  
|-------------|-----------------|---------------------|  
|IDE 工具列|選取 [標準] 工具列上的第一個按鈕。|**ALT**、**CTRL** + **TAB**|  
|工作視窗工具列|將焦點移至工具視窗中的工具列。 <br> <br> **注意：**這適用於大部分的工具視窗，但只限焦點在工具視窗中時。 此外，您必須先選擇 SHIFT 鍵再選擇 ALT 鍵。 在部分工具視窗 (例如 Team Explorer) 中，您必須先按住 SHIFT 鍵再選擇 ALT 鍵。|**SHIFT** + **ALT**|
|工具列|移至下一個工具列中的第一個項目 (當工具列有焦點時)。|**CTRL** + **TAB**|

### <a name="other-useful-shortcut-key-combinations"></a>其他實用快速鍵組合  
有些其他實用快速鍵組合包括下列項目。

|功能|描述|按鍵組合|  
|-------------|-----------------|---------------------|  
|IDE|開啟或關閉高對比。 <br> <br> **注意：**標準 Windows 捷徑|**左 ALT + 左 SHIFT + PRINT SCREEN**|  
|對話方塊|選取或清除對話方塊中的核取方塊選項。 <br> <br> **注意：**標準 Windows 捷徑|**空格鍵**|  
|操作功能表|開啟操作 (滑鼠右鍵) 功能表。 <br> <br> **注意：**標準 Windows 捷徑|**SHIFT** + **F10**|
|Menus|使用其快速鍵來快速存取功能表項目。 選擇後接功能表中加底線字母的 **ALT** 鍵，來啟動命令。 例如，若要檢視 Visual Studio 中的 [開啟專案] 對話方塊，您將選擇 **ALT** + **F** + **O** + **P**。  <br><br> **注意：**標準 Windows 捷徑|**ALT** + **[字母]**|
|[工具箱] 視窗|在 [工具箱] 索引標籤之間移動。|**CTRL** + **向上鍵**<br /><br /> 和<br /><br /> **CTRL** + **向下鍵**|  
|[工具箱] 視窗|將控制項從 [工具箱] 新增至表單或設計工具。|**ENTER**|  
|選項對話方塊、環境、鍵盤|刪除 [按快速鍵] 選項中所輸入的按鍵組合。|**退格鍵**|  

> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。  


## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>使用音效小程式設定組建與中斷點提示
您可以使用 Windows 的音效小程式，指派 Visual Studio 程式事件的音效。 具體而言，您可以指派下列程式事件的音效：

 * 遇到中斷點
 * 已取消組建
 * 組建失敗
 * 組建成功

方式如下：

1. 在執行 Windows 10 電腦的 [搜尋] 方塊中鍵入**變更系統音效**。

  ![Windows 10 的 [搜尋] 方塊](media/type-here-to-search.png "在執行 Windows 10 電腦的 [搜尋] 方塊中鍵入音效")

  (或者，如啟用 Cortana，說出「嘿 Cortana」，接著說出「變更系統音效」。)

2. 按兩下 [變更系統音效]。

  ![Windows 10 的搜尋結果](media/change-system-sounds.png "按兩下搜尋結果中的 [變更系統音效]")

3. 在 [音效] 對話方塊中，按一下 [音效] 索引標籤。 <br><br>
 然後，在 [程式事件] 中捲動到 **Microsoft Visual Studio**，選取您想要套用至所選事件的音效。

  ![Windows 10 音效小程式的 [音效] 索引標籤](media/sound-applet.png "按兩下搜尋結果中的 [變更系統音效]")

4. 按一下 [確定 **Deploying Office Solutions**]。



## <a name="see-also"></a>另請參閱  
* [Visual Studio 的協助工具功能](../../ide/reference/accessibility-features-of-visual-studio.md)
  * [如何：在 Visual Studio 中自訂功能表和工具列](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)
* [Microsoft Accessibility](https://www.microsoft.com/Accessibility) (Microsoft 協助工具)
