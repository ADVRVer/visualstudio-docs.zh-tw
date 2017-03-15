---
title: "IDebugCoreServer2::GetMachineUtilities_V7 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8cec5befece6b3415a903ed84d8d31cbe3988ee8
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
這個方法會取得伺服器的機器公用程式。  
  
> [!NOTE]
>  這個方法已過時︰ 不要使用 ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]一律會傳回`E_NOTIMPL`如果呼叫此方法)。 它會保留歷史的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```c#  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppUtil`  
 [out]傳回`IDebugMDMUtil2_V7`代表機器公用程式資訊的介面。  
  
## <a name="return-value"></a>傳回值  
 一律傳回`E_NOTIMPL`，指出方法未實作。  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]一律傳回`E_NOTIMPL`如果在呼叫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
