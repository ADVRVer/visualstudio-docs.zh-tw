---
title: "建立原始檔控制 VSPackage |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c3fac86583126e94bcfaea65a82c7cf923275769
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-source-control-vspackage"></a>建立原始檔控制 VSPackage
本文件包含連結至原始檔控制封裝與整合的架構概觀[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，API 所實作的介面，並且要取用的服務定義，說明簡單的來源的範例控制封裝的實作。  
  
 您可以使用原始檔控制 VSPackage，建立原始檔控制整合的深度整合路徑[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 它可讓封裝將略過預設原始檔控制所裝載的 UI [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、 原始檔控制要求回應來自專案系統，並與其互動[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]元件，例如**方案總管 中**。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]讓[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]夥伴使用一種機制建立 VSPackage，可以整合與[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用服務模型。  
  
## <a name="in-this-section"></a>本節內容  
 [快速入門](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 討論原始檔控制套件，也就是原始檔控制外掛程式實作中的原始檔控制功能的更進階的替代[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [架構](../../extensibility/internals/source-control-vspackage-architecture.md)  
 呈現的圖表，並說明原始檔控制套件的元件。  
  
 [功能](../../extensibility/internals/source-control-vspackage-features.md)  
 描述各種功能的原始檔控制封裝。  
  
 [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 描述結構的 VSPackage，原始檔控制封裝必須實作的深度整合。  
  
## <a name="related-sections"></a>相關章節  
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 討論如何建立原始檔控制外掛程式，提供在原始檔控制功能[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]原始檔控制使用者介面 (UI)。  
  
 [原始檔控制](../../extensibility/internals/source-control.md)  
 討論的整合功能，以及實作原始檔控制的選項[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。