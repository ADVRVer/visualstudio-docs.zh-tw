---
title: "如何：替代樣板中的參數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "範本參數, 替代"
  - "Visual Studio 範本, 使用參數"
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：替代樣板中的參數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

根據範本建立檔案時，您可以取代範本參數 \(例如類別名稱和命名空間\)。  如需完整的範本參數清單，請參閱[樣板參數](../ide/template-parameters.md)。  
  
## 程序  
 只要根據該範本建立專案時，就可能會取代範本檔案中的參數。  此程序說明使用範本建立新的專案時，如何建立將命名空間名稱取代為安全專案名稱的範本。  
  
#### 使用參數將命名空間名稱取代為專案名稱  
  
1.  在範本的一或多個程式碼檔案中，插入參數。  例如:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  以格式 $*parameter*$ 撰寫範本參數。  
  
2.  在範本的 .vstemplate 檔案中，找出包括此檔案的 `ProjectItem` 項目。  
  
3.  將 `ProjectItem` 項目的 `ReplaceParameters` 屬性設定為 `true`。  例如:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## 請參閱  
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [樣板參數](../ide/template-parameters.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem 項目 \(Visual Studio 項目範本\)](../extensibility/projectitem-element-visual-studio-item-templates.md)