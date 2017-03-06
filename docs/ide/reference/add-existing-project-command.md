---
title: "加入現有專案命令 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2fbbf03ff2e447a44bb00432be590a35dd6cb84a
ms.lasthandoff: 02/22/2017

---
# <a name="add-existing-project-command"></a>加入現有專案命令
將現有專案新增至目前的方案。  
  
## <a name="syntax"></a>語法  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 選擇項。 要新增至方案的專案完整路徑和專案名稱，包括副檔名。  
  
 如果 `filename` 引數包含空格，必須以引號括住。  
  
 如果未指定任何檔名，此命令將會開啟 [檔案] 對話方塊，以供使用者選取專案。  
  
## <a name="remarks"></a>備註  
 自動完成會在您輸入時嘗試找出正確的路徑和檔名。  
  
## <a name="example"></a>範例  
 此範例會將 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 專案 TestProject1 新增至目前的方案。  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
