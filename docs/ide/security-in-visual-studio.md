---
title: "Visual Studio 中的安全性 | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 7314921a9416184c4bd63312bd5a82cef4102ddd
ms.contentlocale: zh-tw
ms.lasthandoff: 05/30/2017

---
# Visual Studio 中的安全性
<a id="security-in-visual-studio" class="xliff"></a>
開發應用程式時，從設計到部署的所有層面都應該考慮到安全性。 從一開始就應盡可能安全地執行 Visual Studio。 請參閱[使用者權限](../ide/user-permissions-and-visual-studio.md)。  
  
 為了協助您有效開發安全的應用程式，您應該對安全性概念和開發平台的安全性功能有基本了解， 而且也應該了解安全性編碼技術。  
  
## 了解安全性
<a id="understanding-security" class="xliff"></a>  
 [安全性](/dotnet/standard/security/index)  
 描述 .NET Framework 程式碼存取安全性、以角色為基礎的安全性、安全性原則，和安全性工具。  
  
 [Defend Your Code with Top Ten Security Tips Every Developer Must Know](http://go.microsoft.com/fwlink/?LinkId=72877) (程式開發人員不可不知的十大保護程式碼祕訣)  
 說明一些您應該要注意的問題，以免危害資料或系統的安全。  
  
## 安全性的編碼
<a id="coding-for-security" class="xliff"></a>  
 大部分產生安全性弱點的編碼錯誤，其發生原因是開發人員在處理使用者輸入時做出不正確的假設，或是他們不完全了解其開發中的平台。  
  
 [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)  
 提供區分元件以便處理安全性問題的方針。  
  
 [安全性最佳做法](/cpp/top/security-best-practices-for-cpp)  
 討論緩衝區滿溢 (Buffer Overrun) 和由 /GS 編譯時間旗標所提供之 Microsoft Visual C++ 安全性檢查功能的完整內容。

## 安全性建置
<a id="building-for-security" class="xliff"></a>  
 在建置程序中，安全性也是很重要的考量。  您可以採取一些額外的步驟來提升部署的應用程式安全性，並協助防止未經授權的反向工程、詐騙或其他攻擊。

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 說明如何設定和開始使用免費的 Protection - Dotfuscator Community Edition，以保護 .NET 組件不受反向工程和未經授權的使用 (例如未經授權的偵錯) 威脅。
  
 [管理組件和資訊清單簽署](managing-assembly-and-manifest-signing.md)  
 探討可以用來唯一識別軟體元件、防止詐騙的強式名稱簽署。
