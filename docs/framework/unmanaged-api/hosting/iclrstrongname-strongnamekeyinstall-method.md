---
description: 了解详细信息： ICLRStrongName：： StrongNameKeyInstall 方法
title: ICLRStrongName::StrongNameKeyInstall 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
ms.openlocfilehash: 8f9e7bfebff555a6430a3970c8ee1c481e341f58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799507"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a>ICLRStrongName::StrongNameKeyInstall 方法

将公钥/私钥对导入容器。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a>参数  

 `wszKeyContainer`  
 中密钥容器的名称。 `wszKeyContainer` 必须为非空字符串。  
  
 `pbKeyBlob`  
 中二进制密钥对。  
  
 `cbKeyBlob`  
 中的大小（以字节为单位） `pbKeyBlob` 。  
  
## <a name="return-value"></a>返回值  

 `S_OK` 如果该方法已成功完成，则为;否则，表示失败的 HRESULT 值 (参阅) 列表的 [常见 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。  
  
## <a name="remarks"></a>备注  

 使用 [ICLRStrongName：： StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) 方法删除密钥容器。  
  
## <a name="requirements"></a>要求  

 **平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** MetaHost  
  
 **库：** 作为中的资源包含 MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [StrongNameKeyDelete 方法](iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName 接口](iclrstrongname-interface.md)
