---
title: "逐步解說： 將資料繫結至 Excel 執行窗格上的控制項 |Microsoft 文件"
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
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8588fef2fc5e9e4737a605e0767b8b68b2f721f4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-binding-data-to-controls-on-an-excel-actions-pane"></a>逐步解說：將資料繫結至 Excel 執行窗格上的控制項
  本逐步解說示範資料繫結至 Microsoft Office Excel 中的 [動作] 窗格上的控制項。 這些控制項會顯示 SQL Server 資料庫中資料表之間的主要/詳細資料關聯。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   將控制項加入工作表。  
  
-   建立執行窗格控制項。  
  
-   將資料繫結 Windows Form 控制項加入執行窗格控制項。  
  
-   顯示應用程式開啟時，[動作] 窗格。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   伺服器的存取權與 Northwind SQL Server 範例資料庫。  
  
-   讀取和寫入至 SQL Server 資料庫的權限。  
  
## <a name="creating-the-project"></a>建立專案  
 第一步是建立 Excel 活頁簿專案。  
  
#### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  建立名稱的 Excel 活頁簿專案**我的 Excel 執行窗格**。 在精靈中，選取**建立新的文件**。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 設計工具中開啟新 Excel 活頁簿，並將**我的 Excel 執行窗格**專案加入**方案總管 中**。  
  
## <a name="adding-a-new-data-source-to-the-project"></a>將新的資料來源加入至專案  
  
#### <a name="to-add-a-new-data-source-to-the-project"></a>將新的資料來源加入至專案  
  
1.  如果看不到 [ **資料來源** ] 視窗，請在功能表列選擇 [ **檢視**]、[ **其他視窗**]、[ **資料來源**] 即可顯示。  
  
2.  選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。  
  
3.  選取**資料庫**，然後按一下 **下一步**。  
  
4.  選取資料連接至 Northwind 範例 SQL Server 資料庫，或加入新的連接使用**新連線** 按鈕。  
  
5.  按 [ **下一步**]。  
  
6.  如果已選取，儲存連接選項，然後按清除**下一步**。  
  
7.  展開**資料表**節點**資料庫物件**視窗。  
  
8.  選取此核取方塊旁的 **供應商**資料表。  
  
9. 展開**產品**資料表，然後選取**ProductName**， **SupplierID**， **QuantityPerUnit**，和**UnitPrice**.  
  
10. 按一下 [ **完成**]。  
  
 精靈會新增**供應商**資料表和**產品**資料表**資料來源**視窗。 它也會將具類型資料集加入至您的專案中可見的**方案總管 中**。  
  
## <a name="adding-controls-to-the-worksheet"></a>將控制項加入工作表  
 接下來，加入<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項和<xref:Microsoft.Office.Tools.Excel.ListObject>第一個工作表的控制項。  
  
#### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>若要加入 NamedRange 控制項和 ListObject 控制項  
  
1.  確認**我的 Excel 動作 Pane.xlsx**活頁簿是在 Visual Studio 設計工具中開啟與`Sheet1`顯示。  
  
2.  在**資料來源**視窗中，展開 **供應商**資料表。  
  
3.  按一下下拉箭號**公司名稱**節點，然後再按一下**NamedRange**。  
  
4.  拖曳**公司名稱**從**資料來源**儲存格的視窗**A2**中`Sheet1`。  
  
     A<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項，名為`CompanyNameNamedRange`建立時，與文字\<CompanyName > 會顯示資料格中**A2**。 同時，<xref:System.Windows.Forms.BindingSource>名為`suppliersBindingSource`，資料表配接器和<xref:System.Data.DataSet>加入至專案。 控制項繫結至<xref:System.Windows.Forms.BindingSource>，它接著會繫結至<xref:System.Data.DataSet>執行個體。  
  
5.  在**資料來源**視窗中，超過在之下的資料行向下捲動**供應商**資料表。 在清單底部**產品**資料表; 這裡是因為它的子系**供應商**資料表。 選取此選項**產品**資料表，不是位於相同的層級**供應商**資料表，然後會出現下拉箭號。  
  
