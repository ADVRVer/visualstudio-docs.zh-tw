---
title: "用於偵測及管理 Visual Studio 執行個體的工具 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: timsneath
ms.author: tims
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: a6c3aa65a2c0198c856f09f6f16f58bf16945d58
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>用於偵測及管理 Visual Studio 執行個體的工具

## <a name="detecting-existing-visual-studio-instances"></a>偵測現有的 Visual Studio 執行個體
我們提供數種工具來協助您偵測及管理用戶端電腦上已安裝的 Visual Studio 執行個體︰

* [VSWhere](https://github.com/microsoft/vswhere)：C++ 可執行檔，協助您從已安裝的 Visual Studio 執行個體找到核心 Visual Studio 工具的位置。
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell)︰PowerShell 指令碼，使用安裝程式組態 API 來識別已安裝的 Visual Studio 執行個體。
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples)：C# 和 C++ 範例，示範如何使用安裝程式組態 API 來查詢現有安裝。

此外，[安裝程式組態 API](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) 還提供介面，讓想要建置其專屬公用程式的開發人員查閱 Visual Studio 執行個體。

>[!TIP]
>如需 Visual Studio 2017 安裝的詳細資訊，請參閱 [Heath Stewart's blog articles](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/) (Heath Stewart 的部落格文章)。


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>編輯 Visual Studio 執行個體的登錄
在 Visual Studio 2017 中，登錄設定會儲存在私人位置，這可在相同電腦上啟用相同版本之 Visual Studio 的多個並存執行個體。

因為這些項目不是儲存在全域登錄中，針對使用登錄編輯程式來變更登錄設定有一些特殊指示︰

1. 如果您有開啟的 Visual Studio 2017 執行個體，請將它關閉。
2. 啟動 `regedit.exe`。
3. 選取 `HKEY_LOCAL_MACHINE` 節點。
4. 從 Regedit 主功能表選取 [檔案] -> [載入登錄區]，然後選取私人登錄檔 (儲存在 **AppData\Local** 資料夾中)。 例如: 
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

> [!NOTE]
> `<config>` 對應至您想要瀏覽的 Visual Studio 執行個體。

系統將會提示您提供登錄區名稱，這會變成您的已隔離登錄區的名稱。 這麼做之後，您應該能在您所建立的已隔離登錄區下瀏覽登錄。

> [!IMPORTANT]
> 在重新啟動 Visual Studio 之前，必須卸載您所建立的已隔離登錄區。 若要這樣做，從 Regedit 主功能表選取 [檔案] -> [解除載入登錄區] (如果您沒有這麼做，則檔案會維持鎖定且 Visual Studio 將無法啟動)。

