---
title: <seealso> - C#程式設計指南
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: ad22b423d085a152f47c4e34d7ee4247ef9836b8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789687"
---
# <a name="seealso-c-programming-guide"></a>\<seealso > （C#程式設計手冊）

## <a name="syntax"></a>語法

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>參數

- cref = " `member`"

  可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。`member` 必須出現在雙引號 (" ") 內。

  如需如何建立泛型型別 cref 參考的資訊，請參閱[\<see>](./see.md)。

## <a name="remarks"></a>備註

\<seealso> 標記可讓您指定要顯示在＜請參閱＞一節中的文字。 使用 [\<see>](./see.md)，以在文字內指定連結。

使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 編譯可處理檔案的文件註解。

## <a name="example"></a>範例

如需使用 \<seealso> 的範例，請參閱 [\<summary>](./summary.md)。

## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../index.md)
- [建議使用的檔註解標記](./recommended-tags-for-documentation-comments.md)
