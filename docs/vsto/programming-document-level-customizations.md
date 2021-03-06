---
title: "文件層級自訂程式設計 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a614173fc33547c3512c031b7e0bd8a5575e7cb2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="programming-document-level-customizations"></a>文件層級自訂程式設計
  當您使用文件層級自訂擴充 Microsoft Office Word 或 Microsoft Office Excel 時，可以執行下列工作：  
  
-   使用物件模型自動化應用程式。  
  
-   將控制項加入文件介面。  
  
-   從自訂組件呼叫文件中的 Visual Basic for Applications (VBA) 程式碼。  
  
-   從 VBA 呼叫自訂組件中的程式碼。  
  
-   在文件位於未安裝 Microsoft Office 的伺服器上時，管理文件的特定層面。  
  
-   自訂應用程式的使用者介面 (UI)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 在文件層級專案中撰寫程式碼時，某些方面會與 Visual Studio 中其他類型的專案不同。 其中有許多差異的原因來自於將 Office 物件模型公開給 Managed 程式碼的方式。 如需詳細資訊，請參閱 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)。  
  
 一般您可以使用 Visual Studio 中的 Office 開發工具建立文件層級自訂和其他類型方案的相關資訊，請參閱[Office 方案開發概觀 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="using-the-generated-classes-in-document-level-projects"></a>使用文件層級專案中產生的類別  
 當您建立文件層級專案時，Visual Studio 會自動在專案中產生類別，供您開始撰寫程式碼。 Visual Studio 會針對 Word 和 Excel 產生不同的類別：  
  
-   在 Word 的文件層級專案中，類別預設名為 `ThisDocument` 。  
  
-   Excel 的文件層級專案具有多個產生的類別：一個用於活頁簿本身，一個用於每個工作表。 根據預設，這些類別具有下列名稱：  
  
    -   `ThisWorkbook`  
  
    -   `Sheet1`  
  
    -   `Sheet2`  
  
    -   `Sheet3`  
  
 產生的類別包含會在開啟或關閉文件時呼叫的事件處理常式。 若要在開啟文件時執行程式碼，請將程式碼加入 `Startup` 事件處理常式。 若要在文件關閉之際執行程式碼，請將程式碼加入 `Shutdown` 事件處理常式。 如需詳細資訊，請參閱 [Deploying Office Solutions](../vsto/events-in-office-projects.md)。  
  
### <a name="understanding-the-design-of-the-generated-classes"></a>了解產生之類別的設計  
 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]為目標的專案中， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的主項目類型是介面，因此，產生的類別無法從中衍生實作。 相反地，產生的類別會改從下列基底類別衍生大部分的成員：  
  
-   `ThisDocument`：衍生自 <xref:Microsoft.Office.Tools.Word.DocumentBase>。  
  
-   `ThisWorkbook`：衍生自 <xref:Microsoft.Office.Tools.Excel.WorkbookBase>。  
  
-   `Sheet` *n*：衍生自 <xref:Microsoft.Office.Tools.Excel.WorksheetBase>。  
  
 這些基底類別會將所有成員的呼叫重新導向至 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]中與其對應之主項目介面的內部實作。 例如，如果呼叫 <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> 類別的 `ThisDocument` 方法， <xref:Microsoft.Office.Tools.Word.DocumentBase> 類別會將此呼叫重新導向至 <xref:Microsoft.Office.Tools.Word.Document> 中 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]介面的內部實作。  
  
## <a name="accessing-the-object-model-of-the-host-application"></a>存取主應用程式的物件模型  
 若要存取主應用程式的物件模型，請使用專案中產生之類別的成員。 這些類別各自對應至 Excel 或 Word 物件模型中的一個物件，並且大多包含相同的屬性、方法和事件。 例如，Word 文件層級專案中 `ThisDocument` 類別與 Word 物件模型中的 <xref:Microsoft.Office.Interop.Word.Document> 物件提供的成員大部分相同。  
  
 下列程式碼範例示範如何使用 Word 物件模型儲存屬於 Word 文件層級自訂一部分的文件。 這個範例適合從 `ThisDocument` 類別執行。  
  
