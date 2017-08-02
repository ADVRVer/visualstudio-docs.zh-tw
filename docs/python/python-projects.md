---
title: "Visual Studio 中的 Python 專案 | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9c53f76-d0ef-4095-8b39-b7eb9bb33aba
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 3190be68fbba464a84a7a25b2d829979944bdb1f
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---

# <a name="python-projects"></a>Python 專案

定義 Python 應用程式時，通常僅使用資料夾和檔案，但隨著應用程式變得越來越大，這可能會變得相當複雜，且可能牽涉到自動產生的檔案、Web 應用程式的 JavaScript 等。 為了協助管理此複雜性，您可以針對 Python 應用程式建立 Visual Studio 專案。 Python 專案 (`.pyproj` 檔案) 會識別與您專案關聯的所有來源和內容檔案、包含每個檔案的建置資訊、維護要與來源控制系統整合的資訊，以及協助您將應用程式組織成邏輯元件。

此外，您一律是在 Visual Studio 的「方案」內管理專案，方案中可以包含任意數目、可能彼此參考的專案。 例如，Python 專案可以參考延伸模組的 C++ 專案，如此一來，當您開始對 Python 專案進行偵錯時，Visual Studio 將會自動建置 C++ 專案 (如有必要)。 (如需一般的討論，請參閱 [Visual Studio 中的方案和專案](../ide/solutions-and-projects-in-visual-studio.md))。

![[方案總管] 中的 Python 專案](~/docs/python/media/projects-solution-explorer.png)

