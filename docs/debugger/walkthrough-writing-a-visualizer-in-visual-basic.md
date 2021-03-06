---
title: "逐步解說： 在 Visual Basic 中撰寫視覺化檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7ad673736334daec79860b9832a056c17781a082
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>逐步解說：在 Visual Basic 中撰寫視覺化檢視
本逐步解說顯示如何使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 撰寫簡易的視覺化檢視。 您在本逐步解說中建立的視覺化檢視會使用 Windows Form 訊息方塊顯示字串的內容。 這個簡易字串視覺化檢視是一個基本範例，示範如何建立更適用專案之其他資料型別的視覺化檢視。  
  
> [!NOTE]
>  根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中所描述的不同。 若要變更您的設定，請移至**工具**功能表，然後選擇 **匯入和匯出**。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
 視覺化檢視的程式碼必須放置在偵錯工具將讀取的 DLL 中。 第一步就是為 DLL 建立類別庫專案。  
  
## <a name="create-and-prepare-a-class-library-project"></a>建立和準備類別庫專案  
  
#### <a name="to-create-a-class-library-project"></a>若要建立類別庫專案  
  
1.  在**檔案**功能表上，選擇**新增**按一下**新專案**。  
  
2.  在**新專案**對話方塊的 **專案類型**s，按一下  **Visual Basic**。  
  
3.  在**範本**方塊中，按一下**類別庫**。  
  
