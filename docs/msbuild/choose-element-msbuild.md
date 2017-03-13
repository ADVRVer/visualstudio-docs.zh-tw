---
title: "Choose 項目 (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
caps.latest.revision: 8
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
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: c4d93013218ace4039267bec73a2525df0c1b370
ms.lasthandoff: 02/22/2017

---
# <a name="choose-element-msbuild"></a>Choose 項目 (MSBuild)
評估子項目，以選取一組要評估的 `ItemGroup` 項目和/或 `PropertyGroup` 項目。  

 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  

## <a name="syntax"></a>語法  

```  
<Choose>  
    <When Condition="'StringA'=='StringB'">... </When>  
    <Otherwise>... </Otherwise>  
</Choose>  
```  

## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  

### <a name="attributes"></a>屬性  
 無。  

### <a name="child-elements"></a>子項目  

|項目|說明|  
|-------------|-----------------|  
|[Otherwise](../msbuild/otherwise-element-msbuild.md)|選擇性項目。<br /><br /> 指定只有當所有 `When` 項目的條件評估為 `false` 時，才需評估的程式碼 `PropertyGroup` 和 `ItemGroup` 項目的區塊。 `Choose` 項目中可能有零或一個 `Otherwise` 項目，而且它必須是最後一個項目。|  
|[When](../msbuild/when-element-msbuild.md)|必要項目。<br /><br /> 指定 `Choose` 項目可能要選取的程式碼區塊。 `Choose` 項目中可能有一或多個 `When` 項目。|  

### <a name="parent-elements"></a>父項目  

|項目|說明|  
|-------------|-----------------|  
|[Otherwise](../msbuild/otherwise-element-msbuild.md)|指定如果所有 `When` 項目的條件評估為 `false`，才需執行的程式碼區塊。|  
|[Project](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔案的必要根項目。|  
|[When](../msbuild/when-element-msbuild.md)|指定 `Choose` 項目可能要選取的程式碼區塊。|  

## <a name="remarks"></a>備註  
 `Choose`、`When` 和 `Otherwise` 項目會一起用於提供一種方式來選取一個程式碼區段，以執行一些可能的替代方案。 如需詳細資訊，請參閱[條件式建構](../msbuild/msbuild-conditional-constructs.md)。  

## <a name="example"></a>範例  
 下列專案使用 `Choose` 項目來選取 `When` 項目中要設定的屬性值集合。 如果這兩個 `When` 項目的 `Condition` 屬性均評估為 `false`，就會設定 `Otherwise` 項目中的屬性值。  

```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
        <Otherwise>  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\$(Configuration)\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
        </Otherwise>  
    </Choose>  
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
</Project>  
```  

## <a name="see-also"></a>另請參閱  
 [條件式建構](../msbuild/msbuild-conditional-constructs.md)   
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)

