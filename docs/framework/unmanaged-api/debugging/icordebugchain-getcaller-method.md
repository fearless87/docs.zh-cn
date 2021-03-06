---
description: 了解详细信息： ICorDebugChain：： GetCaller 方法
title: ICorDebugChain::GetCaller 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
ms.openlocfilehash: 5af2132b7fec9e70704db980b95221db6eb273f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695016"
---
# <a name="icordebugchaingetcaller-method"></a>ICorDebugChain::GetCaller 方法

获取调用此链的链。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a>参数  

 `ppChain`  
 弄指向表示调用链的 ICorDebugChain 对象地址的指针。  
  
 如果此链被自发地称为 (如此链或调试器初始化调用堆栈) ，将为 `ppChain` null。  
  
## <a name="remarks"></a>备注  

 如果调用是在线程间封送的，则调用链可能位于不同的线程上。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头**：CorDebug.idl、CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
