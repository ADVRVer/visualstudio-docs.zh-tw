---
title: "METADATA_ADDRESS_ARRAYELEM |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords:
- METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
caps.latest.revision: 6
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
ms.openlocfilehash: eae86146d4b7fa2290a5610463bbf75ddda82bad
ms.lasthandoff: 02/22/2017

---
# <a name="metadataaddressarrayelem"></a>METADATA_ADDRESS_ARRAYELEM
此結構表示陣列中的項目陣列。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {  
   _mdToken tokMethod;  
   DWORD    dwIndex;  
} METADATA_ADDRESS_ARRAYELEM;  
```  
  
```c#  
public struct METADATA_ADDRESS_ARRAYELEM {  
   public int  tokMethod;  
   public uint dwIndex;  
}  
```  
  
## <a name="terms"></a>詞彙  
 tokMethod  
 識別碼陣列的這個項目是一部分。  
  
 [C++]`_mdToken` is a `typedef` for a 32-bit `int`.  
  
 dwIndex  
 在陣列中這個項目的索引。  
  
## <a name="remarks"></a>備註  
 此結構是在聯集的一部分[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)結構時`dwKind`欄位`DEBUG_ADDRESS_UNION`結構設`ADDRESS_KIND_ARRAYELEM`(介於[ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉型別)。  
  
## <a name="requirements"></a>需求  
 標頭︰ sh.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
