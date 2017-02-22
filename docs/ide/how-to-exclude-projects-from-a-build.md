---
title: "如何：從組建中排除專案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：從組建中排除專案
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以建置方案，而不建置它所包含的所有專案。  例如，您可能會排除會中斷組建的專案。  然後您可以在調查和處理這些問題之後才建置專案。  
  
 您可以利用下列方式排除專案：  
  
-   從作用中的方案組態暫時將其移除。  
  
-   建立不包含專案的方案組態。  
  
 如需詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。  
  
### 從作用中的方案組態暫時將專案移除  
  
1.  在功能表列上，選擇 \[**建置**\]、\[**組態管理員**\]。  
  
2.  在 \[**專案內容**\] 資料表中，找出您想要從組建排除的專案。  
  
3.  在專案的 \[**組建**\] 資料行中，清除核取方塊。  
  
4.  選擇 \[**關閉**\] 按鈕，然後再重新建置方案。  
  
### 建立排除專案的方案組態  
  
1.  在功能表列上，選擇 \[**建置**\]、\[**組態管理員**\]。  
  
2.  在 \[**作用中的方案組態**\] 清單中，選擇 **\<New\>**。  
  
3.  在 \[**名稱**\] 方塊中，輸入方案組態的名稱。  
  
4.  在 \[**複製設定來源**\] 清單中，選擇您要以其為新組態根據的方案組態 \(例如，**偵錯**\)，然後選擇 \[**確定**\] 按鈕。  
  
5.  在 \[**組態管理員**\] 對話方塊中，清除 \[**建置**\] 資料行中您想要排除之專案的核取方塊，然後選擇 \[**關閉**\] 按鈕。  
  
6.  在 \[**標準**\] 工具列上，確認新的方案組態是 \[**方案組態**\] 方塊中的作用中組態。  
  
7.  在功能表列上，選擇 \[**建置**\]、\[**重建方案**\]。  
  
## 請參閱  
 [了解組建組態](../ide/understanding-build-configurations.md)   
 [如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)   
 [如何：同時建置多個組態](../ide/how-to-build-multiple-configurations-simultaneously.md)