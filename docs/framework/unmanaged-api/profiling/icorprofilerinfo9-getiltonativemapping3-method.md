---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 5c49d75432980d2f3af77ee040bc6eb20886b027
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861667"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>ICorProfilerInfo9：： GetILToNativeMapping3 方法

假設機器碼的起始位址，會傳回這個程式碼編譯版本的原生到 IL 對應資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a>參數

- `pNativeCodeStartAddress`

  中的 \[]：原生函式開頭的指標。

- `cMap`

  \[in] `map` 陣列的大小上限。

- `pcMap`

  \[out] 可用 COR_DEBUG_IL_TO_NATIVE_MAP 結構的總數。

- `map`

  \[out] [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md)結構的陣列，其中每一個都會指定位移。 `GetILToNativeMapping3` 方法傳回之後，`map` 將會包含部分或所有 `COR_DEBUG_IL_TO_NATIVE_MAP` 結構。

## <a name="remarks"></a>備註

啟用階層式編譯時，方法可能會有一個以上的機器碼主體。 [ICorProfilerInfo9：： GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md)會傳回所有機器碼主體的起始位址。

## <a name="requirements"></a>需求

**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.NET framework 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>請參閱

- [ICorProfilerInfo9 介面](icorprofilerinfo9-interface.md)