```vb  
Me.Save()  
```  
  
```csharp  
this.Save();  
```  
  
 若要從 `ThisDocument` 類別外執行相同的動作，請使用 `Globals` 物件存取 `ThisDocument` 類別。 例如，如果您要在執行窗格 UI 中包含 [儲存]  按鈕，可以將這個程式碼加入執行窗格程式碼檔案。  
  
```vb  
Globals.ThisDocument.Save()  
```  
  
```csharp  
Globals.ThisDocument.Save();  
```  
  
 因為 `ThisDocument` 類別會從 <xref:Microsoft.Office.Tools.Word.Document> 主項目取得大部分成員，所以這個程式碼中呼叫的 `Save` 方法實際上是 <xref:Microsoft.Office.Tools.Word.Document.Save%2A> 主項目的 <xref:Microsoft.Office.Tools.Word.Document> 方法。 這個方法對應至 Word 物件模型中 <xref:Microsoft.Office.Interop.Word._Document.Save%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Document> 方法。  
  
 如需使用 Word 和 Excel 物件模型的詳細資訊，請參閱 [Word Object Model Overview](../vsto/word-object-model-overview.md) 和 [Excel Object Model Overview](../vsto/excel-object-model-overview.md)。  
  
 如需有關`Globals`物件，請參閱[全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。  
  
## <a name="adding-controls-to-documents"></a>將控制項加入文件  
 若要自訂文件的 UI，您可以將 Windows Forms 控制項或 *「主控制項」* (host control) 加入文件介面。 藉由結合不同組的控制項並撰寫程式碼，您可以將控制項繫結至資料、從使用者收集資訊，以及回應使用者動作。  
  
 主控制項是一種會擴充 Word 和 Excel 物件模型中某些物件的類別。 例如， <xref:Microsoft.Office.Tools.Excel.ListObject> 主控制項會提供 Excel 中 <xref:Microsoft.Office.Interop.Excel.ListObject> 的所有功能。 但是， <xref:Microsoft.Office.Tools.Excel.ListObject> 主控制項還多了一些事件和資料繫結功能。  
  
 如需詳細資訊，請參閱 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) 與 [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
## <a name="combining-vba-and-document-level-customizations"></a>合併 VBA 和文件層級自訂  
 您可以在屬於文件層級自訂一部分的文件中使用 VBA 程式碼。 您可以從自訂組件呼叫文件中的 VBA 程式碼，也可以將專案設定為允許文件中的 VBA 程式碼呼叫自訂組件中的程式碼。  
  
 如需詳細資訊，請參閱 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)。  
  
## <a name="managing-documents-on-a-server"></a>管理伺服器上的文件  
 您可以在未安裝 Microsoft Office Word 或 Microsoft Office Excel 的伺服器上管理文件層級自訂的數個不同層面。 例如，您可以存取及修改文件之資料快取中的資料。 您也可以管理與文件相關聯的自訂組件。 例如，您可以用程式設計的方式從文件中移除組件，讓文件不再執行程式碼，或者用程式設計的方式將組件附加至文件。  
  
 如需詳細資訊，請參閱 [Managing Documents on a Server by Using the ServerDocument Class](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)。  
  
## <a name="customizing-the-user-interface-of-microsoft-office-applications"></a>自訂 Microsoft Office 應用程式的使用者介面  
 您可以使用文件層級自訂，透過下列方式自訂 Word 和 Excel 的 UI：  
  
