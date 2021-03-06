---
title: "案例： 變更您的設計使用視覺化和模型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8ad4a4141d27c9250d53a567ac09b1c5ffa05f49
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>情節：使用視覺化和模型功能變更設計
請使用 Visual Studio 中的視覺化與模型工具，確定您的軟體系統符合使用者的需求。
使用 code map、 相依性圖表和類別圖表來之類的工具：  
  
 若要查看支援各項工具的 Visual Studio 版本有哪些，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
-   釐清使用者的需求與商務程序。  
  
-   探索現有程式碼並將其視覺化。  
  
-   描述現有系統的變更。  
  
-   確認系統符合其需求。  
  
-   讓程式碼與設計保持一致。  
  
 本逐步解說：  
  
-   描述這些工具如何替軟體專案帶來益處。  
  
-   不論您的開發方式為何，都能藉由範例情節來示範如何使用這些工具。  
  
 若要深入了解這些工具與其所支援情節的詳細資訊，請參閱：  
  
-   [分析架構並製作架構模型](../modeling/analyze-and-model-your-architecture.md)  
  
-   [視覺化程式碼](../modeling/visualize-code.md)  
  
##  <a name="ScenarioOverview"></a> 情節概觀  
 本情節描述兩間虛構公司 Dinner Now 與 Lucerne Publishing 在軟體開發週期所發生的事件。 Dinner Now 在西雅圖提供網站架構的餐點外送服務。 客戶可以在 Dinner Now 網站上訂餐並付款。 然後訂單便會傳送到合適的當地餐廳以準備外送。 Lucerne Publishing 是一家位在紐約的公司，營業項目涵蓋幾項網路與非網路服務。 例如，客戶可以在其經營的網站張貼對餐廳的評論。  
  
 Lucerne 最近併購 Dinner Now，並想要進行下列變更：  
  
-   在 Dinner Now 網站中加入餐廳評論功能，藉此整合雙方網站。  
  
-   將 Dinner Now 付款系統更換成 Lucerne 系統。  
  
-   將 Dinner Now 服務範圍擴展到全地區。  
  
 Dinner Now 使用的是 SCRUM 與 eXtreme 程式設計。 其測試涵蓋範圍非常大，不受支援的程式碼非常少。 會先建立小型但可運作的系統版本，然後以累加的方式加入功能，藉此將風險降到最低。 他們採取短暫且頻繁的反覆項目來開發程式碼。 這讓他們對所做的變更很有信心，也能經常重構程式碼，同時避免「預先大量設計」(Big Design Up Front)。  
  
 Lucerne 則維持一個相當大型且複雜的系統集合，其中有些系統已超過 40 年。 有鑑於舊版程式碼的複雜度及範圍，他們對變更相當地謹慎。 他們遵循更嚴格的開發程序，要求設計詳細的解決方案，並將開發期間所做的設計與變更記錄下來。  
  
 雙方小組都使用 Visual Studio 的模型圖表，協助他們開發符合使用者需求的系統。 他們使用 Team Foundation Server 搭配其他工具，協助其規劃、組織及管理工作。  
  
 如需 Team Foundation Server 的詳細資訊，請參閱：  
  
