---
title: "在 Visual Studio 中同步處理設定 | Microsoft Docs"
ms.custom: 
ms.date: 01/23/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 10
author: kempb
ms.author: kempb
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 6bf0181e49d8390eed8f750d16b706780d71f08a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# <a name="synchronize-your-settings-in-visual-studio"></a>在 Visual Studio 中同步處理設定
當您使用相同的個人化帳戶在多部電腦上登入 Visual Studio 時，根據預設所有電腦皆會同步處理您的設定。

## <a name="synchronized-settings"></a>同步設定  
 預設會同步處理下列設定。  

-   開發設定 (您必須在第一次執行 Visual Studio 時選取一組設定，但是可以隨時變更選取範圍。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md))。  

-   [工具] &#124; [選項] 頁面中的下列選項：  

    -   [環境]、[一般] 選項頁面上的 [主題] 和功能表列大小寫設定  

    -   [環境]、[字型和色彩] 選項頁面上的所有設定  

    -   [環境]、[鍵盤] 選項頁面上的所有鍵盤快速鍵  

    -   [環境]、[索引標籤和視窗] 選項頁面上的所有設定  

    -   [環境]、[啟動] 選項頁面上的所有設定  

    -   [文字編輯器] 選項頁面上的所有設定  

-   [XAML 設計工具] 選項頁上的所有設定  

-   使用者定義的命令別名。 如需如何定義命令別名的詳細資訊，請參閱 [Visual Studio 命令別名](../ide/reference/visual-studio-command-aliases.md)。  

-   [視窗] &#124; [管理視窗配置] 頁面中的使用者定義視窗配置  

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>關閉特定電腦的同步設定  
 Visual Studio 的同步設定預設為開啟。 您可以關閉電腦的同步設定，方法是移至 [工具] &#124; [選項] &#124; [環境] &#124; [同步設定] 頁面，並且取消核取核取方塊。  例如，如果您決定不要同步處理電腦 A 上 Visual Studio 的設定，則任何在電腦 A 上的設定變更都不會出現在電腦 B 或電腦 C 上。電腦 B 和 C 會繼續互相同步處理，但不會和電腦 A 同步。  

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>同步處理 Visual Studio 系列產品和版本之間的設定  
 可同步處理任何 Visual Studio 版本 (包含 Community 版本) 之間的設定。 也會同步處理 Visual Studio 系列產品之間的設定。 不過，這些系列產品中的每一個都可能有它自己不會與 Visual Studio 共用的設定。 例如，電腦 A 的某個產品專屬設定會和電腦 B 的另一個產品專屬設定共用，但不會和電腦 A 或 B 上的 Visual Studio 共用。  

## <a name="see-also"></a>請參閱  
 [個人化 IDE](../ide/personalizing-the-visual-studio-ide.md)