6.  按一下**ListObject**下拉式清單中，然後拖曳**產品**表格儲存格**A6**中`Sheet1`。  
  
     A<xref:Microsoft.Office.Tools.Excel.ListObject>控制項，名為`ProductNameListObject`建立在資料格中**A6**。 同時，<xref:System.Windows.Forms.BindingSource>名為`productsBindingSource`和資料表配接器會加入至專案。 控制項繫結至<xref:System.Windows.Forms.BindingSource>，它接著會繫結至<xref:System.Data.DataSet>執行個體。  
  
7.  僅適用 C#，請選取**suppliersBindingSource**元件匣中，以及變更**修飾詞**屬性**內部**中**屬性**視窗。  
  
## <a name="adding-controls-to-the-actions-pane"></a>將控制項加入至 [動作] 窗格  
 接下來，您必須執行窗格控制項包含下拉式方塊。  
  
#### <a name="to-add-an-actions-pane-control"></a>若要加入執行窗格控制項  
  
1.  選取**我的 Excel 執行窗格**專案中**方案總管 中**。  
  
2.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
3.  在**加入新項目**對話方塊中，選取**執行窗格控制項**，其命名**ActionsControl**，然後按一下**新增**。  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>將資料繫結 Windows Form 控制項加入執行窗格控制項  
  
1.  從**通用控制項**索引標籤的**工具箱**，拖曳<xref:System.Windows.Forms.ComboBox>執行窗格控制項的控制項。  
  
2.  變更**大小**屬性**171，21**。  
  
3.  調整大小以配合下拉式方塊的使用者控制項。  
  
## <a name="binding-the-control-on-the-actions-pane-to-data"></a>[動作] 窗格上的控制項繫結至資料  
 在本節中，您將設定資料來源的<xref:System.Windows.Forms.ComboBox>至相同的資料來源<xref:Microsoft.Office.Tools.Excel.NamedRange>工作表上的控制項。  
  
#### <a name="to-set-data-binding-properties-of-the-control"></a>若要設定控制項的資料繫結屬性  
  
1.  執行窗格控制項中，以滑鼠右鍵按一下，然後按一下 **檢視程式碼**。  
  
2.  將下列程式碼加入<xref:System.Windows.Forms.UserControl.Load>執行窗格控制項的事件。  
  
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]  
  
3.  在 C# 中，您必須建立事件處理常式`ActionsControl`。 您可以將放在這段程式碼`ActionsControl`建構函式。 如需有關如何建立事件處理常式的詳細資訊，請參閱[How to： 在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]  
  
## <a name="showing-the-actions-pane"></a>顯示 [動作] 窗格  
 [動作] 窗格不可見，直到您在執行階段加入控制項。  
  
#### <a name="to-show-the-actions-pane"></a>若要顯示 [動作] 窗格  
  
1.  在**方案總管 中**Thisworkbook.cs 或 Thisworkbook.vb，以滑鼠右鍵按一下，然後按**檢視程式碼**。  
  
2.  建立使用者控制項中的新執行個體`ThisWorkbook`類別。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]  
  
3.  在<xref:Microsoft.Office.Tools.Excel.Workbook.Startup>事件處理常式`ThisWorkbook`，將控制項加入 [動作] 窗格。  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 現在您可以測試文件，以確認動作 窗格中，開啟文件開啟時，以及控制項有主要/詳細資料關聯性。  
  
#### <a name="to-test-your-document"></a>測試文件  
  
1.  請按 F5 執行您的專案。  
  
2.  確認 [動作] 窗格已顯示。  
  
3.  選取清單方塊中的公司。 確認公司名稱會列在<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項和產品詳細資料都會列入<xref:Microsoft.Office.Tools.Excel.ListObject>控制項。  
  
4.  選取不同的公司，驗證的公司名稱，然後適當地變更產品詳細資料。  
  
## <a name="next-steps"></a>後續步驟  
 接著可以執行下列一些工作：  
  
-   資料繫結至 Word 中的控制項。 如需詳細資訊，請參閱[逐步解說： 將資料繫結至 Word 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)。  
  
-   部署專案。 如需詳細資訊，請參閱[部署 Office 方案使用 clickonce](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
## <a name="see-also"></a>請參閱  
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [如何： 管理執行窗格控制項配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  