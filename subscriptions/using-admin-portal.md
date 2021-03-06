---
title: "使用系統管理員入口網站 | Visual Studio Marketplace"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn how to manage your organization's Visual Studio subscriptions with the Administrator Portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: cf44f74b32bd830c613adcc1ee35a95b97636772
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
#  <a name="using-the-visual-studio-subscriptions-administrator-portal"></a>使用 Visual Studio 訂用帳戶系統管理員入口網站

使用 Visual Studio 訂用帳戶管理入口網站時，請牢記：
 
- **Visual Studio 訂用帳戶依使用者授權。** 每位訂閱者可以基於開發和測試用途在任意數量的電腦上使用軟體。 
- 根據貴組織購買的 Visual Studio 訂用帳戶，**僅為每位訂閱者指派一個訂用帳戶層級**。 如果您的訂閱者獲派超過一個以上的訂閱等級，請編輯他們的設定，讓他們只擁有一個等級。 
- 如果升級訂閱 (在購買「升級」授權之後) 或以較低等級續訂，**也必須更新訂閱者的訂用帳戶等級**。 
- **請勿讓訂閱者彼此共用訂用帳戶。** 您必須將訂用帳戶指派給使用全部或部分訂用帳戶權益的任一人 (供開發和測試用的軟體、Microsoft Azure、E-learning 等等)。 

## <a name="adminstrator-roles"></a>系統管理員角色
大量授權客戶的新 Visual Studio 訂用帳戶管理入口網站中有兩個不同的角色。 這些角色像是目前 VLSC 中的主要/通知連絡人角色和訂用帳戶管理員角色。 

**超級管理員：**第一次設定組織時，主要或通知連絡人預設會成為超級管理員。 主要或通知連絡人可以選擇指派其他的超級管理員或系統管理員。 超級管理員可以新增和移除其他系統管理員以及訂閱者。 如果系統中有兩個以上的超級管理員，則超級管理員可以刪除所有超級管理員，但最後必須保留兩個以策安全。 

**系統管理員：**系統管理員只能由超級管理員設定。系統管理員可以管理超級管理員在合約中指派給他們的訂閱者。 

## <a name="getting-started"></a>快速入門
### <a name="onboarding"></a>上架
當您的組織隨時可以上架到 Visual Studio 訂用帳戶管理入口網站時，會向主要連絡人及通知連絡人傳送一封電子郵件給，邀請他們完成上架程序。 以下詳細資料是上架到新入口網站的必要步驟。 如果想要處理程序的逐步解說，請參考這段[系統管理員上架影片](https://channel9.msdn.com/Series/Visual-Studio-Subscriptions-Administration/Onboarding-your-organization-to-the-new-Visual-Studio-Subscription-Administration-Portal-and-setting)或這篇[支援文件] (https://support.microsoft.com/help/4013931/visual-studio-subscriptions-administrator-migration-process "Visual Studio 的訂閱：系統管理員遷移程序")。   
1.  **尋找您的 PCN 並登入：**
    - 在電子郵件中，會以唯一的連結提供主要與通知連絡人以及其公開客戶號碼 (PCN) 的末三碼。 * 
    - 為取得完整的 PCN，主要連絡人需要登入 VLSC (在此可以找到尋找 PCN 的指示)。 
    - 取得 PCN 之後，他們需要選取提示他們登入的唯一連結。 他們可以使用工作/學校帳戶 (如果您的組織在 AAD 中) 或 Microsoft 帳戶 (MSA) 登入，如果您的組織不在 AAD 中。 
    - 接下來，他們需要輸入 PCN。 
2.  **設定您的系統管理員。** 輸入 PCN 之後，他們會在新的系統中註冊為超級管理員，可以新增其他超級管理員和系統管理員 (前稱為「訂用帳戶管理員」)。 為避免遺失存取，此項作業應在貴組織的移轉日期前完成。 
3.  **存取新的訂用帳戶管理入口網站。**  組織一旦移轉，就會向最近新增的超級管理員和系統管理員傳送電子郵件，邀請他們存取新的入口網站，開始管理訂用帳戶。  

* *注意：如果主要或通知連絡人收到多份電子郵件，這表示他們有多個 PCN。他們需要使用每份電子郵件中參考的唯一 PCN 連結完成程序。*

如果您需要新增至新的 Visual Studio 訂用帳戶管理入口網站，但不確定主要/通知連絡人是誰，您可以在登入 [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx) 之後尋找此資訊。 如需在 VLSC 中尋找主要/通知連絡人的步驟，請參考[本文](https://www.visualstudio.com/subscriptions/support/locate-primary-contact/ "如何尋找我的主要連絡人？")
如果您已設定為系統管理員身分，就可以直接前往 [Visual Studio 訂用帳戶管理入口網站](https://manage.visualstudio.com)。

### <a name="understanding-the-subscribers-page"></a>了解 [訂閱者] 頁面
一旦指派了訂用帳戶，[訂閱者] 索引標籤就會提供訂閱者的詳細資訊，包括：
- 每位訂閱者的姓名。
- 此使用者的電子郵件地址。
- 已指派給他們的訂用帳戶層級。
- 訂用帳戶指派給他們的日期。 
- 訂用帳戶到期日。
- 選擇性的文字描述。
- 指出訂閱者下載啟用或停用。 
- 他們所在的國家/地區。
- 他們在管理入口網站指派通訊電子郵件的語言設定。
- 選擇性欄位，用於登入通訊以外的其他電子郵件地址。 

在此頁面的左側，您可以看到已購買、指派，及貴組織每份合約仍然可用的訂用帳戶授權數目等其他資訊。

![Visual Studio 訂用帳戶管理入口網站訂閱者頁面](_img/using-admin-portal/subscribers-page.png)

### <a name="understanding-the-details-page"></a>了解 [詳細資料] 頁面
如需目前檢視的合約詳細資訊，請選取 [詳細資料] 索引標籤。它會顯示合約狀態、購買帳戶、組織詳細資料、主要連絡人 (VLSC)、超級管理員 (如有) 和其他相關資訊。

![Visual Studio 訂用帳戶管理入口網站詳細資料頁面](_img/using-admin-portal/details-page.png)

