---
title: "主要和當地語系化附屬組件的版本號碼 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 12
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 555205ade620de3ad46f0fab34d50b85cbed5e40
ms.contentlocale: zh-tw
ms.lasthandoff: 05/30/2017

---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>主要和當地語系化附屬組件的版本號碼
<xref:System.Resources.SatelliteContractVersionAttribute> 類別針對透過資源管理員使用當地語系化資源的主要組件提供了版本控制支援。 將 <xref:System.Resources.SatelliteContractVersionAttribute> 套用至應用程式的主要組件，可讓您更新和重新部署該組件，而不需要更新其附屬組件。 例如，您可以搭配未引進新資源的 Service Pack 使用 <xref:System.Resources.SatelliteContractVersionAttribute> 類別，而不需要重建和重新部署您的附屬組件。 若要使用當地語系化資源，主要組件的附屬合約版本必須與附屬組件的 <xref:System.Reflection.AssemblyVersionAttribute> 類別相符。 您必須在 <xref:System.Resources.SatelliteContractVersionAttribute> 中指定確切的版本號碼；不允許萬用字元，例如 "*"。 如需詳細資訊，請參閱[擷取資源](/dotnet/framework/resources/retrieving-resources-in-desktop-apps)。  
  
## <a name="updating-assemblies"></a>更新組件  
 <xref:System.Resources.SatelliteContractVersionAttribute> 類別可讓您更新主要組件，而不需要更新您的附屬組件，反之亦然。 更新主要組件時，即會變更其組件版本號碼。 如果您要繼續使用現有附屬組件，請變更主要組件的版本號碼，但保留附屬合約版本號碼不變。 例如，第一次發行時，您的主要組件版本可能是 1.0.0.0。 附屬合約版本和附屬組件的組件版本也會是 1.0.0.0。 如果您因為 Service Pack 而需要更新主要組件，您可以將組件版本變更為 1.0.0.1，但將附屬合約版本和附屬組件版本保留為 1.0.0.0。  
  
 如果您需要更新附屬組件而不是主要組件，可以變更附屬組件的 <xref:System.Reflection.AssemblyVersionAttribute>。 除了交付附屬組件之外，您還必須附上原則組件來說明新的附屬組件與舊的附屬組件相容。 如需原則的詳細資訊，請參閱[執行階段如何找出組件](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)。  
  
 下列程式碼示範如何設定附屬合約版本。 您可以將這段程式碼放入建置指令碼或是 AssemblyInfo.vb 或 AssemblyInfo.cs 檔中。  
  
```vb#  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```c#  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段如何找出組件](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)   
 [設定組件屬性](/dotnet/framework/app-domains/set-assembly-attributes)   
 [安全性和當地語系化附屬組件](../ide/security-and-localized-satellite-assemblies.md)   
 [當地語系化應用程式](../ide/localizing-applications.md)   
 [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)
