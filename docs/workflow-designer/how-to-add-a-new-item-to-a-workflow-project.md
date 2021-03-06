---
title: "如何： 將新的項目加入至工作流程專案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: "14"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: e2031f084b11f9879fd94f5d2e454e0966ed3787
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>HOW TO：將新的項目加入至工作流程專案
在建立工作流程專案後，可以將工作流程活動、設計工具和其他熟悉的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 項目加入至專案。  
  
 下表列出您可加入至工作流程專案的 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 項目。  
  
|名稱|描述|  
|----------|-----------------|  
|活動|要由其他活動組成的活動。 選取這個項目是將相同的 XAML 檔案加入專案，當選取時，您會取得**活動程式庫**新的專案範本。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]在此程序，請參閱[How to： 建立活動程式庫](../workflow-designer/how-to-create-an-activity-library.md)。|  
|活動設計工具|可自訂活動之設計階段經驗的設計工具。 選取這個項目是將相同的檔案加入專案，當選取時，您會取得**活動設計工具程式庫**新的專案範本。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]在此程序，請參閱[How to： 建立活動設計工具程式庫](../workflow-designer/how-to-create-an-activity-designer-library.md)。|  
|程式碼活動|包含寫入至程式碼之執行邏輯的活動。 已為您產生包含 <xref:System.Activities.CodeActivity.Execute%2A> 方法之覆寫的原始程式碼檔。|  
|WCF 工作流程服務|使用工作流程活動建置的 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] 服務。 選取這個項目是將相同的檔案加入專案，當選取時，您會取得**WCF 工作流程服務應用程式**新的專案範本。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]在此程序，請參閱[How to： 建立 WCF 工作流程服務應用程式](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md)。|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>若要將新的項目加入至工作流程專案  
  
1.  在**專案**功能表上，按一下 **加入新項目...**.  
  
     **加入新項目**對話方塊隨即開啟。  
  
2.  在**已安裝的範本**窗格中，選取**工作流程**群組。  
  
3.  選取四個項目的其中一個。 上表列出可用的選擇。  
  
4.  輸入適當的名稱中的項目**名稱**方塊 對話方塊的底部。  
  
5.  按一下**新增**將項目加入至目前的工作流程專案。  
  
## <a name="see-also"></a>請參閱  
 [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)