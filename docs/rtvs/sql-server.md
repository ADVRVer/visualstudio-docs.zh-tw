---
title: "整合 SQL Server 與 Visual Studio R 工具 | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 919dfc34-234a-489e-91bf-74a4cefae26c
caps.latest.revision: 1
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
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 44ae1fd825997ff5eab1448ebd86f88a130172a1
ms.contentlocale: zh-tw
ms.lasthandoff: 05/12/2017

---


# <a name="working-with-sql-server-and-r"></a>使用 SQL Server 和 R

Visual Studio R 工具 (RTVS) 利用 Visual Studio 對 SQL Server 的絕佳支援，方便資料科學家運用 SQL 資料庫，主要是建立執行中的 SQL 查詢及利用預存程序。

> [!Note]
> 若要一起使用 SQL 和 R，您必須安裝 SQL Server Data Tools：
> - Visual Studio 2017︰執行 Visual Studio 安裝程式，並選取資料儲存和處理工作負載，包括 SQL Server Data Tools。
> - Visual Studio 2015：依[下載 SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) 中的指示執行。

下列影片 (3 分 03 秒) 簡介 SQL Server 和 R

<iframe width="560" height="315" src="https://www.youtube.com/embed/n4AYr0QIwdQ" frameborder="0" allowfullscreen></iframe>

## <a name="creating-and-running-sql-queries"></a>建立和執行 SQL 查詢

RTVS 支援將 SQL 查詢新增到 R 專案，讓您在不同的內容中反覆開發 SQL 查詢，直到達到您想要的結果。

若要新增 SQL 查詢檔案，請以滑鼠右鍵按一下方案總管中的專案，選取 [新增] > [新增項目...]，然後選取 [SQL 查詢] 檔案類型︰

![將 SQL 查詢項目新增至專案](~/rtvs/media/sql-add-item.png)

這會在 Visual Studio 的 Transact-SQL 編輯器中開啟檔案，提供完整的 IntelliSense for SQL 及執行查詢的能力。 但要使用這些功能，您需要使用編輯器工具列的 [連線] 按鈕，或僅嘗試執行查詢 (Ctrl+Shift+E，也適用於選取)，連線到資料庫。 任一方式都會顯示 [連線] 對話方塊︰

![SQL 連線對話方塊](~/rtvs/media/sql-connection-dialog.png)

一旦建立連線，您就可以執行查詢並查看結果︰

![SQL 視窗查詢結果](~/rtvs/media/sql-query-results.png)

