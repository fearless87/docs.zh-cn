---
description: 了解详细信息： ICorDebugComObjectValue：： GetCachedInterfaceTypes 方法
title: ICorDebugComObjectValue::GetCachedInterfaceTypes 方法
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
ms.openlocfilehash: b1c65979895dfaeacae3d171adbcfd1455b7030d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764614"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a>ICorDebugComObjectValue::GetCachedInterfaceTypes 方法

为当前对象已强制转换为或用作的接口类型提供枚举器。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a>参数  

 `bIInspectableOnly`  
 中一个值，该值指示方法是只返回 (`IInspectable` 接口) 或由运行时可调用 (包装器缓存的所有 COM 接口接口 Windows 运行时接口) 。  
  
 `ppInterfacesEnum`  
 弄指向 ICorDebugTypeEnum 枚举器地址的指针，该枚举数提供对 ICorDebugType 对象的访问，这些对象表示根据筛选的已筛选的缓存接口类型 `bIInspectableOnly` 。  
  
## <a name="remarks"></a>备注  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugComObjectValue 接口](icordebugcomobjectvalue-interface.md)
- [调试接口](debugging-interfaces.md)
