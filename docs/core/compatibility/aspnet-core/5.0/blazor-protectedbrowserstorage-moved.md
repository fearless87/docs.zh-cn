---
title: 中断性变更：Blazor：ProtectedBrowserStorage 功能已移动到共享框架
description: 了解 ASP.NET Core 5.0 中的以下中断性变更：Blazor：ProtectedBrowserStorage 功能已移动到共享框架
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c8058adf8b66aef8dd011ea672cd306ae4de60a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759141"
---
# <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a><span data-ttu-id="e9fef-103">Blazor：ProtectedBrowserStorage 功能已移动到共享框架</span><span class="sxs-lookup"><span data-stu-id="e9fef-103">Blazor: ProtectedBrowserStorage feature moved to shared framework</span></span>

<span data-ttu-id="e9fef-104">作为 ASP.NET Core 5.0 RC2 版本的一部分，`ProtectedBrowserStorage` 功能已移动到 ASP.NET Core 共享框架。</span><span class="sxs-lookup"><span data-stu-id="e9fef-104">As part of the ASP.NET Core 5.0 RC2 release, the `ProtectedBrowserStorage` feature moved to the ASP.NET Core shared framework.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e9fef-105">引入的版本</span><span class="sxs-lookup"><span data-stu-id="e9fef-105">Version introduced</span></span>

<span data-ttu-id="e9fef-106">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="e9fef-106">5.0 RC2</span></span>

## <a name="old-behavior"></a><span data-ttu-id="e9fef-107">旧行为</span><span class="sxs-lookup"><span data-stu-id="e9fef-107">Old behavior</span></span>

<span data-ttu-id="e9fef-108">在 ASP.NET Core 5.0 预览版 8 中，此功能作为 [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) 包的一部分提供，但只能在 Blazor WebAssembly 中使用。</span><span class="sxs-lookup"><span data-stu-id="e9fef-108">In ASP.NET Core 5.0 Preview 8, the feature is available as a part of the [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) package but was only usable in Blazor WebAssembly.</span></span>

<span data-ttu-id="e9fef-109">在 ASP.NET Core 5.0 RC1 中，该功能作为 [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) 包的一部分提供，此包引用 `Microsoft.AspNetCore.App` 共享框架。</span><span class="sxs-lookup"><span data-stu-id="e9fef-109">In ASP.NET Core 5.0 RC1, the feature is available as part of the [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) package, which references the `Microsoft.AspNetCore.App` shared framework.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="e9fef-110">新行为</span><span class="sxs-lookup"><span data-stu-id="e9fef-110">New behavior</span></span>

<span data-ttu-id="e9fef-111">在 ASP.NET Core 5.0 RC2 中，引用和使用该功能时，不再需要 NuGet 包引用。</span><span class="sxs-lookup"><span data-stu-id="e9fef-111">In ASP.NET Core 5.0 RC2, a NuGet package reference is no longer needed to reference and use the feature.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e9fef-112">更改原因</span><span class="sxs-lookup"><span data-stu-id="e9fef-112">Reason for change</span></span>

<span data-ttu-id="e9fef-113">移动到共享框架后，可以更好地提供客户预期的用户体验。</span><span class="sxs-lookup"><span data-stu-id="e9fef-113">The move to the shared framework is a better fit for the user experience customers expect.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e9fef-114">建议操作</span><span class="sxs-lookup"><span data-stu-id="e9fef-114">Recommended action</span></span>

<span data-ttu-id="e9fef-115">如果从 ASP.NET Core 5.0 RC1 升级，请完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="e9fef-115">If upgrading from ASP.NET Core 5.0 RC1, complete the following steps:</span></span>

1. <span data-ttu-id="e9fef-116">从项目中删除 `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` 包引用。</span><span class="sxs-lookup"><span data-stu-id="e9fef-116">Remove the `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` package reference from the project.</span></span>
1. <span data-ttu-id="e9fef-117">将 `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` 替换为 `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`。</span><span class="sxs-lookup"><span data-stu-id="e9fef-117">Replace `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="e9fef-118">从 `Startup` 类中删除对 `AddProtectedBrowserStorage` 的调用。</span><span class="sxs-lookup"><span data-stu-id="e9fef-118">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

<span data-ttu-id="e9fef-119">如果从 ASP.NET Core 5.0 预览版 8 升级，请完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="e9fef-119">If upgrading from ASP.NET Core 5.0 Preview 8, complete the following steps:</span></span>

1. <span data-ttu-id="e9fef-120">从项目中删除 `Microsoft.AspNetCore.Components.Web.Extensions` 包引用。</span><span class="sxs-lookup"><span data-stu-id="e9fef-120">Remove the `Microsoft.AspNetCore.Components.Web.Extensions` package reference from the project.</span></span>
1. <span data-ttu-id="e9fef-121">将 `using Microsoft.AspNetCore.Components.Web.Extensions;` 替换为 `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`。</span><span class="sxs-lookup"><span data-stu-id="e9fef-121">Replace `using Microsoft.AspNetCore.Components.Web.Extensions;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="e9fef-122">从 `Startup` 类中删除对 `AddProtectedBrowserStorage` 的调用。</span><span class="sxs-lookup"><span data-stu-id="e9fef-122">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e9fef-123">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e9fef-123">Affected APIs</span></span>

<span data-ttu-id="e9fef-124">无</span><span class="sxs-lookup"><span data-stu-id="e9fef-124">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->