-   [計劃與追蹤工作](#PlanningTracking)  
  
-   [在經過更新的程式碼中進行測試、驗證及檢查](#TestValidateCheckInCode)  
  
##  <a name="ModelingDiagramsTools"></a> 架構與模型圖表在軟體開發的角色  
 下表描述在軟體開發週期多個及多種階段中，這些工具可以扮演的角色：  
  
||**使用者需求模型化**|**商務程序模型化**|**系統架構與設計**|**程式碼視覺化與探索**|**驗證**|  
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|  
|領域特定語言 (DSL) 圖表|[是]|是|[是]|||  
|相依性圖表中，圖層驗證|||[是]|是|[是]|  
|Code Map|||[是]|是|[是]|  
|類別設計工具 (以程式碼為基礎)||||[是]||  
  
若要繪製相依性圖表，您必須建立在現有的方案或新的模型專案。 這些圖表必須在模型專案中建立。
相依性圖表上的項目位於模型專案中，但它們不會儲存在一般模型。 由程式碼建立的 Code Map 與 .NET 類別圖表則位在模型專案之外。  
  
 請參閱：  
  
-   [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [如何：將類別圖表新增至專案 (類別設計工具)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
-   [Modeling SDK for Visual Studio - 特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
 雙方小組也會使用相依性驗證以確定開發中的程式碼保持與設計一致。  
  
 請參閱：  
  
-   [讓程式碼與設計保持一致](#ValidatingCode)  
  
-   [描述邏輯架構： 相依性圖表](#DescribeLayers)  
  
-   [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)  
  
    > [!NOTE]
    >  某些版本的 Visual Studio 支援相依性驗證和 code map 的唯讀版本用於視覺化與模型化。 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
##  <a name="UnderstandingCommunicating"></a> 了解並傳達系統的相關資訊  
 Visual Studio 模型圖表並沒有規定使用順序，所以您可以依需求或方法來加以使用。 小組在整個專案進行期間，通常會頻繁地反覆重新審視其模型。 每個圖表都具有特定優勢，可協助您了解、描述及溝通開發中系統的不同層面。  
  
 Dinner Now 及 Lucerne 在彼此溝通以及與專案關係人溝通時，會使用圖表作為其共同語言。 例如，Dinner Now 會使用圖表執行這些工作：  
  
-   將現有程式碼視覺化。  
  
-   與 Lucerne 溝通新的或已更新的使用者劇本。  
  
-   識別出支援新的或已更新的使用者劇本所必須進行的變更。  
  
 Lucerne 會使用圖表執行這些工作：  
  
-   了解 Dinner Now 的商務程序。  
  
-   了解系統的設計。  
  
-   與 Dinner Now 溝通有關新的或已更新的使用者需求。  
  
-   記錄對系統所做的更新。  
  
 圖表會與 Team Foundation Server 整合，如此小組就可以更輕鬆地規劃、管理及追蹤其工作。 例如，他們會使用模型來識別測試案例及開發工作，以及評估其工作。 Lucerne 將 Team Foundation Server 工作項目連結到模型項目，以便監控進度並確保系統符合使用者的需求。 例如，他們將使用案例連結到測試案例工作項目，如此在所有測試通過時即可知道使用案例已完成。  
  
 小組在其變更簽入之前，會驗證根據測試及設計的程式碼所執行的組建，包含相依性驗證與自動化的測試。 這樣有助於確定更新的程式碼不會與設計衝突，且不會破壞先前可運作的功能。  
  
 請參閱：  
  
-   [識別現有系統的變更](#DeterminingChanges)  
  
-   [Keeping code consistent with the design](#ValidatingCode)  
  
-   [與建立及使用模型相關的一般提示](#GeneralTips)  
  
-   [計劃與追蹤工作](#PlanningTracking)  
  
-   [在經過更新的程式碼中進行測試、驗證及檢查](#TestValidateCheckInCode)  

###  <a name="DeterminingChanges"></a> Identifying Changes to the Existing System  
 Dinner Now 必須評估符合新需求所需的成本。 這有一部分取決於此變更對系統其他部分會造成多大的影響。 為協助他們了解，Dinner Now 的其中一位開發人員從現有程式碼建立下列地圖和圖表：  
  
|**地圖或圖表**|**顯示**|  
|------------------------|---------------|  
|*Code Map*<br /><br /> 請參閱：<br /><br /> -   [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)<br />-   [瀏覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)<br />-   [藉由編輯 DGML 檔案自訂 code map](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|程式碼中的相依性及其他關聯性<br /><br /> 例如，Dinner Now 可能一開始會檢閱組件 Code Map，以取得組件及其相依性的概觀。 他們可以深入研究此地圖，以探索這些組件中的命名空間及類別。<br /><br /> Dinner Now 也可以建立地圖，以探索程式碼中的特定區域及其他種類的關聯性。 他們可以使用 [方案總管] 來尋找並選取其感興趣的區域及關聯性。|  
|*以程式碼為基礎的類別圖表*<br /><br /> 請參閱 [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)。|程式碼中的現有類別|  
  
 例如，開發人員建立了 Code Map。 接著調整其範圍以便將焦點放在新情節會影響的區域。 這些區域在地圖上會處於選取及醒目提示的狀態：  
  
 ![命名空間相依性圖形](../modeling/media/namespace_reviewsystem.png "Namespace_ReviewSystem")  
  
 **命名空間 Code Map**  
  
 開發人員展開選取的命名空間以查看其類別、方法及關聯性：  
  
 ![展開的命名空間相依性圖形](../modeling/media/dep_reviewsystem.png "Dep_ReviewSystem")  
  
 **展開的命名空間 Code Map，包含可見的跨群組連結**  
  
 開發人員檢查程式碼以找出受影響的類別及方法。 若要在每次變更時查看所產生的影響，請在每次變更後重新產生 Code Map。 請參閱[視覺化程式碼](../modeling/visualize-code.md)。  
  
 若要描述對系統其他部分 (例如元件或互動) 所造成的變更，小組可能會在白板上繪製這些項目。 他們也可能會在 Visual Studio 中繪製下列圖表，如此雙方小組皆可擷取、管理及了解詳細資料。  
  
|**圖表**|**描述**|  
|------------------|-------------------|  
|*以程式碼為基礎的類別圖表*<br /><br /> 請參閱 [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)。|程式碼中的現有類別。|  
  
###  <a name="ValidatingCode"></a> 讓程式碼與設計保持一致  
 Dinner Now 必須確定已更新的程式碼與設計保持一致。 他們建立的層級的功能描述系統中，指定允許的相依性，以及關聯的方案成品與這些圖層之間的相依性圖表。  
  
|**圖表**|**描述**|  
|-----------------|-------------------|  
|*相依性圖表*<br /><br /> 請參閱：<br /><br /> -   [從程式碼中建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [相依性圖表： 參考](../modeling/layer-diagrams-reference.md)<br />-   [相依性圖表： 指導方針](../modeling/layer-diagrams-guidelines.md)<br />-   [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)|程式碼的邏輯架構。<br /><br /> 相依性圖表會組織並將對應中的成品[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]解決方案抽象群組稱為*層*。 這些圖層可識別這些成品在系統中執行的角色、工作或功能。<br /><br /> 分層圖有助於說明系統的預定設計，以及根據該設計來驗證不斷演變的程式碼。<br /><br /> 若要建立圖層，請從 [方案總管]、[Code Map]、[類別檢視] 以及 [物件瀏覽器] 拖曳項目。 若要繪製新圖層，請使用工具箱或以滑鼠右鍵按一下圖表介面。<br /><br /> 若要檢視現有相依性，請以滑鼠右鍵按一下分層圖介面，然後按一下 [產生相依性] 。 若要指定預定的相依性，請繪製新相依性。|  
  
 例如，下列相依性圖表描述圖層與每個圖層相關聯的成品數目之間的相依性：  
  
 ![整合式的付款系統的相依性圖表](../modeling/media/layer_integrated_dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **相依性圖表**  
  
 若要確定與設計衝突不會發生在程式碼開發期間，小組的會在相依性驗證組建，會執行 Team Foundation Build 上。 它們也可以建立自訂 MSBuild 工作，需要在簽入作業中的相依性驗證。 他們會使用組建報告來收集驗證錯誤。  
  
 請參閱：  
  
-   [定義建置流程](http://msdn.microsoft.com/Library/61593e10-d24b-492f-b19a-af4d85abea6b)  
  
-   [使用閘道簽入建置流程來驗證變更](http://msdn.microsoft.com/Library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)  
  
-   [自訂建置流程範本](http://msdn.microsoft.com/Library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
###  <a name="GeneralTips"></a> General Tips for Creating and Using Models  
  
-   大部分的圖表是由以線條連結之節點所組成。 針對每個圖表類型，工具箱會提供不同種類的節點及線條。  
  
     若要開啟工具箱，請在 [檢視]  功能表上按一下 [工具箱] 。  
  
-   若要建立節點，請將其從工具箱拖曳到圖表。 特定種類的節點必須拖曳到現有節點上。 例如，在元件圖表上，必須將新連接埠加入現有元件中。  
  
-   若要建立線條或是連接，請在工具箱中依序按一下適當的工具、來源節點以及目標節點。 某些線條只能在特定種類的節點之間建立。 當您將指標移到可能的來源或目標上，指標就會指出您是否可以建立連接。  
  
###  <a name="PlanningTracking"></a> Planning and Tracking Work  
 Visual Studio 模型圖表已經與 Team Foundation Server 整合，以便您可以更輕鬆地計畫、管理及追蹤工作。 兩個小組都使用模型來識別測試案例及開發工作，以及評估其工作。 Lucerne 建立 Team Foundation Server 工作項目並將其連結到模型項目，例如使用案例或元件。 這樣可協助他們監視進度及針對使用者需求追蹤工作。 也可協助他們確定所做的變更能持續符合這些需求。  
  
 當工作進行時，小組會更新工作項目以反映實際花在工作上的時間。 他們也會使用下列 Team Foundation Server 功能來監視及報告工作狀態：  
  
-   每日 *「待執行工作報表」* (Burndown Report)，此報表會顯示他們是否會在預定時間內完成計劃的工作。 他們會從 Team Foundation Server 產生其他類似的報表來追蹤 Bug 進度。  
  
-   *「反覆項目工作表」* (Iteration Worksheet)，此工作表使用 Microsoft Excel 協助小組監視及平衡小組成員間的工作量。 此工作表連結到 Team Foundation Server，並在定期進度會議中提供討論重點。  
  
-   *「開發儀表板」* (Development Dashboard)，此儀表板使用 Office Project 讓小組隨時獲知重要的專案資訊。  
  
 請參閱：  
  
-   [使用 Visual Studio Team Services 或 Team Foundation Server 來追蹤工作](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)  
  
-   [Visual Studio ALM 的圖表、儀表板和報表](http://msdn.microsoft.com/Library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)  
  
-   [使用 Project 建立您的待處理項目和工作](http://msdn.microsoft.com/Library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)  
  
###  <a name="TestValidateCheckInCode"></a> 在程式碼中進行測試、驗證及檢查  
 當小組完成每項工作時，他們會將程式碼簽入至 Team Foundation 版本控制，如果忘了這麼做，則會收到 Team Foundation Server 的提醒。 Team Foundation Server 接受簽入之前，小組會執行單元測試和相依性驗證來驗證針對測試案例及設計程式碼。 他們使用 Team Foundation Server 來執行組建、 自動化的單元測試，以及定期相依性驗證。 此行為有助於確定程式碼符合下列準則：  
  
-   這麼做確實有成效。  
  
-   不會破壞先前運作的程式碼。  
  
-   不會與設計衝突。  
  
 Dinner Now 擁有大型自動化測試集合，因為這些測試幾乎仍適用，所以 Lucerne 可重複使用。 Lucerne 也可以根據這些測試進行建置，並加入新測試以涵蓋新功能。 同時也會使用 Visual Studio 執行手動測試。  
  
 若要確定程式碼符合設計，小組會設定其組建以包含相依性驗證 Team Foundation Build 中。 如果發生任何衝突，則會產生包含詳細資料的報表。  
  
 請參閱：  
  
-   [測試應用程式](https://www.visualstudio.com/docs/test/overview)  
  
-   [在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)  
  
-   [使用版本控制](http://go.microsoft.com/fwlink/?LinkID=525605)  
  
-   [建置及發行](/vsts/build-release/index)  
  
##  <a name="UpdatingSystem"></a> Updating the System Using Visualization and Modeling  
 Lucerne 及 Dinner Now 必須整合其付款系統。 下列各節將示範 Visual Studio 中的模型圖表如何協助其執行這項工作：  
  
-   [將現有程式碼視覺化：Code Map](#VisualizeCode)  
  
-   [定義類型的詞彙：類別圖表](#DefineClasses)  
  
-   [描述邏輯架構： 相依性圖表](#DescribeLayers)  
  
 請參閱：  
  
-   [視覺化程式碼](../modeling/visualize-code.md)  
  
-   [在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)  
  
-   [建立應用程式架構的模型](../modeling/model-your-app-s-architecture.md)  
 
###  <a name="VisualizeCode"></a> 將現有程式碼視覺化：Code Map  
 Code Map 顯示程式碼的目前組織及關聯性。 項目在地圖上是以 *「節點」* (Node) 來代表，關聯性則是以 *「連結」*(Link) 來代表。 Code Map 可協助您執行下列種類的工作：  
  
-   探索不熟悉的程式碼。  
  
-   了解提議的變更可能會影響現有程式碼的哪些部分以及影響的方式。  
  
-   尋找複雜度、 自然的相依性或模式，或是從改進獲益的其他區域。  
  
 例如，Dinner Now 必須評估更新 PaymentProcessing 元件所需的成本。 這有一部分取決於此變更對系統其他部分會造成多大的影響。 為協助他們了解，Dinner Now 開發人員從程式碼產生 Code Map，並將範圍焦點調整在可能受變更影響的區域：  
  
 下列地圖顯示 PaymentProcessing 類別及 Dinner Now 系統其他部分之間的相依性，其以選取狀態顯示：  
  
 ![Dinner Now 付款系統相依性圖形](../modeling/media/dep_dnpayment.png "Dep_DNPayment")  
  
 **Dinner Now 付款系統的 Code Map**  
  
 開發人員展開 PaymentProcessing 類別並選取其成員以探索地圖，進而查看可能受影響的區域。  
  
 ![PaymentProcessing 和相依性內部的方法](../modeling/media/depgraph_expandeddn.png "DepGraph_ExpandedDN")  
  
 **PaymentProcessing 類別內部方法及其相依性**  
  
 他們針對 Lucerne 付款系統產生下列地圖以查看其類別、方法與相依性。 小組發現 Lucerne 系統可能也需要處理，以與 Dinner Now 系統其他部分互動：  
  
 ![Lucerne 付款系統相依性圖形](../modeling/media/depgraph_lucernepay.png "DepGraph_LucernePay")  
  
 **Lucerne 付款系統的 Code Map**  
  
 雙方小組一塊合作，判斷整合雙方系統所需進行的變更。 他們決定重構部分程式碼，以方便進行更新。 PaymentApprover 類別將移到 DinnerNow.Business 命名空間，且需要一些新方法。 處理交易的 Dinner Now 類別將擁有自己的命名空間。 小組建立並使用工作項目以規劃、組織及追蹤工作。 他們將工作項目連結到對模型項目有用之處。  
  
 在重新組織程式碼之後，小組產生新的 Code Map 來查看已更新的結構及關聯性：  
  
 ![已重新組織程式碼的相依性圖形](../modeling/media/depgraph_integrated.png "DepGraph_Integrated")  
  
 **程式碼已重新組織過的 Code Map**  
  
 此地圖顯示 PaymentApprover 類別目前已位於 DinnerNow.Business 命名空間中，且具有一些新方法。 Dinner Now 交易類別現在已擁有自己的 PaymentSystem 命名空間，之後處理該程式碼會變得更容易。  
  
#### <a name="creating-a-code-map"></a>建立 Code Map  
  
-   如需快速取得原始程式碼的概觀，請遵循這些步驟來產生 Code Map：  
  
     在 [架構]  功能表上，按一下 [產生方案的 Code Map] 。  
  
     若要快速取得已編譯程式碼的概觀，請建立空白的 Code Map，然後將組件檔或二進位檔拖曳到地圖介面上。  
  
-   若要探索特定程式碼或方案項目，請使用 [方案總管] 來選取想要視覺化的項目及關聯性。 然後您可以產生新地圖，或將所選項目加入現有地圖中。 請參閱[對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)。  
  
-   為了協助您探索地圖，請重新整理配置，以便其符合您要執行的工作種類。  
  
     例如，若要將程式碼的圖層視覺化，請選取樹狀配置。 請參閱[瀏覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)。  
  
#### <a name="summary-strengths-of-code-maps"></a>摘要：Code Map 的優勢  
 Code Map 可協助您：  
  
-   深入了解現有程式碼的組織及關聯性。  
  
-   識別所提議的變更可能影響的區域。  
  
-   尋找複雜度、模式、圖層的區域，或可加以改善而讓程式碼更易於維護、變更及重複使用的其他區域。  
  
#### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性  
  
|**圖表**|**描述**|  
|-----------------|-------------------|  
|相依性圖表|系統的邏輯架構。 使用相依性驗證以確定程式碼保持與設計一致。<br /><br /> 若要易於識別現有 dependencys 或預期的 dependencys，請建立 code map 並相關項目分組。 若要建立相依性圖表，請參閱：<br /><br /> -   [從程式碼中建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [相依性圖表： 指導方針](../modeling/layer-diagrams-guidelines.md)|  
|類別圖表 (以程式碼為基礎)|特定專案程式碼中的現有類別。<br /><br /> 若要修改程式碼中的現有類別並將其視覺化，請使用 [類別設計工具]。<br /><br /> 請參閱 [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)。|  
  
###  <a name="DefineClasses"></a> 定義類型的詞彙：類別圖表  
 類別圖表定義參與系統的實體、詞彙或概念，以及彼此的關聯性。 例如，您可以在開發期間使用這些圖表來描述每個類別的屬性及作業，不論其實作語言或樣式為何。  
  
 為了協助 Lucerne 描述及討論參與「處理付款」使用案例的實體，他們繪製了下列類別圖表：  
  
 ![處理付款 」 實體類別圖表上的](../modeling/media/uml_payentities.png "UML_PayEntities")  
  
 **類別圖表上的「處理付款」實體**  
  
 此圖表顯示「客戶」可以有多個訂單及不同的付款方式。 BankAccount 與 CreditCard 都繼承自 Payment。  
  
 在開發期間，Lucerne 使用下列類別圖表來描述及討論每個類別的詳細資料：  
  
 ![處理付款 」 實體詳細資料在類別圖表上的](../modeling/media/uml_payment.png "UML_Payment")  
  
 **類別圖表上的「處理付款」詳細資料**  
    
#### <a name="drawing-a-class-diagram"></a>繪製類別圖表  
 類別圖表具有下列主要功能：  
  
-   類型，例如類別、介面及列舉：  
  
    -   *「類別」* (Class) 是物件的定義，而這些物件共用特定的結構或行為特性。  
  
    -   *「介面」* (Interface) 會定義物件外部可見行為的一部分。  
  
    -   *「列舉」* (Enumeration) 是包含常值清單的分類器。  
  
-   *「屬性」* (Attribute) 是特定類型的值，其描述 *「分類器」*(Classifier) 的每個執行個體。 分類器是類型、元件、使用案例的一般名稱，甚至是執行者的一般名稱。  
  
-   *「作業」* (Operation) 是分類器執行個體可以執行的方法或函式。  
  
-   *「關聯」* (Association) 表示兩個分類器之間的某種關聯性。  
  
    -   *「彙總」* (Aggregation) 是一種關聯，表示兩個分類器之間的共用擁有權。  
  
    -   *「組合」* (Composition) 是一種關聯，表示兩個分類器之間的整體-部分關聯性。  
  
     若要顯示彙總或組合，請在關聯上設定 **彙總** 屬性。 **共用** 顯示彙總， **組合** 則顯示組合。  
  
-   *「相依性」* (Dependency) 表示若變更某個分類器的定義，可能會變更另一個分類器的定義。  
  
-   *「一般化」* (Generalization) 表示特定分類器的部分定義繼承自一般分類器。 *「實現」* (Realization) 表示類別實作介面提供的作業及屬性。  
  
     若要建立這些關聯性，請使用 [繼承]  工具。 另外，實現可以用 *「棒棒糖符號」*(Lollipop) 表示。  
  
-   *「封裝」* (Package) 是分類器、關聯、生命線、元件及其他封裝的群組。 *「匯入」* (Import) 關聯性表示某個封裝包含另一個封裝的所有定義。  
  
 您可以使用 [類別設計工具] 從程式碼建立類別圖，來開始探索及討論現有類別。  
  
-   [如何：將類別圖表新增至專案 (類別設計工具)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
#### <a name="summary-strengths-of-class-diagrams"></a>摘要：類別圖表的優勢  
 類別圖表可協助您定義下列項目：  
  
-   討論使用者需求及參與系統的實體時可使用的常用詞彙。 請參閱[模型使用者需求](../modeling/model-user-requirements.md)。  
  
-   系統組成部分 (例如元件) 使用的類型，不論其實作為何。 請參閱[您的應用程式架構模型](../modeling/model-your-app-s-architecture.md)。  
  
-   類型之間的關聯性 (例如相依性)。 例如，您可以顯示某個類型可以與另一個類型的多個執行個體相關聯。  
  
#### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性  
  
|**圖表**|**描述**|  
|-----------------|---------------------|  
|相依性圖表|定義與類別相關的系統邏輯架構。<br /><br /> 使用相依性驗證以確定程式碼保持與設計一致。<br /><br /> 請參閱：<br /><br /> -   [從程式碼中建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [相依性圖表： 參考](../modeling/layer-diagrams-reference.md)<br />-   [相依性圖表： 指導方針](../modeling/layer-diagrams-guidelines.md)<br />-   [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)|  
|Code Map|將現有程式碼中的組織與關聯性視覺化。<br /><br /> 若要識別類別、其關聯性及方法，請建立會顯示這些項目的 Code Map。<br /><br /> 請參閱：<br /><br /> -   [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)|  
  
###  <a name="DescribeLayers"></a>描述邏輯架構： 相依性圖表  
 相依性圖表描述系統的邏輯架構方案中的成品組織成抽象群組，或*層*。 成品可以是多個項目，例如命名空間、專案、類別、方法等等。 圖層代表及描述成品在系統中執行的角色或工作。 您也可以在組建中加入圖層驗證並簽入作業，以確定程式碼與設計維持一致。  
  
 若要讓程式碼與設計一致，Dinner Now 及 Lucerne 會使用下列相依性圖表來驗證演變的程式碼：  
  
 ![整合式的付款系統的相依性圖表](../modeling/media/layer_integrated_dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **描述 Dinner now 與 Lucerne 整合的相依性圖表**  
  
 這個圖表上的圖層會連結到對應的 Dinner Now 及 Lucerne 方案成品。 例如，商務圖層會連結到 DinnerNow.Business 命名空間及其成員，其目前已包含 PaymentApprover 類別。 資源存取圖層會連結到 DinnerNow.Data 命名空間。 箭號 (也就是 *「相依性」*(Dependency)) 會指定只有商務圖層可以使用位於資源存取圖層中的功能。 小組在更新程式碼時，圖層驗證會定期執行，以便在發生衝突時加以攔截，並協助小組立即解決衝突。  
  
 小組共同合作，以逐步進行整合並測試這兩個系統。 他們首先確定 PaymentApprover 與 Dinner Now 其餘部分彼此可順利運作，才會處理 PaymentProcessing。  
  
 下列 Code Map 顯示 Dinner Now 及 PaymentApprover 之間的新呼叫：  
  
 ![與整合的系統更新的相依性圖形](../modeling/media/depgraph_intsystem.png "DepGraph_IntSystem")  
  
 **內含已更新方法呼叫的 Code Map**  
  
 在確定系統如預期運作之後，Dinner Now 會將 PaymentProcessing 程式碼註解化。 圖層驗證報表結果無誤，且產生的 Code Map 顯示沒有任何 PaymentProcessing 相依性存在：  
  
 ![未含 PaymentProcessing 的相依性圖形](../modeling/media/depgraph_nomore.png "DepGraph_NoMore")  
  
 **未含 PaymentProcessing 的 Code Map**  
  
#### <a name="drawing-a-dependency-diagram"></a>繪製相依性圖表  
 相依性圖表具有下列主要功能：  
  
-   *「圖層」* (Layer) 描述成品的邏輯群組。  
  
-   *「連結」* (Link) 是圖層與成品之間的關聯。  
  
     若要從成品建立圖層，請從 [方案總管]、[Code Map]、[類別檢視] 或 [物件瀏覽器] 拖曳項目。 若要繪製新圖層再連結到成品，請使用工具箱或以滑鼠右鍵按一下圖表介面以建立圖層，然後將項目拖曳到這些圖層。  
  
     圖層上的數字會顯示圖層連結的成品數目。 這些成品可以是命名空間、專案、類別、方法等等。 當您解譯圖層上的成品數目時，請記住下列事項：  
  
    -   如果圖層連結的成品有包含其他成品，但圖層未直接連結這些其他成品，則數字將只包含連結的成品。 然而，在圖層驗證期間會加入其他成品以進行分析。  
  
         例如，如果圖層連結到單一命名空間，即使命名空間包含類別，連結的成品數目仍為 1。 如果圖層也有命名空間中每個類別的連結，則數字將包含這些已連結的類別。  
  
    -   如果圖層包含已連結到成品的其他圖層，即使此容器圖層上的數字未包含那些成品，容器圖層也會連結到那些成品。  
  
     若要查看連結至圖層的成品，相依性，以滑鼠右鍵按一下，然後按一下 **檢視連結**開啟**圖層總管**。  
  
-   *「相依性」* (Dependency) 表示某個圖層可以使用另一個圖層中的功能，但反過來則不行。 *「雙向相依性」* (Bidirectional Dependency) 表示某個圖層可以使用另一個圖層中的功能，反之亦然。  
  
     若要在相依性圖表上顯示現有相依性，以滑鼠右鍵按一下圖表介面，然後**產生相依性**。 若要描述預定的相依性，請繪製新的相依性。  
  
 請參閱：  
  
-   [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [相依性圖表︰參考](../modeling/layer-diagrams-reference.md)  
  
-   [相依性圖表︰方針](../modeling/layer-diagrams-guidelines.md)  
  
-   [使用相依性圖表驗證程式碼](../modeling/validate-code-with-layer-diagrams.md)  
  
#### <a name="summary-strengths-of-dependency-diagrams"></a>摘要： 相依性圖表的優勢  
 相依性圖表，可協助您：  
  
-   根據成品功能描述系統的邏輯架構。  
  
-   確保開發中的程式碼符合指定的設計。  
  
#### <a name="relationship-to-other-diagrams"></a>與其他圖表的關聯性  
  
|**圖表**|**描述**|  
|-----------------|---------------------|  
|Code Map|將現有程式碼中的組織與關聯性視覺化。<br /><br /> 若要建立圖層，請產生 Code Map，然後在地圖上將項目分組為可能的圖層。 將群組從地圖拖曳到相依性圖表。<br /><br /> 請參閱：<br /><br /> -   [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)<br />-   [瀏覽和重新排列 code map](../modeling/browse-and-rearrange-code-maps.md)|  
  
## <a name="external-resources"></a>外部資源  
  
|**分類**|**Links**|  
|------------------|---------------|  
|**論壇**|-   [Visual Studio Visualization & Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL 工具)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>另請參閱

[將程式碼視覺化](../modeling/visualize-code.md)   
[在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)   
[在敏捷式開發中使用模型](http://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)   
[在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)
 
