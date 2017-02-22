---
title: "如何︰ 安裝原始檔控制外掛程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安裝 [Visual Studio SDK]，原始檔控制外掛程式"
  - "原始檔控制外掛程式安裝"
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: 32
caps.handback.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何︰ 安裝原始檔控制外掛程式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

建立原始檔控制外掛程式包含三個步驟︰  
  
1.  與此文件的原始檔控制外掛程式 API 參考區段中定義的函式建立的 DLL。  
  
2.  實作原始檔控制外掛程式 API 定義的函式。 當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 呼叫，讓介面和對話方塊可從外掛程式。  
  
3.  藉由適當的登錄項目註冊的 DLL。  
  
## <a name="integration-with-visual-studio"></a>與 Visual Studio 整合  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援原始檔控制外掛程式符合原始檔控制外掛程式 API。  
  
### <a name="registering-the-source-control-plug-in"></a>註冊原始檔控制外掛程式  
 原始檔控制系統可以呼叫執行的整合式的開發環境 (IDE) 之前，它必須先找到原始檔控制外掛程式 API 會將匯出的 DLL。  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>若要註冊的原始檔控制外掛程式 DLL  
  
1.  指定您的公司名稱的子機碼後面接著您產品名稱的子機碼的軟體子機碼中加入 HKEY_LOCAL_MACHINE 機碼下的兩個項目。 模式是 HKEY_LOCAL_MACHINE\SOFTWARE\\*[公司名稱]*\\*[產品名稱]*\\*[entry]* = value。 SCCServerName 和 SCCServerPath，永遠會呼叫兩個項目。 每一個都是規則的字串。  
  
     例如，如果您的公司名稱是 Microsoft，以及您的原始檔控制產品會命名為 SourceSafe，則此登錄路徑會是 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe。 這個子機碼，在第一個項目，SCCServerName，是使用者可讀取的字串，命名您的產品。 第二個項目，SCCServerPath，是來源的完整路徑控制 IDE 應該連接到的外掛程式 DLL。 以下提供範例登錄項目︰  
  
    |範例登錄項目|範例值|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  SCCServerPath 是 SourceSafe 外掛程式的完整路徑。 您的原始檔控制外掛程式會使用不同的公司和產品的名稱，但相同的登錄項目路徑。  
  
2.  下列選擇性的登錄項目可以用來修改您的原始檔控制外掛程式的行為。 這些項目放在相同的子機碼為 SccServerName 和 SccServerPath。  
  
    -   如果您不想控制隨插即用-以外掛程式選擇清單中會顯示您的來源，可以使用 HideInVisualStudioregistry 項目 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 此項目也會影響自動切換至原始檔控制外掛程式。 此項目的可能用途之一，是如果您提供原始檔控制套件，以取代您的原始檔控制外掛程式，但您想要更方便使用的外掛程式，以便在原始檔控制套件的原始檔控制移轉使用者。 安裝原始檔控制套件時，它會將此登錄項目，會隱藏外掛程式。  
  
         HideInVisualStudio 是 DWORD 值，並設為 1，即可隱藏外掛程式或 0，以顯示外掛程式。 如果未出現的登錄項目，預設行為是顯示外掛程式。  
  
    -   DisableSccManager 登錄項目可以用來停用或隱藏 **啟動 \< 原始檔控制伺服器>** 通常會在出現的功能表選項 **檔案** -> **原始檔控制** 子功能表。 選取此功能表選項呼叫 [SccRunScc](../../extensibility/sccrunscc-function.md) 函式。 您的原始檔控制外掛程式可能不支援外部程式，因此您可能想要停用或甚至隱藏 **啟動** 功能表選項。  
  
         DisableSccManager 是 DWORD 值會設定為 0，以便於 **啟動 \< 原始檔控制伺服器>** 功能表選項設為 1 可停用功能表選項，並以隱藏功能表選項設定為 2。 如果未出現此登錄項目，預設行為是顯示功能表選項。  
  
    |範例登錄項目|範例值|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  新增子機碼，SourceCodeControlProvider，HKEY_LOCAL_MACHINE 機碼中的軟體子機碼。  
  
     這個子機碼下的登錄項目 ProviderRegKey 設為字串，表示您放置在步驟 1 中的登錄子機碼。 模式是 HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey = SOFTWARE\\*[公司名稱]*\\*[產品名稱]*。  
  
     以下是這個子機碼的範例內容。  
  
    |登錄項目|範例值|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  您的原始檔控制外掛程式會使用相同的子機碼和項目名稱，但值可能會不同。  
  