Transact-SQL 編輯器支援各種不同的其他功能，例如檢視查詢執行計劃、查詢偵錯工具。Transact-SQL 編輯器中有許多其他功能可用。 如需詳細資訊，請參閱[使用 Transact-SQL 編輯器，編輯和執行指令碼](https://msdn.microsoft.com/library/hh272706.aspx)。

## <a name="working-with-sql-server-stored-procedures"></a>使用 SQL Server 預存程序

[SQL Server R 服務](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 和更新版本) 讓您從 T-SQL 預存程序內嵌及執行 R 程式碼。 這表示您可以執行 R 程式碼 SQL Server 電腦、操作從 SQL 查詢傳回的資料，以及產生 SQL 結果集，供日後的 SQL 處理或傳回用戶端。

如下列各節所述，RTVS 簡化因將 SQL 和 R 程式碼結合在單一的 SQL 陳述式中，本來會很龐大且容易發生錯誤的程序︰

- [新增資料庫連接](#add-a-database-connection)
- [撰寫及測試 SQL 預存程序](#write-and-test-a-sql-stored-procedure)
- [發行 SQL 預存程序](#publish-a-sql-stored-procedure)

下列影片 (6 分 09 秒) 也會提供這些功能的概觀︰

<iframe width="560" height="315" src="https://www.youtube.com/embed/dFKIT2OitWQ" frameborder="0" allowfullscreen></iframe>

### <a name="add-a-database-connection"></a>新增資料庫連接

1. 選取 [R 工具] > [資料] > [新增資料庫連線] 即會顯示 [連接屬性] 對話方塊，在此指定資料來源的名稱 (本例中為 SQL Server)、伺服器名稱、驗證模式以及資料庫名稱。 您可以選取 [測試連接] 先驗證您的輸入，再關閉對話。
 
    ![SQL 連線對話方塊](~/rtvs/media/sql-connection-string-dialog.png)

1. 一旦您對有效的連線選取 [確定]，Visual Studio 就會在新的 `settings.R` 檔案中產生名為 `dbConnection` 的連接字串。 RTVS 自動將此檔案設為來源 (執行)，因此您可以立即使用 R 指令碼中的連接︰

![SQL Settings.R 檔案](~/rtvs/media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>撰寫及測試 SQL 預存程序

若要新增新的 SQL 預存程序，請以滑鼠右鍵按一下您的專案，選取 [新增] > [新增項目...]，然後從範本清單中選取 [使用 R 的 SQL 預存程序]，指定檔案的名稱 (本例中為 `StoredProcedure.R`)，再選取 [確定]。
 
RTVS 建立三個預存程序檔案：`.R` 檔案供 R 程式碼使用、`.Query.sql` 檔案供 SQL 程式碼使用，而 `.Template.sql` 檔案則結合兩者。 後面兩個會出現在方案總管中，作為 `.R` 檔案的子系︰

![使用 R 之 SQL 預存程序的方案總管展開檢視](~/rtvs/media/sql-solution-explorer-expanded.png)

您會在 `StoredProcedure.R` (本例中) 撰寫 R 程式碼。 預設內容如下所示︰

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

簡言之，程式碼會接收稱為 `InputDataSet` 的 R 資料框架，並使用 `OutputDataSet` 傳回其結果，範本程式碼只將輸入複製到輸出。

> [!Note]
> 這些資料框架的名稱是由 `sp_execute_external_script` 系統預存程序呼叫中的 `@input_data_1_name` 和 `@output_data_1_name` 參數所控制。 如需此呼叫慣例設計及其用法範例的詳細資訊，請參閱 [sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)。

在註解中產生的其他程式碼是小型的測試指令碼，會使用 [RODBC 套件](https://cran.r-project.org/web/packages/RODBC/index.html) 將 SQL 陳述式傳輸至 SQL Server、執行它，並擷取其結果集為 R 資料框架。 您可以取消註解此測試程式碼，以互動方式針對您從 SQL Server 中取得的結果集撰寫 R 程式碼。

您在 `StoredProcedure.Query.sql` 撰寫並測試 SQL 查詢，其產生 `InputDataSet` 資料。 因為這是 `.sql` 檔案，您可使用所有的 Transact-SQL 編輯器功能。

對 SQL 程式碼感到滿意後，只要將 `.sql` 檔案拖曳至 `.R` 檔案的開放式編輯器，您就可以輕鬆地將它與 R 程式碼整合在 `StoredProcedure.R` 中。 在下圖中，`StoredProcedure.Query.sql` 已拖曳至 `sqlQuery(channel, )` 的逗號後面的點：

![將 SQL 檔案讀入 R 字串變數](~/rtvs/media/sql-reference-sql-file-from-r.png)

如您所見，這個簡單的步驟會自動產生 R 程式碼以開啟 `.sql` 檔案，將其內容讀入字串，並將它傳遞給 RODBC 套件以傳送給 SQL Server。

此項目就緒後，您就可以互動方式撰寫 R 程式碼，管理所需的 `InputDataSet` 資料框架。 請記住，您在編輯器中可以只選取 R 程式碼，按 Ctrl+Enter 將它傳送至[互動視窗](interactive-repl.md)。

最後，`StoredProcedure.Template.sql` 包含範本以產生您的 SQL 預存程序︰

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- `StoredProcedure.R` 的內容會取代 `_RCODE_` 預留位置。
- `StoredProcedure.Query.sql` 的內容會取代 `_INPUT_QUERY_` 預留位置。
- 您需要編輯 `WITH RESULT SETS` 子句，描述預存程序傳回之結果集的結構描述。 特別要識別來自您想要傳回給預存程序呼叫端的 `OutputDataSet` 資料框架的資料行。 

以下列查詢為例：

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

您可以使用下列 `WITH RESULT SETS` 子句來指定傳回值的資料類型︰

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>發行 SQL 預存程序

1. 選取 [R 工具] > [資料] > [以選項發行...] 功能表命令。
1. 在出現的對話方塊中，將 [發行到:] 變更為 [資料庫]、指定目標，然後選取 [發行]，RTVS 就會建置及發行預存程序︰

    ![發行預存程序對話方塊](~/rtvs/media/sql-publish-with-options.png)

1. 若要在專案中發行所有預存程序，您也可以使用 [R 工具] > [資料] > [發行預存程序] 命令，以滑鼠右鍵按一下方案總管中的專案也可取得。

> [!Tip]
> 如果您在 Visual Studio 中開啟 SQL Server 物件總管，您也會在資料庫的 [可程式性] > [預存程序] 資料夾中看到您已發行的預存程序。 您也可以滑鼠右鍵按一下並選取 [執行程序]，或藉由在 `.sql` 查詢視窗中以互動方式呼叫它，以從物件總管中執行它。

