---
title: "CommandPlacement 項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a6a5c8d9220b0cd2c0dddfee283d222f4efb9ab8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="commandplacement-element"></a>CommandPlacement 項目
按鈕、 群組和包含在一個以上的群組或功能表的功能表，可讓 CommandPlacement 項目。 使用 CommandPlacement 項目，讓您不必完全重新定義這些項目，才能修改使用者介面的外觀。  
  
 如需詳細資訊，請參閱[建立可重複使用群組的按鈕](../extensibility/creating-reusable-groups-of-buttons.md)。  
  
## <a name="syntax"></a>語法  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|Guid|必要。 中所定義的命令集的 guid[符號項目](../extensibility/symbols-element.md)。|  
|id|必要。 功能表、 群組或要放置，如中所定義的命令識別碼`Symbols Element`。|  
|priority|必要。 決定 visual 位置的項目在其父項目。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|父代|必要。 功能表或裝載要放置項目群組中。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandPlacements 元素](../extensibility/commandplacements-element.md)|指定 CommandPlacements 和 CommandPlacement 項目群組。|  
  
## <a name="example"></a>範例  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>請參閱  
 [CommandPlacements 項目](../extensibility/commandplacements-element.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)