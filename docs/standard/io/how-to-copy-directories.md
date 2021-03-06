---
title: 如何：複製目錄
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: 223e83a5ff6a73825985ec4e3b6b601fb196fe5e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707896"
---
# <a name="how-to-copy-directories"></a>如何：複製目錄
本主題示範如何使用 I/O 類別將某一個目錄的內容同步複製到另一個位置。 

如需非同步檔案複製的範例，請參閱[非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)。 

此範例會將 `DirectoryCopy` 方法的 `copySubDirs` 設定為 `true` 來複製子目錄。 `DirectoryCopy` 方法會以遞迴方式複製子目錄，方法是在每個子目錄上呼叫其本身，直到沒有其他要複製的子目錄為止。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [檔案和資料流 I/O](../../../docs/standard/io/index.md)
- [一般 I/O 工作](../../../docs/standard/io/common-i-o-tasks.md)
- [非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)
