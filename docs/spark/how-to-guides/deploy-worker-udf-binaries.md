---
title: 針對 Apache Spark 的背景工作角色和使用者定義的函數二進位檔部署 .NET
description: 瞭解如何部署適用于 Apache Spark 背景工作角色和使用者定義函數二進位檔的 .NET。
ms.date: 01/21/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f9197ca3cf8066f0849ebbe70d7757c9035d02f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76748528"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>針對 Apache Spark 的背景工作角色和使用者定義的函數二進位檔部署 .NET

本 how to 提供如何針對 Apache Spark worker 和使用者定義函數二進位檔部署 .NET 的一般指示。 您會瞭解要設定的環境變數，以及用來啟動具有 `spark-submit`之應用程式的一些常用參數。

## <a name="configurations"></a>設定
設定會顯示一般環境變數和參數設定，以便為 Apache Spark 的背景工作角色和使用者定義的函數二進位檔部署 .NET。

### <a name="environment-variables"></a>環境變數
部署背景工作角色和寫入 Udf 時，您可能需要設定幾個常用的環境變數： 

| 環境變數         | 描述
| :--------------------------- | :---------- 
| DOTNET_WORKER_DIR            | 已產生 <code>Microsoft.Spark.Worker</code> 二進位檔的路徑。</br>它是由 Spark 驅動程式使用，並會傳遞給 Spark 執行程式。 如果未設定此變數，Spark 執行執行會搜尋 <code>PATH</code> 環境變數中指定的路徑。</br>_例如 "C:\bin\Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | 以逗號分隔的路徑，其中 <code>Microsoft.Spark.Worker</code> 會載入元件。</br>請注意，如果路徑是以 "." 開頭，則會在前面加上工作目錄。 如果在**yarn 模式**中，"." 會代表容器的工作目錄。</br>_例如，"C:\Users\\&lt;使用者名稱&gt;\\&lt;mysparkapp&gt;\bin\Debug\\&lt;dotnet 版本&gt;"_
| DOTNET_WORKER_DEBUG          | 如果您想要對<a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">UDF 進行調試</a>，請在執行 <code>spark-submit</code>之前，將此環境變數設定為 <code>1</code>。

### <a name="parameter-options"></a>參數選項
一旦將 Spark 應用程式[配套](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies)之後，您就可以使用 `spark-submit`來啟動它。 下表顯示一些常用的選項： 

| 參數名稱        | 描述
| :---------------------| :---------- 
| --class               | 應用程式的進入點。</br>_例如，dotnet. DotnetRunner。_
| --master              | 叢集的<a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">主要 URL</a> 。</br>_例如 yarn_
| --部署模式         | 是否要將您的驅動程式部署在背景工作角色節點（<code>cluster</code>）或本機上做為外部用戶端（<code>client</code>）。</br>預設值：<code>client</code>
| --會議                | <code>key=value</code> 格式的任意 Spark 設定屬性。</br>_例如，yarn. appMasterEnv. DOTNET_WORKER_DIR = .\worker\Microsoft.Spark.Worker_
| --files               | 要放入每個執行程式之工作目錄中的檔案清單（以逗號分隔）。<br/><ul><li>請注意，此選項僅適用于 yarn 模式。</li><li>它支援使用與 Hadoop 相似的 # 來指定檔案名。</br></ul>_例如 <code>myLocalSparkApp.dll#appSeen.dll</code>。在 YARN 上執行時，您的應用程式應該使用名稱做為 <code>appSeen.dll</code> 來參考 <code>myLocalSparkApp.dll</code>。_</li>
| --封存          | 要解壓縮到每個執行程式工作目錄的封存清單（以逗號分隔）。</br><ul><li>請注意，此選項僅適用于 yarn 模式。</li><li>它支援使用與 Hadoop 相似的 # 來指定檔案名。</br></ul>_例如 <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code>。這會將 zip 檔案複製並解壓縮至 <code>worker</code> 資料夾。_</li>
| 應用程式-jar       | 配套的 jar 路徑，包括您的應用程式和所有相依性。</br>_例如，hdfs://&lt;您的 jar&gt;/microsoft-spark-&lt;版本&gt;.jar 的路徑_
| 應用程式引數 | 傳遞至主要類別之 main 方法的引數（如果有的話）。</br>_例如，hdfs://應用程式&lt;路徑&gt;/&lt;您的應用程式&gt;應用程式名稱 &lt;&gt; 應用程式引數 &lt;_

