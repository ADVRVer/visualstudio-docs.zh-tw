---
title: "如何： 建立事件接收器的特定清單執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 66801e82f64e23ee24e66c63a62dd895c58389dc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>如何：為特定的清單執行個體建立事件接收器
  清單執行個體的事件接收器會回應在清單中定義的任何執行個體中發生的事件。 雖然事件接收器範本不會啟用目標的特定清單執行個體，您可以修改事件接收器，以便以回應事件中的特定清單執行個體的清單定義為範圍。  
  
 若要為目標的特定清單執行個體，在事件接收器，Elements.xml 取代`ListTemplateId`與`ListUrl`並加入清單執行個體的 URL。  
  
## <a name="creating-a-list-instance-event-receiver"></a>建立清單執行個體的事件接收器  
 下列步驟顯示如何修改自訂的公告清單執行個體中發生的事件只回應的清單項目事件接收器。  
  
#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>若要修改的特定清單執行個體回應的事件接收器  
  
1.  在瀏覽器中開啟 SharePoint 網站。  
  
2.  在瀏覽窗格中，**列出**連結。  
  
3.  在**所有網站內容**頁面上，選擇**建立**連結。  
  
4.  在**建立**對話方塊方塊中，選擇**公告**類型，將公告命名**TestAnnouncements**，然後選擇 [**建立**] 按鈕。  
  
5.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，建立事件接收器專案。  
  
6.  在**您要何種類型的事件接收器？**清單中，選擇**清單項目事件**。  
  
    > [!NOTE]  
    >  您也可以選取任何其他種類的事件接收器，例如，會設定為清單定義**列出的電子郵件事件**或**清單工作流程事件**。  
  
7.  在**何種項目應該做為事件來源？**清單中，選擇**公告**。  
  
8.  在**處理下列事件**清單中，選取**正在加入項目**核取方塊，，然後選擇 [**完成**] 按鈕。  
  
9. 在**方案總管] 中**，在 [eventreceiver1]，開啟 [Elements.xml。  
  
     事件接收器目前是使用下列程式碼行參考 [公告] 清單定義：  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     請將這行變更為以下文字：  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     這會將事件接收器，只發生在新的事件回應導向**TestAnnouncements**您剛才建立的公告清單。 您可以變更`ListURL`屬性，來參照任何 SharePoint 伺服器上的清單執行個體。  
  
10. 開啟事件接收器程式碼檔案，將中斷點放在 ItemAdding 方法。  
  
11. 選擇 F5 鍵，建置並執行方案。  
  
12. 在 SharePoint 中，選擇  **TestAnnouncements**瀏覽窗格中的連結。  
  
13. 選擇**新增新的 announcement**連結。  
  
14. 輸入公告的標題，然後選擇**儲存** 按鈕。  
  
     請注意，自訂的公告清單中加入新項目時叫用中斷點。  
  
15. 選擇 F5 鍵繼續。  
  
16. 在瀏覽窗格中，選擇 **列出**連結，，然後選擇 **公告**連結。  
  
17. 加入新的通知。  
  
     請注意，事件接收器將不會在新的 announcement 因為收件者已設定為只回應中的自訂公告清單執行個體中，事件才會觸發**TestAnnouncements**。  
  
## <a name="see-also"></a>請參閱  
 [如何： 建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  