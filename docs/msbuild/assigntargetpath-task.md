---
title: "AssignTargetPath 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 144b8b82209b63262db8b7a25f2478b9a4c89edb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="assigntargetpath-task"></a>AssignTargetPath 工作
此工作接受檔案清單，並新增 `<TargetPath>` 屬性 (如果尚未指定)。  
  
## <a name="task-parameters"></a>工作參數  
 下表說明 `AssignTargetPath` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`RootFolder`|選擇性 `string` 輸入參數。<br /><br /> 包含有目標連結的資料夾路徑。|  
|`Files`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸入參數。<br /><br /> 包含傳入的檔案清單。|  
|`AssignedFiles`|Optional<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem> `[]` 輸出參數。<br /><br /> 包含產生的檔案清單。|  
  
## <a name="remarks"></a>備註  
 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>範例  
 下列範例會執行 `AssignTargetPath` 工作來設定專案。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)