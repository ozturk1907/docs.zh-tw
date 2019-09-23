---
ms.openlocfilehash: ba543414d4f84362c9b9b876395815e837efbd3f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181756"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="c4c28-101">MyServices 命名空間中的類型無法使用</span><span class="sxs-lookup"><span data-stu-id="c4c28-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="c4c28-102"><xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>命名空間中的類型無法使用。</span><span class="sxs-lookup"><span data-stu-id="c4c28-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c4c28-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c4c28-103">Version introduced</span></span>

<span data-ttu-id="c4c28-104">.NET Core 3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="c4c28-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="c4c28-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c4c28-105">Details</span></span>

<span data-ttu-id="c4c28-106"><xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>命名空間中的類型可在某些 .net Core 3.0 Preview 版本中取得。</span><span class="sxs-lookup"><span data-stu-id="c4c28-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="c4c28-107">從 .NET Core 3.0 Preview 9 開始就不再提供這些功能。</span><span class="sxs-lookup"><span data-stu-id="c4c28-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="c4c28-108">已移除類型，以避免不必要的元件相依性或後續版本中的重大變更。</span><span class="sxs-lookup"><span data-stu-id="c4c28-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="c4c28-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c4c28-109">Recommended action</span></span>

<span data-ttu-id="c4c28-110">如果您的程式碼相依于**MyServices**類型及其成員，則 .net 類別庫中會有對應的類型和成員。</span><span class="sxs-lookup"><span data-stu-id="c4c28-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="c4c28-111">以下是**MyServices**類型對應到其對等 .net 類別庫類型的對應：</span><span class="sxs-lookup"><span data-stu-id="c4c28-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="c4c28-112">MyServices 類型</span><span class="sxs-lookup"><span data-stu-id="c4c28-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="c4c28-113">.NET 類別庫類型</span><span class="sxs-lookup"><span data-stu-id="c4c28-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="c4c28-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType>針對 WPF 應用程式<xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> ，適用于 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="c4c28-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>| 
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="c4c28-115">命名空間中<xref:System.IO>的類型</span><span class="sxs-lookup"><span data-stu-id="c4c28-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="c4c28-116"><xref:Microsoft.Win32>命名空間中與登錄相關的類型</span><span class="sxs-lookup"><span data-stu-id="c4c28-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="c4c28-117">分類</span><span class="sxs-lookup"><span data-stu-id="c4c28-117">Category</span></span>

<span data-ttu-id="c4c28-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4c28-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c4c28-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c4c28-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >
