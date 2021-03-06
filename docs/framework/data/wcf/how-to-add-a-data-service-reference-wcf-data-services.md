---
description: '了解有关以下内容的详细信息：如何：添加数据服务引用 (WCF Data Services) '
title: 如何：添加数据服务引用（WCF 数据服务）
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 907ad9a7dc3710a6e565de55c74a0d279d20e159
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765745"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>如何： (WCF Data Services 中添加数据服务引用) 

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

您可以使用 Visual Studio 中的 **添加服务引用** 对话框添加对 WCF Data Services 的引用。 这使您可以更轻松地在使用 Visual Studio 开发的客户端应用程序中访问数据服务。 完成此过程后，会基于从数据服务获取的元数据生成数据类。 有关详细信息，请参阅 [生成数据服务客户端库](generating-the-data-service-client-library-wcf-data-services.md)。

## <a name="add-a-data-service-reference"></a>添加数据服务引用

1. （可选）如果数据服务不是解决方案的一部分，且未运行，请启动数据服务，并记下数据服务的 URI。

2. 在 Visual Studio 的 **解决方案资源管理器** 中，右键单击客户端项目，然后选择 "**添加**  >  **服务引用**"。

3. 如果数据服务是当前解决方案的一部分，请单击 " **发现**"。

     \- 或 -

     在 " **地址** " 文本框中，键入数据服务的基 URL （例如）， `http://localhost:1234/Northwind.svc` 然后单击 " **开始**"。

4. 选择“确定”。

     一个新的代码文件，其中包含可以访问数据服务资源并与其交互的数据类将添加到该项目中。

## <a name="see-also"></a>请参阅

- [快速入门](quickstart-wcf-data-services.md)
