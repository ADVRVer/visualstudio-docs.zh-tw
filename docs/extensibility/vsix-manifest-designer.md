---
title: "VSIX 資訊清單設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Sdk.VsixManifestEditor"
helpviewer_keywords: 
  - "vsixmanifest"
  - "vsix 資訊清單"
  - "資訊清單設計工具"
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# VSIX 資訊清單設計工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

修改 VSIX 封裝資訊清單檔，它可以設定 Visual Studio 擴充功能的安裝行為。  
  
 **VSIX 資訊清單設計工具** 對應至基礎 VSIX 結構描述。 在設計工具中使用對應的控制項，可以設定結構描述中的每個項目。 如需結構描述的詳細資訊，請參閱 [VSIX 擴充功能 2.0 結構描述參考](../extensibility/vsix-extension-schema-2-0-reference.md)。  
  
 若要開啟 **VSIX 資訊清單設計工具**, ，找出 source.extension.vsixmanifest 檔案中的 **方案總管\] 中**, ，然後開啟檔案。 如果檔案不包含有效的 XML，將無法開啟資訊清單設計工具。  
  
> [!NOTE]
>  Source.extension.vsixmanifest 建置套件時 extension.vsixmanifest 的輸出。  
  
## UIElement 清單  
 **VSIX 資訊清單設計工具** 包含四個區段，對應的結構描述這些最上層項目︰  
  
-   中繼資料  
  
-   安裝目標  
  
-   資產  
  
-   相依性  
  
 \[標題\] 區域包含下列控制項。  
  
 **產品名稱**  
 描述擴充功能名稱。  
  
 **產品識別碼**  
 指定此套件的唯一識別資訊。  
  
 **作者**  
 指定延伸模組的作者的名稱。  
  
 **版本**  
 指定延伸模組的版本號碼。  
  
 **中繼資料** \] 索引標籤包含下列控制項。  
  
 **描述**  
 提供擴充功能中顯示的文字描述 **擴充管理員**。  
  
 **語言**  
 指定的預設語言套件，對應到資訊清單中的文字資料。`Language` 屬性會遵循 common language runtime \(CLR\) 地區設定程式碼慣例資源組件，例如，en\-us\-我們，en，若為 fr\-fr。 根據預設，值不多不少。這表示此封裝將在 Visual Studio 的任何語言版本上執行。  
  
 **授權**  
 指定的文字檔案，其中包含使用者授權合約中，如果有的話。  
  
 **圖示**  
 指定包含要顯示在圖示的圖形檔 （.png、.bmp、.jpeg、.ico） **擴充管理員**, ，如果出現的圖示。 圖示影像必須是 32 x 32 像素為單位，或將這些維度調整大小。 如果指定的圖示， **擴充管理員** 會使用預設圖示。  
  
 **預覽影像**  
 指定包含要顯示在預覽影像的圖形檔 （.png、.bmp、.jpeg、.ico） **擴充管理員**, ，如果沒有預覽影像。 預覽影像必須是 200 x 200 像素為單位。 如果指定了沒有預覽影像， **擴充管理員** 會使用預設映像。  
  
 **標記**  
 新增要用於搜尋提示的文字標籤。  
  
 **版本資訊**  
 指定包含版本資訊的檔案 （.txt、.rtf）。 也會顯示版本資訊網站的 URL。  
  
 **使用者入門指南**  
 指定包含如何使用擴充功能或內容，在 VSIX 套件的相關資訊的檔案 （.txt、.rtf）。 擴充功能安裝完成時，會顯示本指南。 也會顯示快速入門網站的 URL。  
  
 **詳細資訊的 URL**  
 指定包含產品的其他資訊的網站 URL。  
  
 **安裝目標** \] 索引標籤包含下列控制項。  
  
 **安裝類型**  
 列出 **Visual Studio 擴充功能** 和 **擴充功能 SDK** 目標安裝類型。 選項會因您所選擇的類型而有所不同。  
  
 **Visual Studio 擴充功能**  
 列出 **InstallationTarget** 描述如何先安裝套件和此延伸模組可以安裝到 Visual Studio 產品中哪些項目。 每項產品是由名稱和版本或版本範圍單獨識別。  產品可以加入至清單、 修改和刪除。 名稱和產品的版本會對應到 **識別碼** 和 **版本** 屬性相關聯的 **InstallationTarget** 項目。  
  
 **版本範圍** 是 \[12.0，14.0\]，並使用下列標記法︰  
  
-   \[\-最小版本 （含）  
  
-   \] – 最大版本 （含）  
  
-   \(\-獨佔的最低版本  
  
-   \) – 獨佔的最大版本  
  
-   單一版本 \#\-指定的版本  
  
 **擴充功能 SDK**  
 指定不只限於特定產品和版本的全域安裝。**目標平台識別項** 是平台，例如 「 Windows 」，您的目標。**目標平台版本** 是版本，例如 8.0 的目標平台。**SDK 名稱** 和 **SDK 版本** 分別是名稱和 SDK 的版本號碼。  
  
 **此 VSIX 會針對所有使用者安裝 （需要提高權限，在安裝）** 核取方塊  
 如果選取此核取方塊，此延伸模組已安裝的所有使用者。否則，它會安裝只會針對目前的使用者。  
  
 **Windows Installer 會安裝此 VSIX** 核取方塊  
 如果選取此核取方塊，此延伸模組會安裝 Windows Installer （.msi 檔案）。否則，它會安裝為一般的 VSIX 套件 （.vsix 檔案）。  
  
 **資產** \] 索引標籤包含下列控制項。  
  
 **資產清單**  
 列出資產項目描述的擴充功能或內容的項目，此封裝的介面。 每個擴充功能或內容項目會個別列出的來源、 類型和路徑。 可以加入至清單、 修改和刪除擴充功能和內容項目。 型別和擴充功能或內容項目的路徑對應至 `Type` 和 `Path` 屬性相關聯的 `Asset` 項目。 已知下列類型︰  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 要新增或編輯資產，您必須指定資產類型中，資產是目前方案中的專案或檔案在檔案系統和專案的名稱。 您也可以指定要在其中內嵌資料夾的名稱。  
  
 您也可以建立自己的型別，並為它們提供唯一的名稱。  
  
 **相依性** \] 索引標籤包含下列控制項。  
  
 **名稱、 來源和版本範圍**  
 列出這個封裝，相依性項目也就是這個套件相依於其他封裝。 如果指定相依性套件，則它必須先安裝會安裝此封裝。否則，此套件必須安裝它。  
  
 相依性套件的指定方式識別項、 名稱、 版本範圍、 來源和相依性的解決方式。 每個相依性套件會個別列出依名稱、 版本及來源。 相依性套件可以加入至清單、 修改和刪除。  
  
 識別項必須符合 `ID` 的相依性套件中繼資料屬性。 來源可以是目前的方案、 目前已安裝的擴充功能或檔案中的專案。**的相依性解析方式** 設定可以是巢狀套件的相對路徑或相依性的下載位置的 URL。 識別碼、 版本和相依性套件的解析度對應至 `Id`, ，`Version`, ，和 `Location` 屬性相關聯的 `Dependency` 項目。  
  
## 請參閱  
 [VSIX 擴充功能 2.0 結構描述參考](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [VSIX 套件的剖析](../extensibility/anatomy-of-a-vsix-package.md)