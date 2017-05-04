---
title: "如何：在應用程式中加入自訂工作窗格 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "自訂工作窗格 [Visual Studio 中的 Office 程式開發], 加入至應用程式"
  - "工作窗格 [Visual Studio 中的 Office 程式開發], 加入至應用程式"
ms.assetid: 67b4ed5b-d77e-4630-b851-34bb25bdc9b3
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 如何：在應用程式中加入自訂工作窗格
  您可以使用 VSTO 增益集，將自訂工作窗格加入上面所列的應用程式。  如需詳細資訊，請參閱[自訂工作窗格](../vsto/custom-task-panes.md)。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 在應用程式中加入自訂工作窗格  
  
#### 若要在應用程式中加入自訂工作窗格  
  
1.  針對上面所列的其中一個應用程式，開啟或建立 VSTO 增益集專案。  如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在 \[專案\] 功能表上，按一下 \[加入使用者控制項\]。  
  
3.  在 \[加入新項目\] 對話方塊中，將新使用者控制項的名稱變更為 **MyUserControl**，然後按一下 \[加入\]。  
  
     使用者控制項隨即在設計工具中開啟。  
  
4.  將一個或多個 Windows Form 控制項從 \[工具箱\] 加入使用者控制項。  
  
5.  開啟 **ThisAddIn.cs** 或 **ThisAddIn.vb** 程式碼檔案。  
  
6.  將下列程式碼加入 `ThisAddIn` 類別。  此程式碼會將 `MyUserControl` 和 <xref:Microsoft.Office.Tools.CustomTaskPane> 的執行個體宣告為 `ThisAddIn` 類別的成員。  
  
     [!code-csharp[Trin_TaskPaneBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#1)]  
  
7.  將下列程式碼加入至 `ThisAddIn_Startup` 事件處理常式。  此程式碼會建立新的 <xref:Microsoft.Office.Tools.CustomTaskPane>，方法是將 `MyUserControl` 物件加入 `CustomTaskPanes` 集合。  程式碼也會顯示工作窗格。  
  
     [!code-csharp[Trin_TaskPaneBasic#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneBasic#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#2)]  
  
    > [!NOTE]  
    >  這個程式碼會使您自訂的工作窗格與應用程式中的現用視窗相關聯。  對於某些應用程式，您可能想要修改這個程式碼以確保工作窗格會隨其他文件或項目一起在應用程式中顯示。  如需詳細資訊，請參閱[自訂工作窗格](../vsto/custom-task-panes.md)。  
  
## 請參閱  
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [自訂工作窗格](../vsto/custom-task-panes.md)   
 [逐步解說：運用自訂工作窗格自動化應用程式](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
  
  