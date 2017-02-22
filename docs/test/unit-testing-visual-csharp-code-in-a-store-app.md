---
title: "對市集應用程式中的 Visual C# 程式碼進行單元測試 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23cb0d82-0451-464e-98ea-fa66e7010ead
caps.latest.revision: 19
caps.handback.revision: 19
author: "alexhomer1"
ms.author: "ahomer"
manager: "robinr"
---
# 對市集應用程式中的 Visual C# 程式碼進行單元測試
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何在 Windows 市集應用程式中建立 Visual C\# 類別的單元測試。  Rooter 類別會藉由實作計算某數值的平方根估計數的函式，示範微積分中極限理論的模糊記憶。  然後 Maths 應用程式就可以使用這個函式向使用者展現許多可運用數學運算執行的有趣作業。  
  
 本主題示範如何使用單元測試做為開發工作的第一步。  採用這種方式時，您會先撰寫測試方法，用來驗證要測試之系統中的特定行為，然後撰寫通過測試的程式碼。  依照下列程序的順序進行變更，您就可以反轉策略，先撰寫要測試的程式碼，再撰寫單元測試。  
  
 本主題還會建立單一 Visual Studio 方案，以及用於單元測試和要測試之 DLL 的個別專案。  您也可以直接在 DLL 專案中包含單元測試，或是針對單元測試和 DLL 建立個別方案。  
  
