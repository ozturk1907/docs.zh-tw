---
title: 使用 .NET Core 來建立 REST 用戶端
description: 本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: eb7946d669de60c3469ca8098e40b159082ea270
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921093"
---
# <a name="rest-client"></a>REST 用戶端

本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。 您將了解：

* .NET Core CLI 的基本概念。
* 「C# 語言」功能的概觀。
* 使用 NuGet 來管理相依性
* HTTP 通訊
* 處理 JSON 資訊
* 使用「屬性」來管理組態。

您將建置一個對 GitHub 上的 REST 服務發出「HTTP 要求」的應用程式。 您將讀取 JSON 格式的資訊，並將該 JSON 封包轉換成 C# 物件。 最後，您將了解如何使用 C# 物件。

本教學課程中有許多功能。 讓我們來逐一建置它們。

如果您偏好追蹤本主題的[最終範例](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)，則可以下載它。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

## <a name="prerequisites"></a>必要條件：

您將必須設定電腦以執行 .NET Core。 您可以在[.Net Core 下載](https://dotnet.microsoft.com/download)頁面上找到安裝指示。 您可以在 Windows、Linux、macOS 或是 Docker 容器中執行此應用程式。
您將必須安裝慣用的程式碼編輯器。 以下說明使用 [Visual Studio Code (英文)](https://code.visualstudio.com/)，這是開放原始碼的跨平台編輯器。 不過，您可以使用您熟悉的任何工具。

## <a name="create-the-application"></a>建立應用程式

第一個步驟是建立新的應用程式。 請開啟命令提示字元，然後為您的應用程式建立新目錄。 使該目錄成為目前的目錄。 在主控台視窗中輸入下列命令：

```dotnetcli
dotnet new console --name WebApiClient
```

這會建立基本 "Hello World" 應用程式的起始檔案。 專案名稱為 "WebApiClient"。 因為這是新的專案，所以沒有任何相依性。 第一次執行時，會下載 .NET Core framework、安裝開發憑證，以及執行 NuGet 套件管理員，以還原遺失的相依性。

在您開始建立修改前，請先在命令提示字元中鍵入 `dotnet run` ([請參閱附註](#dotnet-restore-note))，執行您的應用程式。 如果您的環境缺少相依性，`dotnet run` 會自動執行 `dotnet restore`。 如果您的應用程式需要重建，它也會執行 `dotnet build`。
在初始安裝之後，當它對您的專案有意義時，您只需要執行 `dotnet restore` 或 `dotnet build`。

## <a name="adding-new-dependencies"></a>新增新的相依性

.NET Core 的其中一個主要設計目標就是將 .NET 安裝大小縮減到最小。 如果應用程式的某些功能需要額外的程式庫，您可以將這些相依性新增到 C# 專案檔 (\*.csproj) 中。 在我們的範例中，您必須新增 `System.Runtime.Serialization.Json` 套件，讓您的應用程式可以處理 JSON 回應。

您將需要此應用程式的 `System.Runtime.Serialization.Json` 套件。 執行下列[.NET CLI](../../core/tools/dotnet-add-package.md)命令，將它新增至您的專案：

```console
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a>提出 Web 要求

現在您已經準備好開始從 Web 接收資料。 在此應用程式中，您將從 [GitHub API](https://developer.github.com/v3/) 讀取資訊。 讓我們在 [.NET Foundation](https://www.dotnetfoundation.org/) 的庇護下讀取專案的相關資訊。 您將從對 GitHub API 提出要求以擷取專案相關資訊著手。 您將使用的端點是：<https://api.github.com/orgs/dotnet/repos>。 您想要擷取這些專案的所有相關資訊，因此您將使用 HTTP GET 要求。
您的瀏覽器也會使用 HTTP GET 要求，因此您可以將該 URL 貼到瀏覽器中，以查看您將接收和處理的資訊。

您需使用 <xref:System.Net.Http.HttpClient> 類別來提出 Web 要求。 與所有新式 .NET API 相同，<xref:System.Net.Http.HttpClient> 針對它的長時間執行 API 只支援非同步方法。
請從建立非同步方法著手。 您將在建置應用程式的功能時填入實作。 請從開啟您專案目錄中的 `program.cs` 檔案並將下列方法新增到 `Program` 類別著手：

```csharp
private static async Task ProcessRepositories()
{
}
```

您將需要在 `Main` 方法的頂端加入 `using` 指示詞，讓C#編譯器能夠辨識 <xref:System.Threading.Tasks.Task> 的類型：

```csharp
using System.Threading.Tasks;
```

如果您在此時建置專案，您將會收到針對此方法產生的警告，因為它不包含任何 `await` 運算子，所以將會以同步方式執行。 目前請先忽略該警告；您將在填入方法時新增 `await` 運算子。

接著，請將 `namespace` 陳述式中定義的命名空間從其預設值 `ConsoleApp` 重新命名為 `WebAPIClient`。 我們稍後將會在此命名空間中定義 `repo` 類別。

接著，請將 `Main` 方法更新成呼叫此方法。 `ProcessRepositories` 方法會傳回工作，而且您不應該在該工作完成之前結束程式。 因此，您必須變更 `Main`的簽章。 新增 `async` 修飾詞，並將傳回類型變更為 `Task`。 然後，在方法的主體中，新增對 `ProcessRepositories`的呼叫。 將 `await` 關鍵字新增至該方法呼叫：

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

現在，您擁有一個不會執行任何動作但會以非同步方式執行的程式。 來加以改善吧。

首先，您需要一個能夠從網路擷取資料的物件；使用 <xref:System.Net.Http.HttpClient> 即可達成。 此物件會處理要求和回應。 在*Program.cs*檔案內的 `Program` 類別中，具現化該類型的單一實例。

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static async Task Main(string[] args)
        {
            //...
        }
    }
}
```

讓我們回到 `ProcessRepositories` 方法並填入其第一個版本：

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

您也必須在檔案頂端加入兩個新的 `using` 指示詞，以進行編譯：

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

第一個版本會提出 Web 要求來讀取 dotnet foundation 組織底下的所有儲存機制清單。 (.NET Foundation 的 gitHub 識別碼是 'dotnet')。 前幾行會為這個要求設定 <xref:System.Net.Http.HttpClient>。 首先，會將它設定為接受 GitHub JSON 回應。
此格式就是 JSON。 下一行會將「使用者代理程式」標頭新增到來自此物件的所有要求。 這兩個標頭會受到 GitHub 伺服器程式碼檢查，並且是從 GitHub 擷取資訊的必要標頭。

設定 <xref:System.Net.Http.HttpClient> 之後，您需提出 Web 要求並擷取回應。 在這個第一版中，您會使用 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> 便利方法。 這個便利方法會啟動一個提出 Web 要求的工作，然後當要求返回時，它會讀取回應資料流並從該資料流擷取內容。 回應本文會以 <xref:System.String> 的形式傳回。 當工作完成時，就會提供該字串。

此方法的最後兩行會等候該工作，然後將回應顯示在主控台中。
請建置應用程式並執行它。 建置警告現在已消失，因為 `ProcessRepositories` 現在確實包含 `await` 運算子。 您將會看到一長串顯示的 JSON 格式文字。

## <a name="processing-the-json-result"></a>處理 JSON 結果

此時，您已撰寫程式碼來從 Web 伺服器擷取回應，並顯示包含在該回應中的文字。 接著，讓我們將該 JSON 回應轉換成 C# 物件。

<xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> 類別會將物件序列化為 JSON，並將 JSON 還原序列化為物件。 一開始請先定義類別，以代表從 GitHub API 傳回的 `repo` JSON 物件：

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; }
    }
}
```

請將上述程式碼放在名為 'repo.cs' 的新檔案中。 這個類別版本代表處理 JSON 資料的最簡單路徑。 類別名稱和成員名稱會符合 JSON 封包中使用的名稱，而不是符合下列 C# 慣例。 您將在稍後藉由提供一些其他組態屬性來修正此問題。 此類別示範了 JSON 序列化和還原序列化的另一個重要功能：並非 JSON 封包中的所有欄位都屬於此類別。
JSON 序列化程式將會忽略未包含在所要使用之類別型別中的資訊。
這個功能可讓您更容易建立只對 JSON 封包中的欄位子集有作用的型別。

現在您已經建立型別，讓我們來將它還原序列化。 

接著，您將使用序列化程式將 JSON 轉換成 C# 物件。 將您 `ProcessRepositories` 方法中 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> 的呼叫取代為下列三行：

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

您使用的是新的命名空間，因此您也必須將它新增至檔案頂端：

```csharp
using System.Text.Json;
```

請注意，您現在使用的是 <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> 而不是 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>。 序列化程式會使用資料流 (而不是字串) 作為其來源。 讓我們來說明上述程式碼片段第C#二行中所使用的一些語言功能。 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> 的第一個引數是 `await` 運算式。 （其他兩個參數是選擇性的，而且會在程式碼片段中省略）。Await 運算式可以出現在您程式碼中的任何位置，雖然目前為止，您只會看到它們是指派語句的一部分。 `Deserialize` 方法是*泛型*，這表示您必須提供類型引數，以供應該從 JSON 文字建立的物件種類。 在此範例中，您要還原序列化為 `List<Repository>`，也就是另一個泛型物件，也就是 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>。 `List<>` 類別會儲存物件的集合。 型別引數會宣告儲存在 `List<>`中的物件類型。 JSON 文字代表存放庫物件的集合，因此 `Repository`類型引數。

您差不多已經完成這個部分。 現在您已將 JSON 轉換成 C# 物件，讓我們來顯示每個儲存機制的名稱。 將下列幾行：

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

取代為：

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

編譯並執行應用程式。 它將會列印出隸屬於 .NET Foundation 的儲存機制名稱。

## <a name="controlling-serialization"></a>控制序列化

在您新增更多功能之前，讓我們先使用 `[JsonPropertyName]` 屬性來處理 `name` 屬性。 請對 repo.cs 中 `name` 欄位的宣告進行下列變更：

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

若要使用 `[JsonPropertyName]` 屬性，您必須將 <xref:System.Text.Json.Serialization> 命名空間新增至 `using` 指示詞：

```csharp
using System.Text.Json.Serialization;
```

這項變更意謂著您必須變更 program.cs 中寫入每個儲存機制名稱的程式碼：

```csharp
Console.WriteLine(repo.Name);
```

執行 `dotnet run` 以確定對應正確。 您應該會看到與之前相同的輸出。

讓我們在新增新功能之前，再多進行一項變更。 `ProcessRepositories` 方法可以執行非同步工作，然後傳回儲存機制的集合。 讓我們從該方法傳回 `List<Repository>`，並將寫入資訊的程式碼移到 `Main` 方法中。

請變更 `ProcessRepositories` 的簽章以傳回其結果為 `Repository` 物件清單的工作：

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

接著，在處理 JSON 回應後，直接傳回儲存機制：

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

編譯器會產生用於傳回的 `Task<T>` 物件，因為您已將此方法標示為 `async`。
接著，讓我們來修改 `Main` 方法，使它擷取那些結果並將每個儲存機制名稱寫入到主控台。 您的 `Main` 方法現在看起來會像這樣：

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a>讀取更多資訊

讓我們再多處理 GitHub API 所傳送之 JSON 封包中的幾個屬性，來結束這個部分。 您不會想要全盤了解，但新增幾個屬性將可示範更多一些的 C# 語言功能。

讓我們從再多將幾個簡單型別新增到 `Repository` 類別定義著手。 請將下列屬性新增到該類別：

```csharp
[JsonPropertyName("description")]
public string Description { get; set; }

[JsonPropertyName("html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName("homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName("watchers")]
public int Watchers { get; set; }
```

這些屬性具有從字串型別 (JSON 封包所包含的型別) 轉換成目標型別的內建轉換。 您可能不熟悉 <xref:System.Uri> 型別。 它代表 URI，或在此案例中是代表 URL。 在 `Uri` 和 `int` 型別的案例中，如果 JSON 封包包含不會轉換成目標型別的資料，序列化動作將會擲回例外狀況。

在您新增這些屬性之後，請更新 `Main` 方法以顯示下列元素：

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```

在最後一個步驟中，讓我們新增最後一個推送作業的資訊。 此資訊會在 JSON 回應中採用下列形式的格式：

```json
2016-02-08T21:27:00Z
```

該格式並不符合任何標準 .NET <xref:System.DateTime> 格式。 因此，您將需要撰寫一個自訂的轉換方法。 您可能也不會想要對 `Repository` 類別的使用者公開原始字串。 屬性也可以幫助控制該行為。 首先，定義一個 `public` 屬性，以保存您 `Repository` 類別中日期和時間的字串表示，以及一個會傳回格式字串的 `LastPush` `readonly` 屬性，該字串代表所傳回的日期：

```csharp
[JsonPropertyName("pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

讓我們來看一下我們剛才定義的新結構。 `LastPush` 屬性是使用 `get` 存取子的*運算式主體成員*所定義。 沒有 `set` 存取子。 省略 `set` 存取子是您在中C#定義*唯讀*屬性的方式。 （是的，您可以在中C#建立*僅限寫入的*屬性，但其值有限）。<xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> 方法會剖析字串並使用提供的日期格式來建立 <xref:System.DateTime> 物件，並使用 `CultureInfo` 物件將額外的中繼資料新增至 `DateTime`。 如果剖析作業失敗，屬性存取子就會擲回例外狀況。

若要使用 <xref:System.Globalization.CultureInfo.InvariantCulture>，您必須將 <xref:System.Globalization> 命名空間新增至 `repo.cs`中的 `using` 指示詞：

```csharp
using System.Globalization;
```

最後，請在主控台中再多新增一個輸出陳述式，這樣您便已準備好來重新建置及執行此應用程式：

```csharp
Console.WriteLine(repo.LastPush);
```

您的版本現在應該與[完成範例](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)相符。

## <a name="conclusion"></a>結論

本教學課程示範了如何提出 Web 要求、剖析結果，以及顯示這些結果的屬性。 您也在專案中新增了新的套件作為相依性。 您已了解一些支援物件導向技術的 C# 語言功能。

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
