---
title: "IDebugProcess2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2
helpviewer_keywords: IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 896448526f41514fb74b385f8605839908708305
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2"></a>IDebugProcess2
此介面代表連接埠上執行的處理序。 如果連接埠是本機連接埠，則`IDebugProcess2`通常表示本機電腦上的實體程序。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 若要以群組方式管理程式自訂連接埠供應商被實作這個介面。 連接埠提供者必須實作這個介面。  
  
 偵錯引擎也會實作這個介面，如果支援啟動透過程式[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面稱為主要是由工作階段的偵錯管理員 (SDM) 才能與此程序所識別的程式群組互動。  
  
 呼叫[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)或[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)取得此介面。 此介面也會傳回呼叫`IDebugEngineLaunch2::LaunchSuspended`。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugProcess2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|取得處理序的描述。|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|列舉包含在此程序中的程式。|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|取得標題、 易記名稱或檔案的處理序名稱。|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|取得的 server 執行此程序之機器的執行個體。|  
|[終止](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|終止處理序。|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|附加至處理序。|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|決定是否 SDM 可以卸離程序。|  
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|從處理序偵錯工具會中斷連結。|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|取得系統處理序識別碼。|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|取得這個處理序的全域唯一識別碼。|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [DEPRECATED]|取得正在偵錯的處理程序之工作階段的名稱。<br /><br /> [已被取代。 應該永遠傳回`E_NOTIMPL`。]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|列舉處理序中執行的執行緒。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|要求在此處理程序停止執行程式碼的下一個程式。|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|取得連接埠上執行此程序。|  
  
## <a name="remarks"></a>備註  
 `IDebugProcess2`包含一或多個[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)