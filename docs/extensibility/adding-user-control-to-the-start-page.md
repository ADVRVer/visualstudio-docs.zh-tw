---
title: "將使用者控制項加入至 [開始] 頁面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
caps.latest.revision: 16
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 69c2ff24616af373461de0cbf4456499db63f902
ms.lasthandoff: 02/22/2017

---
# <a name="adding-user-control-to-the-start-page"></a>將使用者控制項加入至 [開始] 頁面
本逐步解說示範如何加入自訂的起始頁 DLL 的參考。 範例會新增至方案中，使用者控制項建置使用者控制項，並再建置的組件參考起始頁.xaml 檔案。 新的索引標籤裝載使用者控制項，其做為基本的 Web 瀏覽器功能。  
  
 您可以使用相同的程序加入任何可以從.xaml 檔案中呼叫的組件。  
  
## <a name="adding-a-wpf-user-control-to-the-solution"></a>將 WPF 使用者控制項加入至方案  
 首先，Windows Presentation Foundation (WPF) 使用者控制項加入起始頁方案。  
  
1.  建立起始頁面使用我們建立在[建立自訂起始頁](../extensibility/creating-a-custom-start-page.md)。  
  
2.  在**方案總管] 中**，以滑鼠右鍵按一下方案，按一下**新增**，然後按一下 [**新的專案**。  
  
3.  在左窗格中**新的專案**對話方塊方塊中，展開  **Visual Basic**或**Visual C#**節點，然後按一下  **Windows**。 在中間窗格中，選取**WPF 使用者控制項程式庫**。  
  
4.  將控制項`WebUserControl`然後按一下 **確定**。  
  
## <a name="implementing-the-user-control"></a>實作使用者控制項  
 若要實作 WPF 使用者控制項，建置在 XAML 中的使用者介面 (UI)，然後以 C# 或其他.NET 語言撰寫的程式碼後置事件。  
  
#### <a name="to-write-the-xaml-for-the-user-control"></a>撰寫使用者控制項的 XAML  
  
1.  開啟使用者控制項的 XAML 檔案。 在\<方格 > 項目，將下列的資料列定義加入至控制項。  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  在 main`Grid`項目，新增下列新`Grid`元素，其中包含文字方塊中輸入網站位址和設定新的地址 按鈕。  
  
    ```xml  
    <Grid Grid.Row="0">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="*" />  
            <ColumnDefinition Width="Auto" />  
        </Grid.ColumnDefinitions>  
        <TextBox x:Name="UserSource" Grid.Column="0" />  
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
    </Grid>  
    ```  
  
3.  將下列的畫面格加入至最上層`Grid`元素後方`Grid`包含按鈕和文字方塊項目。  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  下列範例顯示完整的 XAML 使用者控制項。  
  
    ```xml  
    <UserControl x:Class="WebUserControl.UserControl1"  
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
                 mc:Ignorable="d"   
                 d:DesignHeight="300" d:DesignWidth="300">  
        <Grid>  
            <Grid.RowDefinitions>  
                <RowDefinition Height="Auto"/>  
                <RowDefinition Height="*" />  
            </Grid.RowDefinitions>  
            <Grid Grid.Row="0">  
                <Grid.ColumnDefinitions>  
                    <ColumnDefinition Width="*" />  
                    <ColumnDefinition Width="Auto" />  
                </Grid.ColumnDefinitions>  
                <TextBox x:Name="UserSource" Grid.Column="0" />  
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
            </Grid>  
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
        </Grid>  
    </UserControl>  
  
    ```  
  
#### <a name="to-write-the-code-behind-events-for-the-user-control"></a>撰寫使用者控制項的程式碼後置事件。  
  
1.  在 XAML 設計工具中，按兩下**設定位址**按鈕加入至控制項。  
  
     UserControl1.cs 檔案會在程式碼編輯器中開啟。  
  
2.  填入 SetButton_Click 事件處理常式，如下所示。  
  
    ```c#  
    private void SetButton_Click(object sender, RoutedEventArgs e)  
    {  
        try  
        {  
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);  
        }  
        catch (Exception error)  
        {  
            MessageBox.Show(error.Message);  
        }  
    }  
    ```  
  
     此程式碼會設定在文字方塊中輸入做為目標的 Web 瀏覽器的網址。 如果位址不正確，程式碼擲回錯誤。  
  
3.  您也必須處理 WebFrame_Navigated 事件︰  
  
    ```c#  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  建置方案。  
  
## <a name="adding-the-user-control-to-the-start-page"></a>將使用者控制項加入至 [開始] 頁面  
 若要將此控制項的起始頁專案，使用入門 頁面上的專案檔中，加入新的控制項程式庫的參考。 然後您可以將控制項加入 [啟動] 頁面的 XAML 標記。  
  
1.  在**方案總管] 中**，在起始頁專案中，以滑鼠右鍵按一下**參考**然後按一下 [**加入參考**。  
  
2.  在**專案**索引標籤上，選取**WebUserControl**然後按一下 **確定**。  
  
3.  在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
     建置方案讓使用者控制 IntelliSense 可以使用其他方案中的檔案。  
  
 若要將控制項加入至 [啟動] 頁面的 XAML 標記，加入命名空間參考組件，然後放在頁面上的控制項。  
  
#### <a name="to-add-the-control-to-the-markup"></a>將控制項加入至標記  
  
1.  在**方案總管 中**，開啟 啟動 頁面上的.xaml 檔案。  
  
2.  在**XAML**  窗格中，將下列命名空間宣告加入至最上層<xref:System.Windows.Controls.Grid>項目。</xref:System.Windows.Controls.Grid>  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  在**XAML**  窗格中，捲動到\<方格 > 一節。  
  
     區段包含<xref:System.Windows.Controls.TabControl>中的項目<xref:System.Windows.Controls.Grid>項目。</xref:System.Windows.Controls.Grid> </xref:System.Windows.Controls.TabControl>  
  
4.  新增\<TabControl > 項目包含\<TabItem >，其中包含您的使用者控制項的參考。  
  
    ```xml  
  
    <TabItem Header="Web" Height="Auto">  
        <vsc:UserControl1 />  
    </TabItem>  
  
    ```  
  
 現在您可以測試控制項。  
  
## <a name="testing-a-manually-created-custom-start-page"></a>測試以手動方式建立的自訂起始頁  
  
1.  複製您的 XAML 檔案，並支援文字檔案或標記檔案，為**%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\ **資料夾。  
  
2.  如果您的起始頁參考任何控制項或未安裝 Visual studio 組件中的型別，將組件，然後貼在*Visual Studio 安裝資料夾***\Common7\IDE\PrivateAssemblies\\**。  
  
3.  在 Visual Studio 命令提示字元中，輸入**devenv /rootsuffix Exp**若要開啟的 Visual Studio 的實驗執行個體。  
  
4.  在實驗執行個體中，移至**工具 / 選項 / 環境 / 啟動**頁面，並選取您的 XAML 檔案從**自訂起始頁**下拉式清單。  
  
5.  在 [檢視]  功能表上，按一下 [起始頁] 。  
  
     應該會顯示自訂起始頁。 如果您想要變更的任何檔案，您必須關閉的實驗執行個體、 進行變更、 複製並貼變更的檔案，然後再重新開啟實驗性的執行個體，以檢視所做的變更。  
  
## <a name="see-also"></a>另請參閱  
 [WPF 容器控制項](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)   
 [逐步解說︰ 將自訂的 XAML 加入至 [開始] 頁面](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
