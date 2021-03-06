---
title: "標籤 （偵錯介面存取 SDK） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- locations, in program code
- Label symbol
ms.assetid: 8cef7620-5bc8-4500-8bd0-e9e638bccb24
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 090ed3ca526a2fb7d36a2b6c81d2563ba254dc07
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="label-debug-interface-access-sdk"></a>標籤 (偵錯介面存取 SDK)
程式碼的位置由`SymTagLabel`符號。  
  
## <a name="properties"></a>屬性  
 下表顯示適用於此符號類型的屬性。  
  
|屬性|資料類型|描述|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|時差部分的位置。如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|區段組件的位置。如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`如果標籤使用的自訂呼叫慣例。|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`如果標籤執行遠傳回。|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`如果標籤包含來自插斷。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封入編譯、 區塊或函式的符號。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙父符號的識別碼。|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|標籤都有靜態的位置。如需詳細資訊，請參閱[符號位置](../../debugger/debug-interface-access/symbol-locations.md)列舉型別。|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|標籤的名稱。|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`如果您已指定標籤[noinline](/cpp/cpp/noinline)屬性。|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`如果您已指定標籤[noreturn](/cpp/cpp/noreturn)屬性。|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`如果從未呼叫標籤。|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|在記憶體中; 符號的位移如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)， `LocIsRegRel`。|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`如果您的程式碼偵錯最佳化程式碼的資訊。|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|此標籤在其模組中的相對位置。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回`SymTagFuncDebugLabel`(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值)。|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|此標籤的可執行檔映像的位置。|  
  
## <a name="see-also"></a>請參閱  
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)   
 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)