Visual Studio 提供各種 Python 專案範本，可讓您快速設定一些應用程式結構，包括可從現有資料夾樹狀目錄建立專案的範本，以及可建立乾淨空專案的範本。 如需相關索引，請參閱下面的[專案範本](#project-templates)。

本主題內容：

- [新增檔案、指派啟動檔案及設定環境](#adding-files-assigning-a-startup-file-and-setting-environments)
- [專案範本](#project-templates)
- [連結的檔案](#linked-files)
- [參考](#references)

<a name="lightweight-usage-project-free"</a>
> [!Tip]
> 即使在沒有專案的情況下，Visual Studio 也能夠與 Python 程式碼順暢搭配運作，您可以單獨開啟 Python 檔案來享用自動完成、IntellSense 及偵錯功能 (透過在編輯器中按一下滑鼠右鍵，然後選取 [開始偵錯] 或 [啟動但不偵錯])。 因為這類程式碼一律會使用預設全域環境，不過，如果程式碼是針對不同的環境，您可能就會看到不正確的完成或錯誤。 此外，Visual Studio 還會分析您從中開啟單一檔案之資料夾中的所有檔案和套件，這可能會耗費相當多的 CPU 時間。
>
> 從現有的程式碼建立 Visual Studio 專案相當簡單，如下面的[從現有的檔案建立專案](#creating-a-project-from-existing-files)所述。

如需 Visual Studio 中 Python 專案的簡介，請參閱[開始使用 Python 工具第 2 部：專案 (英文)](https://youtu.be/KHPoVpL7zHg?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) (youtube.com，3 分鐘 18 秒)。

> [!VIDEO https://www.youtube.com/embed/KHPoVpL7zHg]

另請參閱[深度剖析：使用原始檔控制搭配 Python 專案 (英文)](https://youtu.be/Aq8eqApnugM) 影片 (youtube.com，8 分鐘 55 秒)。

> [!VIDEO https://www.youtube.com/embed/Aq8eqApnugM]


## <a name="adding-files-assigning-a-startup-file-and-setting-environments"></a>新增檔案、指派啟動檔案及設定環境

當您開發應用程式時，通常需要將不同類型的新檔案新增到專案中。 您可以輕鬆執行此操作，方法是在專案上按一下滑鼠右鍵，然後選取 [新增] > [現有項目]，使用此方式時，您可以瀏覽要新增的檔案；或是選取 [新增] > [新項目]，這會顯示一個對話方塊，內含各種項目範本，包括空白的 Python 檔案、Python 類別、單元測試及與 Web 應用程式相關的各種檔案。 我們鼓勵您使用測試專案來探索這些選項，以了解您的 Visual Studio 版本中提供哪些選項。

每個 Python 專案都有一個指派的啟動檔案，在 [方案總管] 中是以粗體顯示。 這是當您開始偵錯 (F5 或 [偵錯] > [開始偵錯]) 時所執行的檔案，或是在互動式視窗中執行專案 (Shift+Alt+F5 或 [偵錯] > [Execute Project in Python Interactive] (在 Python 互動式視窗中執行專案)) 時所執行的檔案。 若要變更它，請在新檔案上按一下滑鼠右鍵，然後選取 [啟動檔案]。

> [!Tip]
> 如果您從專案移除選取的啟動檔案，且不選取新的啟動檔案，則嘗試執行專案會造成出現 Python 輸出視窗，但接著幾乎立即消失。 如果您遇到這個問題，請確認您已指派啟動檔案。 此外，若要在此情況下讓輸出視窗保持開啟，請以滑鼠右鍵按一下專案，依序選取 [屬性]**、**[偵錯] 索引標籤，然後將 `-i` 加入 [解譯器引數] 欄位。 這會導致程式完成之後，解譯器進入互動模式，並在您輸入 Ctrl + Z、Enter 以結束之前保持視窗開啟。

新專案一律會與預設的全域 Python 環境關聯。 若要將專案與不同的環境 (包括虛擬環境) 建立關聯，請在專案中的 [Python Environments (Python 環境)] 節點上按一下滑鼠右鍵，選取 [Add/Remove Python Environments (新增/移除 Python 環境)]，然後選取您想要的環境。 若要變更作用中的環境，請在想要的環境上按一下滑鼠右鍵，然後選取 [Activate Environment (啟用環境)]。 如需更多詳細資料，請參閱 [Python 環境](python-environments.md#project-specific-environments)。

![啟用 Python 專案的環境](~/docs/python/media/projects-activate-environment.png)

<a name="project-types"</a>
## <a name="project-templates"></a>專案範本

Visual Studio 提供您一些方法來建立 Python 專案，不論是從頭開始或是從現有的程式碼，都可以。 若要使用範本，請選取 [檔案] > [新增] > [專案] 功能表命令，或在 [方案總管] 中的方案上按一下滑鼠右鍵，然後選取 [新增] > [新增專案]，這兩種方式都會顯示以下的 [新增專案] 對話方塊。 若要查看 Python 特定的範本，請依據 "Python" 進行搜尋或選取 [範本] > [其他語言] > [Python] 節點：

![含有 Python 範本的 [新增專案] 對話方塊](~/docs/python/media/projects-new-project-dialog.png)

下表摘要說明 Visual Studio 2017 中可用的範本 (並非所有範本在所有舊版中都有提供)：

| 範本 | 描述 | 
| --- | --- |
| [從現有的 Python 程式碼](#creating-a-project-from-existing-files) | 從資料夾結構中的現有 Python 程式碼建立 Visual Studio 專案。  |
| Python 應用程式 | 具有單一空白原始程式檔的新 Python 應用程式基本專案結構。 根據預設，專案會在預設全域環境的主控台解譯器中執行，您可以透過[指派不同的環境](python-environments.md#project-specific-environments)來變更此環境。 |
| [Azure 雲端服務](template-azure-cloud-service.md) | 以 Python 撰寫的「Azure 雲端服務」專案。 |
| [Web 專案](template-web.md) | 以各種架構 (包括 Bottle、Django、Flask 及 Flask/Jade) 為基礎的 Web 伺服器專案。 |
| IronPython 應用程式 | 與「Python 應用程式」範本類似，但預設使用 IronPython，可藉由 .NET 語言啟用 .NET 互通性及混合模式偵錯。 |
| IronPython WPF 應用程式 | 一種針對應用程式的使用者介面使用 IronPython 搭配 Windows Presentation Foundation XAML 檔案的專案結構。 Visual Studio 會提供 XAML UI 設計工具、程式碼後置可以用 Python 來撰寫，應用程式則會在不顯示主控台的情況下執行。 |
| IronPython Silverlight 網頁 | 一種使用 Silverlight 在瀏覽器中執行的 IronPython 專案。 應用程式的 Python 程式碼會以指令碼的形式包含在網頁中。 樣板指令碼標記會向下拖曳出一些 JavaScript 程式碼，這些程式碼會將在 Silverlight 內部執行的 IronPython 初始化，而您的 Python 程式碼便可從中與 DOM 互動。 |
| IronPython Windows Forms 應用程式 | 一種使用 IronPython 的專案結構，其中是使用程式碼搭配 Windows Forms 來建立 UI。 應用程式會在不顯示主控台的情況下執行。 |
| 背景應用程式 (IoT) | 支援將 Python 專案部署成在裝置上以背景服務的形式執行。 如需詳細資訊，請瀏覽 [Windows IoT 開發人員中心](https://dev.windows.com/en-us/iot)。 |
| Python 延伸模組 | 如果您已在 Visual Studio 2017 中搭配 Python 工作負載安裝「Python 原生開發工具」(請參閱[安裝](installation.md))，此範本會出現在 Visual C++ 底下。 它提供的 C++ 延伸模組 DLL 的核心結構，類似於[建立適用於 Python 的 C++ 延伸模組](cpp-and-python.md)中所述。 |

<a name="create-project-from-existing-files"</a>
### <a name="creating-a-project-from-existing-files"></a>從現有的檔案建立專案

1. 選取 [檔案] > [新增] > [專案] 功能表，然後選取 [從現有的 Python 程式碼] 範本。
1. 在下列對話方塊中，設定您現有程式碼的路徑、檔案類型的篩選，以及您專案所需的任何搜尋路徑，然後選取 [下一步]：

    ![來自現有程式碼的新專案 (步驟一)](~/docs/python/media/projects-from-existing-1.png)

1. 選擇專案的環境和啟動檔案，然後按 [下一步]。 (請注意，此對話方塊只會顯示在資料夾樹狀目錄根目錄中的檔案；如果您想要的檔案在子資料夾中，請將啟動檔案保留空白，稍後再於 [方案總管] 中設定它)。

    ![來自現有程式碼的新專案 (步驟二)](~/docs/python/media/projects-from-existing-2.png)

1. 選取要儲存專案檔的位置 (這不會移動或複製原始的原始程式檔，因此如果您想要一個複本，就應該在使用範本之前先建立該複本)。 在這個對話方塊中，您也可以包含虛擬環境的自動偵測，以及自訂適用於不同 Web 架構的專案。

    ![來自現有程式碼的新專案 (步驟三)](~/docs/python/media/projects-from-existing-3.png)

1.  選取 [完成]，Visual Studio 就會建立專案並在 [方案總管] 中開啟它。 如果您想要將 .pyproj 檔案移到其他地方，請在 [方案總管] 中選取它，然後選擇 [檔案] > [另存新檔]。 這會更新專案中的檔案參考，但不會移動任何程式碼檔案。

## <a name="linked-files"></a>連結的檔案

連結的檔案係指已導入專案中但通常位於應用程式專案資料夾外的檔案。 它們在 [方案總管] 中會顯示為帶有重疊捷徑圖示的一般檔案： ![[連結的檔案] 圖示](~/docs/python/media/projects-linked-file-icon.png)

指定連結的檔案時，是在 `.pyproj` 檔案中使用一般的 `<Compile Include="...">` 元素來指定。 它們可以是隱含的連結檔案 (如果它們使用位於目錄結構外的相對路徑)，也可以是明確的連結檔案 (如果在 [方案總管] 內指定它們的路徑)：

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

在下列任一情況下，將會忽略連結的檔案：

- 連結的檔案包含 Link 中繼資料，且 Include 屬性中指定的路徑是在專案目錄內
- 連結的檔案與專案階層中已存在的檔案重複
- 連結的檔案包含 Link 中繼資料，且 Link 路徑是位於專案階層外的相對路徑
- 連結路徑是根目錄

### <a name="working-with-linked-files"></a>使用連結的檔案

若要新增現有的項目作為連結，請在專案中您要新增檔案的資料夾上按一下滑鼠右鍵，然後選取 [新增] > [現有項目]。 在顯示的對話方塊中，選取檔案，然後從 [新增] 按鈕上的下拉式清單中選擇 [加入連結]。 在沒有任何衝突檔案的情況下，這會在選取的資料夾中建立連結。 不過，如果已經有相同名稱的檔案存在，或專案中已經有該檔案的連結存在，就不會新增連結。

如果您嘗試連結到已經存在於專案資料夾中的檔案，系統將會把它新增為一般檔案而不是連結。 若要將檔案轉換成連結，請選取 [檔案] > [另存新檔] 來將檔案儲存在專案階層外的位置；Visual Studio 將會自動將它轉換成連結。 同樣地，您也可以使用 [檔案] > [另存新檔] 來將檔案儲存在專案階層內的某個位置。 

如果您在 [方案總管] 中移動某個連結的檔案，將會移動該連結，但實際的檔案則不受影響。 同樣地，刪除某個連結將會移除該連結，但不會影響到檔案。

您無法重新命名連結的檔案。

## <a name="references"></a>參考

Visual Studio 專案支援新增對專案和擴充功能的參考，這些參考會顯示在 [方案總管] 中的 [參考] 節點底下：

![Python 專案中的擴充功能參考](~/docs/python/media/projects-extension-references.png)

擴充功能參考通常會指出專案之間的相依性，並可用來在設計階段提供 IntelliSense 或在編譯階段提供連結。 Python 專案使用參考的方式類似，但由於 Python 的動態本質緣故，因此主要是在設計階段使用參考來提供改進的 IntelliSense。 您也可以使用它們來部署到 Microsoft Azure 以安裝額外的相依性。

### <a name="extension-modules"></a>延伸模組

對 `.pyd` 檔案的參考可以為產生的模組啟用 IntelliSense。 Visual Studio 會將 `.pyd` 檔案載入到 Python 解譯器，並自我檢查其型別和函式。 它也會嘗試剖析文件字串來找出提供簽章說明的函式。

在任何時候，只要更新了磁碟上的擴充模組，Visual Studio 都會在背景中重新分析該模組。 這對執行階段行為並沒有影響，但在分析完成前，可能會無法使用某些完成項。

您可能也需要新增包含該模組之資料夾的[搜尋路徑](python-environments.md#search-paths)。

### <a name="net-projects"></a>.NET 專案

使用 IronPython 時，您可以新增對 .NET 組件的參考來啟用 IntelliSense。 針對您方案中的 .NET 專案，請在 Python 專案中的 [參考] 節點上按一下滑鼠右鍵，依序選取 [加入參考]、[專案] 索引標籤，然後瀏覽至想要的專案。 針對您已個別下載的 DLL，請改為選取 [瀏覽] 索引標籤，然後瀏覽至想要的 DLL。

由於 IronPython 的參考必須等到呼叫 `clr.AddReference('AssemblyName')` 之後才可供使用，因此您還必須將 `clr.AddReference` 呼叫新增到組件中。

### <a name="webpi-projects"></a>WebPI 專案

您可以新增對 WebPI 產品項目的參考以供部署到「Microsoft Azure 雲端服務」，然後在該處透過 WebPI 摘要來安裝額外的元件。 根據預設，顯示的摘要是 Python 特定的，並且包含 Django、CPython 及其他核心元件。 您也可以選取自己的摘要，如以下所示。 當發佈到 Microsoft Azure 時，安裝作業將會安裝所有參考的產品。

![WebPI 參考](~/docs/python/media/projects-webPI-components.png)
