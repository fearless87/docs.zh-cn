---
title: 中断性变更：CA2013:请勿将 ReferenceEquals 与值类型结合使用
description: 了解 .NET 5.0 中启用代码分析规则 CA2013 所致的中断性变更。
ms.date: 09/03/2020
ms.openlocfilehash: ca2b845427eff547b996b577394c6859e30f50bf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759066"
---
# <a name="warning-ca2013-do-not-use-referenceequals-with-value-types"></a><span data-ttu-id="e0f78-103">警告 CA2013：请勿将 ReferenceEquals 与值类型结合使用</span><span class="sxs-lookup"><span data-stu-id="e0f78-103">Warning CA2013: Do not use ReferenceEquals with value types</span></span>

<span data-ttu-id="e0f78-104">从 .NET 5.0 开始，默认启用 .NET 代码分析器规则 [CA2013](/visualstudio/code-quality/ca2013)。</span><span class="sxs-lookup"><span data-stu-id="e0f78-104">.NET code analyzer rule [CA2013](/visualstudio/code-quality/ca2013) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="e0f78-105">对于使用 <xref:System.Object.ReferenceEquals(System.Object,System.Object)> 比较一个或多个值类型的相等性的代码，它会生成任何生成警告。</span><span class="sxs-lookup"><span data-stu-id="e0f78-105">It produces a build warning for any code where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span>

## <a name="change-description"></a><span data-ttu-id="e0f78-106">更改说明</span><span class="sxs-lookup"><span data-stu-id="e0f78-106">Change description</span></span>

<span data-ttu-id="e0f78-107">从 .NET 5.0 开始，.NET SDK 包括 [.NET 源代码分析器](../../../../fundamentals/code-analysis/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e0f78-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="e0f78-108">其中一些规则会默认启用，包括 [CA2013](/visualstudio/code-quality/ca2013)。</span><span class="sxs-lookup"><span data-stu-id="e0f78-108">Several of these rules are enabled, by default, including [CA2013](/visualstudio/code-quality/ca2013).</span></span> <span data-ttu-id="e0f78-109">如果项目包含违反此规则的代码，并已被配置为将警告视为错误，则此更改可能会中断生成。</span><span class="sxs-lookup"><span data-stu-id="e0f78-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="e0f78-110">规则 CA2013 查找使用 <xref:System.Object.ReferenceEquals(System.Object,System.Object)> 比较一个或多个值类型的相等性的实例。</span><span class="sxs-lookup"><span data-stu-id="e0f78-110">Rule CA2013 finds instances where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span> <span data-ttu-id="e0f78-111">通过此方式比较值类型的相等性可能会导致错误的结果，因为会先限定这些值，然后再将其进行比较。</span><span class="sxs-lookup"><span data-stu-id="e0f78-111">Comparing value types for equality in this way can lead to incorrect results, because the values are boxed before they're compared.</span></span> <span data-ttu-id="e0f78-112">即使比较的值表示值类型的同一个实例，<xref:System.Object.ReferenceEquals(System.Object,System.Object)> 也会返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="e0f78-112"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> will return `false` even if the compared values represent the same instance of a value type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e0f78-113">引入的版本</span><span class="sxs-lookup"><span data-stu-id="e0f78-113">Version introduced</span></span>

<span data-ttu-id="e0f78-114">5.0</span><span class="sxs-lookup"><span data-stu-id="e0f78-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e0f78-115">建议操作</span><span class="sxs-lookup"><span data-stu-id="e0f78-115">Recommended action</span></span>

- <span data-ttu-id="e0f78-116">更改代码以使用适当的相等运算符，例如 `==`。</span><span class="sxs-lookup"><span data-stu-id="e0f78-116">Change the code to use an appropriate equality operator, such as `==`.</span></span> <span data-ttu-id="e0f78-117">不应禁止显示此警告。</span><span class="sxs-lookup"><span data-stu-id="e0f78-117">You should not suppress this warning.</span></span>

- <span data-ttu-id="e0f78-118">若要完全禁用代码分析，请在项目文件中将 `EnableNETAnalyzers` 设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="e0f78-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="e0f78-119">有关详细信息，请参阅 [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="e0f78-119">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e0f78-120">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e0f78-120">Affected APIs</span></span>

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

### Category

Code analysis

-->