---
title: "使用內含清單信任 Office 方案 | Microsoft Docs"
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
  - "使用權限 [Visual Studio 中的 Office 程式開發]"
  - "內含清單 [Visual Studio 中的 Office 程式開發]，關於內含清單"
  - "安全性 [Visual Studio 中的 Office 程式開發]，內含清單"
  - "內含清單 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 6dae0128-435b-4fa1-aed9-73e728fdcacf
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 使用內含清單信任 Office 方案
  內含清單可讓使用者將信任授與使用可識別發行者的憑證所簽署的 Office 方案。 內含清單是使用者專屬的，可以用於文件層級自訂和 VSTO 增益集。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 當使用者啟動該使用者未授與信任的 Office 方案時， Microsoft Office 方案會以 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示來提示使用者安全性決策。 如果使用者決定信任方案，即會執行自訂，且下次不再提示使用者。  
  
## 內含清單和 Windows Installer  
 您需有系統管理員權限，才能使用 Windows Installer 將 Office 方案安裝至 Program Files 目錄。 針對 Program Files 目錄中的 Office 方案，因為已授與 Office 方案 FullTrust 權限，Visual Studio Visual Studio Tools for Office Runtime 不會再檢查內含清單。  
  
## ClickOnce 信任提示  
 使用 Office 方案的 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 實作，系統管理員就可以將信任提示層級設定為允許提示、停用提示或需要信任的憑證。 此設定可以藉由使用控制存取內含清單的登錄機碼來完成。  
  
 如果停用提示，就只能安裝具有已知信任憑證的方案。 如果提示層級設為需要 Authenticode，則方案必須用已知的授權單位所提供的憑證來簽署，但是這個憑證不需要鏈結至信任的根授權單位 \(即信任的憑證\)。 如果允許提示，則方案可以用具有未知識別的憑證來簽署。 在這個情況下，信任決策會委託給使用者，且暫存憑證就足以安裝方案。  
  
 如需詳細資訊，請參閱[如何：設定內含清單的安全性](../vsto/how-to-configure-inclusion-list-security.md)和[設定 ClickOnce 信任的發行者](http://go.microsoft.com/fwlink/?LinkId=94774)中的表 2「提示層級登錄機碼值啟動效果」。  
  
## 內含清單的結構  
 有效的內含清單項目有兩個部分：部署資訊清單的路徑，和用以簽署方案的公開金鑰。 方案加入至內含清單之後，就會被視為信任的方案。 當執行 Office 方案時，Office 應用程式會比較內含清單中的公開金鑰與部署資訊清單中的簽署金鑰，以確認目前執行的方案與原始信任的版本相同。  
  
## 請參閱  
 [授與信任給 Office 方案](../vsto/granting-trust-to-office-solutions.md)   
 [保護 Office 方案](../vsto/securing-office-solutions.md)  
  
  