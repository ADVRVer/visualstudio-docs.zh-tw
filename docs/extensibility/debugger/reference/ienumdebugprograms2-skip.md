---
title: "IEnumDebugPrograms2::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPrograms2::Skip"
helpviewer_keywords: 
  - "IEnumDebugPrograms2::Skip"
ms.assetid: b283858b-b375-4760-bfec-ab37de89958d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPrograms2::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

略過指定的項目數。  
  
## 語法  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### 參數  
 `celt`  
 \[in\]若要跳過的項目數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果`celt`大於其餘的項目 ； 數目 否則，會傳回錯誤碼。  
  
## 備註  
 如果`celt`指定的值是無效的其餘的項目，列舉型別設定為 \[結束和`S_FALSE`會傳回。  
  
## 請參閱  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)