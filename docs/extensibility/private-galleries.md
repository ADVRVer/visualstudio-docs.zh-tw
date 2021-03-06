---
title: "私用組件庫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5226ff7a4ed77333d2a6f9287f129c6a6d754cac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="private-galleries"></a>Private Galleries
控制項、 範本和公佈到您開發的工具，您可以共用*私用組件庫*內部為您的組織，如下所示：  
  
-   建立 Atom (RSS) 摘要，您的內部網路上的適當地設定中央位置 （儲存機制）。 如需詳細資訊，請參閱[How to： 建立私用組件庫的 Atom 摘要](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)。  
  
-   將發佈.pkgdef 檔案，其中描述私用組件庫。 我們建議此組態的系統管理員想要連接到多部電腦的私用組件庫在相同的時間。  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>加入擴充功能和更新 Visual Studio 中的私用組件庫  
 當私用組件庫功能時，您可以將它加入**擴充功能和更新**Visual Studio 中。  
  
 ![擴充管理員新增對話方塊](../extensibility/media/em_adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>加入擴充功能和更新的私用組件庫  
  
1.  在功能表列上選擇 [工具] 、[選項] 。  
  
2.  在**環境**節點中，選取**擴充功能和更新**。  
  
3.  選擇 [ **加入** ] 按鈕。  
  
4.  在**名稱**欄位中，輸入私用組件庫的名稱，例如`My Gallery`。  
  
5.  在**URL**欄位中，輸入 Atom 摘要或 SharePoint 網站裝載私用組件庫的 URL。  
  
    1.  如果主機是 Atom 摘要，連線至私用組件庫時，URL 會看起來像這樣： http://www.mywebsite/mygallery/atom.xml。  這個 URL 可以參考檔案或網路路徑。  
  
    2.  如果主機是在 SharePoint 網站，URL 會看起來像這樣： http://mysharepoint/sites/mygallery/forms/AllItems.aspx。  
  
### <a name="managing-private-galleries"></a>管理私用組件庫  
 系統管理員可以對私用組件庫提供數部電腦同時藉由修改每一部電腦的系統登錄。 若要達成此目的，建立描述新的登錄機碼和其值的.pkgdef 檔。  此檔案的格式如下所示。  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 如需詳細資訊，請參閱[如何： 管理私用組件庫所使用登錄設定](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)。  
  
## <a name="installing-extensions-from-a-private-gallery"></a>安裝私人組件庫中的擴充功能  
 您可以搜尋從並安裝 Visual Studio 擴充功能私用組件庫中**擴充功能和更新**。 下列步驟是使用名為私用組件庫`My Gallery`。  
  
 ![安裝私人組件庫的擴充管理員](../extensibility/media/em_.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>搜尋並安裝擴充功能，從私用組件庫  
  
1.  在功能表列上，選擇 [工具]、[延伸模組和更新]。  
  
2.  在左窗格中，選取**線上擴充**，然後選取**我圖庫**。  
  
3.  在右窗格中，選取 [擴充功能，，然後選擇**下載**] 按鈕。  
  
## <a name="updating-extensions-from-a-private-gallery"></a>更新私人組件庫中的擴充功能  
 張貼新版本的 Visual Studio 擴充功能私用組件庫中，您可以更新已安裝的擴充功能。 下列步驟是使用名為私用組件庫`My Repository`。  
  
 ![更新擴充功能管理員私用組件庫](../extensibility/media/em_update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>若要更新已安裝的擴充，從私用組件庫  
  
1.  在功能表列上，選擇 [工具]、[延伸模組和更新]。  
  
2.  在左窗格中，選取**更新**，然後選取**我的儲存機制**。  
  
3.  在右窗格中，選取 [擴充功能，，然後選擇**更新**] 按鈕。  
  
## <a name="see-also"></a>請參閱  
 [尋找及使用 Visual Studio 擴充功能](../ide/finding-and-using-visual-studio-extensions.md)   
 [推出 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)