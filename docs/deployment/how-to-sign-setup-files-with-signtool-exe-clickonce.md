---
title: "如何： 簽署安裝程式檔案使用 SignTool.exe (ClickOnce) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 38fec52a9ca4c152a8bb1065e2d33aa1ea52c97f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>如何：使用 SignTool.exe 簽署安裝程式檔案 (ClickOnce)
您可以使用 SignTool.exe 簽署安裝程式 (setup.exe)。 這項程序有助於確保不會在使用者電腦上安裝遭到修改的檔案。  
  
 根據預設，ClickOnce 具有已簽署的資訊清單和已簽署的安裝程式。 不過，如果您稍後要變更安裝程式的參數，就必須在稍後簽署安裝程式。 如果在簽署安裝程式之後變更參數，簽章會損毀。  
  
 下列程序會產生未簽署的資訊清單和未簽署的安裝程式。 接著在 Visual Studio 中啟用 ClickOnce 的簽署功能，產生已簽署的資訊清單。 安裝程式保留未簽署，因此客戶可以用自己的憑證來簽署可執行檔。  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>產生未簽署的安裝程式並在稍後簽署  
  
1.  在開發電腦上，安裝您要用來簽署資訊清單的憑證。  
  
2.  選取的專案中**方案總管 中**。  
  
3.  在**專案**功能表上，按一下  *ProjectName* **屬性**。  
  
4.  在**簽署**頁面上，清除**簽署 ClickOnce 資訊清單**。  
  
5.  在**發行**頁面上，按一下**必要條件**。  
  
6.  確認所有先決條件都已選取，然後按一下**確定**。  
  
7.  在**發行**頁面上，確認發行設定，然後按一下**立即發行**。  
  
     方案隨即將未簽署的應用程式資訊清單、未簽署的部署資訊清單、版本特定檔案，以及未簽署的安裝程式發行至發行資料夾位置。  
  
8.  在**發行**頁面上，按一下**必要條件**。  
  
9. 在**必要條件**對話方塊中，清除**建立安裝程式以安裝必要條件元件**。  
  
10. 在**發行**頁面上，確認發行設定，然後按一下**立即發行**。  
  
     方案隨即將已簽署的應用程式資訊清單、已簽署的部署資訊清單，以及版本特定檔案發行至發行資料夾位置。 發行流程不會覆寫未簽署的安裝程式。  
  
11. 在客戶端開啟命令提示字元。  
  
12. 變更為包含 .exe 檔的目錄。  
  
13. 使用下列命令簽署 .exe 檔：  
  
    ```  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     例如，若要簽署安裝程式，請使用下列其中一個命令：  
  
    ```  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>請參閱  
 [如何：重新簽署應用程式和部署資訊清單](../deployment/how-to-re-sign-application-and-deployment-manifests.md)