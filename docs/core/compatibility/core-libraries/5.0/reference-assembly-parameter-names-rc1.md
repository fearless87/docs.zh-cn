---
title: 中断性变更：RC2 中的参数名称已更改
description: 了解核心 .NET 库中的以下 .NET 5.0 中断性变更：某些引用程序集参数名称已从 .NET 5.0 的预览版本和候选发布版本更改。
ms.date: 11/01/2020
ms.openlocfilehash: 554a4fa9e08fdb504f380465496d7e7e9df85814
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759153"
---
# <a name="parameter-names-changed-in-rc2"></a><span data-ttu-id="46d69-103">RC2 中的参数名称已更改</span><span class="sxs-lookup"><span data-stu-id="46d69-103">Parameter names changed in RC2</span></span>

<span data-ttu-id="46d69-104">某些引用程序集参数名称已更改以匹配实现程序集中的参数名称。</span><span class="sxs-lookup"><span data-stu-id="46d69-104">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

## <a name="change-description"></a><span data-ttu-id="46d69-105">更改描述</span><span class="sxs-lookup"><span data-stu-id="46d69-105">Change description</span></span>

<span data-ttu-id="46d69-106">在以前的 .NET 5.0 预览版和 RC 版本中，某些[引用程序集](../../../../standard/assembly/reference-assemblies.md)参数名称与实现程序集中的对应参数不同。</span><span class="sxs-lookup"><span data-stu-id="46d69-106">In previous .NET 5.0 preview and RC versions, some [reference assembly](../../../../standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="46d69-107">使用命名参数和反射时，这可能会导致出现问题。</span><span class="sxs-lookup"><span data-stu-id="46d69-107">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="46d69-108">在 .NET 5.0 RC2 中，这些不匹配的参数名称在引用程序集中已更新，以与实现程序集中的相应参数名完全匹配。</span><span class="sxs-lookup"><span data-stu-id="46d69-108">In .NET 5.0 RC2, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="46d69-109">下表显示了更改的 API 和参数名称。</span><span class="sxs-lookup"><span data-stu-id="46d69-109">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="46d69-110">API</span><span class="sxs-lookup"><span data-stu-id="46d69-110">API</span></span> | <span data-ttu-id="46d69-111">旧参数名称</span><span class="sxs-lookup"><span data-stu-id="46d69-111">Old parameter name</span></span> | <span data-ttu-id="46d69-112">新参数名称</span><span class="sxs-lookup"><span data-stu-id="46d69-112">New parameter name</span></span> |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

## <a name="reason-for-change"></a><span data-ttu-id="46d69-113">更改原因</span><span class="sxs-lookup"><span data-stu-id="46d69-113">Reason for change</span></span>

<span data-ttu-id="46d69-114">更改参数名称以保持一致性，避免在使用命名参数和反射时出现故障。</span><span class="sxs-lookup"><span data-stu-id="46d69-114">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="46d69-115">引入的版本</span><span class="sxs-lookup"><span data-stu-id="46d69-115">Version introduced</span></span>

<span data-ttu-id="46d69-116">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="46d69-116">5.0 RC2</span></span>

## <a name="recommended-action"></a><span data-ttu-id="46d69-117">建议操作</span><span class="sxs-lookup"><span data-stu-id="46d69-117">Recommended action</span></span>

<span data-ttu-id="46d69-118">如果由于参数名称更改而遇到编译器错误，请相应地更新参数名称。</span><span class="sxs-lookup"><span data-stu-id="46d69-118">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="46d69-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="46d69-119">Affected APIs</span></span>

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->