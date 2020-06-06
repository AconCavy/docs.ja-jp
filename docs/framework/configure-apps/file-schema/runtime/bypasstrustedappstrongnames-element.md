---
title: <bypassTrustedAppStrongNames> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 96361a6742d1d2f76cb237344189d3277d7c8069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739083"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="89080-102">\<bypassTrustedAppStrongNames> 要素</span><span class="sxs-lookup"><span data-stu-id="89080-102">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="89080-103">完全に信頼されているアセンブリでの厳密な名前の検証をバイパスするかどうかを指定し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="89080-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a><span data-ttu-id="89080-104">構文</span><span class="sxs-lookup"><span data-stu-id="89080-104">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="89080-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="89080-105">Attributes and Elements</span></span>

<span data-ttu-id="89080-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="89080-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="89080-107">属性</span><span class="sxs-lookup"><span data-stu-id="89080-107">Attributes</span></span>

|<span data-ttu-id="89080-108">属性</span><span class="sxs-lookup"><span data-stu-id="89080-108">Attribute</span></span>|<span data-ttu-id="89080-109">説明</span><span class="sxs-lookup"><span data-stu-id="89080-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="89080-110">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="89080-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="89080-111">完全に信頼されたアセンブリの厳密な名前の検証を回避するバイパス機能が有効かどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="89080-111">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="89080-112">この機能が有効になっている場合、アセンブリの読み込み時に厳密な名前が正しいかどうかは検証されません。</span><span class="sxs-lookup"><span data-stu-id="89080-112">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="89080-113">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="89080-113">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="89080-114">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="89080-114">enabled Attribute</span></span>

|<span data-ttu-id="89080-115">値</span><span class="sxs-lookup"><span data-stu-id="89080-115">Value</span></span>|<span data-ttu-id="89080-116">Description</span><span class="sxs-lookup"><span data-stu-id="89080-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="89080-117">完全に信頼されたアセンブリの厳密な名前の署名は、アセンブリが完全に信頼されているときには検証されません <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="89080-117">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="89080-118">既定値です。</span><span class="sxs-lookup"><span data-stu-id="89080-118">This is the default.</span></span>|
|`false`|<span data-ttu-id="89080-119">完全に信頼されたアセンブリの厳密な名前の署名は、アセンブリが完全信頼に読み込まれるときに検証され <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="89080-119">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="89080-120">厳密な名前の署名は、署名が正しいかどうかのみを確認します。一致のために別の厳密な名前と比較されることはありません。</span><span class="sxs-lookup"><span data-stu-id="89080-120">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="89080-121">子要素</span><span class="sxs-lookup"><span data-stu-id="89080-121">Child Elements</span></span>

<span data-ttu-id="89080-122">なし。</span><span class="sxs-lookup"><span data-stu-id="89080-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="89080-123">親要素</span><span class="sxs-lookup"><span data-stu-id="89080-123">Parent Elements</span></span>

|<span data-ttu-id="89080-124">要素</span><span class="sxs-lookup"><span data-stu-id="89080-124">Element</span></span>|<span data-ttu-id="89080-125">Description</span><span class="sxs-lookup"><span data-stu-id="89080-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="89080-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="89080-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="89080-127">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="89080-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89080-128">解説</span><span class="sxs-lookup"><span data-stu-id="89080-128">Remarks</span></span>

<span data-ttu-id="89080-129">厳密な名前のバイパス機能を使用すると、完全に信頼されたアセンブリに対する厳密な名前の署名の検証のオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="89080-129">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="89080-130">バイ パス機能は、厳密な名前で署名されていて、次の特性を持つアセンブリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="89080-130">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="89080-131">証拠なしで完全 <xref:System.Security.Policy.StrongName> に信頼されている (たとえば、 `MyComputer` ゾーン証拠がある)。</span><span class="sxs-lookup"><span data-stu-id="89080-131">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="89080-132">完全に信頼された <xref:System.AppDomain> に読み込まれる。</span><span class="sxs-lookup"><span data-stu-id="89080-132">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="89080-133">その <xref:System.AppDomain> の <xref:System.AppDomainSetup.ApplicationBase%2A> プロパティに基づいた場所から読み込まれる。</span><span class="sxs-lookup"><span data-stu-id="89080-133">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="89080-134">遅延署名されていない。</span><span class="sxs-lookup"><span data-stu-id="89080-134">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="89080-135">レジストリキーを使用して、コンピューター上のすべてのアプリケーションでバイパス機能が無効になっている場合、この構成ファイルの設定は無効です。</span><span class="sxs-lookup"><span data-stu-id="89080-135">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="89080-136">詳細については、「[方法: 厳密な名前のバイパス機能を無効](../../../../standard/assembly/disable-strong-name-bypass-feature.md)にする」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89080-136">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="89080-137">例</span><span class="sxs-lookup"><span data-stu-id="89080-137">Example</span></span>

<span data-ttu-id="89080-138">次の例は、完全に信頼されたアセンブリの厳密な名前の署名を検証する動作を指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="89080-138">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="89080-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="89080-139">See also</span></span>

- [<span data-ttu-id="89080-140">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="89080-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="89080-141">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="89080-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="89080-142">方法: 厳密な名前のバイパス機能を無効にする</span><span class="sxs-lookup"><span data-stu-id="89080-142">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