> [!NOTE]
>  Visual Studio Community、Enterprise   及 Professional 均提供針對單元測試的額外功能。  
>   
>  -   請使用任何協力廠商及開放原始碼單元測試架構，只要該架構已經為 Microsoft \[測試總管\] 建立附加配接器即可。  您也可以分析及顯示測試的程式碼涵蓋範圍資訊。  
> -   每次建置後都執行測試。  
> -   VS Enterprise 還包含 Microsoft Fakes，這是一種 Managed 程式碼的隔離架構，會以測試程式碼替代系統和協力廠商功能，幫助您將測試焦點放在自己的程式碼上。  
>   
>  如需詳細資訊，請參閱 MSDN Library 中的[使用單元測試驗證程式碼](http://msdn.microsoft.com/library/dd264975.aspx)。  
  
##  <a name="BKMK_In_this_topic"></a> 本主題內容  
 [建立方案和單元測試專案](#BKMK_Create_the_solution_and_the_unit_test_project)  
  
 [驗證測試總管中執行的測試](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)  
  
 [將 Rooter 類別新增至 Maths 專案](#BKMK_Add_the_Rooter_class_to_the_Maths_project)  
  
 [將測試專案與應用程式專案結合](#BKMK_Couple_the_test_project_to_the_app_project)  
  
 [反覆擴大測試範圍並使其通過](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)  
  
 [對失敗的測試進行偵錯](#BKMK_Debug_a_failing_test)  
  
 [重構程式碼](#BKMK_Refactor_the_code_)  
  
##  <a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> 建立方案和單元測試專案  
  
1.  選擇 \[**檔案**\] 功能表上的 \[**新增**\]，然後選擇 \[**新專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊上，展開 \[**已安裝的**\]，然後展開 \[**Visual C\#**\]，並選擇 \[**Windows 市集**\]。  然後從專案範本清單中選擇 \[**空白應用程式**\]。  
  
3.  將專案命名為 `Maths`，並確認已選取 \[**為方案建立目錄**\]。  
  
4.  在 \[方案總管\] 中選擇方案名稱，從捷徑功能表選擇 \[**新增**\]，然後選擇 \[**新專案**\]。  
  
5.  在 \[新增專案\] 對話方塊中，展開 \[已安裝\]，然後展開 \[Visual C\#\]，並選擇 \[Windows 市集\]。  接著從專案範本清單中選擇 \[**單元測試程式庫 \(Windows 市集應用程式\)**\]。  
  
     ![建立單元測試專案](../test/media/ute_cs_windows_createunittestproject.png "UTE\_Cs\_windows\_CreateUnitTestProject")  
  
6.  在 Visual Studio 編輯器中開啟 UnitTest1.cs。  
  
    ```c#  
  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;  
    using Maths;  
  
    namespace RooterTests  
    {  
        [TestClass]  
        public class UnitTest1  
  
            [TestMethod]  
            public void TestMethod1()  
            {  
  
            }  
  
    ```  
  
     請注意：  
  
    1.  每一項測試都是使用 `[TestMethod]` 定義。  測試方法必須傳回 void，而且不可以有任何參數。  
  
    2.  測試方法必須在以 `[TestClass]` 屬性裝飾的類別中。  
  
         在測試執行時，會建立每個測試類別的執行個體。  將會以非指定的順序來呼叫測試方法。  
  
    3.  您可以定義在每個模組、類別或方法之前和之後叫用的特殊方法。  如需詳細資訊，請參閱 MSDN Library 中的[在單元測試中使用 Microsoft.VisualStudio.TestTools.UnitTesting 成員](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)。  
  
##  <a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> 驗證測試總管中執行的測試  
  
1.  在 `TestMethod1` 檔案的 **UnitTest1.cs** 中插入一些測試程式碼：  
  
    ```c#  
  
    [TestMethod]  
    public void TestMethod1()  
    {  
        Assert.AreEqual(0, 0);  
    }  
  
    ```  
  
     請注意，`Assert` 類別會提供數種靜態方法，可讓您用來驗證測試方法的結果。  
  
2.  選擇 \[**測試**\] 功能表上的 \[**執行**\]，然後選擇 \[**全部執行**\]。  
  
     測試專案隨即建置並執行。  \[測試總管\] 視窗隨即開啟，而且測試會在 \[**通過的測試**\] 底下列出。  視窗底部的 \[摘要\] 窗格會提供有關所選取測試的其他詳細資料。  
  
     ![測試總管](../test/media/ute_cpp_testexplorer_testmethod1.png "UTE\_Cpp\_TestExplorer\_TestMethod1")  
  
##  <a name="BKMK_Add_the_Rooter_class_to_the_Maths_project"></a> 將 Rooter 類別新增至 Maths 專案  
  
1.  在 \[方案總管\] 中選擇 \[**Maths**\] 專案名稱。  從捷徑功能表中選擇 \[**新增**\]，然後選擇 \[**類別**\]。  
  
2.  將類別檔案命名為 `Rooter.cs`  
  
3.  將下列程式碼新增至 Rooter 類別 **Rooter.cs** 檔案：  
  
    ```c#  
  
    public Rooter()  
    {  
    }  
  
    // estimate the square root of a number  
    public double SquareRoot(double x)  
    {  
        return 0.0;  
    }  
  
    ```  
  
     `Rooter` 類別會宣告建構函式和 `SqareRoot` 評估工具方法。  
  
4.  `SqareRoot` 方法只是最簡單的實作，剛好足夠進行測試設定的基本結構測試。  
  
##  <a name="BKMK_Couple_the_test_project_to_the_app_project"></a> 將測試專案與應用程式專案結合  
  
1.  將 Maths 應用程式的參考新增至 RooterTests 專案。  
  
    1.  在 \[方案總管\] 中選擇 \[**RooterTests**\] 專案，然後在捷徑功能表上選擇 \[**加入參考**\]。  
  
    2.  在 \[**加入參考 \- RooterTests**\] 對話方塊中，展開 \[**方案**\] 並選擇 \[**專案**\]。  然後選取 \[**Maths**\] 項目。  
  
         ![將參考加入 Maths 專案](../test/media/ute_cs_windows_addreference.png "UTE\_Cs\_windows\_AddReference")  
  
2.  將 using 陳述式新增至 UnitTest1.cs 檔案：  
  
    1.  開啟 **UnitTest1.cs**。  
  
    2.  將這個程式碼新增至 `using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;` 這一行下方：  
  
        ```c#  
        using Maths;  
        ```  
  
3.  新增使用 Rooter 函式的測試。  將下列程式碼新增至 **UnitTest1.cpp**：  
  
    ```c#  
    [TestMethod]  
    public void BasicTest()  
    {  
        Maths.Rooter rooter = new Rooter();  
        double expected = 0.0;  
        double actual = rooter.SquareRoot(expected * expected);  
        double tolerance = .001;  
        Assert.AreEqual(expected, actual, tolerance);  
    }  
  
    ```  
  
4.  建置方案。  
  
     新測試會出現在 \[測試總管\] 的 \[**未執行的測試**\] 節點中。  
  
5.  在 \[測試總管\] 中選擇 \[**全部執行**\]。  
  
     ![基本測試成功](../test/media/ute_cpp_testexplorer_basictest.png "UTE\_Cpp\_TestExplorer\_BasicTest")  
  
 您已經設定測試和程式碼專案，並確認您可以執行在程式碼專案中執行函式的測試。  現在您可以開始撰寫真正的測試和程式碼。  
  
##  <a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> 反覆擴大測試範圍並使其通過  
  
1.  加入新的測試：  
  
    ```c#  
    [TestMethod]  
    public void RangeTest()  
    {  
        Rooter rooter = new Rooter();  
        for (double v = 1e-6; v < 1e6; v = v * 3.2)  
        {  
            double expected = v;  
            double actual = rooter.SquareRoot(v*v);  
            double tolerance = ToleranceHelper(expected);  
            Assert.AreEqual(expected, actual, tolerance);  
        }  
    }  
  
    ```  
  
    > [!TIP]
    >  建議您不要變更已通過的測試。  相反地，請加入新的測試，更新程式碼，使測試通過，然後再加入另一個測試，依此類推。  
    >   
    >  當您的使用者變更他們的需求時，請停用已不再正確的測試。  撰寫新測試，並以相同的遞增方式一次讓一項測試成功。  
  
2.  在 \[測試總管\] 中選擇 \[**全部執行**\]。  
  
3.  測試失敗。  
  
     ![RangeTest 失敗](../test/media/ute_cpp_testexplorer_rangetest_fail.png "UTE\_Cpp\_TestExplorer\_RangeTest\_Fail")  
  
    > [!TIP]
    >  在您撰寫每一項測試之後立即確認其失敗。  這樣有助於避免撰寫永遠不會失敗的測試這種易犯的錯誤。  
  
4.  透過測試強化程式碼，讓新的測試都成功。  將 `SqareRoot` 中的 **Rooter.cs** 函式變更如下：  
  
    ```c#  
    public double SquareRoot(double x)  
    {  
        double estimate = x;  
        double diff = x;  
        while (diff > estimate / 1000)  
        {  
            double previousEstimate = estimate;  
            estimate = estimate - (estimate * estimate - x) / (2 * estimate);  
            diff = Math.Abs(previousEstimate - estimate);  
        }  
        return estimate;  
    }  
  
    ```  
  
5.  建置方案，然後在 \[測試總管\] 中選擇 \[**全部執行**\]。  
  
     現在三項測試都會成功。  
  
> [!TIP]
>  開發程式碼時，一次加入一個測試。  確定所有測試在每次反覆之後都通過。  
  
##  <a name="BKMK_Debug_a_failing_test"></a> 對失敗的測試進行偵錯  
  
1.  新增另一項測試至 **UnitTest1.cs**：  
  
    ```c#  
    // Verify that negative inputs throw an exception.  
    [TestMethod]  
    public void NegativeRangeTest()  
    {  
        string message;  
        Rooter rooter = new Rooter();  
        for (double v = -0.1; v > -3.0; v = v - 0.5)  
        {  
            try  
            {  
                // Should raise an exception:  
                double actual = rooter.SquareRoot(v);  
  
                message = String.Format("No exception for input {0}", v);  
                Assert.Fail(message);  
            }  
            catch (ArgumentOutOfRangeException ex)  
            {  
                continue; // Correct exception.  
            }  
            catch (Exception e)  
            {  
                message = String.Format("Incorrect exception for {0}", v);  
                Assert.Fail(message);  
            }  
        }  
    }  
  
    ```  
  
2.  在 \[測試總管\] 中選擇 \[**全部執行**\]。  
  
     測試失敗。  在 \[測試總管\] 中選擇測試名稱。  失敗的判斷提示會反白顯示。  \[測試總管\] 的詳細資料窗格中會顯示失敗的訊息。  
  
     ![NegativeRangeTests 失敗](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png "UTE\_Cpp\_TestExplorer\_NegativeRangeTest\_Fail")  
  
3.  若要查看測試失敗的原因，請逐步執行函式：  
  
    1.  在 `SquareRoot` 函式的開頭設定中斷點。  
  
    2.  在失敗的測試之捷徑功能表上，選擇 \[**偵測選取的測試**\]。  
  
         執行到中斷點停止時，請逐步執行程式碼。  
  
    3.  將程式碼新增至 Rooter 方法以擷取例外狀況：  
  
        ```c#  
        public double SquareRoot(double x)  
        {  
            if (x < 0.0)  
            {  
                throw new ArgumentOutOfRangeException();  
        }  
  
        ```  
  
    1.  在 \[測試總管\] 中，選擇 \[**全部執行**\] 測試修正過的方法，並確定並未導入回復 \(Regression\)。  
  
 現在所有測試都會成功。  
  
 ![所有測試都成功](../test/media/ute_ult_alltestspass.png "UTE\_ULT\_AllTestsPass")  
  
##  <a name="BKMK_Refactor_the_code_"></a> 重構程式碼  
 **簡化 SquareRoot 函式的主要計算。**  
  
1.  變更結果實作  
  
    ```c#  
    // old code  
    //result = result - (result*result - v)/(2*result);  
    // new code  
    result = (result + v/result) / 2.0;  
  
    ```  
  
2.  選擇 \[**全部執行**\] 測試重構的方法，並確定並未導入回復 \(Regression\)。  
  
> [!TIP]
>  一組穩定而良好的單元測試，可確認您並未在變更程式碼時引入錯誤。  
  
 **重構測試程式碼以消除重複的程式碼。**  
  
 請注意，`RangeTest` 方法會對 `Assert` 方法中所使用容錯變數的分母採用硬式編碼。  如果您打算新增其他使用相同容錯計算的測試，則在多個位置使用硬式編碼值可能導致錯誤。  
  
1.  將私用方法新增至 Unit1Test 類別以計算容錯值，然後改為呼叫該方法。  
  
    ```c#  
    private double ToleranceHelper(double expected)  
    {  
        return expected / 1000;  
    }  
  
    ...  
  
    [TestMethod]  
    public void RangeTest()  
    {  
        ...  
        // old code  
        // double tolerance = expected/1000;  
        // new code  
        double tolerance = ToleranceHelper(expected);  
        Assert.AreEqual(expected, actual, tolerance);  
    }  
    ...  
  
    ```  
  
2.  選擇 \[**全部執行**\] 測試重構的方法，並確定並未導入錯誤。  
  
> [!NOTE]
>  若要將協助程式方法新增至測試類別，請不要將 `[TestMethod]` 屬性新增至方法。  \[測試總管\] 並未登錄要執行的方法。