---
description: 了解更多相关信息： Visual Basic 中继承的事件处理程序疑难解答
title: 继承的事件处理程序疑难解答
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: b489b6c85510bb942b403a508b6bbe232c3e1853
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424471"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>有关 Visual Basic 中继承的事件处理程序的疑难解答

本主题列出了继承的组件中的事件处理程序所发生的常见问题。  
  
## <a name="procedures"></a>过程  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>事件处理程序中的代码对每个调用执行两次  
  
- 继承的事件处理程序不得包含 [Handles](../../../language-reference/statements/handles-clause.md) 子句。 基类中的方法已与事件关联，并会相应地激发。 `Handles`从继承的方法中删除子句。  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- 如果继承的方法不具有 `Handles` 关键字，请验证你的代码不包含额外的 [AddHandler 语句](../../../language-reference/statements/addhandler-statement.md) 或处理相同事件的任何其他方法。  
  
## <a name="see-also"></a>请参阅

- [事件](index.md)