-   將主控制項或 Windows Forms 控制項加入文件介面。  
  
     如需詳細資訊，請參閱 [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)、 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)和 [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
-   在文件中加入執行窗格。  
  
     如需詳細資訊，請參閱 [Actions Pane Overview](../vsto/actions-pane-overview.md)。  
  
-   在功能區中新增自訂索引標籤。  
  
     如需詳細資訊，請參閱[功能區概觀](../vsto/ribbon-overview.md)。  
  
-   將自訂群組新增至功能區上的內建索引標籤。  
  
     如需詳細資訊，請參閱 [How to: Customize a Built-in Tab](../vsto/how-to-customize-a-built-in-tab.md)。  
  
 如需有關自訂的 Microsoft Office 應用程式 UI 的詳細資訊，請參閱[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
## <a name="getting-extended-objects-from-native-office-objects-in-document-level-customizations"></a>在文件層級自訂中，取得從原生 Office 物件擴充的物件  
 Office 事件的多數事件處理常式都會接收代表引發事件之活頁簿、工作表或文件的原生 Office 物件。 某些情況下，您可能只有在文件層級自訂的活頁簿或文件引發事件時，才想要執行一些程式碼。 例如，使用 Excel 的文件層級自訂時，您可能想要在使用者啟動自訂活頁簿內其中一個工作表時執行一些程式碼，但不要在使用者啟動某個恰巧同時開啟之其他活頁簿內的工作表時執行程式碼。  
  
 當您有原生 Office 物件時，可以測試該物件是否已擴充成為文件層級自訂中的 *「主項目」* (host item) 或 *「主控制項」* (host control)。 主項目和主控制項是 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 提供的類型，這些類型可將功能加入原本就存在於 Word 或 Excel 物件模型的物件，稱為 *「原生 Office 物件」*(native Office object)。 通常，主項目和主控制項也稱為 *「擴充物件」*(extended object)。 如需主項目和主控制項的詳細資訊，請參閱 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
## <a name="understanding-the-getvstoobject-and-hasvstoobject-methods"></a>了解 GetVstoObject 和 HasVstoObject 方法  
 若要測試的原生 Office 物件，使用 HasVstoObject 和 GetVstoObject 方法在專案中：  
  
-   如果您想要判斷原生 Office 物件是否具有擴充的物件，在自訂中，請使用 HasVstoObject 方法。 如果原生 Office 物件具有擴充物件，這個方法會傳回 **true** 否則傳回 **false** 。  
  
-   如果您想要取得原生 Office 物件擴充的物件，請使用 GetVstoObject 方法。 如果指定的原生 Office 物件具有擴充物件，這個方法會傳回 <xref:Microsoft.Office.Tools.Excel.ListObject>、 <xref:Microsoft.Office.Tools.Excel.Workbook>、 <xref:Microsoft.Office.Tools.Excel.Worksheet>或 <xref:Microsoft.Office.Tools.Word.Document> 物件。 反之則傳回 GetVstoObject **null**。 GetVstoObject 方法會傳回例如<xref:Microsoft.Office.Tools.Word.Document>如果指定<xref:Microsoft.Office.Interop.Word.Document>是 Word 文件專案中文件的基礎物件。  
  
 在文件層級專案中，您無法使用 GetVstoObject 方法來建立新的<xref:Microsoft.Office.Tools.Excel.Workbook>， <xref:Microsoft.Office.Tools.Excel.Worksheet>，或<xref:Microsoft.Office.Tools.Word.Document>主項目，在執行階段。 您只能使用這個方法來存取在設計階段產生於專案中的現有主項目。 如果您想要在執行階段建立新的主項目，則必須開發 VSTO 增益集專案。 如需詳細資訊，請參閱 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) 與 [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
## <a name="using-the-getvstoobject-and-hasvstoobject-methods"></a>使用 GetVstoObject 和 HasVstoObject 方法  
 若要呼叫 HasVstoObject 和 GetVstoObject 方法時，使用的 Globals.Factory.GetVstoObject 或 Globals.Factory.HasVstoObject 方法並傳入原生 Word 或 Excel 物件 (例如<xref:Microsoft.Office.Interop.Word.Document>或<xref:Microsoft.Office.Interop.Excel.Worksheet>) 您想要測試。  
  
## <a name="see-also"></a>請參閱  
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [使用 ServerDocument 類別管理伺服器上的文件](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  