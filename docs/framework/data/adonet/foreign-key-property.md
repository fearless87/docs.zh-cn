---
description: 了解详细信息：外键属性
title: 外键属性
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 1666e4477c09dd5d0ed3d2c35a93ca21824e8a0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724123"
---
# <a name="foreign-key-property"></a>外键属性

实体数据模型 (EDM) 中的 *外键属性* 是一个基元类型 [属性](property.md)， (或一组基元类型属性) 在包含另一个实体类型的 [实体键](entity-key.md)的 [实体类型](entity-type.md)上。  
  
 外键属性相当于关系数据库中的外键列。 与在关系数据库中使用外键列来创建表中各行之间的关系一样，概念模型中的外键属性用于建立实体类型之间的 [关联](association-type.md) 。 当一个类型具有外键属性时， [引用完整性约束](referential-integrity-constraint.md) 用于定义两个实体类型之间的关联。  
  
## <a name="example"></a>示例  

 下图显示了一个具有三个实体类型的概念模型：`Book`、`Publisher` 和 `Author`。 `Book` 实体类型有一个属性 `PublisherId`，当您为 `Publisher` 关联定义一个引用完整性约束时，它将引用 `PublishedBy` 实体类型的实体键。  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "引用约束模型的示例")  
  
 [ADO.NET 实体框架](./ef/index.md)使用一种特定于域的语言 (DSL) 称为概念架构定义语言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 来定义概念模型。 下面的 CSDL 使用外键属性 `PublisherId` 为上图所示的概念模型中的 `PublishedBy` 关联定义了一个引用完整性约束。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>请参阅

- [实体数据模型关键概念](entity-data-model-key-concepts.md)
- [实体数据模型](entity-data-model.md)
