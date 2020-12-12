---
title: 如何使用 System.Text.Json 忽略属性
description: 了解使用 .NET 中的 System.Text.Json 进行序列化时如何忽略属性。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: ed7ef8509d6660bbbbaf194a87aa9d4815143507
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439753"
---
# <a name="how-to-ignore-properties-with-no-locsystemtextjson"></a><span data-ttu-id="efd93-103">如何使用 System.Text.Json 忽略属性</span><span class="sxs-lookup"><span data-stu-id="efd93-103">How to ignore properties with System.Text.Json</span></span>

<span data-ttu-id="efd93-104">将 C# 对象序列化为 JavaScript 对象表示法 (JSON) 时，默认情况下，所有公共属性都会序列化。</span><span class="sxs-lookup"><span data-stu-id="efd93-104">When serializing C# objects to JavaScript Object Notation (JSON), by default, all public properties are serialized.</span></span> <span data-ttu-id="efd93-105">如果不想让某些属性出现在生成的 JSON 中，则有几个选项可用。</span><span class="sxs-lookup"><span data-stu-id="efd93-105">If you don't want some of them to appear in the resulting JSON, you have several options.</span></span> <span data-ttu-id="efd93-106">本文将介绍如何根据各种条件忽略属性：</span><span class="sxs-lookup"><span data-stu-id="efd93-106">In this article you learn how to ignore properties based on various criteria:</span></span>

::: zone pivot="dotnet-5-0"

