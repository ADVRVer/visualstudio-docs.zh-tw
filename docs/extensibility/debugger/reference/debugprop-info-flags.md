---
title: "DEBUGPROP_INFO_FLAGS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
caps.latest.revision: 11
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
ms.openlocfilehash: c5b749cffbc05fcc3fa6c533dc4bb3bdcd1ad1c0
ms.lasthandoff: 02/22/2017

---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
指定要擷取偵錯屬性物件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## <a name="members"></a>Members  
 DEBUGPROP_INFO_FULLNAME  
 初始化/使用`bstrFullName`欄位。  
  
 DEBUGPROP_INFO_NAME  
 初始化/使用`bstrName`欄位。  
  
 DEBUGPROP_INFO_TYPE  
 初始化/使用`bstrType`欄位。  
  
 DEBUGPROP_INFO_VALUE  
 初始化/使用`bstrValue`欄位。  
  
 DEBUGPROP_INFO_ATTRIB  
 初始化/使用`dwAttrib`欄位。  
  
 DEBUGPROP_INFO_PROP，  
 初始化/使用`pProperty`欄位，其中包含[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面。  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 指定 [值] 欄位應包含的自動展開的值，是否有的話，這種類型的物件。  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 已取代。  
  
 DEBUGPROP_INFO_VALUE_RAW  
 不會傳回任何 beautified 的值或成員 （也就是不會格式化值）。  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 不會傳回任何特殊的合成的值 (例如，請勿呼叫`ToString()`上用來產生值的物件)。  
  
 DEBUGPROP_INFO_NONE  
 指定設定任何旗標。  
  
 DEBUGPROP_INFO_STANDARD  
 初始化/使用`dwAttrib`， `bstrName`， `bstrType`，和`bstrValue`欄位。  
  
 DEBUGPROP_INFO_All  
 表示所有旗標的遮罩。  
  
## <a name="remarks"></a>備註  
 這些值會傳遞給[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)， [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)，和[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)方法以指出哪些欄位是初始化[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構。  
  
 這些值也會用於`dwFields`成員`DEBUG_PROPERTY_INFO`結構，表示結構的哪些欄位已使用和有效時，會傳回這個結構。  
  
 這些值可結合的位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭︰ msdbg.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
