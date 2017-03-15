---
title: "替代字串中使用。Pkgdef 和。Pkgundef 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 4
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: c64a760b821663ba488f6f9dab415bad13d6047d
ms.lasthandoff: 02/22/2017

---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>替代字串中使用。Pkgdef 和。Pkgundef 檔案
您可以使用列在下面.pkgdef 將替代字串和.pkgundef 檔案，您定義您的 Visual Studio 隔離 shell 應用程式。  
  
## <a name="substitution-strings"></a>替代字串  
  
|字串|描述|  
|------------|-----------------|  
|$=*RegistryEntry*$|值*RegistryEntry*項目。 如果登錄項目字串的結尾反斜線 (\\)，則會使用預設值的登錄子機碼。 例如，替代字串 $= 的 HKEY_CURRENT_USER\Environment\TEMP$ 展開目前使用者的暫存資料夾。|  
|$AppName $|傳遞至 AppEnv.dll 進入點的應用程式限定的名稱。 限定的名稱是由應用程式名稱、 底線和應用程式的自動化物件，也會記錄為 ThisVersionDTECLSID 設定專案.pkgdef 檔中的值的類別識別項 (CLSID) 所組成。|  
|$AppDataLocalFolder|此應用程式 %LOCALAPPDATA%底下的子資料夾。|  
|$BaseInstallDir $|安裝 Visual Studio 所在位置的完整路徑。|  
|$CommonFiles $|%Commonprogramfiles%環境變數的值。|  
|$MyDocuments $|目前使用者的 [我的文件] 資料夾的完整路徑。|  
|$PackageFolder $|包含應用程式的封裝組件檔的目錄完整路徑。|  
|$ProgramFiles $|%Programfiles%環境變數的值。|  
|$RootFolder $|應用程式的根目錄完整路徑。|  
|$RootKey $|應用程式的根登錄機碼。 預設的根是在 HKEY_CURRENT_USER\Software\\*CompanyName*\\*ProjectName*\\*VersionNumber* （當應用程式執行時，_Config 會附加至這個索引鍵）。 設定中的 RegistryRoot 值*SolutionName*.pkgdef 檔。<br /><br /> $RootKey$ 字串可以用來擷取應用程式的子機碼下的登錄值。 例如，字串"$= $RootKey$ \AppIcon$"會傳回應用程式根目錄的子機碼下 AppIcon 項目的值。<br /><br /> 剖析器，循序處理.pkgdef 檔和先前已定義的項目時，才可以存取應用程式的子機碼下的登錄項目|  
|$ShellFolder $|安裝 Visual Studio 所在位置的完整路徑。|  
|$System $|Windows\system32 資料夾中。|  
|$WINDIR $|[Windows] 資料夾中。|  
  
 如果剖析器不會辨識替代字串，或是無法判定登錄項目或環境變數的值，則它不會執行替代字串的一部分。
