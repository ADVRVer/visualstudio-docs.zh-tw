---
title: "如何： 擴充 O R 設計工具所產生的程式碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: e5b38288cc8d0d58e18e4aea3de2b80470783ea6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>如何：擴充 O/R 設計工具產生的程式碼
變更設計工具介面上的實體 (Entity) 類別 (Class) 和其他物件時，系統會重新產生 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]所產生的程式碼。 因為有這項重新產生作業，所以當設計工具重新產生程式碼時，您之前加入至所產生程式碼的程式碼，通常都會遭覆寫。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]可以產生部分類別檔案，您可以在其中加入不要覆寫的程式碼。 需要將自訂程式碼加入至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]所產生程式碼的其中一個範例，就是將資料驗證加入至 LINQ to SQL (實體) 類別。 如需資訊，請參閱[如何： 為實體類別加入驗證](../data-tools/how-to-add-validation-to-entity-classes.md)。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="adding-code-to-an-entity-class"></a>將程式碼加入至實體類別  
  
#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>若要建立部分類別並將程式碼加入至實體類別  
  
1.  開啟或建立新的 LINQ to SQL 類別檔案 (**.dbml**檔案) 中[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 (按兩下**.dbml**檔案**方案總管 中**/**資料庫總管**。)  
  
2.  在[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，以滑鼠右鍵按一下您要加入驗證，然後按一下 的類別**檢視程式碼**。  
  
     [程式碼編輯器] 會以所選取實體類別的部分類別開啟。  
  
3.  在實體類別的部分類別宣告中，加入程式碼。  
  
## <a name="adding-code-to-a-datacontext"></a>將程式碼加入至 DataContext  
  
#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>若要建立部分類別並將程式碼加入至 DataContext  
  
1.  開啟或建立新的 LINQ to SQL 類別檔案 (**.dbml**檔案) 中[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 (按兩下**.dbml**檔案**方案總管 中**/**資料庫總管**。)  
  
2.  在[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，以滑鼠右鍵按一下設計工具上的空白區域，然後按一下**檢視程式碼**。  
  
     [程式碼編輯器] 會以 DataContext 的部分類別開啟。  
  
3.  在 DataContext 的部分類別宣告中，加入程式碼。  
  
## <a name="see-also"></a>請參閱  
 [LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [逐步解說： 建立 LINQ to SQL 類別 （O R 設計工具）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 