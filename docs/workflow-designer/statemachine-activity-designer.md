---
title: "StateMachine 活動設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: "5"
ms.author: sdanie
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 1800bfc9e60d52ea5c06bb94fdb765348a977681
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="statemachine-activity-designer"></a>StateMachine 活動設計工具
<xref:System.Activities.Statements.StateMachine> 活動包含狀態和模型工作流程的集合，這些工作流程使用熟悉的狀態機器開發架構。  
  
## <a name="using-the-statemachine-activity-designer"></a>使用 StateMachine 活動設計工具  
 若要加入<xref:System.Activities.Statements.StateMachine>拖曳的活動**StateMachine**活動設計工具，從**狀態機器**區段**工具箱**拖放入[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]介面。 若要加入至這個子狀態<xref:System.Activities.Statements.StateMachine>活動，拖曳<xref:System.Activities.Statements.State>或<xref:System.Activities.Core.Presentation.FinalState>從**工具箱**並將其放置**StateMachine**。  
  
### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 StateMachine 活動屬性  
 下表顯示可使用工作流程設計工具設定的 <xref:System.Activities.Statements.StateMachine> 屬性，並說明如何在設計工具中使用它們。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在設計工具介面上編輯。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.StateMachine> 活動設計工具在標頭中的易記名稱。 預設值是**StateMachine**。 此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。 <xref:System.Activities.Activity.DisplayName%2A> 可用於階層連結巡覽，顯示在工作流程設計工具的頂端。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
  
## <a name="see-also"></a>請參閱  
 [流程圖](../workflow-designer/flowchart-activity-designer.md)   
 [控制流程](../workflow-designer/control-flow-activity-designers.md)