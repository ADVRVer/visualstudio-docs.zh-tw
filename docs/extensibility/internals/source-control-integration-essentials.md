---
title: "原始檔控制整合 Essentials |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5d474e00186cf2110dd8e701d980a1a4562beb8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-integration-essentials"></a>原始檔控制整合 Essentials
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援兩種類型的原始檔控制整合： 原始檔控制外掛程式，提供基本功能，並會使用原始檔控制外掛程式 API （之前稱為 MSSCCI API） 和 VSPackage 為基礎的原始檔控制整合方案所建置的提供更強固的功能。  
  
## <a name="source-control-plug-in"></a>原始檔控制外掛程式  
 原始檔控制外掛程式會寫入做為實作原始檔控制外掛程式 API 的 DLL。 註冊和原始檔控制整合功能是透過 API 來提供。 這個方法會比原始檔控制 VSPackage，容易實作，並使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]大部分的原始檔控制作業的使用者介面 (UI)。  
  
 若要實作原始檔控制外掛程式使用原始檔控制外掛程式 API，請遵循下列步驟：  
  
1.  建立實作中指定的函式的 DLL[原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)。  
  
2.  中所述，藉由適當的登錄項目中，登錄 DLL[如何： 安裝原始檔控制外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)。  
  
3.  建立協助程式 UI，並顯示原始檔控制配接器封裝程式出現提示時 ([!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]處理透過原始檔控制外掛程式的原始檔控制功能的元件)。  
  
 如需詳細資訊，請參閱[建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)。  
  
## <a name="source-control-vspackage"></a>原始檔控制 VSPackage  
 原始檔控制 VSPackage 實作可讓您開發自訂的取代[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]原始檔控制 UI。 這種方法讓原始檔控制整合，擁有完整控制權，但這需要您提供的 UI 項目，否則就會提供外掛程式的方法之下的來源控制項介面的實作。  
  
 若要實作 VSPackage 的原始檔控制，您必須：  
  
1.  建立並註冊您自己的原始檔控制 VSPackage 中, 所述[註冊和選取範圍](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)。  
  
2.  預設原始檔控制 UI 取代為您自訂的 UI。 請參閱[自訂使用者介面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)。  
  
3.  指定在使用，並處理圖像**方案總管 中**圖像 （glyph） 事件。 請參閱[圖像控制項](../../extensibility/internals/glyph-control-source-control-vspackage.md)。  
  
4.  處理查詢編輯和儲存查詢的事件中所示[查詢編輯查詢儲存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)。  
  
 如需詳細資訊，請參閱[建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。  
  
## <a name="see-also"></a>請參閱  
 [概觀](../../extensibility/internals/source-control-integration-overview.md)   
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)