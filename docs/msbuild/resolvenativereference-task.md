---
title: "ResolveNativeReference 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
caps.latest.revision: 9
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b0b08a9602c81e504bf2cd01d1d1ce9720dc6b2a
ms.lasthandoff: 02/22/2017

---
# <a name="resolvenativereference-task"></a>ResolveNativeReference 工作
解析原生參考。 實作 <xref:Microsoft.Build.Tasks.ResolveNativeReference> 類別。 此類別支援的 .NET Framework 結構不適合直接從程式碼使用。  
  
## <a name="task-parameters"></a>工作參數  
 下表說明 `ResolveNativeReference` 工作的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`AdditionalSearchPaths`|必要的 [String](assetId:///String?qualifyHint=False&autoUpgrade=True)`[]` 參數。<br /><br /> 取得或設定搜尋路徑，以解析原生參考的組件識別碼。|  
|`ContainedComComponents`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 取得或設定原生組譯碼的 COM 元件。|  
|`ContainedLooseEtcFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 取得或設定原生資訊清單中列出的鬆散 Etc 檔案。|  
|`ContainedLooseTlbFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 取得或設定原生組譯碼的鬆散 .tlb 檔案。|  
|`ContainedPrerequisiteAssemblies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 取得或設定必須存在才能使用資訊清單的組件。|  
|`ContainedTypeLibraries`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 取得或設定原生組譯碼的類型程式庫。|  
|`ContainingReferenceFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 取得或設定參考檔。|  
|`NativeReferences`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 取得或設定 Win32 原生組件參考。|  
  
## <a name="remarks"></a>備註  
 除了上面所列的參數，此工作會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而其本身是繼承自 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
