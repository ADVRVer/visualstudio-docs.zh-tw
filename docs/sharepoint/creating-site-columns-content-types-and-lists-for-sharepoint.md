---
title: "建立 SharePoint 的網站資料行、 內容類型和清單 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.ListDesigner.ContentTypeSetting
- VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage
- VS.SharePointTools.ListDesigner.CreatingLists
- VS.SharePointTools.ListDesigner.ListPage
- VS.SharePointTools.ListDesigner.ViewPage
- VS.SharePointTools.ListDesigner.CommonPropertiesPage
- VS.SharePointTools.ContentTypeDesigner.ColumnsPage
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6f6ca2ad09bd41206873045f9eeb26b5e590a049
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="creating-site-columns-content-types-and-lists-for-sharepoint"></a>建立 SharePoint 的網站資料行、內容類型和清單
  Visual Studio 為許多不同的基本 SharePoint 項目，包括提供專案項目範本*列出*和*內容類型*，兩者都可以合併網站資料行 (或*欄位*)。 內容類型和清單的新設計工具讓您就以往更容易建立這些項目。  
  
## <a name="site-columns"></a>網站資料行  
 網站資料行是可以加入至 SharePoint 專案的其中一種最基本的項目。 網站資料行代表資料類型，例如電話號碼、註解，或是連絡人清單中連絡人居住的城市。  
  
 新的網站資料行專案項目範本可讓您比在舊版 Visual Studio 中更容易建立網站資料行。 在建立新的網站資料行之後，您可以修改在網站資料行的 Elements.xml 檔案中的 XML，以包含您想要的資訊，例如它的顯示名稱、資料類型，以及網站資料行在 SharePoint 中顯示時所屬的群組。 如需網站資料行的詳細資訊，請參閱[Introduction to 資料行](http://go.microsoft.com/fwlink/?LinkId=224996)。  
  
## <a name="content-types-and-lists"></a>內容類型和清單  
 內容類型和清單是 SharePoint 中最常使用的項目。  
  
 內容類型負責定義 SharePoint 清單或文件庫中項目分類的中繼資料、工作流程和行為。 例如，您可以為連絡人清單或工作清單中的資訊建立內容類型。 連絡人內容類型可能包含像是名稱、電子郵件、電話號碼和位址等資料行。 您在網站層級定義的內容類型與網站中的任何清單或文件庫並不相關。 您可以對 SharePoint 網站上不同的清單或文件庫使用相同的內容類型。 您也可以在相同的清單或文件庫上使用數種內容類型。  
  
 清單是指 SharePoint 中您可與其他人共用的資訊集合。 清單是由包含資料的數列資料行所組成。 清單的範例包括：工作清單、連絡人清單以及公告清單。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中新的內容類型和清單設計工具，讓建立網站內容類型和清單的工作比在舊版 Visual Studio 中更簡單而直覺。 UI 可讓您以視覺化且熟悉的方式建構內容類型和清單，並且讓您排序和分組清單中的資料，以及使用群組標頭。 如需有關內容類型的詳細資訊，請參閱[內容型別](http://go.microsoft.com/fwlink/?LinkId=224997)。 如需清單的詳細資訊，請參閱[清單表單](http://go.microsoft.com/fwlink/?LinkId=224998)和[清單檢視](http://go.microsoft.com/fwlink/?LinkId=224999)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|示範如何建立用於自訂內容類型的網站資料行。 這個內容類型之後可在自訂清單中使用。|  
  
## <a name="see-also"></a>請參閱  
 [SharePoint 2010 上開發快速入門](http://go.microsoft.com/fwlink/?LinkId=225000)  
  
  