---
title: "IRemoteDebugApplication::EnumGlobalExpressionContexts |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplication.EnumGlobalExpressionContexts
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplication::EnumGlobalExpressionContexts
ms.assetid: 61598a34-f409-42a2-810d-a9e92e2f4861
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99a805d810c928e8e9a1b6f4e569f8eaa89f63d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationenumglobalexpressioncontexts"></a>IRemoteDebugApplication::EnumGlobalExpressionContexts
列舉執行此應用程式中的所有語言通用的運算式內容。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumGlobalExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppedec`  
 [out]列出此應用程式中執行的所有語言通用的運算式內容的列舉值。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會列舉此應用程式中執行的所有語言通用的運算式內容。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)