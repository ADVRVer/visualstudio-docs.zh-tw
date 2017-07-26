---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 3
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 6e74ef38969cb62790629b34041ceef535ff6f9e
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
通知 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 合併系統上的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 套件，並檢查 MEF 快取中的任何變更。  
  
## <a name="syntax"></a>語法  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>備註  
 當您安裝 VSIX 套件時，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會自動執行此命令。 您應該在修補檔案之後執行 `devenv.exe /updateconfiguration`，讓 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 更新 MEF 快取。 這可讓您評估您的修正是否足夠。  
  
## <a name="example"></a>範例  
 下列命令列會使 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 合併系統上的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 套件，並檢查 MEF 快取中的任何變更。  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>另請參閱  
 [將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)   
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