4.  建立名為 InstalledSCCProviders，SourceCodeControlProvider 子機碼下的子機碼，然後將該子機碼下的一個項目。  
  
     這個項目的名稱 （如同 SCCServerName 項目指定的值），提供者的使用者可讀名稱且值為，同樣地，在步驟 1 中建立的子機碼。 模式是 HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\*[顯示名稱]* = SOFTWARE\\*[公司名稱]*\\*[產品名稱]*。  
  
     例如：  
  
    |範例登錄項目|範例值|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  可以有多個原始檔控制外掛程式在這種方式中註冊。 這是如何 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 尋找所有已安裝原始檔控制外掛程式 API 為基礎的外掛程式。  
  
## <a name="how-an-ide-locates-the-dll"></a>IDE 如何找出 DLL  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 提供兩種尋找來源控制外掛程式 DLL:  
  
-   尋找預設原始檔控制外掛程式，並以無訊息方式連線到它。  
  
-   尋找所有已註冊的原始檔控制外掛程式，從中使用者選擇其中一個。  
  
 若要尋找之 DLL 中第一種方式，IDE 會尋找項目 ProviderRegKey HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider 子機碼下。 此項目的值會指向另一個子機碼。 IDE 接著會尋找名為 SccServerPath，HKEY_LOCAL_MACHINE 底下的第二個子機碼中的項目。 此項目的值會指向 DLL 中的 IDE。  
  
> [!NOTE]
>  IDE 不會從相對路徑 (例如，.\NewProvider.DLL) 載入 Dll。 必須指定 DLL 的完整路徑 (例如，c:\Providers\NewProvider.DLL)。 這可防止未經授權或模擬外掛程式 Dll 的載入加強 IDE 的安全性。  
  
 若要找的 DLL 中的第二個方法，IDE 會尋找所有項目的 HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders 子機碼下*。* 每個項目都有一個名稱和值。 IDE 會向使用者顯示這些名稱的清單*。* 當使用者選擇的名稱時，IDE 會尋找所選取之名稱的子機碼值。 IDE 會尋找名為 SccServerPath，HKEY_LOCAL_MACHINE 底下的子機碼中的項目。 該項目的值會指向正確的 DLL 中的 IDE。  
  
 原始檔控制外掛程式必須支援找出 DLL 的這兩種方式，因此，設定 ProviderRegKey，覆寫任何先前的設定。 更重要的是，它必須將本身加入 InstalledSccProviders 清單讓使用者可以選擇来使用的原始檔控制外掛程式。  
  
> [!NOTE]
>  因為使用 HKEY_LOCAL_MACHINE 機碼時，只有一個原始檔控制外掛程式可以登錄為預設原始檔控制外掛程式指定的電腦上 (不過， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 讓使用者可以判斷哪一個原始檔控制外掛程式他們想要實際上是使用特定的解決方案)。 在安裝過程中，存回原始檔控制外掛程式是否已設定。如果是這樣，，詢問使用者要設定新的原始檔控制外掛程式安裝為預設值。 在解除安裝期間請勿移除通用於所有原始檔控制外掛程式 HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider; 在其他登錄子機碼移除只您特定 SCC 子機碼。  
  
## <a name="how-the-ide-detects-version-1213-support"></a>IDE 會 1.2/1.3 版支援的偵測  
 如何沒有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵測是否外掛程式支援原始檔控制外掛程式 API 版本 1.2 和 1.3 功能嗎？ 若要宣告進階的功能，原始檔控制外掛程式必須實作對應的函式。  
  
 首先， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會檢查呼叫所傳回的值 [SccGetVersion](../../extensibility/sccgetversion-function.md)。 它必須是大於或等於 1.2。  
  
 下一步] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 判斷是否支援特定的新功能檢查 `lpSccCaps` 引數上的 [SccInitialize](../../extensibility/sccinitialize-function.md)。  
  
 如果這些條件都符合，就可以呼叫在 1.2 和 1.3 版所支援的新函數。  
  
## <a name="see-also"></a>請參閱  
 [開始使用](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)