> [!NOTE]
> 使用 `spark-submit`啟動應用程式之前，請 `application-jar` 先指定所有的 `--options`，否則會予以忽略。 如需詳細資訊，請參閱[`spark-submit` 選項](https://spark.apache.org/docs/latest/submitting-applications.html)和[在 YARN 上執行 spark 詳細資料](https://spark.apache.org/docs/latest/running-on-yarn.html)。

## <a name="frequently-asked-questions"></a>常見問題集
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>當我使用 Udf 執行 spark 應用程式時，會收到「FileNotFoundException」錯誤。 我該怎麼做？
> **錯誤：** [錯誤] [TaskRunner] [0] ProcessStream （）失敗，發生例外狀況： FileNotFoundException：元件 ' MySparkApp，版本 = 1.0.0.0，文化特性 = 中性，PublicKeyToken = null ' 找不到檔案： ' mySparkApp .dll '

**答：** 檢查是否已正確設定 `DOTNET_ASSEMBLY_SEARCH_PATHS` 環境變數。 它應該是包含您 `mySparkApp.dll`的路徑。

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>升級 Apache Spark 版本的 .NET 並重設 `DOTNET_WORKER_DIR` 環境變數之後，為什麼仍然會出現下列 `IOException` 錯誤？
> **錯誤：** 在階段11.0 中遺失工作0.0 （TID 24、localhost、執行器驅動程式）： IOException：無法執行程式 "nuget.exe"： CreateProcess 錯誤 = 2，系統找不到指定的檔案。

**答：** 請先嘗試重新開機您的 PowerShell 視窗（或其他命令視窗），使其可以接受最新的環境變數值。 然後啟動您的程式。

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>提交 Spark 應用程式之後，我收到 `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'`的錯誤。
> **錯誤：** [錯誤] [TaskRunner] [0] ProcessStream （）失敗，發生例外狀況： TypeLoadException：無法從元件 ' Mscorlib，Version = 4.0.0.0，Culture = 中性，PublicKeyToken = ... ' 載入類型 ' system.object '。

**答：** 檢查您所使用的 `Microsoft.Spark.Worker` 版本。 有兩種版本： **.NET Framework 4.6.1**和 **.net Core 2.1. x**。 在此情況下，應該使用 `Microsoft.Spark.Worker.net461.win-x64-<version>` （您可以[下載](https://github.com/dotnet/spark/releases)），因為 `System.Runtime.Remoting.Contexts.Context` 僅適用于 .NET Framework。

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>如何? 在 YARN 上使用 Udf 執行我的 spark 應用程式？ 我應該使用哪些環境變數與參數？

**答：** 若要在 YARN 上啟動 spark 應用程式，應將環境變數指定為 `spark.yarn.appMasterEnv.[EnvironmentVariableName]`。 請參閱下面的範例，以使用 `spark-submit`：

```powershell
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master yarn \
--deploy-mode cluster \
--conf spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=./worker/Microsoft.Spark.Worker-<version> \
--conf spark.yarn.appMasterEnv.DOTNET_ASSEMBLY_SEARCH_PATHS=./udfs \
--archives hdfs://<path to your files>/Microsoft.Spark.Worker.net461.win-x64-<version>.zip#worker,hdfs://<path to your files>/mySparkApp.zip#udfs \
hdfs://<path to jar file>/microsoft-spark-2.4.x-<version>.jar \
hdfs://<path to your files>/mySparkApp.zip mySparkApp
```

## <a name="next-steps"></a>後續步驟

* [開始使用 .NET for Apache Spark](../tutorials/get-started.md)
* [在 Windows 上針對 Apache Spark 應用程式的 .NET 進行 Debug](../how-to-guides/debug.md)
