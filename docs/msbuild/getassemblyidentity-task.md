---
title: "GetAssemblyIdentity Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, GetAssemblyIdentity task"
  - "GetAssemblyIdentity task [MSBuild]"
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetAssemblyIdentity Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

從指定的檔案擷取組件 \(Assembly\) 識別 \(Identity\) 並輸出識別資訊。  
  
## 工作參數  
 下表說明 `GetAssemblyIdentity` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`Assemblies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含擷取的組件識別。|  
|`AssemblyFiles`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要從中擷取識別的檔案。|  
  
## 備註  
 `Assemblies` 參數所輸出的項目，含有名為 `Version`、 `PublicKeyToken` 和 `Culture` 的項目中繼資料 \(Metadata\) 項目。  
  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 範例  
 下列範例擷取 `MyAssemblies` 項目中所指定檔案的識別，並輸出到 `MyAssemblyIdentities` 項目中。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="File1.dll;File2.dll" />  
    </ItemGroup>  
  
    <Target Name="RetrieveIdentities>  
        <GetAssemblyIdentity  
            AssemblyFiles="@(MyAssemblies)"  
            <Output  
                TaskParameter="Assemblies"  
                ItemName="MyAssemblyIdentities"  
    </Target>  
  
</Project>  
```  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)