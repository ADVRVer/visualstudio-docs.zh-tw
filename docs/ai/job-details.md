# <a name="view-recent-job-performance-and-details"></a>檢視最近的作業效能和詳細資料
提交作業之後，您可以檢視作業清單，以查看它們的狀態、期間及其他資訊。

1. 在 [伺服器總管] 中，展開特定的計算內容 
1. 在 [作業] 上按兩下
1. 您會看到已提交到該計算內容的作業清單。 
1. 在清單中選取特定的 [作業] 來檢視詳細資料

![監視作業](media\job-details\monitor-jobs.png)

> 提交到 Linux VM 的作業歷程記錄會儲存在 VM 上的 /tmp 目錄中。 因此，每當重新啟動時，作業歷程記錄便會清除。 若要永久儲存您的作業歷程記錄，請在 Azure Machine Learning 中將您的 VM 設定為計算內容，然後提交作業到 Azure Machine Learning (選取您的 VM 作為計算內容)