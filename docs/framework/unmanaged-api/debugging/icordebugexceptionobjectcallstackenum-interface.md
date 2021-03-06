---
title: ICorDebugExceptionObjectCallStackEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: 9d98bccdfb83cec547b185693c28f25017d3225f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782801"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a>ICorDebugExceptionObjectCallStackEnum 介面
提供例外狀況物件中內嵌之呼叫堆疊資訊的列舉值。 這個介面是 ICorDebugEnum 介面的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ICorDebugExceptionObjectCallStackEnum：： Next](icordebugexceptionobjectcallstackenum-next-method.md)|取得指定數目的[CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md)物件，其中包含例外狀況物件之呼叫堆疊的相關資訊。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugExceptionObjectCallStackEnum` 介面會執行 ICorDebugEnum 介面。  
  
 `ICorDebugExceptionObjectCallStackEnum` 實例會藉由呼叫[ICorDebugExceptionObjectValue：： EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)方法來填入[CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md)物件。 您可以藉由呼叫[ICorDebugExceptionObjectCallStackEnum：： Next](icordebugexceptionobjectcallstackenum-next-method.md)方法來列舉集合中的呼叫堆疊專案。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
