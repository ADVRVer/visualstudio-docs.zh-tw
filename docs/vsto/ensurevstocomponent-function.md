---
title: "EnsureVSTOComponent 函式 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 78c56c26edaa6539eb3b7c385392fca5f276014d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="ensurevstocomponent-function"></a>EnsureVSTOComponent 函式
  這個 API 支援 Office 基礎結構，並不適合直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*pProject*|請勿使用。|  
  
## <a name="return-value"></a>傳回值  
 如果函式成功，它會傳回**S_OK**。 如果函式失敗，它會傳回錯誤碼。  
  
  