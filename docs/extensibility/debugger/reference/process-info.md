---
title: "PROCESS_INFO |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 9
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
ms.openlocfilehash: 791686d7ab4516f5eb4da0642d97acb9df730f12
ms.lasthandoff: 02/22/2017

---
# <a name="processinfo"></a>PROCESS_INFO
包含處理序的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```c#  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>Members  
 欄位  
 從旗標的組合[PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)指定哪些欄位都已填寫的列舉型別。  
  
 bstrFileName  
 程序的完整路徑名稱。 相當於呼叫[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)方法與參數`GN_FILENAME`。  
  
 bstrBaseName  
 檔案名稱和副檔名的處理程序。 相當於呼叫`IDebugProcess2::Getname`方法與參數`GN_BASENAME`。  
  
 bstrTitle  
 此程序，如果有標題。 相當於呼叫`IDebugProcess2::Getname`方法與參數`GN_TITLE`。  
  
 ProcessId  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)識別處理序的結構。 相當於呼叫[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)方法。  
  
 dwSessionId  
 偵錯工作階段中執行此程序的識別碼。  
  
 bstrAttachedSessionName  
 附加工作階段名稱。 相當於呼叫[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)方法。  
  
 CreationTime  
 建立處理程序的時間。  
  
 旗標  
 從旗標的組合[PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)列舉，指定屬性的程序。  
  
## <a name="remarks"></a>備註  
 此結構會傳遞至[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)填滿其中的方法。  
  
## <a name="requirements"></a>需求  
 標頭︰ msdbg.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
