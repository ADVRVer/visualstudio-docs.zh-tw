---
title: "必要條件對話方塊 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3d97e1f37c1e60c3ec5bb122a6b3f26c2fb086f9
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="prerequisites-dialog-box"></a>Prerequisites Dialog Box

這個對話方塊可指定已安裝的必要條件元件、安裝方式，以及套件的安裝順序。

若要存取這個對話方塊，請選取方案總管中的專案節點，然後按一下 [專案] 功能表上的 [屬性]。 當 [ **專案設計工具** ] 出現時，請按一下 [ **發行** ] 索引標籤。在 [發行] 頁面上，按一下 [必要條件]。 針對安裝專案，按一下 [專案] 功能表上的 [屬性]。 出現 [屬性頁] 對話方塊時，按一下 [必要條件]。

## <a name="uielement-list"></a>UIElement 清單

|元素|描述|
|-------------|-----------------|
|**建立安裝程式以安裝必要條件元件**|將必要條件元件包含在應用程式的安裝程式 (Setup.exe) 中，才能在安裝應用程式之前，依照相依性的順序進行安裝。 根據預設，這個選項是選取的。 如果沒有選取這個選項，則不會建立 Setup.exe。|
|**選擇要安裝的必要條件**|指定是否要安裝元件，例如 [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]、Crystal Reports 等。<br /><br /> 例如，選取 [SQL Server 2005 Express Edition SP2] 旁的核取方塊，即指定安裝程式確認這個元件是否已安裝在目標電腦上，如果尚未安裝就會進行安裝。<br /><br /> 如需各個必要條件套件的詳細資訊，請參閱本主題稍後的「必要條件資訊」表格。|
|**檢查 Microsoft Update 以取得更多可轉散發元件**|按一下這個連結會帶您前往[啟動載入器套件轉散發元件](http://go.microsoft.com/fwlink/?LinkId=208835)網站，以檢查更新。|
|**從元件廠商的網站下載必要條件**|指定從廠商的網站安裝必要條件元件。 這是預設選項。|
|**從應用程式的相同位置下載必要條件**|指定從應用程式的相同位置安裝必要條件元件。 這個選項會將所有的必要條件套件複製到發行位置。 必要條件套件必須放在開發電腦上，這個選項才能正常運作。|
|**從下列位置下載必要條件**|指定從您選取的位置安裝必要條件元件。 您可以使用 [瀏覽] 按鈕來選取位置。|

## <a name="prerequisites-information"></a>必要條件資訊

[必要條件] 對話方塊中顯示的必要條件元件，可能和以下所列的不同。 第一次開啟該對話方塊時，會自動設定**必要條件對話方塊**中所列的必要條件套件。 如果您接著變更專案的目標架構，您就必須手動選取必要條件以符合新的目標架構。

|元素|描述|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|這個套件會安裝下列項目：<br /><br /> -   .NET Framework 2.0、3.0 和 3.5 版。<br />-   支援 32 位元 (x86) 及 64 位元 (x64) 作業系統上的所有 .NET Framework 版本。<br />-   隨著這個套件一併安裝之每個 .NET Framework 版本的語言套件。<br />-   .NET Framework 2.0 及 3.0 的 Service Pack。<br /><br /> .NET Framework 3.0 隨附於 Windows Vista，.NET Framework 3.5 則隨附於 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 所有針對 32 位元作業系統編譯，而且目標架構設定為 [.NET Framework 3.5] 的 Visual Basic 和 C# 專案，以及針對 64 位元作業系統編譯的 Visual Basic 和 C# 專案，都需要 .NET Framework 3.5。 (不支援 IA64)。請注意，根據預設，Visual Basic 和 C# 專案是針對任何 CPU 架構編譯。 如需詳細資訊，請參閱 [Visual Studio 多目標概觀](../../ide/visual-studio-multi-targeting-overview.md)和 [64 位元應用程式的部署必要條件](../../deployment/deploying-prerequisites-for-64-bit-applications.md)。<br /><br /> 這個項目預設為選取。|
|**Microsoft .NET Framework 4.x**|這個套件會在 x86 和 x64 平台安裝 .NET Framework 4.x。|
|**Microsoft System CLR Types for SQL Server 2014 (x64 和 x86)**|此套件會安裝適用於 x64 或 x86 SQL Server 2014 的 Microsoft System CLR Types。|
|**SQL Server 2008 R2 Express**|此套件會安裝 Microsoft SQL Server 2008 R2 Express (Microsoft SQL Server 2008 R2 的免費版本)，這是適用於小型網路、伺服器或桌面應用程式的理想資料庫。 它可以免費用於開發和生產環境。 隨同應用程式散發 SQL Server 2008 R2 Express 時，必須要有免費的[註冊](http://go.microsoft.com/fwlink/?LinkId=130380)。|
|**SQL Server 2012 Express**|此套件會安裝 Microsoft SQL Server 2012 Express。|
|**SQL Server 2012 Express LocalDB**|此套件會安裝 Microsoft SQL Server 2012 Express LocalDB。|
|**Visual C++ "14" 執行階段程式庫 (ARM)**|這個套件會安裝適用於 Itanium 架構的 Visual C++ 執行階段程式庫，以提供 Microsoft Windows 作業系統程式設計所需的常式。 這些常式會自動執行 C 和 C++ 語言所未提供的許多常見的程式設計工作。<br /><br /> 如需詳細資訊，請參閱 [C 執行階段程式庫參考](/cpp/c-runtime-library/c-run-time-library-reference)。|
|**Visual C++ "14" 執行階段程式庫 (x64)**|這個套件會安裝適用於 x64 作業系統的 Visual C++ 執行階段程式庫，以提供 Microsoft Windows 作業系統程式設計所需的常式。 這些常式會自動執行 C 和 C++ 語言所未提供的許多常見的程式設計工作。<br /><br /> 如需詳細資訊，請參閱 [C 執行階段程式庫參考](/cpp/c-runtime-library/c-run-time-library-reference)。|
|**Visual C++ "14" 執行階段程式庫 (x86)**|這個套件會安裝適用於 x86 作業系統的 Visual C++ 執行階段程式庫，以提供 Microsoft Windows 作業系統程式設計所需的常式。 這些常式會自動執行 C 和 C++ 語言所未提供的許多常見的程式設計工作。<br /><br /> 如需詳細資訊，請參閱 [C 執行階段程式庫參考](/cpp/c-runtime-library/c-run-time-library-reference)。|

## <a name="see-also"></a>另請參閱

[專案設計工具、發行頁面](../../ide/reference/publish-page-project-designer.md)  
[應用程式部署必要條件](../../deployment/application-deployment-prerequisites.md)  
[64 位元應用程式的部署必要條件](../../deployment/deploying-prerequisites-for-64-bit-applications.md)  
[Visual Studio 多目標概觀](../../ide/visual-studio-multi-targeting-overview.md)
