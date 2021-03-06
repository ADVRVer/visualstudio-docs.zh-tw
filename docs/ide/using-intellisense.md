---
title: "使用 IntelliSense | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- IntelliSense, Complete Word
- IntelliSense, completion mode
- parameter information
- IntelliSense, List Members
- Quick Info
- Parameter Info
- IntelliSense [Visual Studio]
- IntelliSense, suggestion mode
- IntelliSense, Parameter Info
- IntelliSense, customizing
- Complete Word
- IntelliSense
- List Members
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 42e34f5933d06bf9021ff8e0cab5b12f316ef52e
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="using-intellisense"></a>Using IntelliSense

IntelliSense 是一些功能的概括詞彙：列出成員、參數資訊，快速諮詢和自動完成文字。 這些功能有助於深入了解您使用的程式碼，追蹤所輸入的參數，以及幾個按鍵即可加入屬性和方法呼叫。

IntelliSense 的許多方面是特定語言專屬的。 如需不同語言之 IntelliSense 的詳細資訊，請參閱[另請參閱](#see-also)小節中所列的主題。

## <a name="list-members"></a>列出成員

類型 (或命名空間) 中的有效成員清單隨即在您輸入觸發字元 (例如，Managed 程式碼中的句點 (`.`) 或 C++ 中的 `::`) 之後出現。 如果您繼續鍵入字元，則會篩選清單，只包含以這些字元開頭的成員，或名稱內「任何」字組開頭是以這些字元開頭的成員。 IntelliSense 也會執行「駝峰式大小寫」比對，因此您可以只鍵入成員名稱中每個駝峰式大小寫字組的第一個字母以查看相符項目。

選取項目之後，您可以按 **Tab** 鍵或鍵入一個空格，將它插入程式碼中。 如果您選取項目並輸入句號，則項目出現時，後面會接著句號，並顯示另一個成員清單。 當您選取某項目時，在插入項目前，會取得項目的快速諮詢。

在成員清單中，左方的圖示代表成員的類型，如命名空間、類別、函式或變數。 如需圖示清單，請參閱[類別檢視和物件瀏覽器圖示](../ide/class-view-and-object-browser-icons.md)。 清單可能相當長，因此您可以按 **PgUp** 和 **PgDn**，以在清單中上下移動。

![Visual Studio 成員清單](../ide/media/vs2015_intellisense.png "vs2015_Intellisense")

您可以鍵入 **CTRL** + **J**，並選擇 [編輯] > [IntelliSense] > [列出成員]，或選擇編輯器工具列上的 [列出成員] 按鈕，手動叫用 [列出成員] 功能。 在空白行或可辨識範圍外叫用清單時，清單會顯示全域命名空間中的符號。

若要預設關閉 [列出成員] (除非明確地叫用，否則不會出現)，請移至 [工具] > [選項] > [所有語言]，然後取消選取 [自動列出成員]。 如果您想要只關閉特定語言的 [列出成員]，請移至該語言的 [一般] 設定。

您也可以變更為建議模式，在此模式中只會將您輸入的文字插入程式碼。 例如，如果您輸入不在清單中的識別碼並按 **Tab** 鍵，則在完成模式中，項目會取代所鍵入的識別碼。 若要在完成模式與建議模式之間進行切換，請按 **Ctrl** + **Alt** +  **空格鍵**，或選擇 [編輯] > [IntelliSense] > [切換完成模式]。

## <a name="parameter-info"></a>參數資訊

[參數資訊] 會提供方法、屬性泛型型別參數 (C# 中) 或範本 (C++ 中) 所需參數的數目、名稱和類型相關資訊。

粗體的參數表示您輸入函式時，所需的下一個參數。 對於多載函式，您可以使用向上鍵和向下鍵檢視函式多載的替代參數資訊。

![參數資訊](../ide/media/vs2015_param_info.png "VS2015_param_Info")

當您以 XML 文件註解來標註函式和參數時，這些註解將會顯示成 [參數資訊]。 如需詳細資訊，請參閱[提供 XML 程式碼註解](../ide/supplying-xml-code-comments.md)。

您可以選擇 [編輯] > [IntelliSense] > [參數資訊]、按 **Ctrl** + **Shift** + **空格鍵**，或選擇編輯器工具列上的 [參數資訊] 按鈕，手動叫用 [參數資訊]。

## <a name="quick-info"></a>快速諮詢

[快速諮詢] 會顯示程式碼中任一識別項的完整宣告。

![Visual Studio 快速諮詢](../ide/media/vs2015_quick_info.png "VS2015_Quick_info")

當您從 [列出成員] 方塊中選取成員時，也會出現 [快速諮詢]。

![C&#35; 程式碼檔中的參數資訊](../ide/media/vs2015_paraminfo.png "VS2015_ParamInfo")

您可以選擇 [編輯] > [IntelliSense] > [快速諮詢]、按 **Ctrl** + **I**，或選擇編輯器工具列上的 [快速諮詢] 按鈕，手動叫用 [快速諮詢]。

如果函式是多載函式，IntelliSense 可能不會顯示所有多載形式的資訊。

您可以導覽至 [工具] > [選項] > [文字編輯器] > [C/C++] > [進階]，然後將 [自動快速諮詢] 設定為 `false`，以關閉 C++ 程式碼的 [快速諮詢]。

## <a name="complete-word"></a>自動完成文字

在您輸入足夠的字元可清楚識別詞彙之後，[自動完成文字] 就會輸入變數、命令或函式名稱的其餘部分。 您可以選擇 [編輯] > [IntelliSense] > [自動完成文字]、按 **Ctrl** + **空格鍵**，或選擇編輯器工具列上的 [自動完成文字] 按鈕，叫用 [自動完成文字]。

## <a name="intellisense-options"></a>IntelliSense 選項

IntelliSense 選項預設為開啟。 若要關閉它們，請選擇 [工具] > [選項] > [文字編輯器]，然後取消選取 [參數資訊] 或 [自動列出成員] (如果您不想要列出成員功能)。

## <a name="troubleshooting-intellisense"></a>疑難排解 IntelliSense

IntelliSense 選項在某些情況下可能不會依照您的預期運作。

**游標位於程式碼錯誤下方。** 如果游標上方的程式碼有不完整的函式或其他錯誤，您可能會無法使用 IntelliSense，因為 IntelliSense 可能無法剖析程式碼項目。 您可以註解適用的程式碼來解決這個問題。

**游標位於程式碼註解內。** 如果游標位於原始程式檔的註解中，則無法使用 IntelliSense。

**游標位於字串常值中。** 如果游標如下列範例所示位於用引號括住的字串常值中，則無法使用 IntelliSense：

```cpp
MessageBox( hWnd, "String literal|")
```

**會關閉自動選項。** IntelliSense 預設會自動運作，但您可將其停用。 即使停用自動陳述式完成，還是可以叫用 IntelliSense 功能。

## <a name="see-also"></a>另請參閱

[Visual Basic 特定的 IntelliSense](../ide/visual-basic-specific-intellisense.md)  
[C# IntelliSense](../ide/visual-csharp-intellisense.md)  
[JavaScript IntelliSense](../ide/javascript-intellisense.md)  
[撰寫及重構程式碼 (C++)](/cpp/ide/writing-and-refactoring-code-cpp)  
[提供 XML 程式碼註解](../ide/supplying-xml-code-comments.md)
