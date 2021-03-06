---
title: "Visual Studio 編碼與分行符號字元 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8a472a09a4d4d67f59d7879d03b466932d1445e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="encodings-and-line-breaks"></a>編碼與分行符號
在 Visual Studio 中，會將下列字元解譯為分行符號：  
  
-   CR LF：歸位字元 + 換行字元、Unicode 字元 000D + 000A  
  
-   LF：換行字元、Unicode 字元 000A  
  
-   NEL：下一行、Unicode 字元 0085  
  
-   LS：行分隔符號、Unicode 字元 2028  
  
-   PS：段落分隔符號、Unicode 字元 2029  
  
從其他應用程式複製的文字會保留原始編碼和分行符號字元。 例如，當您從 [記事本] 中複製文字，並將它貼到 Visual Studio 中的文字檔，文字的設定會與它在 [記事本] 中的設定相同。  
  
當您開啟的檔案包含不同的分行符號字元時，可能會看到一個對話方塊，詢問是否應該正規化不一致的分行符號字元以及要選擇哪一種分行符號類型。

您可以使用 [檔案]、[進階儲存選項] 對話方塊，判斷您要的分行符號字元類型。 您也可以變更具有相同設定之檔案的編碼。

![[進階儲存選項] 對話方塊](media/line_endings.png)
  
> [!NOTE]
>  如果您在 [檔案] 功能表上看不到 [進階儲存選項]，您可以新增它。 選擇 [工具]、[自訂...]，然後選擇 [命令] 索引標籤。在 [功能表列] 下拉式清單中，選擇 [檔案]，然後選擇 [新增命令...] 按鈕。 在 [新增命令] 對話方塊的 [類別] 下，選擇 [檔案]，然後在 [命令] 清單中選擇 [進階儲存選項...]。選擇 [確定]，然後選擇 [下移] 按鈕，將命令移至功能表中的任何位置。 選擇 [關閉] 以關閉 [自訂] 對話方塊。 如需詳細資訊，請參閱[自訂功能表和工具列](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu)。

或者，您可以選擇 [檔案]、[另存 \<檔案\> 為...] 來存取 [進階儲存選項] 對話方塊。在 [另存新檔] 對話方塊中，選擇 [儲存] 按鈕旁的下拉式三角形，然後選擇 [以編碼方式儲存...]。

## <a name="see-also"></a>另請參閱
[在編輯器中撰寫程式碼](../ide/writing-code-in-the-code-and-text-editor.md)