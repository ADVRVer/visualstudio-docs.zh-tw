---
title: "如何解除鎖定 Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/20/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: c3521e1de25854db012cb91bbe09d9463ecb42c7
ms.openlocfilehash: db9fff46d52be80e53bd5c09fb8ab9d1f06d4f3c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/21/2017

---

# <a name="how-to-unlock-visual-studio"></a>如何解除鎖定 Visual Studio
您最多可以免費評估 Visual Studio 30 天。 登入整合式開發環境 (IDE) 可將試用期延展為 90 天。 若要繼續使用 Visual Studio，請透過下列方式解除鎖定 IDE：  
  
1.  使用線上訂閱，或是  
1.  輸入產品金鑰。  
  
ed## 使用線上訂閱解除鎖定 Visual Studio  
 若要使用與 Microsoft 帳戶或公司/學校帳戶關聯的 MSDN 訂閱或 Visual Studio Team Service 訂閱來解除鎖定 Visual Studio：  
  
1.  按一下 IDE 右上角的 [登入] 按鈕 (或移至 [檔案] > [帳戶設定] 開啟 [帳戶設定] 對話方塊，然後按一下 [登入] 按鈕)。  
  
1.  輸入 Microsoft 帳戶或工作/學校帳戶的認證。 Visual Studio 將會尋找與您的帳戶關聯的 MSDN 訂閱或 Visual Studio Team Services 訂閱。  
  
> [!IMPORTANT]
>  當您從 Team Explorer 工具視窗連線到 Visual Studio Team Services 帳戶時，Visual Studio 會自動尋找關聯的線上訂閱。 當您連線到 Visual Studio Team Services 帳戶時，您可以使用 Microsoft 帳戶和工作/學校帳戶進行登入。 如果該使用者帳戶有線上訂閱，Visual Studio 會自動為您解除鎖定 IDE。  
  
## <a name="to-unlock-visual-studio-with-a-product-key"></a>使用產品金鑰解除鎖定 Visual Studio  
  
1.  選取 [檔案] > [帳戶設定] 開啟 [帳戶設定] 對話方塊，然後按一下 [使用產品金鑰授權] 連結。  
1.  在提供的空格中輸入產品金鑰。  
  
> [!TIP]
>  Visual Studio 發行前版本不需要產品金鑰。 您必須登入 IDE 才能使用發行前版本。  
  
## <a name="address-license-problem-states"></a>解決授權問題狀態  
  
### <a name="update-stale-licenses"></a>更新過時的授權  
 您可能看到「您的授權已過時，必須更新。」的訊息，代表您的授權在 Visual Studio 中已過時。
  
 ![Visual Studio 授權過時訊息](~/docs/ide/media/vs2017_stale-license.png)  
  
 這個訊息表示，雖然您的訂閱可能仍然有效，但是基於下列其中一個原因尚未重新整理 Visual Studio 用來保持最新訂閱的授權權杖，而且該權杖已經過時：  
  
1.  您尚未使用 Visual Studio，或有很長一段時間沒有網際網路連線。   
1.  您已登出 Visual Studio。  
  
 在授權權杖過期之前，Visual Studio 會先顯示一個警告訊息，要求您重新輸入認證。  
  
 如果您未重新輸入認證，權杖將會過時，且 [帳戶設定] 對話方塊會顯示權杖完全過期之前的天數。 權杖過期之後，您必須使用上述另一個方法重新輸入這個帳戶或授權的認證，才能繼續使用 Visual Studio。  
  
> [!Important]
>  如果您在限制存取或無法存取網際網路的環境中使用 Visual Studio 很長一段時間，則應使用產品金鑰來解除鎖定 Visual Studio，以避免中斷。  
  
### <a name="update-expired-licenses"></a>更新到期的授權  
 如果您的訂閱完全到期，而不再具有 Visual Studio 的存取權限，您必須：  
  
1.  更新您的訂閱 若要查看您正在使用之授權的詳細資訊，請移至 [檔案] > [帳戶設定]，並查看對話方塊右側的授權資訊。  
  
1.  如果您有與不同帳戶關聯的其他訂閱，請選取 [新增帳戶] 連結，將該帳戶新增到 [檔案] > [帳戶設定] 對話方塊左側的 [所有帳戶] 清單。  
  
## <a name="see-also"></a>請參閱  
 [登入 Visual Studio](../ide/signing-in-to-visual-studio.md)