* [<span data-ttu-id="efd93-107">单个属性</span><span class="sxs-lookup"><span data-stu-id="efd93-107">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="efd93-108">所有只读属性</span><span class="sxs-lookup"><span data-stu-id="efd93-108">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="efd93-109">所有 null 值属性</span><span class="sxs-lookup"><span data-stu-id="efd93-109">All null-value properties</span></span>](#ignore-all-null-value-properties)
* [<span data-ttu-id="efd93-110">所有默认值属性</span><span class="sxs-lookup"><span data-stu-id="efd93-110">All default-value properties</span></span>](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [<span data-ttu-id="efd93-111">单个属性</span><span class="sxs-lookup"><span data-stu-id="efd93-111">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="efd93-112">所有只读属性</span><span class="sxs-lookup"><span data-stu-id="efd93-112">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="efd93-113">所有 null 值属性</span><span class="sxs-lookup"><span data-stu-id="efd93-113">All null-value properties</span></span>](#ignore-all-null-value-properties)
::: zone-end

## <a name="ignore-individual-properties"></a><span data-ttu-id="efd93-114">忽略单个属性</span><span class="sxs-lookup"><span data-stu-id="efd93-114">Ignore individual properties</span></span>

<span data-ttu-id="efd93-115">若要忽略单个属性，请使用 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 特性。</span><span class="sxs-lookup"><span data-stu-id="efd93-115">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="efd93-116">下面是要进行序列化的示例类型和 JSON 输出：</span><span class="sxs-lookup"><span data-stu-id="efd93-116">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithIgnoreAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
<span data-ttu-id="efd93-117">可以通过设置 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 特性的 `Condition` 属性来指定条件排除。</span><span class="sxs-lookup"><span data-stu-id="efd93-117">You can specify conditional exclusion by setting the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property.</span></span> <span data-ttu-id="efd93-118"><xref:System.Text.Json.Serialization.JsonIgnoreCondition> 枚举提供下列选项：</span><span class="sxs-lookup"><span data-stu-id="efd93-118">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition> enum provides the following options:</span></span>

* <span data-ttu-id="efd93-119">`Always` - 始终忽略属性。</span><span class="sxs-lookup"><span data-stu-id="efd93-119">`Always` - The property is always ignored.</span></span> <span data-ttu-id="efd93-120">如果未指定 `Condition`，则假设此选项。</span><span class="sxs-lookup"><span data-stu-id="efd93-120">If no `Condition` is specified, this option is assumed.</span></span>
* <span data-ttu-id="efd93-121">`Never` - 无论 `DefaultIgnoreCondition`、`IgnoreReadOnlyProperties` 和 `IgnoreReadOnlyFields` 全局设置如何，始终序列化和反序列化属性。</span><span class="sxs-lookup"><span data-stu-id="efd93-121">`Never` - The property is always serialized and deserialized, regardless of the `DefaultIgnoreCondition`, `IgnoreReadOnlyProperties`, and `IgnoreReadOnlyFields` global settings.</span></span>
* <span data-ttu-id="efd93-122">`WhenWritingDefault` - 如果属性是引用类型 `null`可为 null 的值类型 `null` 或值类型 `default`，则在序列化中忽略属性。</span><span class="sxs-lookup"><span data-stu-id="efd93-122">`WhenWritingDefault` - The property is ignored on serialization if it's a reference type `null`, a nullable value type `null`, or a value type `default`.</span></span>
* <span data-ttu-id="efd93-123">`WhenWritingNull` - 如果属性是引用类型 `null` 或可为 null 的值类型 `null`，则在序列化中忽略属性。</span><span class="sxs-lookup"><span data-stu-id="efd93-123">`WhenWritingNull` - The property is ignored on serialization if it's a reference type `null`, or a nullable value type `null`.</span></span>

<span data-ttu-id="efd93-124">下面的示例说明 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 特性的 `Condition` 属性的用法：</span><span class="sxs-lookup"><span data-stu-id="efd93-124">The following example illustrates use of the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

## <a name="ignore-all-read-only-properties"></a><span data-ttu-id="efd93-125">忽略所有只读属性</span><span class="sxs-lookup"><span data-stu-id="efd93-125">Ignore all read-only properties</span></span>

<span data-ttu-id="efd93-126">如果属性包含公共 getter 而不是公共 setter，则属性为只读。</span><span class="sxs-lookup"><span data-stu-id="efd93-126">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="efd93-127">若要在序列化时忽略所有只读属性，请将 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> 设置为 `true`，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="efd93-127">To ignore all read-only properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs" id="Serialize":::

<span data-ttu-id="efd93-128">下面是要进行序列化的示例类型和 JSON 输出：</span><span class="sxs-lookup"><span data-stu-id="efd93-128">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithROProperty":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="efd93-129">此选项仅适用于序列化。</span><span class="sxs-lookup"><span data-stu-id="efd93-129">This option applies only to serialization.</span></span> <span data-ttu-id="efd93-130">在反序列化过程中，默认情况下会忽略只读属性。</span><span class="sxs-lookup"><span data-stu-id="efd93-130">During deserialization, read-only properties are ignored by default.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="efd93-131">此选项仅适用于属性。</span><span class="sxs-lookup"><span data-stu-id="efd93-131">This option applies only to properties.</span></span> <span data-ttu-id="efd93-132">若要在[序列化字段](system-text-json-how-to.md#include-fields)时忽略只读字段，请使用 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> 全局设置。</span><span class="sxs-lookup"><span data-stu-id="efd93-132">To ignore read-only fields when [serializing fields](system-text-json-how-to.md#include-fields), use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

## <a name="ignore-all-null-value-properties"></a><span data-ttu-id="efd93-133">忽略所有 null 值属性</span><span class="sxs-lookup"><span data-stu-id="efd93-133">Ignore all null-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="efd93-134">若要忽略所有 null 值属性，请将 <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> 属性设置为 <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull>，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="efd93-134">To ignore all null-value properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="efd93-135">若要在序列化时忽略所有 null 值属性，请将 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> 属性设置为 `true`，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="efd93-135">To ignore all null-value properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs" id="Serialize":::

<span data-ttu-id="efd93-136">下面是要进行序列化的示例对象和 JSON 输出：</span><span class="sxs-lookup"><span data-stu-id="efd93-136">Here's an example object to serialize and JSON output:</span></span>

| <span data-ttu-id="efd93-137">Property</span><span class="sxs-lookup"><span data-stu-id="efd93-137">Property</span></span>             | <span data-ttu-id="efd93-138">值</span><span class="sxs-lookup"><span data-stu-id="efd93-138">Value</span></span>                         |
|----------------------|-------------------------------|
| `Date`               | `8/1/2019 12:00:00 AM -07:00` |
| `TemperatureCelsius` | `25`                          |
| `Summary`            | `null`                        |

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

## <a name="ignore-all-default-value-properties"></a><span data-ttu-id="efd93-139">忽略所有默认值属性</span><span class="sxs-lookup"><span data-stu-id="efd93-139">Ignore all default-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="efd93-140">若要防止对值类型属性中的默认值进行序列化，请将 <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> 属性设置为 <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault>，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="efd93-140">To prevent serialization of default values in value type properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

<span data-ttu-id="efd93-141"><xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> 设置还会阻止对 null 值引用类型和可为 null 的值类型属性进行序列化。</span><span class="sxs-lookup"><span data-stu-id="efd93-141">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> setting also prevents serialization of null-value reference type and nullable value type properties.</span></span>

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="efd93-142">在 .NET Core 3.1 的 `System.Text.Json` 中，无内置方式来阻止对值类型为默认值的属性进行序列化。</span><span class="sxs-lookup"><span data-stu-id="efd93-142">There is no built-in way to prevent serialization of properties with value type defaults in `System.Text.Json` in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="efd93-143">请参阅</span><span class="sxs-lookup"><span data-stu-id="efd93-143">See also</span></span>

* [<span data-ttu-id="efd93-144">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="efd93-144">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="efd93-145">实例化 JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="efd93-145">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="efd93-146">启用不区分大小写的匹配</span><span class="sxs-lookup"><span data-stu-id="efd93-146">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="efd93-147">自定义属性名称和值</span><span class="sxs-lookup"><span data-stu-id="efd93-147">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="efd93-148">允许无效的 JSON</span><span class="sxs-lookup"><span data-stu-id="efd93-148">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="efd93-149">处理溢出 JSON</span><span class="sxs-lookup"><span data-stu-id="efd93-149">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="efd93-150">保留循环引用</span><span class="sxs-lookup"><span data-stu-id="efd93-150">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="efd93-151">不可变类型和非公共访问器</span><span class="sxs-lookup"><span data-stu-id="efd93-151">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="efd93-152">多态序列化</span><span class="sxs-lookup"><span data-stu-id="efd93-152">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="efd93-153">[System.Text.Json API 参考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="efd93-153">[System.Text.Json API reference](xref:System.Text.Json)</span></span>