---
title: "Visual Studio 安裝的命令列參數範例 | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
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
ms.openlocfilehash: 0f07824b29e7851e353d472838a897853e227d6c
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Visual Studio 2017 安裝的命令列參數範例
為了說明如何[使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)，以下是幾個範例，您可以自訂以符合您的需求。

在每個範例中，`vs_enterprise.exe`、`vs_professional.exe` 和 `vs_community.exe` 表示 Visual Studio 啟動載入器的個別版本，這是起始下載程序的小型檔案 (約 1 MB)。 如果您使用不同的版本，請取代為適當的啟動載入器名稱。

> [!NOTE]
> 所有命令都需要提升系統管理權限，如果未從已提升權限的提示字元啟動程序，則會顯示 [使用者帳戶控制] 提示。

> [!NOTE]
>  您可以在命令列結尾處使用 `^` 字元，將多行串連成單一命令。 或者，您也可以直接將這幾行放到一列。 在 PowerShell 中，對等項目為倒引號 (`` ` ``) 字元。 

* 安裝 Visual Studio 的最小執行個體，不會顯示互動式提示，但會顯示進度：
```
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* 使用法文語言套件以無訊息方式安裝 Visual Studio 的桌面執行個體，並只在安裝產品時傳回。
```
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
```

> [!NOTE]
>  `--wait` 參數是專為在批次檔中使用所設計。 在批次檔中，直到安裝完成之後，才會繼續執行下一個命令。 `%ERRORLEVEL%` 環境變數會包含命令的傳回值，如[使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md) 頁面中所述。

* 下載 Visual Studio 核心編輯器 (最基本的 Visual Studio 設定)。 只包含英文語言套件：

```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
```

* 下載 .NET 桌面和 .NET Web 工作負載，以及所有建議的元件和 GitHub 延伸模組。 只包含英文語言套件：
```
vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
```

* 啟動 Visual Studio 2017 Enterprise 版中可用之所有工作負載和元件的互動式安裝：
```
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* 在已安裝 Visual Studio 2017 Community 版的電腦上安裝第二個名為 Visual Studio 2017 Professional 的執行個體，並提供 Node.js 開發的支援：
```
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
```

* 從預設安裝的 Visual Studio 執行個體移除程式碼剖析工具元件：
```
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

## <a name="see-also"></a>請參閱

 * [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
 * [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [建立 Visual Studio 2017 的離線安裝](create-an-offline-installation-of-visual-studio.md)

