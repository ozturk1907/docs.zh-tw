---
title: invalidVariant MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c34f160b643a0431168097d3832357b4ac6e4557
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052566"
---
# <a name="invalidvariant-mda"></a>invalidVariant MDA
當從機器碼或 Unmanaged 程式碼呼叫至 Managed 程式碼時遇到無效的 `VARIANT` 結構，就會啟動 `invalidVariant` Managed 偵錯助理 (MDA)。  
  
## <a name="symptoms"></a>徵兆  
 在機器碼和 Managed 程式碼轉換期間的未預期行為，這會牽涉到封送處理 `VARIANT` 給物件。  
  
## <a name="cause"></a>原因  
 機器碼傳遞格式不正確的 `VARIANT` 結構給 Managed 程式碼。  如果 `VARIANT` 無效，則執行階段嘗試封送處理 `VARIANT` 給物件，並啟動 MDA。 無效的 `VARIANT` 範例，包含具有 `VARTYPE` VT_EMPTY &#124; VT_BYREF 的 `VARIANT` 或具有 `VARTYPE` VT_VARIANT 的 `VARIANT`。  
  
## <a name="resolution"></a>解決方式  
 傳遞 `VARIANT` 的機器碼或 Unmanaged 程式碼必須確保 `VARIANT` 格式正確且已初始化。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對執行階段行為沒有影響。  
  
## <a name="output"></a>Output  
 MDA 訊息，指出執行階段偵測到無效的 `VARIANT` 由 Unmanaged 模組傳遞至 Managed 程式碼。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [診斷 Managed 偵錯助理的錯誤](diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../interop/interop-marshaling.md)
