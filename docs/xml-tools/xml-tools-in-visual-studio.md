---
title: "Visual Studio 中的 XML 工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.xmldesigner"
helpviewer_keywords: 
  - "類別 [Visual Studio], XML"
  - "CSS, XML 的樣式表"
  - "資料 [Visual Studio], XML"
  - "資料集 [Visual Basic], XML 結構描述"
  - "探索檔, XML"
  - "企業樣板, XML 和"
  - "伺服器控制項, XML 和"
  - "SGML, XML"
  - "樣式表, XML"
  - "Web 伺服器控制項, XML"
  - "Web 服務"
  - "XML [Visual Studio]"
  - "XML [Visual Studio], .NET Framework 類別"
  - "XML [Visual Studio], 資料來源"
  - "XML [Visual Studio], 資源"
  - "XML [Visual Studio], SGML 的關聯"
  - "XML 結構描述"
  - "XMLDataDocument 類別"
  - "XSD 結構描述"
  - "XSL"
  - "XSL, 樣式表"
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual Studio 中的 XML 工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*「可延伸標記語言」*\(Extensible Markup Language，XML\) 是一種標記語言，提供描述資料的格式。  這種語言可以協助在多個平台之間更精確地宣告內容，以及提供更有意義的搜尋結果。  此外，XML 可將資料的呈現方式與資料本身分開。  例如在 HTML 中，您可以使用標記來指示瀏覽器以粗體或斜體顯示資料，但在 XML 中，您只能使用標記來描述資料，例如城市名稱、溫度和氣壓。  在 XML 中，您可以使用可延伸樣式表語言 \(XSL\) 和階層式樣式表 \(CSS\) 等樣式表，在瀏覽器中呈現資料。  XML 可將資料的呈現方式和處理分開。  這讓您可以套用不同的樣式表和應用程式，以您想要的方式來顯示及處理資料。  
  
 XML 是 SGML 的子集，已針對在網路上傳送進行最佳化。  它是由全球資訊網協會 \(W3C\) 所定義。  這項標準可確保結構化資料一致，並與應用程式或廠商無關。  
  
 XML 是許多 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 功能的核心。  下列主題列出 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 所提供之與 XML 相關的工具和功能名稱。  
  
 如需詳細資訊，請參閱 [XML 開發人員中心](http://go.microsoft.com/fwlink/?LinkID=100176)，其中提供適用於 XML 開發人員的最新文件、技術資訊、下載、新聞群組和其他資源。  
  
## 在本節中  
 [使用 XML 資料](../xml-tools/working-with-xml-data.md)  
 討論 XML 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之資料處理方式中所扮演的角色。  
  
 [偵錯 XSLT](../xml-tools/debugging-xslt.md)  
 提供使用 Visual Studio 偵錯工具來偵錯 XSLT 的主題連結。  
  
## 參考  
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
 針對任何 XML 文件，透過 [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) 公開 [XML 編輯器](http://go.microsoft.com/fwlink/?LinkId=228249)剖析樹狀目錄。  
  
 [XML 標準參考](http://msdn.microsoft.com/zh-tw/79c78508-c9d0-423a-a00f-672e855de401)  
 提供 XML 技術的資訊，包括 XML、文件類型定義 \(DTD\)、XML 結構描述定義語言 \(XSD\) 和 XSLT。  
  
 <xref:System.Xml?displayProperty=fullName>  
 說明 <xref:System.Xml> 命名空間的組成類別和其他項目，並且提供每個項目的詳細資訊連結。  
  
 <xref:System.Xml.Serialization?displayProperty=fullName>  
 說明 <xref:System.Xml.Serialization> 命名空間的組成類別和其他項目，並且提供每個項目的詳細資訊連結。  
  
## 相關章節  
 [XML 文件物件模型 \(DOM\)](../Topic/XML%20Document%20Object%20Model%20\(DOM\).md)  
 說明 <xref:System.Xml.XmlDocument> 及其相關類別如何符合 W3C 文件物件模型 \(核心\) 層級 1 和層級 2 命名空間支援規格。  
  
 [Reading XML with the XmlReader](http://msdn.microsoft.com/zh-tw/3029834c-a27e-4331-b7aa-711924062182)  
 說明 <xref:System.Xml.XmlReader> 如何在 XML 資料流上提供非快取、順向、唯讀的 XML 資料存取。  
  
 [Writing XML with the XmlWriter](http://msdn.microsoft.com/zh-tw/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)  
 說明 <xref:System.Xml.XmlWriter> 如何以非快取、順向的方式產生 XML 資料流，並且協助您建置符合 W3C 標準的 XML 文件。  
  
 [XSLT 轉換](../Topic/XSLT%20Transformations.md)  
 說明 <xref:System.Xml.Xsl.XslCompiledTransform> 類別如何實作 XSLT 1.0 建議。  
  
 [使用 XPath 資料模型處理 XML 資料](../Topic/Process%20XML%20Data%20Using%20the%20XPath%20Data%20Model.md)  
 說明 <xref:System.Xml.XPath.XPathNavigator> 類別如何處理儲存在 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中的 XML 資料。  <xref:System.Xml.XPath.XPathNavigator> 類別以 XQuery 1.0 和 XPath 2.0 資料模型為基礎，可用以巡覽和編輯 XML 資料。  
  
 [XML 結構描述物件模型 \(SOM\)](../Topic/XML%20Schema%20Object%20Model%20\(SOM\).md)  
 說明用於建立及操作 XML 結構描述的類別，方法是提供 <xref:System.Xml.Schema.XmlSchema> 類別來載入及編輯結構描述。