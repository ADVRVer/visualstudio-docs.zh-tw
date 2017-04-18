---
title: "選項、文字編輯器、C/C++、實驗 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 47c39bd711b69efdb863d71f11e3e472054a3ce3
ms.openlocfilehash: 889d538b732b360b475788ec6d67b47920703c73
ms.lasthandoff: 04/06/2017

---
# <a name="options-text-editor-cc-experimental"></a>選項、文字編輯器、C/C++、實驗
藉由變更這些選項，您可以變更進行 C 或 C++ 程式設計時之 IntelliSense 和瀏覽資料庫的相關行為。 這些功能是真正實驗性質，可能會修改或從 Visual Studio 未來版本中移除。 本主題說明 Visual Studio 2017 中的選項。 若是 Visual Studio 2015，請參閱[選項、文字編輯器、C/C++、實驗性](https://msdn.microsoft.com/library/mt591979.aspx) 
  
 若要存取本屬性頁面，請按 **Control + Q** 啟動 `Quick Launch`，然後鍵入 "experimental"。 鍵入前幾個字母之後，快速啟動就會找到頁面。 您也可以選擇 [工具 | 選項] 並依序展開 [文字編輯器] 和 [C/C++]，然後選擇 [實驗性]，即到達頁面。  

 Visual Studio 2017 安裝提供這些功能。  
  
> [!NOTE]
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## <a name="enable-predictive-intellisense"></a>啟用預測性 Intellisense
預測性 IntelliSense 會限制顯示在 IntelliSense 下拉式清單中的結果數，讓您只看到內容相關的結果。 例如，如果您輸入 <code>int x =</code> 並叫用 IntelliSense 下拉式清單，您只會看到整數或傳回整數的函式。 根據預設，會關閉預測性 IntelliSense。

## <a name="enable-faster-project-load"></a>啟用更快的專案載入
這個選項讓 Visual Studio 能夠快取專案資料，以便在您下次開啟專案時，載入那份快取的資料，而不必重新從專案檔計算資料。 使用快取資料可以大幅加速專案載入時間。  

## <a name="additional-features-in-the-visual-studio-gallery"></a>Visual Studio 組件庫中的其他功能
如需 Visual Studio 組件庫中的其他文字編輯器功能，請參閱[這裡](http://go.microsoft.com/fwlink/?LinkId=692016)的清單。 [C++ 快速修正](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)即為一例，其支援下列項目：  
  
-   **加入遺漏的 #include** - 建議相關的 #include 來表示程式碼中的未知符號  
  
-   **加入 Using 命名空間/完整限定符號** - 類似上一個項目，但針對命名空間  
  
-   **新增遺漏分號**  
  
-   **MSDN 說明** - 搜尋 MSDN 中的錯誤訊息  
  
 您可以將游標停留在波浪線上，或是使用預設鍵盤快速鍵 Ctrl+點 (Ctrl +)，來取得燈泡。 請注意，針對鍵盤快速鍵，您的插入號不需要放在特定錯誤或語彙基元上；您可以直接在錯誤所在的同一行，叫用該行上任何項目的建議。  
  
## <a name="see-also"></a>另請參閱  
 [設定語言特定編輯器選項](../../ide/reference/setting-language-specific-editor-options.md)   
 [Refactoring in C++ (VC Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx) (在 C++ 中重構 (VC 部落格))

