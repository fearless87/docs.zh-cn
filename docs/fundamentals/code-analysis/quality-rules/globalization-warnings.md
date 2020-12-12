---
title: " (代码分析) 全球化规则"
description: 了解代码分析规则全球化规则
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- rules, globalization
- globalization rules
- globalization [Visual Studio], rules
- managed code analysis rules, globalization rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 83ecc52c5e20e074c6c1aed68204a574494f42d5
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2020
ms.locfileid: "96590447"
---
# <a name="globalization-rules"></a><span data-ttu-id="9ffe2-103">全球化规则</span><span class="sxs-lookup"><span data-stu-id="9ffe2-103">Globalization rules</span></span>

<span data-ttu-id="9ffe2-104">全球化规则支持世界通用库和应用程序。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-104">Globalization rules support world-ready libraries and applications.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9ffe2-105">在本节中</span><span class="sxs-lookup"><span data-stu-id="9ffe2-105">In this section</span></span>

|<span data-ttu-id="9ffe2-106">规则</span><span class="sxs-lookup"><span data-stu-id="9ffe2-106">Rule</span></span>|<span data-ttu-id="9ffe2-107">描述</span><span class="sxs-lookup"><span data-stu-id="9ffe2-107">Description</span></span>|
|----------|-----------------|
|[<span data-ttu-id="9ffe2-108">CA1303:请不要将文本作为本地化参数传递</span><span class="sxs-lookup"><span data-stu-id="9ffe2-108">CA1303: Do not pass literals as localized parameters</span></span>](ca1303.md)|<span data-ttu-id="9ffe2-109">外部可见方法将字符串文本作为参数传递给 .NET 构造函数或方法，并且该字符串应可本地化。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-109">An externally visible method passes a string literal as a parameter to a .NET constructor or method, and that string should be localizable.</span></span>|
|[<span data-ttu-id="9ffe2-110">CA1304:指定 CultureInfo</span><span class="sxs-lookup"><span data-stu-id="9ffe2-110">CA1304: Specify CultureInfo</span></span>](ca1304.md)|<span data-ttu-id="9ffe2-111">某方法或构造函数调用的成员有一个接受 System.Globalization.CultureInfo 参数的重载，但该方法或构造函数没有调用接受 CultureInfo 参数的重载。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-111">A method or constructor calls a member that has an overload that accepts a System.Globalization.CultureInfo parameter, and the method or constructor does not call the overload that takes the CultureInfo parameter.</span></span> <span data-ttu-id="9ffe2-112">如果未提供 CultureInfo 或 System.IFormatProvider 对象，则重载成员提供的默认值可能不会在所有区域设置中产生您想要的效果。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-112">When a CultureInfo or System.IFormatProvider object is not supplied, the default value that is supplied by the overloaded member might not have the effect that you want in all locales.</span></span>|
|[<span data-ttu-id="9ffe2-113">CA1305:指定 IFormatProvider</span><span class="sxs-lookup"><span data-stu-id="9ffe2-113">CA1305: Specify IFormatProvider</span></span>](ca1305.md)|<span data-ttu-id="9ffe2-114">某方法或构造函数调用的一个或多个成员有接受 System.IFormatProvider 参数的重载，但该方法或构造函数没有调用接受 IFormatProvider 参数的重载。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-114">A method or constructor calls one or more members that have overloads that accept a System.IFormatProvider parameter, and the method or constructor does not call the overload that takes the IFormatProvider parameter.</span></span> <span data-ttu-id="9ffe2-115">如果未提供 System.Globalization.CultureInfo 或 IFormatProvider 对象，则重载成员提供的默认值可能不会在所有区域设置中产生您想要的效果。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-115">When a System.Globalization.CultureInfo or IFormatProvider object is not supplied, the default value that is supplied by the overloaded member might not have the effect that you want in all locales.</span></span>|
|[<span data-ttu-id="9ffe2-116">CA1307:为了清晰起见，请指定 StringComparison</span><span class="sxs-lookup"><span data-stu-id="9ffe2-116">CA1307: Specify StringComparison for clarity</span></span>](ca1307.md)|<span data-ttu-id="9ffe2-117">字符串比较运算使用不设置 StringComparison 参数的方法重载。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-117">A string comparison operation uses a method overload that does not set a StringComparison parameter.</span></span>|
|[<span data-ttu-id="9ffe2-118">CA1308:将字符串规范化为大写</span><span class="sxs-lookup"><span data-stu-id="9ffe2-118">CA1308: Normalize strings to uppercase</span></span>](ca1308.md)|<span data-ttu-id="9ffe2-119">字符串应正常化为大写字母。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-119">Strings should be normalized to uppercase.</span></span> <span data-ttu-id="9ffe2-120">少量字符转换为小写字母后不能再转换回来。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-120">A small group of characters cannot make a round trip when they are converted to lowercase.</span></span>|
|[<span data-ttu-id="9ffe2-121">CA1309:使用按顺序的 StringComparison</span><span class="sxs-lookup"><span data-stu-id="9ffe2-121">CA1309: Use ordinal StringComparison</span></span>](ca1309.md)|<span data-ttu-id="9ffe2-122">非语义的字符串比较运算不会将 StringComparison 参数设置为 Ordinal 或 OrdinalIgnoreCase。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-122">A string comparison operation that is nonlinguistic does not set the StringComparison parameter to either Ordinal or OrdinalIgnoreCase.</span></span> <span data-ttu-id="9ffe2-123">因此，通过将参数显式设置为 StringComparison.Ordinal 或 StringComparison.OrdinalIgnoreCase，通常可以提高代码的速度、正确性和可靠性。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-123">By explicitly setting the parameter to either StringComparison.Ordinal or StringComparison.OrdinalIgnoreCase, your code often gains speed, becomes more correct, and becomes more reliable.</span></span>|
|[<span data-ttu-id="9ffe2-124">CA1310：为了确保正确，请指定 StringComparison</span><span class="sxs-lookup"><span data-stu-id="9ffe2-124">CA1310: Specify StringComparison for correctness</span></span>](ca1310.md)|<span data-ttu-id="9ffe2-125">在默认情况下，字符串比较操作使用未设置 StringComparison 参数并使用特定于区域性的字符串比较的方法重载。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-125">A string comparison operation uses a method overload that does not set a StringComparison parameter and uses culture-specific string comparison by default.</span></span>|
|[<span data-ttu-id="9ffe2-126">CA2101：为 P/Invoke 字符串参数指定封送处理</span><span class="sxs-lookup"><span data-stu-id="9ffe2-126">CA2101: Specify marshaling for P/Invoke string arguments</span></span>](ca2101.md)|<span data-ttu-id="9ffe2-127">平台调用成员允许部分受信任的调用方，具有字符串参数，并不显式封送字符串。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-127">A platform invoke member allows for partially trusted callers, has a string parameter, and does not explicitly marshal the string.</span></span> <span data-ttu-id="9ffe2-128">这可能导致潜在的安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="9ffe2-128">This can cause a potential security vulnerability.</span></span>|