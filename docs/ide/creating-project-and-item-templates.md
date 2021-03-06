---
title: "適用於專案和檔案的 Visual Studio 範本 | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3959b01fdfc0ff77bdd5a3ffa0c96366b9da87d7
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="project-and-item-templates"></a>專案範本與項目範本

專案範本與項目範本提供可重複使用的虛設常式，讓使用者有一些基本的程式碼和結構可依其目的來自行自訂。

## <a name="visual-studio-templates"></a>Visual Studio 範本

安裝 Visual Studio 時會安裝一些預先定義的專案範本和項目範本。 例如，[新增專案] 對話方塊中顯示的 Visual Basic 和 C# **Windows Forms 應用程式**以及**類別庫**範本，就是專案範本。 項目範本會顯示在 [新增項目] 對話方塊中，並且包含程式碼檔案、XML 檔案、HTML 網頁和樣式表等項目。

使用者可將這些範本當作起點開始建立專案，或擴充現有的專案。 專案範本提供特定專案類型所需的檔案、包含標準組件參考，並設定預設專案屬性和編譯器選項。 項目範本複雜多變，從有特定副檔名的單一空檔案，到包含有虛設常式程式碼的原始程式碼檔案、設計工具資訊檔案和內嵌資源等等的多檔案項目，都有可能。

除了 [新增專案] 和 [新增項目] 對話方塊中已安裝的範本之外，您還可以撰寫自己的範本，或下載並使用社群所建立的範本。 如需詳細資訊，請參閱[如何：建立專案範本](../ide/how-to-create-project-templates.md)和[如何：建立項目範本](../ide/how-to-create-item-templates.md)。

## <a name="contents-of-a-template"></a>範本的內容

所有專案範本和項目範本，不論是隨 Visual Studio 一起安裝或由您建立，都以相同的原理運作且具有相似的內容。 所有範本都包含下列項目：

- 使用範本時要建立的檔案。 這包括原始程式碼檔案、內嵌資源、專案檔等等。

- 一個 .vstemplate 檔案。 此檔案包含的中繼資料提供必要資訊，在 [新增專案] 和 [新增項目] 對話方塊中顯示範本，以及從範本建立專案或項目。 如需 .vstemplate 檔案的詳細資訊，請參閱[範本參數](../ide/template-parameters.md)。

當這些檔案壓縮成 .zip 檔案並放入正確的資料夾時，Visual Studio 會自動在下列位置顯示它們：

- 專案範本會出現在 [新增專案] 對話方塊中。

- 項目範本會出現在 [新增項目] 對話方塊中。

如需範本資料夾的詳細資訊，請參閱[如何：尋找並整理範本](../ide/how-to-locate-and-organize-project-and-item-templates.md)。

## <a name="starter-kits"></a>入門套件

入門套件是增強的範本，可以與社群的其他成員共用。 入門套件包含可編譯的程式碼範例、文件和其他資源，協助使用者經由建置實際有用的應用程式，學習新的工具和程式設計技巧。 入門套件的基本內容和程序，與範本完全相同。 如需詳細資訊，請參閱[如何：建立入門套件](../ide/how-to-create-starter-kits.md)。

## <a name="see-also"></a>另請參閱

[如何：建立專案範本](../ide/how-to-create-project-templates.md)  
[如何：建立項目範本](../ide/how-to-create-item-templates.md)  
[範本參數](../ide/template-parameters.md)  
[自訂範本](../ide/customizing-project-and-item-templates.md)  
[Visual Studio 範本中的 NuGet 套件](/nuget/visual-studio-extensibility/visual-studio-templates)