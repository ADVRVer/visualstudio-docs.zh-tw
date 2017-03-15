---
title: "如何：設定 ClickOnce 應用程式的自訂使用權限 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 應用程式, 權限"
  - "權限, ClickOnce 應用程式"
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：設定 ClickOnce 應用程式的自訂使用權限
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以部署對網際網路或近端內部網路區域使用預設權限的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。 或者，您可以建立應用程式所需特定權限的自訂區域。 做法是在 \[專案設計工具\] 的 \[安全性\] 頁面上自訂安全性權限。  
  
### 自訂權限  
  
1.  在方案總管中選取專案之後，按一下 \[專案\] 功能表中 \[屬性\]。  
  
2.  按一下 \[**安全性**\] 索引標籤。  
  
3.  選取 \[啟用 ClickOnce 安全性設定\] 核取方塊。  
  
4.  選取 \[這是部分信任的應用程式\] 選項按鈕。  
  
     這會啟用 \[ClickOnce 安全性權限\] 區段中的控制項。  
  
5.  從 \[安裝應用程式的區域\] 下拉式清單中，按一下 \[\(自訂\)\]。  
  
6.  按一下 \[編輯權限 XML\]。  
  
     即會在 \[XML 編輯器\] 中開啟 app.manifest 檔案。  
  
7.  在 `</applicationRequestMinimum>` 項目之前，新增應用程式所需權限的 XML 程式碼。  
  
    > [!NOTE]
    >  您可以使用權限集的 `ToXml` 方法，產生應用程式資訊清單的 XML 程式碼。 例如，若要產生 <xref:System.Security.Permissions.EnvironmentPermission> 權限集的 XML，請呼叫 <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> 方法。 如需權限集 XML 結構的詳細資訊，請參閱 [NIB: How to: Import a Permission Set by Using an XML File](http://msdn.microsoft.com/zh-tw/dea16b54-c108-408a-ac36-cdc05f746236)。  
  
## 請參閱  
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 應用程式的程式碼存取安全性](../deployment/code-access-security-for-clickonce-applications.md)   
 [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)