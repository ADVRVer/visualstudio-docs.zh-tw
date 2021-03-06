---
title: "提供的服務 (原始檔控制 VSPackage) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6951881e915b44c0cb0c85685280f2b770647f3a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="services-provided-source-control-vspackage"></a>提供的服務 (原始檔控制 VSPackage)
服務是透過此功能會共用 Vspackage 之間，以及 Visual Studio 整合式的開發環境 (IDE) 和其安裝的 Vspackage 之間的主要機制。 如需詳細的服務和 Visual Studio IDE 中的重要性的詳細說明，請參閱[使用並提供服務](../../extensibility/using-and-providing-services.md)。  
  
## <a name="the-source-control-service"></a>原始檔控制服務  
 Visual Studio 提供兩個圖層的服務、 IDE 層級的服務和封裝層級服務。 Visual Studio IDE 原生提供 IDE 層級服務。 原始檔控制套件會使用其中某些服務。 為 VSPackage 的原始檔控制套件共用其原始檔控制功能，藉由提供自己的私用的原始檔控制服務。 原始檔控制套件封裝控制項相關合約，可供 Visual Studio IDE 的表單中所實作之介面的來源的集合。  
  
## <a name="see-also"></a>請參閱  
 [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)