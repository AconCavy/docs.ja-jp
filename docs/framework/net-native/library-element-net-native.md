---
title: <Library>要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: f94bfe047fa7a95b6f24264bae0b27112c589dfd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128364"
---
# <a name="library-element-net-native"></a><span data-ttu-id="78fbb-102">\<Library>要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="78fbb-102">\<Library> Element (.NET Native)</span></span>
<span data-ttu-id="78fbb-103">実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。</span><span class="sxs-lookup"><span data-stu-id="78fbb-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="78fbb-104">\<Directives> 要素</span><span class="sxs-lookup"><span data-stu-id="78fbb-104">\<Directives> Element</span></span>  
<span data-ttu-id="78fbb-105">\<Library> 要素</span><span class="sxs-lookup"><span data-stu-id="78fbb-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78fbb-106">構文</span><span class="sxs-lookup"><span data-stu-id="78fbb-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78fbb-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="78fbb-107">Attributes and Elements</span></span>  
 <span data-ttu-id="78fbb-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="78fbb-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78fbb-109">属性</span><span class="sxs-lookup"><span data-stu-id="78fbb-109">Attributes</span></span>  
  
|<span data-ttu-id="78fbb-110">属性</span><span class="sxs-lookup"><span data-stu-id="78fbb-110">Attribute</span></span>|<span data-ttu-id="78fbb-111">説明</span><span class="sxs-lookup"><span data-stu-id="78fbb-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="78fbb-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="78fbb-112">Required attribute.</span></span> <span data-ttu-id="78fbb-113">アセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="78fbb-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="78fbb-114">この `<Library>` 要素の子要素によって、このアセンブリ内にある型と型のメンバーのランタイム リフレクション ポリシーが定義されます。</span><span class="sxs-lookup"><span data-stu-id="78fbb-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="78fbb-115">Name 属性</span><span class="sxs-lookup"><span data-stu-id="78fbb-115">Name attribute</span></span>  
  
|<span data-ttu-id="78fbb-116">値</span><span class="sxs-lookup"><span data-stu-id="78fbb-116">Value</span></span>|<span data-ttu-id="78fbb-117">Description</span><span class="sxs-lookup"><span data-stu-id="78fbb-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="78fbb-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="78fbb-118">*assembly_name*</span></span>|<span data-ttu-id="78fbb-119">ファイル拡張子のないアセンブリの簡易名です。</span><span class="sxs-lookup"><span data-stu-id="78fbb-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="78fbb-120">この属性は、<xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> プロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="78fbb-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="78fbb-121">たとえば、Extensions.dll というアセンブリの名前は "Extensions" です。</span><span class="sxs-lookup"><span data-stu-id="78fbb-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="78fbb-122">アセンブリのメタデータの条件付きインクルードをサポートする特殊な形式の *assembly_name* については、「解説」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78fbb-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78fbb-123">子要素</span><span class="sxs-lookup"><span data-stu-id="78fbb-123">Child Elements</span></span>  
  
|<span data-ttu-id="78fbb-124">要素</span><span class="sxs-lookup"><span data-stu-id="78fbb-124">Element</span></span>|<span data-ttu-id="78fbb-125">Description</span><span class="sxs-lookup"><span data-stu-id="78fbb-125">Description</span></span>|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="78fbb-126">特定のアセンブリ内のすべての型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="78fbb-126">Applies policy to all the types in a particular assembly.</span></span>|  
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="78fbb-127">特定の名前空間内のすべての型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="78fbb-127">Applies policy to all the types in a particular namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="78fbb-128">クラスや構造体などの特定の型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="78fbb-128">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="78fbb-129">構築されたジェネリック型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="78fbb-129">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="78fbb-130">たとえば、要素を [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 使用して、型のポリシーを定義することができ `List<String>` ます。</span><span class="sxs-lookup"><span data-stu-id="78fbb-130">For example, a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78fbb-131">親要素</span><span class="sxs-lookup"><span data-stu-id="78fbb-131">Parent Elements</span></span>  
  
|<span data-ttu-id="78fbb-132">要素</span><span class="sxs-lookup"><span data-stu-id="78fbb-132">Element</span></span>|<span data-ttu-id="78fbb-133">Description</span><span class="sxs-lookup"><span data-stu-id="78fbb-133">Description</span></span>|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|<span data-ttu-id="78fbb-134">ランタイム ディレクティブ ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="78fbb-134">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78fbb-135">解説</span><span class="sxs-lookup"><span data-stu-id="78fbb-135">Remarks</span></span>  
 <span data-ttu-id="78fbb-136">要素には、 [\<Directives>](directives-element-net-native.md) 0 個以上の要素を含めることができ `<Library>` ます。</span><span class="sxs-lookup"><span data-stu-id="78fbb-136">The [\<Directives>](directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="78fbb-137">`<Library>` 要素は、実行時に必要なメタデータを持つプログラム要素を定義するためのコンテナーとして機能します。この要素はポリシーを表しません。</span><span class="sxs-lookup"><span data-stu-id="78fbb-137">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="78fbb-138">コンパイル時に、コンパイラ ツールは `<Library>` 要素により指定されたライブラリでのみ、その子要素により示されるプログラム要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="78fbb-138">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="78fbb-139">これに対して、コンパイラツールは、要素の子要素によって識別されるプログラム要素のすべてのライブラリ (including.NET Framework core ライブラリ) を検索し [\<Application>](application-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="78fbb-139">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="78fbb-140">`<Library>` ディレクティブは、条件付きで使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="78fbb-140">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="78fbb-141">要素の名前の `<Library>` 先頭と末尾がアスタリスク () の場合 \* 、このディレクティブは、 `<Library>` アスタリスクによって指定されたアセンブリがアプリによって参照されている場合にのみ効果があります。</span><span class="sxs-lookup"><span data-stu-id="78fbb-141">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="78fbb-142">たとえば、次のランタイムディレクティブは、ユーティリティ .dll アセンブリがアプリによって参照されている場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="78fbb-142">For example, the following runtime directive applies only if the Utilities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="78fbb-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="78fbb-143">See also</span></span>

- [<span data-ttu-id="78fbb-144">\<Application>Element</span><span class="sxs-lookup"><span data-stu-id="78fbb-144">\<Application> Element</span></span>](application-element-net-native.md)
- [<span data-ttu-id="78fbb-145">\<Directives>Element</span><span class="sxs-lookup"><span data-stu-id="78fbb-145">\<Directives> Element</span></span>](directives-element-net-native.md)
- [<span data-ttu-id="78fbb-146">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="78fbb-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="78fbb-147">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="78fbb-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
