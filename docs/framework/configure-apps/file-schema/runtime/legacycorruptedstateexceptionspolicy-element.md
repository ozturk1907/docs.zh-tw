---
title: <legacyCorruptedStateExceptionsPolicy> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: d1d29a37999a01f3e370897a1052f4f94435a218
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116464"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a>\<legacyCorruptedStateExceptionsPolicy > 元素
指定通用語言執行時間是否允許 managed 程式碼攔截存取違規和其他損毀狀態例外狀況。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<legacyCorruptedStateExceptionsPolicy >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定應用程式將會攔截損毀狀態例外狀況失敗，例如存取違規。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|應用程式將不會攔截損毀狀態例外狀況失敗，例如存取違規。 這是預設值。|  
|`true`|應用程式將會攔截損毀狀態例外狀況失敗，例如存取違規。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在 .NET Framework 版本3.5 和舊版中，通用語言執行平臺允許 managed 程式碼攔截因進程狀態損毀而引發的例外狀況。 存取違規是這類例外狀況的範例。  
  
 從 .NET Framework 4 開始，managed 程式碼就不會再于 `catch` 組塊中捕捉這些類型的例外狀況。 不過，您可以透過兩種方式來覆寫此變更並維護損毀狀態例外狀況的處理：  
  
- 將 `<legacyCorruptedStateExceptionsPolicy>` 元素的 `enabled` 屬性設定為 [`true`]。 此設定會套用 processwide，並會影響所有方法。  
  
 -或-  
  
- 將 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> 屬性套用至包含例外狀況 `catch` 區塊的方法。  
  
 此 configuration 元素僅適用于 .NET Framework 4 和更新版本。  
  
## <a name="example"></a>範例  
 下列範例顯示如何指定應用程式應該還原為 .NET Framework 4 之前的行為，並攔截所有損毀狀態例外狀況失敗。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