4.  在**名稱**方塊中，輸入適當的名稱，為該類別庫，例如**MyFirstVisualizer**。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
 建立類別庫之後，必須加入 Microsoft.VisualStudio.DebuggerVisualizers.DLL 的參考，如此您才能使用這個位置中定義的類別。 但請先為專案提供一個有意義的名稱。  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>若要重新命名 Class1.vb 和加入 Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**Class1.vb**，捷徑功能表上，按一下 [**重新命名**。  
  
2.  將 Class1.vb 變更成有意義的名稱，例如 DebuggerSide.vb。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會自動變更 DebuggerSide.vb 中的類別宣告，以符合新的檔案名稱。  
  
3.  在**方案總管] 中**，以滑鼠右鍵按一下**My First Visualizer**，捷徑功能表上，按一下 [**加入參考**。  
  
4.  在**加入參考**對話方塊**.NET**索引標籤上，按一下 Microsoft.VisualStudio.DebuggerVisualizers.DLL。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
6.  在 DebuggerSide.vb 中，將下列陳述式加入至 `Imports` 陳述式：  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## <a name="add-the-debugger-side-code"></a>加入偵錯工具端程式碼  
 現在，您就可以準備建立偵錯工具端的程式碼。 這是在偵錯工具內執行的程式碼，用以顯示您要視覺化的資訊。 首先，您必須變更 `DebuggerSide` 物件的宣告，使其繼承基底類別 (Base Class) `DialogDebuggerVisualizer`。  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>若要繼承自 DialogDebuggerVisualizer  
  
1.  在 DebuggerSide.vb 中，移至下列程式碼行：  
  
    ```  
    Public Class DebuggerSide  
    ```  
  
2.  編輯程式碼使其看來如下所示：  
  
    ```  
    Public Class DebuggerSide  
    Inherits DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer` 含有一個您必須覆寫的抽象方法 `Show`。  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>若要覆寫 DialogDebuggerVisualizer.Show 方法  
  
-   在 `public class DebuggerSide` 中加入下列方法：  
  
    ```  
    Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
        End Sub  
    ```  
  
 `Show` 方法中包含實際建立視覺化檢視對話方塊 (或其他使用者介面) 的程式碼，並會在偵錯工具中顯示已傳遞至視覺化檢視的資訊。 您必須加入該程式碼，以建立對話方塊並顯示資訊。 在本逐步解說中，您將使用 Windows Form 訊息方塊進行上述動作。 首先，您必須加入 `Imports` 的參考和 <xref:System.Windows.Forms> 陳述式。  
  
#### <a name="to-add-systemwindowsforms"></a>若要加入 System.Windows.Forms  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**參考**，捷徑功能表上，按一下 [**加入參考**。  
  
2.  在**加入參考**對話方塊**.NET**索引標籤上，按一下  **System.Windows.Forms**。  
  
3.  按一下 [確定 **Deploying Office Solutions**]。  
  
4.  在 DebuggerSide.cs 中，將下列陳述式加入至 `Imports` 陳述式：  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>建立視覺化檢視的使用者介面  
 現在，您可以加入某些程式碼，建立並顯示視覺化檢視的使用者介面。 由於這是您的第一個視覺化檢視，因此我們盡量簡化使用者介面，並且會使用訊息方塊。  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>若要在對話方塊中顯示視覺化檢視輸出  
  
1.  在 `Show` 方法中，加入下列程式碼行：  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     這個程式碼範例不包括錯誤處理。 在真實的視覺化檢視或其他任何類型的應用程式中，都應該包括錯誤處理功能。  
  
2.  在**建置**功能表上，按一下 **建置 MyFirstVisualizer**。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。  
  
## <a name="add-the-necessary-attribute"></a>加入必要屬性  
 這是偵錯工具端的程式碼結尾。 但是還有一個步驟，就是加入告知偵錯項目端構成視覺化檢視類別集合的屬性。  
  
#### <a name="to-add-the-debugee-side-code"></a>若要加入偵錯項目端程式碼  
  
1.  將下列屬性程式碼加入至 DebuggerSide.vb，放置在 `Imports` 陳述式之後，`namespace MyFirstVisualizer` 之前：  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2.  在**建置**功能表上，按一下 **建置 MyFirstVisualizer**。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。  
  
## <a name="create-a-test-harness"></a>建立 Test Harness  
 這時，您的第一個視覺化檢視已完成。 如果您正確遵循這些步驟的話，應該能夠建置視覺化檢視，並將它安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中。 但是，在將視覺化檢視安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之前，應該先進行測試以確定它能正確執行。 現在，您將建立 Test Harness 來執行這個視覺化檢視，而不將它安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中。  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>若要加入顯示視覺化檢視的測試方法  
  
1.  將下列方法加入至 `public DebuggerSide` 類別：  
  
    ```  
    Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
        Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
    visualizerHost.ShowVisualizer()  
    End Sub  
    ```  
  
2.  在**建置**功能表上，按一下 **建置 MyFirstVisualizer**。 專案應該會順利建置。 在繼續進行之前，請更正任何建置錯誤。  
  
 接下來，您必須建立可執行的專案，以呼叫視覺化檢視的 DLL。 為簡單起見請使用主控台應用程式專案。  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>若要將主控台應用程式專案加入至方案  
  
1.  上**檔案**功能表上，按一下 **新增**，然後按一下 **新專案**。  
  
2.  在**加入新的專案**對話方塊中，於**範本**方塊中，按一下**主控台應用程式**。  
  
3.  在**名稱**方塊中，輸入有意義的名稱，為主控台應用程式，例如**MyTestConsole**。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
 此時，你必須加入必要的參考，如此 MyTestConsole 才能呼叫 MyFirstVisualizer。  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>若要將必要參考加入至 MyTestConsole  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**MyTestConsole**，捷徑功能表上，按一下 [**加入參考**。  
  
2.  在**加入參考**對話方塊**.NET**索引標籤上，按一下 [microsoft.visualstudio.debuggervisualizers]。  
  
3.  按一下 [確定 **Deploying Office Solutions**]。  
  
4.  以滑鼠右鍵按一下**MyTestConsole**，然後按一下 **加入參考**一次。  
  
5.  在**加入參考**對話方塊中，按一下 **專案**索引標籤，然後選取 MyFirstVisualizer。  
  
6.  按一下 [確定 **Deploying Office Solutions**]。  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>完成 Test Harness 並測試視覺化檢閱  
 現在，您就可以加入程式碼來完成 Test Harness。  
  
#### <a name="to-add-code-to-mytestconsole"></a>若要將程式碼加入至 MyTestConsole  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**Program.vb**，捷徑功能表上，按一下 [**重新命名**。  
  
2.  編輯名稱將 module1.vb 適當，例如**TestConsole.vb**。  
  
     請注意，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會自動變更 TestConsole.vb 中的類別宣告，以符合新的檔案名稱。  
  
3.  在 TestConsole。 vb，加入下列`Imports`陳述式：  
  
    ```  
    Imports MyFirstVisualizer  
    ```  
  
4.  在 `Main` 方法中，加入下列程式碼：  
  
    ```  
    Dim myString As String = "Hello, World"  
    DebuggerSide.TestShowVisualizer(myString)  
    ```  
  
 現在，您已經準備好可以測試第一個視覺化檢視。  
  
#### <a name="to-test-the-visualizer"></a>若要測試視覺化檢視  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**MyTestConsole**，捷徑功能表上，按一下 [**設定為啟始專案**。  
  
2.  在**偵錯**功能表上，按一下 **啟動**。  
  
     這時會啟動主控台應用程式。 視覺化檢視隨即出現，顯示字串 "Hello, World"。  
  
 恭喜您！ 您已完成建置和測試第一個視覺化檢視。  
  
 如果您想在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中使用視覺化檢視，而不只是從測試控管中進行呼叫，就必須安裝該視覺化檢視。 如需詳細資訊，請參閱[如何： 安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)。  
  
## <a name="see-also"></a>請參閱  
 [視覺化檢視架構](../debugger/visualizer-architecture.md)   
 [如何： 安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)   
 [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)