---
title: "Idiasourcefile:: Get_checksum |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3cc815608c1871de7269a432e02f95acbb3e0d81
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
會將位元組擷取總和檢查碼。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cbData`  
 [in]資料緩衝區，以位元組為單位的大小。  
  
 `pcbData`  
 [out]傳回總和檢查碼的位元組的數目。 此參數不得為`NULL`。  
  
 `data`  
 [in、 out]緩衝區填滿的總和檢查碼位元組。 如果這個參數是`NULL`，然後`pcbData`傳回所需的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 若要決定用來產生總和檢查碼位元組的總和檢查碼演算法的類型，請呼叫[idiasourcefile:: Get_checksumtype](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)方法。  
  
 總和檢查碼通常會產生從來源檔案的映像，所以原始程式檔中的變更會反映在總和檢查碼 （位元組） 的變更。 如果不相符的總和檢查碼位元組產生從載入的映像的檔案，則應該視為檔案的總和檢查碼損毀或遭到竄改。  
  
 典型的總和檢查碼絕不會超過 32 個位元組的大小，但不是會假設這是最大大小的總和檢查碼。 設定`data`參數`NULL`取得擷取總和檢查碼所需的位元組數目。 然後配置適當大小的緩衝區，並呼叫這個方法一次使用新的緩衝區。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)