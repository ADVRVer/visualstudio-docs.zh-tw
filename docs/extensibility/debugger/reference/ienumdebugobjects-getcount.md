---
title: "IEnumDebugObjects::GetCount |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugObjects::GetCount
helpviewer_keywords: IEnumDebugObjects::GetCount method
ms.assetid: 9cbc5db4-03ae-479f-a664-13cad66ad210
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: eea93b33e82023f811e40ae706b87658dfebe6ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugobjectsgetcount"></a>IEnumDebugObjects::GetCount
這個方法會傳回在列舉中的項目數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcelt`  
 [out]列舉中傳回的項目數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法不是慣用的 COM 列舉介面會指定只有下一步、 複製、 Skip 和重設需要實作的一部分。  
  
## <a name="see-also"></a>請參閱  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)