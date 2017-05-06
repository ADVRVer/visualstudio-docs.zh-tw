---
title: "Office 方案的事件記錄"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發]，事件檢視器"
  - "ClickOnce 部署 [Visual Studio 中的 Office 程式開發]，事件檢視器"
  - "部署應用程式 [Visual Studio 中的 Office 程式開發]，事件檢視器"
  - "Visual Studio 中的 Office 程式開發，事件檢視器"
ms.assetid: 31a246fe-ce1c-4f0e-9a21-9cf974c247fe
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Office 方案的事件記錄
  在安裝或解除安裝 Office 方案時，您可以使用 Windows 的事件檢視器查看 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 擷取的例外狀況訊息。 您可以使用事件記錄器的這些訊息，解決安裝和部署問題。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 讀取事件記錄檔  
 開啟 \[事件檢視器\] 並篩選出您要查看的事件。  
  
#### 在 Windows Server 2003 和 Windows XP 中讀取事件記錄檔  
  
1.  在 \[控制台\] 中，開啟 \[系統管理工具\]。  
  
2.  啟動 \[事件檢視器\]。  
  
3.  在事件記錄檔清單中，選取 \[應用程式\]。  
  
4.  在 \[檢視\] 功能表上，按一下 \[篩選\]。  
  
5.  在 \[事件來源\] 清單中，選取 \[VSTO 4.0\]。  
  
6.  針對安裝事件，在 \[事件識別碼\] 方塊中輸入 **4096**。  
  
7.  按一下 \[確定\] 以查看篩選過的檢視。  
  
#### 在 Windows 7、Windows Vista 和 Windows Server 2008 中讀取事件記錄檔  
  
1.  在 \[控制台\] 中，開啟 \[系統管理工具\]。  
  
2.  啟動 \[事件檢視器\]。  
  
3.  展開 \[Windows 記錄\]。  
  
4.  在事件記錄檔清單中，選取 \[應用程式\]。  
  
5.  在 \[動作\] 功能表上，按一下 \[篩選目前的記錄\]。  
  
6.  在 \[事件來源\] 清單中，選取 \[VSTO 4.0\]。  
  
7.  針對安裝事件，在 \[事件識別碼\] 方塊中輸入 **4096**。  
  
8.  按一下 \[確定\] 以查看篩選過的檢視。  
  
 事件檢視器包含下列資訊：  
  
-   方案的部署資訊清單位置。  
  
-   說明錯誤或例外狀況原因的訊息。  
  
 這些例外狀況訊息可協助您判斷安裝問題的原因，例如憑證未受信任、文件位置未受信任或部署資訊清單無效。  
  
 解除安裝 Office 方案之後，例外狀況訊息仍會保留在事件記錄檔中。  
  
 若要顯示或記錄 Office 方案執行時的例外狀況訊息，請參閱[偵錯 Office 專案](../vsto/debugging-office-projects.md)和[偵錯 Office 專案](../vsto/debugging-office-projects.md)。  
  
### 當地語系化  
 例外狀況訊息語言取決於 Visual Studio Tools for Office Runtime 語言。 例如，如果使用者電腦安裝了日文語言套件，則會用日文將例外狀況訊息寫入事件記錄檔。  
  
## 停用事件記錄器  
 當您安裝或解除安裝 Office 方案時，預設會啟用事件記錄器。 您可以將 VSTO\_EVENTLOGDISABLED 環境變數設定為 "1" \(一\)，以停用事件記錄器。  
  
#### 停用事件記錄檔  
  
1.  在 \[控制台\] 中，開啟 \[系統\]。  
  
2.  按一下 \[**進階**\] 索引標籤上的 \[**環境變數**\]。  
  
3.  在 \[系統變數\] 窗格中，按一下 \[新增\]。  
  
4.  在 \[新增系統變數\] 對話方塊的 \[變數名稱\] 方塊中，輸入 **VSTO\_EVENTLOGDISABLED**。  
  
5.  在 \[變數值\] 方塊中，輸入**1**。  
  
6.  按一下 \[**確定**\]。  
  
## 請參閱  
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [Office 方案部署疑難排解](../vsto/troubleshooting-office-solution-deployment.md)  
  
  