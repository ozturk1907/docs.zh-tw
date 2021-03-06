---
title: GetRequestedRuntimeVersion 函式
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: be7d6ce29a9c9c4e3e530df40432b1a4c3b2d389
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136348"
---
# <a name="getrequestedruntimeversion-function"></a>GetRequestedRuntimeVersion 函式
取得指定的應用程式所要求的 common language runtime （CLR）版本號碼。 如果未安裝該版本，會取得所要求版本之前所安裝的最新版本。  
  
 此函式在 .NET Framework 4 中已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a>參數  
 `pExe`  
 在應用程式的名稱。  
  
 `pVersion`  
 脫銷一個緩衝區，其中包含成功完成時的版本號碼字串。  
  
 `cchBuffer`  
 在版本緩衝區的長度。  
  
 `pdwLength`  
 脫銷版本號碼字串長度的指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準元件物件模型（COM）錯誤碼（如 Winerror.h 中所定義），以及下列值。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|ERROR_INSUFFICIENT_BUFFER|版本緩衝區不夠大，無法儲存版本字串。|  
|E_POINTER|`pdwLength` 為 null。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [GetRequestedRuntimeInfo 函式](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetVersionFromProcess 函式](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
