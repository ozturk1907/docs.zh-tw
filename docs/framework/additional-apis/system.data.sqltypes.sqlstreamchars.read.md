---
title: SqlStreamChars.Read (Char []，Int32，Int32) 方法 (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 87bff6dd78743ae08a5a3db8a783b56a0b7c3f24
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152531"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="d264b-102">SqlStreamChars.Read (Char []，Int32，Int32) 方法</span><span class="sxs-lookup"><span data-stu-id="d264b-102">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="d264b-103">當在衍生類別中覆寫時，請從輸入資料流讀取下的一組字元。</span><span class="sxs-lookup"><span data-stu-id="d264b-103">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="d264b-104">包含這個方法的組件有 SQLAccess.dll friend 關聯性。</span><span class="sxs-lookup"><span data-stu-id="d264b-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="d264b-105">它適用於 SQL server。</span><span class="sxs-lookup"><span data-stu-id="d264b-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="d264b-106">其他資料庫，請使用該資料庫所提供的主控機制。</span><span class="sxs-lookup"><span data-stu-id="d264b-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="d264b-107">參數</span><span class="sxs-lookup"><span data-stu-id="d264b-107">Parameters</span></span>

`buffer`\
<span data-ttu-id="d264b-108">要讀取的字元陣列。</span><span class="sxs-lookup"><span data-stu-id="d264b-108">A char array to read.</span></span>

`offset`\
<span data-ttu-id="d264b-109">相對於原點的位移。</span><span class="sxs-lookup"><span data-stu-id="d264b-109">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="d264b-110">若要從目前資料流讀取的字元數。</span><span class="sxs-lookup"><span data-stu-id="d264b-110">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="d264b-111">Returns</span><span class="sxs-lookup"><span data-stu-id="d264b-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="d264b-112">讀入緩衝區的字元總數。</span><span class="sxs-lookup"><span data-stu-id="d264b-112">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="d264b-113">備註</span><span class="sxs-lookup"><span data-stu-id="d264b-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="d264b-114">`SqlStreamChars.Read`方法是私用，而且不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="d264b-114">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d264b-115">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="d264b-115">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="d264b-116">需求</span><span class="sxs-lookup"><span data-stu-id="d264b-116">Requirements</span></span>

<span data-ttu-id="d264b-117">**命名空間︰** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="d264b-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="d264b-118">**組件：** System.Data （在 System.Data.dll 中)</span><span class="sxs-lookup"><span data-stu-id="d264b-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="d264b-119">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="d264b-119">**.NET Framework versions:** Available since 2.0.</span></span>