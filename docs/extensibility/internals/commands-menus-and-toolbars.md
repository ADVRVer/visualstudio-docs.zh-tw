---
title: "命令、 功能表和工具列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: "60"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa1513bcd61ac63fb9d2a59f69a8b2ce22cf5114
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="commands-menus-and-toolbars"></a>命令、 功能表和工具列
功能表和工具列是使用者的方式存取您的 VSPackage 中的命令。 命令是完成工作 (例如，列印文件、重新整理檢視，或建立新檔案) 的功能。 功能表和工具列是一種圖形方式，方便向使用者呈現您的命令。 通常，相關的命令會一起聚集在相同的功能表或工具列上。  
  
-   功能表通常會顯示為聚集在整合式開發環境 (IDE) 或工具視窗頂端的一連串單字字串。 功能表也可以顯示為滑鼠右鍵事件的結果，並且指的是該內容中的快顯功能表。 按一下時，會展開功能表以顯示一個或多個命令。 按一下時，命令可以執行工作，或啟動包含其他命令的子功能表。 一些已知功能表名稱是 [檔案]、[編輯]、[檢視] 和 [視窗]。 如需詳細資訊，請參閱[擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
-   工具列通常是數串的按鈕和其他控制項 (例如下拉式方塊、清單方塊、文字方塊和功能表控制器)。 所有工具列控制項都是與命令相關聯。 按一下工具列按鈕時，會啟動其相關聯的命令。 工具列按鈕通常會有圖示建議基礎命令 (例如 [列印] 命令的印表機)。 在下拉式清單控制項中，清單中的每個項目都是與不同的命令相關聯。 功能表控制器是一種混合體，其中，控制項的一邊是工具列按鈕，另一邊則是按一下時顯示其他命令的向下箭號。 如需詳細資訊，請參閱[功能表控制器加入工具列](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)。  
  
-   建立命令時，也必須一併建立它的事件處理常式。 事件處理常式可判斷命令的顯示和啟用時間、可讓您修改其文字，並確保在啟動時適當地回應命令 (路由遞送)。 在大部分情況下，IDE 會處理命令使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。 中的命令[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]路由在階層的方式，並根據本機選取範圍，並繼續到最外層的內容，根據全域選取範圍的最內層命令內容開始。 加入主功能表的命令可立即用於指令碼編寫。 如需詳細資訊，請參閱[MenuCommands Vs。OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)和[選擇內容物件](../../extensibility/internals/selection-context-objects.md)。  
  
 若要定義新的功能表和工具列，您必須以 Visual Studio 命令表 (.vsct) 檔案描述它們。 Visual Studio 封裝樣板會建立這個檔案以及必要項目，以支援您在樣板中所選取的任何命令、工具列和編輯器。 或者，您可以撰寫專屬.vsct 檔案中，使用此處所描述的 xml 結構描述： [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)。  
  
 如需使用.vsct 檔案的詳細資訊，請參閱[Visual Studio 命令表 (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
 本節中的主題說明命令、 功能表和工具列在 Vspackage 中運作的方式。  
  
## <a name="in-this-section"></a>本節內容  
 [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 命令資料表格式規格的深入描述。  
  
 [Visual Studio 命令表檔案 (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 描述 XML 為基礎的語法和命令資料表編譯器。  
  
 [預設的命令、群組及工具列位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 描述預先定義的命令、 群組、 功能表和工具列。  
  
 [IDE 定義的命令、功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 指定預先定義的功能表、 命令及可供使用的命令群組[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
 [命令設計](../../extensibility/internals/command-design.md)  
 說明如何設計命令。  
  
 [將功能表和工具列命令最佳化](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 命令提供指導方針。  
  
 [提供可用的命令](../../extensibility/internals/making-commands-available.md)  
 說明如何讓 Visual Studio 中使用的命令。  
  
 [使用 Interop 組件的命令和功能表](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 說明如何實作使用 interop 組件的命令。  
  
## <a name="related-sections"></a>相關章節  
 [在 VSPackage 中路由傳送命令](../../extensibility/internals/command-routing-in-vspackages.md)  
 說明在 Vspackage 中的命令路由。