---
title: "管理外部工具 | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 38
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
ms.openlocfilehash: 1d273749cc41eb975dc9f93329edf9a57aaae09a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# 管理外部工具
<a id="manage-external-tools" class="xliff"></a>
您可以使用 [工具]，從 Visual Studio 內部呼叫外部工具。 [工具] 功能表中有提供一些預設的工具，但您可以另外加入自己的可執行檔。  

## Visual Studio [工具] 功能表上提供的工具
<a id="tools-available-on-the-visual-studio-tools-menu" class="xliff"></a>
 [工具] 功能表包含數個內建命令，例如：

*  [延伸模組和更新] 可用來[管理 Visual Studio 延伸模組](finding-and-using-visual-studio-extensions.md)
*  [程式碼片段管理員...] 可用來[組織程式碼片段](code-snippets.md#code-snippet-manager)
*  [PreEmptive Protection - Dotfuscator] 可用來啟動 [Dotfuscator Community Edition (CE)](dotfuscator/index.md) (若[已安裝](dotfuscator/install.md)的話)
*  [自訂...] 可用來[自訂功能表和工具列](how-to-customize-menus-and-toolbars-in-visual-studio.md)
*  [選項...] 可用來[設定各種不同的 Visual Studio IDE 和其他工具選項](reference/options-dialog-box-visual-studio.md)

## 將新的工具新增至 [工具] 功能表
<a id="add-new-tools-to-the-tools-menu" class="xliff"></a> 
 您可將外部工具加入 [工具] 功能表。 開啟 [外部工具...] 對話方塊，按一下 [加入]，然後填入資訊。 例如，下列輸入內容會讓 Windows 檔案總管的開啟位置，會是於 Visual Studio 中目前所開啟之檔案所在的目錄：  
  
1.  標題：*Open File Location*
  
2.  命令：`explorer.exe`  
  
3.  引數：`/root, "$(ItemDir)"`  
  
 以下是在定義外部工具時可以使用的引數完整清單。
  
> [!NOTE]
>  IDE 狀態列會顯示目前這一行和目前資料行的變數，以指出插入點在作用中程式碼編輯器的位置。 目前的文字變數則會傳回在該位置選取的文字或程式碼。  
  
|名稱|引數|描述|  
|----------|--------------|-----------------|  
|項目路徑|$(ItemPath)|目前檔案的完整檔案名稱 (磁碟機 + 路徑 + 檔案名稱)。|  
|項目目錄|$(ItemDir)|目前檔案的目錄 (磁碟機 + 路徑)。|  
|項目檔名|$(ItemFilename)|目前檔案的檔案名稱 (檔案名稱)。|  
|項目副檔名|$(ItemExt)|目前檔案的副檔名。|  
|目前的行|$(CurLine)|程式碼視窗中滑鼠游標目前的行位置。|  
|目前的資料行|$(CurCol)|程式碼視窗中滑鼠游標目前的資料行位置。|  
|目前的文字|$(CurText)|選取的文字。|  
|目標路徑|$(TargetPath)|要建置之項目的完整檔案名稱 (磁碟機 + 路徑 + 檔案名稱)。|  
|目標目錄|$(TargetDir)|要建置之項目的目錄。|  
|目標名稱|$(TargetName)|要建置之項目的檔案名稱。|  
|目標副檔名|$(TargetExt)|要建置之項目的副檔名。|  
|二進位檔目錄|$(BinDir)|正在建置之二進位檔的最終位置 (定義為磁碟機 + 路徑)。 例如：**\\...\My Documents\Visual Studio \<本>\\<專案名稱\>\bin\debug**|  
|專案目錄|$(ProjDir)|目前專案的目錄 (磁碟機 + 路徑)。|  
|專案檔名|$(ProjFileName)|目前專案的檔案名稱 (磁碟機 + 路徑 + 檔案名稱)。|  
|方案目錄|$(SolutionDir)|目前方案的目錄 (磁碟機 + 路徑)。|  
|方案檔名|$(SolutionFileName)|目前方案的檔案名稱 (磁碟機 + 路徑 + 檔案名稱)。|  

## 請參閱
<a id="see-also" class="xliff"></a>  
 [C/C++ 建置工具](/cpp/build/reference/c-cpp-build-tools)

