---
title: "在 Visual Studio for Mac 中編譯和建置"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: ea98f80d037a03912cf3d8212588ebb7520b4bbb
ms.contentlocale: zh-tw
ms.lasthandoff: 08/11/2017

---

# <a name="compiling-and-building-in-visual-studio-for-mac"></a>在 Visual Studio for Mac 中編譯和建置

Visual Studio for Mac 可用來在專案開發期間建置應用程式和建立組件。 請務必及早且經常編譯和建置您的程式碼，讓您能夠識別類型不符以及其他的編譯時期錯誤。

## <a name="choosing-a-build-method"></a>選擇建置方法：

### <a name="using-the-ide"></a>使用 IDE

使用 Visual Studio for Mac 可讓您立即建立和執行組建，同時仍然能夠控制組建功能。 Visual Studio for Mac 會使用 MSBuild 作為基礎建置系統。

在 IDE 中建立的所有專案和方案都會有預設的組建組態，以定義組建的內容。 您可以編輯這些組態，也可以建立自己的組態。 建立或修改這些組態會自動更新專案檔，MSBuild 之後會使用該檔案來建置專案。  

如需如何在 IDE 中建立專案和方案的詳細資訊，請參閱[建置和清除專案與方案](~/building-and-cleaning-projects-and-solutions.md)指南。

Visual Studio for Mac 也可用來執行下列作業：

* 變更輸出路徑。 這是在您的專案選項中進行編輯：

    ![變更輸出路徑](media/compiling-and-building-image4.png)

* 變更組建輸出的詳細資訊：

    ![變更組建的詳細資訊](media/compiling-and-building-image5.png)

* 在建置或清除之前、期間或之後加入自訂命令：

    ![新增自訂命令](media/compiling-and-building-image6.png)

### <a name="building-from-command-line"></a>從命令列建置

您可以使用 MSBuild 組建引擎，透過命令列建置應用程式。

如需使用 MSBuild 的詳細資訊，請參閱 [MSBuild](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild) 內容。

### <a name="using-visual-studio-team-services"></a>使用 Visual Studio Team Services

* [建置 Xamarin 應用程式](https://www.visualstudio.com/en-us/docs/build/apps/mobile/xamarin)
* [使用 Xamarin 的連續整合](https://developer.xamarin.com/guides/cross-platform/ci/)