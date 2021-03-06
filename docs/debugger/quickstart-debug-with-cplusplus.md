---
title: "使用 c + + 使用 Visual Studio 偵錯工具進行偵錯 |Microsoft 文件"
ms.custom: 
ms.date: 12/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ddf6aadc6b2debcb7423df589fb11739039c6476
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="debug-with-c-using-the-visual-studio-debugger"></a>使用 c + + 使用 Visual Studio 偵錯工具進行偵錯

Visual Studio 偵錯工具會提供許多功能強大的功能，可協助您偵錯您的應用程式。 本主題提供快速的方法，若要了解的一些基本功能。

## <a name="create-a-new-project"></a>建立新專案 

1. 在 Visual Studio 中，選擇 **檔案 > 新的專案**。

2. 在下**Visual c + +**，選擇**Windows 桌面**，然後在中間窗格選擇**Windows 主控台應用程式**。

    如果您沒有看到**Windows 主控台應用程式**專案範本，請按一下**開啟 Visual Studio 安裝程式**的左窗格中的連結**新專案** 對話方塊。 Visual Studio 安裝程式即會啟動。 選擇**的 c + + 桌面應用程式開發**工作負載，然後選擇 **修改**。

3. 輸入的名稱，例如**MyDbgApp**按一下**確定**。

    Visual Studio 建立專案。

4. 在 MyDbgApp.cpp，取代下列程式碼

    ```c++
    int main()
    {
        return 0;
    }
    ```

    這個程式碼 (請勿移除`#include "stdafx.h"`):

    ```c++
    #include <list>  
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>設定中斷點

A*中斷點*會指出 Visual Studio 應暫停程式執行的地方的標記程式碼，讓您可以查看變數的值或記憶體，或正在執行的程式碼分支是否的行為。 這是在偵錯最基本的功能。

1. 若要設定中斷點，請按一下左邊的裝訂邊中`doWork`函式呼叫 (或是選取該行程式碼，然後按**F9**)。

    ![設定中斷點](../debugger/media/dbg-qs-set-breakpoint.png "設定中斷點")

2. 現在按**F5** (或選擇**偵錯 > 開始偵錯**)。

    ![叫用中斷點](../debugger/media/dbg-qs-hit-breakpoint.png "叫用中斷點")

    偵錯工具暫停，您用來設定中斷點。 暫停偵錯工具和應用程式執行的所在的陳述式會以黃色箭號。 線條`doWork`函式呼叫尚未執行。

    > [!TIP]
    > 如果您有在迴圈或遞迴時，中斷點，或如果您有很多經常逐步執行，中斷點使用[條件中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)以確定程式碼只在符合特定條件時暫停。 這可以節省時間，也可做讓更容易偵錯難以重現的問題。

    當您嘗試偵錯記憶體相關的失敗，c + + 中，您也可以使用中斷點來檢查位址值 （尋找 NULL） 和參考計數。 

## <a name="navigate-code"></a>巡覽程式碼

有不同的命令，以指示偵錯工具繼續。 我們將顯示新功能 Visual Studio 2017 的有用的程式碼瀏覽命令。

- 當在中斷點暫停時，將滑鼠停留在陳述式`c1.push_back(20)`直到綠色**按一下執行**按鈕![執行按一下](../debugger/media/dbg-tour-run-to-click.png "RunToClick")隨即出現，並再按下**按一下執行** 按鈕。

    ![按一下 [執行](../debugger/media/dbg-qs-run-to-click.png "執行]，按一下")

    在應用程式繼續執行時，呼叫`doWork`，並在您按下按鈕的程式碼行上暫停。

    常見的鍵盤命令用來逐步執行程式碼包含**F10**和**F11**。 深入了解的詳細指示，請參閱[初級開發人員指南](../debugger/getting-started-with-the-debugger.md)。

## <a name="inspect-variables-in-a-datatip"></a>檢查資料提示方塊中的變數

1. 目前這一行 （標示黃色執行指標） 的程式碼，將滑鼠停留在`c1`物件，使用滑鼠來顯示資料提示方塊。

    ![檢視資料提示方塊](../debugger/media/dbg-qs-data-tip.png "檢視資料提示方塊")

    資料提示方塊會顯示目前的值`c1`變數，並可讓您檢查其屬性。 偵錯時，如果您看到未預期的值，您可能有 bug 前面或呼叫行程式碼。 

2. 展開以查看目前的屬性值的資料提示方塊`c1`物件。

3. 如果您想要固定 datatip，讓您可以繼續以查看值`c1`時執行程式碼時，按一下 小釘選圖示。 （您可以到方便的位置移動固定資料提示方塊）。

## <a name="edit-code-and-continue-debugging"></a>編輯程式碼，然後繼續偵錯

如果您找出您想要測試在您的程式碼執行偵錯工作階段時變更，您可以執行。

1. 按一下第二個執行個體`c2.front()`並變更`c2.front()`至`c2.back()`。

2. 按**F10** (或**偵錯 > 不進入函式**) 數次前進偵錯工具並執行已編輯的程式碼。

    ![編輯後繼續](../debugger/media/dbg-qs-edit-and-continue.gif "編輯後繼續")

    **F10**進階偵錯工具的其中一個陳述式，在一段期間，但步驟於函式，而不是逐步執行到它們 （仍執行您略過的程式碼）。

如需詳細資訊和功能限制上使用 編輯後繼續，請參閱[編輯後繼續](../debugger/edit-and-continue.md)。

## <a name="next-steps"></a>後續步驟

- 若要深入了解偵錯工具，請參閱[啟動偵錯工具並瀏覽程式碼](../debugger/getting-started-with-the-debugger.md)。
- 若要了解有關中斷點的詳細資訊，請參閱[使用中斷點](../debugger/using-breakpoints.md)。

## <a name="see-also"></a>請參閱  
 [Visual Studio 偵錯](../debugger/index.md)  
 [偵錯工具功能導覽](../debugger/debugger-feature-tour.md)
