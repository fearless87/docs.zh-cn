---
ms.openlocfilehash: d75dc2caa3a002b9d34ac74f2c5c5e192281c0df
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281287"
---
### <a name="default-activityidformat-is-w3c"></a><span data-ttu-id="0e7b6-101">默认 ActivityIdFormat 为 W3C</span><span class="sxs-lookup"><span data-stu-id="0e7b6-101">Default ActivityIdFormat is W3C</span></span>

<span data-ttu-id="0e7b6-102">活动 (<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType>) 的默认标识符格式现在为 <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-102">The default identifier format for activity (<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType>) is now <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0e7b6-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="0e7b6-103">Change description</span></span>

<span data-ttu-id="0e7b6-104">.NET Core 3.0 中引入了 W3C 活动 ID 格式，作为分层 ID 格式的替代格式。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-104">The W3C activity ID format was introduced in .NET Core 3.0 as an alternative to the hierarchical ID format.</span></span> <span data-ttu-id="0e7b6-105">但是，为了保持兼容性，直到 .NET 5.0 才将 W3C 格式设置为默认格式。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-105">However, to preserve compatibility, the W3C format wasn't made the default until .NET 5.0.</span></span> <span data-ttu-id="0e7b6-106">.NET 5.0 中更改了默认格式，因为 [W3C 格式已获得批准](https://www.w3.org/TR/trace-context/)，并广泛用于多种语言实现。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-106">The default was changed in .NET 5.0 because the [W3C format has been ratified](https://www.w3.org/TR/trace-context/) and gained traction across multiple language implementations.</span></span>

<span data-ttu-id="0e7b6-107">如果应用面向除 .NET 5.0 或更高版本之外的平台，那么它会使用旧行为，其中的默认格式为 <xref:System.Diagnostics.ActivityIdFormat.Hierarchical>。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-107">If your app targets a platform other than .NET 5.0 or later, it will experience the old behavior, where <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> is the default format.</span></span> <span data-ttu-id="0e7b6-108">此默认格式适用于平台 net45+、netstandard1.1+ 和 netcoreapp （1.x、2.x 和 3.x）。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-108">This default applies to platforms net45+, netstandard1.1+, and netcoreapp (1.x, 2.x, and 3.x).</span></span> <span data-ttu-id="0e7b6-109">在 .NET 5.0 及更高版本中，<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> 设置为 <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-109">In .NET 5.0 and later, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> is set to <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0e7b6-110">引入的版本</span><span class="sxs-lookup"><span data-stu-id="0e7b6-110">Version introduced</span></span>

<span data-ttu-id="0e7b6-111">5.0 预览版 7</span><span class="sxs-lookup"><span data-stu-id="0e7b6-111">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0e7b6-112">建议操作</span><span class="sxs-lookup"><span data-stu-id="0e7b6-112">Recommended action</span></span>

<span data-ttu-id="0e7b6-113">如果应用程序与用于分布式跟踪的标识符无关，则无需执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-113">If your application is agnostic to the identifier that's used for distributed tracing, no action is needed.</span></span> <span data-ttu-id="0e7b6-114">ASP.NET Core 和 <xref:System.Net.Http.HttpClient> 等库可以使用或传播两个版本的 <xref:System.Diagnostics.ActivityIdFormat>。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-114">Libraries such as ASP.NET Core and <xref:System.Net.Http.HttpClient> can consume or propagate both versions of the <xref:System.Diagnostics.ActivityIdFormat>.</span></span>

<span data-ttu-id="0e7b6-115">如果需要与现有系统的互操作性，或当前系统依赖于标识符的格式，则可以通过将 <xref:System.Diagnostics.Activity.DefaultIdFormat> 设置为 <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> 来保留旧行为。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-115">If you require interoperability with existing systems, or current systems rely on the format of the identifier, you can preserve the old behavior by setting <xref:System.Diagnostics.Activity.DefaultIdFormat> to <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0e7b6-116">或者，可以通过以下三种方式之一来设置 AppContext 开关：</span><span class="sxs-lookup"><span data-stu-id="0e7b6-116">Alternatively, you can set an AppContext switch in one of three ways:</span></span>

- <span data-ttu-id="0e7b6-117">在项目文件中。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-117">In the project file.</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="0e7b6-118">在 runtimeconfig.json 文件中。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-118">In the *runtimeconfig.json* file.</span></span>

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- <span data-ttu-id="0e7b6-119">通过环境变量。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-119">Through an environment variable.</span></span>

  <span data-ttu-id="0e7b6-120">将 `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` 设置为 `true` 或 1。</span><span class="sxs-lookup"><span data-stu-id="0e7b6-120">Set `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` to `true` or 1.</span></span>

#### <a name="category"></a><span data-ttu-id="0e7b6-121">类别</span><span class="sxs-lookup"><span data-stu-id="0e7b6-121">Category</span></span>

<span data-ttu-id="0e7b6-122">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="0e7b6-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0e7b6-123">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="0e7b6-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->