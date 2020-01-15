---
title: データ コントラクト スキーマの参照
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: af183fa02ea3ec98f316979198624351d9b25f21
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963367"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="b2ffa-102">データ コントラクト スキーマの参照</span><span class="sxs-lookup"><span data-stu-id="b2ffa-102">Data Contract Schema Reference</span></span>

<span data-ttu-id="b2ffa-103">ここでは、XML シリアル化用の共通言語ランタイム (CLR) 型を表すために <xref:System.Runtime.Serialization.DataContractSerializer> が使用する XML スキーマ (XSD) のサブセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>

## <a name="datacontractserializer-mappings"></a><span data-ttu-id="b2ffa-104">DataContractSerializer のマッピング</span><span class="sxs-lookup"><span data-stu-id="b2ffa-104">DataContractSerializer Mappings</span></span>

<span data-ttu-id="b2ffa-105">`DataContractSerializer` は、メタデータエンドポイントまたは[ServiceModel メタデータユーティリティツール (svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、WINDOWS COMMUNICATION FOUNDATION (WCF) サービスからメタデータをエクスポートするときに、CLR 型を XSD にマップします。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="b2ffa-106">詳細については、「[データコントラクトシリアライザー](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-106">For more information, see [Data Contract Serializer](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span></span>

<span data-ttu-id="b2ffa-107">また、 `DataContractSerializer` は、Svcutil.exe を使用して Web サービス記述言語 (WSDL) や XSD ドキュメントにアクセスし、サービスまたはクライアントのデータ コントラクトを生成するときに、XSD を CLR 型にマッピングします。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>

<span data-ttu-id="b2ffa-108">`DataContractSerializer`を使用して CLR 型にマッピングできるのは、この文書に記載されている要件に適合する XML スキーマ インスタンスに限られます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>

### <a name="support-levels"></a><span data-ttu-id="b2ffa-109">サポート レベル</span><span class="sxs-lookup"><span data-stu-id="b2ffa-109">Support Levels</span></span>

<span data-ttu-id="b2ffa-110">`DataContractSerializer` は、特定の XML スキーマ機能に次のサポート レベルを提供します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>

- <span data-ttu-id="b2ffa-111">**サポートあり**。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-111">**Supported**.</span></span> <span data-ttu-id="b2ffa-112">この機能から CLR 型または属性の一方または両方への、 `DataContractSerializer`を使用する明示的なマッピングが存在します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>

- <span data-ttu-id="b2ffa-113">**無視**。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-113">**Ignored**.</span></span> <span data-ttu-id="b2ffa-114">この機能は、 `DataContractSerializer`によってインポートされたスキーマで使用できますが、コードの生成に影響しません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>

- <span data-ttu-id="b2ffa-115">**禁止**。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-115">**Forbidden**.</span></span> <span data-ttu-id="b2ffa-116">`DataContractSerializer` は、この機能を使用するスキーマのインポートをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="b2ffa-117">たとえば、Svcutil.exe は、この機能を使用するスキーマに基づいて WSDL にアクセスする場合、代わりに <xref:System.Xml.Serialization.XmlSerializer> を使用します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="b2ffa-118">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-118">This is by default.</span></span>

## <a name="general-information"></a><span data-ttu-id="b2ffa-119">一般情報</span><span class="sxs-lookup"><span data-stu-id="b2ffa-119">General Information</span></span>

- <span data-ttu-id="b2ffa-120">スキーマ名前空間については、「 [XML Schema (XML スキーマ)](https://www.w3.org/2001/XMLSchema)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-120">The schema namespace is described at [XML Schema](https://www.w3.org/2001/XMLSchema).</span></span> <span data-ttu-id="b2ffa-121">このドキュメントでは、プレフィックス "xs" を使用しています。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-121">The prefix "xs" is used in this document.</span></span>

- <span data-ttu-id="b2ffa-122">スキーマ以外の名前空間を含む属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-122">Any attributes with a non-schema namespace are ignored.</span></span>

- <span data-ttu-id="b2ffa-123">注釈 (このドキュメントで説明しているものを除きます) はすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-123">Any annotations (except for those described in this document) are ignored.</span></span>

### <a name="xsschema-attributes"></a><span data-ttu-id="b2ffa-124">\<xs: schema >: attributes</span><span class="sxs-lookup"><span data-stu-id="b2ffa-124">\<xs:schema>: attributes</span></span>

|<span data-ttu-id="b2ffa-125">属性</span><span class="sxs-lookup"><span data-stu-id="b2ffa-125">Attribute</span></span>|<span data-ttu-id="b2ffa-126">DataContract</span><span class="sxs-lookup"><span data-stu-id="b2ffa-126">DataContract</span></span>|
|---------------|------------------|
|`attributeFormDefault`|<span data-ttu-id="b2ffa-127">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-127">Ignored.</span></span>|
|`blockDefault`|<span data-ttu-id="b2ffa-128">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-128">Ignored.</span></span>|
|`elementFormDefault`|<span data-ttu-id="b2ffa-129">修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-129">Must be qualified.</span></span> <span data-ttu-id="b2ffa-130">`DataContractSerializer`でスキーマをサポートするには、すべての要素を修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="b2ffa-131">これを行うには、xs:schema/@elementFormDefault を "qualified" に設定するか、個々の要素宣言で xs:element/@form を "qualified" に設定します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|
|`finalDefault`|<span data-ttu-id="b2ffa-132">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-132">Ignored.</span></span>|
|`Id`|<span data-ttu-id="b2ffa-133">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-133">Ignored.</span></span>|
|`targetNamespace`|<span data-ttu-id="b2ffa-134">サポートされます。データ コントラクト名前空間にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="b2ffa-135">この属性を指定しなかった場合は、空の名前空間が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="b2ffa-136">予約された名前空間をすることはできません `http://schemas.microsoft.com/2003/10/Serialization/` です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-136">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|
|`version`|<span data-ttu-id="b2ffa-137">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-137">Ignored.</span></span>|

### <a name="xsschema-contents"></a><span data-ttu-id="b2ffa-138">\<xs: schema >: コンテンツ</span><span class="sxs-lookup"><span data-stu-id="b2ffa-138">\<xs:schema>: contents</span></span>

|<span data-ttu-id="b2ffa-139">目次</span><span class="sxs-lookup"><span data-stu-id="b2ffa-139">Contents</span></span>|<span data-ttu-id="b2ffa-140">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-140">Schema</span></span>|
|--------------|------------|
|`include`|<span data-ttu-id="b2ffa-141">サポートあり。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-141">Supported.</span></span> <span data-ttu-id="b2ffa-142">`DataContractSerializer` では xs:include と xs:import がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="b2ffa-143">ただし、メタデータをローカル ファイルから読み込む場合、Svcutil.exe では、後続の `xs:include/@schemaLocation` 参照と `xs:import/@location` 参照が制限されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="b2ffa-144">この場合、 `include` ではなく帯域外機構を通じてスキーマ ファイルの一覧を渡す必要があります。 `include`されたスキーマ ドキュメントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`redefine`|<span data-ttu-id="b2ffa-145">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-145">Forbidden.</span></span> <span data-ttu-id="b2ffa-146">セキュリティ上の理由により、 `xs:redefine` では、 `DataContractSerializer` の使用が禁止されています。 `x:redefine` では、 `schemaLocation` を後続させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="b2ffa-147">状況によっては、DataContract を使用する Svcutil.exe では、 `schemaLocation`の使用が制限されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|
|`import`|<span data-ttu-id="b2ffa-148">サポートあり。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-148">Supported.</span></span> <span data-ttu-id="b2ffa-149">`DataContractSerializer` では、 `xs:include` と `xs:import`がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="b2ffa-150">ただし、メタデータをローカル ファイルから読み込む場合、Svcutil.exe では、後続の `xs:include/@schemaLocation` 参照と `xs:import/@location` 参照が制限されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="b2ffa-151">この場合、 `include` ではなく帯域外機構を通じてスキーマ ファイルの一覧を渡す必要があります。 `include`されたスキーマ ドキュメントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`simpleType`|<span data-ttu-id="b2ffa-152">サポートあり。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-152">Supported.</span></span> <span data-ttu-id="b2ffa-153">`xs:simpleType` のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-153">See the `xs:simpleType` section.</span></span>|
|`complexType`|<span data-ttu-id="b2ffa-154">サポートされます。データ コントラクトにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="b2ffa-155">`xs:complexType` のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-155">See the `xs:complexType` section.</span></span>|
|`group`|<span data-ttu-id="b2ffa-156">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-156">Ignored.</span></span> <span data-ttu-id="b2ffa-157">`DataContractSerializer` では、 `xs:group`、 `xs:attributeGroup`、および `xs:attribute`の使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="b2ffa-158">これらの宣言は `xs:schema`の子として無視され、 `complexType` やその他のサポートされている構文内から参照できません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`attributeGroup`|<span data-ttu-id="b2ffa-159">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-159">Ignored.</span></span> <span data-ttu-id="b2ffa-160">`DataContractSerializer` では、 `xs:group`、 `xs:attributeGroup`、および `xs:attribute`の使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="b2ffa-161">これらの宣言は `xs:schema`の子として無視され、 `complexType` やその他のサポートされている構文内から参照できません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`element`|<span data-ttu-id="b2ffa-162">サポートあり。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-162">Supported.</span></span> <span data-ttu-id="b2ffa-163">グローバル要素宣言 (GED) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-163">See Global Element Declaration (GED).</span></span>|
|`attribute`|<span data-ttu-id="b2ffa-164">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-164">Ignored.</span></span> <span data-ttu-id="b2ffa-165">`DataContractSerializer` では、 `xs:group`、 `xs:attributeGroup`、および `xs:attribute`の使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="b2ffa-166">これらの宣言は `xs:schema`の子として無視され、 `complexType` やその他のサポートされている構文内から参照できません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`notation`|<span data-ttu-id="b2ffa-167">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-167">Ignored.</span></span>|

## <a name="complex-types--xscomplextype"></a><span data-ttu-id="b2ffa-168">複合型– \<xs: complexType ></span><span class="sxs-lookup"><span data-stu-id="b2ffa-168">Complex Types – \<xs:complexType></span></span>

### <a name="general-information"></a><span data-ttu-id="b2ffa-169">一般情報</span><span class="sxs-lookup"><span data-stu-id="b2ffa-169">General Information</span></span>

<span data-ttu-id="b2ffa-170">各複合型 \<xs: complexType >、データコントラクトにマップされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>

### <a name="xscomplextype-attributes"></a><span data-ttu-id="b2ffa-171">\<xs: complexType >: attributes</span><span class="sxs-lookup"><span data-stu-id="b2ffa-171">\<xs:complexType>: attributes</span></span>

|<span data-ttu-id="b2ffa-172">属性</span><span class="sxs-lookup"><span data-stu-id="b2ffa-172">Attribute</span></span>|<span data-ttu-id="b2ffa-173">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-173">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="b2ffa-174">false (既定) のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-174">Must be false (default).</span></span>|
|`block`|<span data-ttu-id="b2ffa-175">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-175">Forbidden.</span></span>|
|`final`|<span data-ttu-id="b2ffa-176">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-176">Ignored.</span></span>|
|`id`|<span data-ttu-id="b2ffa-177">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-177">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="b2ffa-178">false (既定) のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-178">Must be false (default).</span></span>|
|`name`|<span data-ttu-id="b2ffa-179">サポートされています。データ コントラクト名にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="b2ffa-180">名前にピリオドが含まれている場合は、内部型への型のマッピングが実行されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="b2ffa-181">たとえば、 `A.B` という名前の複合型は、データ コントラクト名 `A`を持つ型の内部型であるデータ コントラクト型にマッピングされますが、このようなデータ コントラクト型が存在する場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="b2ffa-182">複数レベルの入れ子が可能です。たとえば、 `A.B.C` という内部型も可能ですが、これは、 `A` と `A.B` の両方が存在する場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|

### <a name="xscomplextype-contents"></a><span data-ttu-id="b2ffa-183">\<xs:complexType>: contents</span><span class="sxs-lookup"><span data-stu-id="b2ffa-183">\<xs:complexType>: contents</span></span>

|<span data-ttu-id="b2ffa-184">目次</span><span class="sxs-lookup"><span data-stu-id="b2ffa-184">Contents</span></span>|<span data-ttu-id="b2ffa-185">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-185">Schema</span></span>|
|--------------|------------|
|`simpleContent`|<span data-ttu-id="b2ffa-186">拡張は禁止です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="b2ffa-187">制限は、 `anySimpleType`からのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-187">Restriction is allowed only from `anySimpleType`.</span></span>|
|`complexContent`|<span data-ttu-id="b2ffa-188">サポートあり。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-188">Supported.</span></span> <span data-ttu-id="b2ffa-189">「継承」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-189">See "Inheritance".</span></span>|
|`group`|<span data-ttu-id="b2ffa-190">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-190">Forbidden.</span></span>|
|`all`|<span data-ttu-id="b2ffa-191">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-191">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="b2ffa-192">許可されていません</span><span class="sxs-lookup"><span data-stu-id="b2ffa-192">Forbidden</span></span>|
|`sequence`|<span data-ttu-id="b2ffa-193">サポートされます。データ コントラクトのデータ メンバーにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-193">Supported, maps to data members of a data contract.</span></span>|
|`attribute`|<span data-ttu-id="b2ffa-194">use="prohibited" の場合でも禁止です (ただし、例外が 1 つあります)。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="b2ffa-195">標準シリアル化スキーマ名前空間のオプションの属性のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="b2ffa-196">これらは、データ コントラクト プログラミング モデルのデータ メンバーにマッピングされません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="b2ffa-197">現在、これらの属性で意味のあるものは 1 つだけです。詳細については、ISerializable のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="b2ffa-198">他の属性はすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-198">All others are ignored.</span></span>|
|`attributeGroup`|<span data-ttu-id="b2ffa-199">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-199">Forbidden.</span></span> <span data-ttu-id="b2ffa-200">WCF v1 リリースでは、`DataContractSerializer` は `xs:complexType`内の `attributeGroup` の存在を無視します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-200">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|
|`anyAttribute`|<span data-ttu-id="b2ffa-201">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-201">Forbidden.</span></span>|
|<span data-ttu-id="b2ffa-202">(空)</span><span class="sxs-lookup"><span data-stu-id="b2ffa-202">(empty)</span></span>|<span data-ttu-id="b2ffa-203">データ メンバーを持たないデータ コントラクトにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-203">Maps to a data contract with no data members.</span></span>|

### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="b2ffa-204">\<xs: sequence > 複合型: attributes</span><span class="sxs-lookup"><span data-stu-id="b2ffa-204">\<xs:sequence> in a complex type: attributes</span></span>

|<span data-ttu-id="b2ffa-205">属性</span><span class="sxs-lookup"><span data-stu-id="b2ffa-205">Attribute</span></span>|<span data-ttu-id="b2ffa-206">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-206">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="b2ffa-207">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-207">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="b2ffa-208">1 (既定) のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-208">Must be 1 (default).</span></span>|
|`minOccurs`|<span data-ttu-id="b2ffa-209">1 (既定) のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-209">Must be 1 (default).</span></span>|

### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="b2ffa-210">\<xs: sequence > 複合型: コンテンツ</span><span class="sxs-lookup"><span data-stu-id="b2ffa-210">\<xs:sequence> in a complex type: contents</span></span>

|<span data-ttu-id="b2ffa-211">目次</span><span class="sxs-lookup"><span data-stu-id="b2ffa-211">Contents</span></span>|<span data-ttu-id="b2ffa-212">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-212">Schema</span></span>|
|--------------|------------|
|`element`|<span data-ttu-id="b2ffa-213">各インスタンスがデータ メンバーにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-213">Each instance maps to a data member.</span></span>|
|`group`|<span data-ttu-id="b2ffa-214">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-214">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="b2ffa-215">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-215">Forbidden.</span></span>|
|`sequence`|<span data-ttu-id="b2ffa-216">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-216">Forbidden.</span></span>|
|`any`|<span data-ttu-id="b2ffa-217">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-217">Forbidden.</span></span>|
|<span data-ttu-id="b2ffa-218">(空)</span><span class="sxs-lookup"><span data-stu-id="b2ffa-218">(empty)</span></span>|<span data-ttu-id="b2ffa-219">データ メンバーを持たないデータ コントラクトにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-219">Maps to a data contract with no data members.</span></span>|

## <a name="elements--xselement"></a><span data-ttu-id="b2ffa-220">要素– \<xs: element ></span><span class="sxs-lookup"><span data-stu-id="b2ffa-220">Elements – \<xs:element></span></span>

### <a name="general-information"></a><span data-ttu-id="b2ffa-221">一般情報</span><span class="sxs-lookup"><span data-stu-id="b2ffa-221">General Information</span></span>

<span data-ttu-id="b2ffa-222">`<xs:element>` は、次の構文で発生します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-222">`<xs:element>` can occur in the following contexts:</span></span>

- <span data-ttu-id="b2ffa-223">`<xs:sequence>`内で発生し、通常 (コレクション以外) のデータ コントラクトのデータ メンバーを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="b2ffa-224">この場合、 `maxOccurs` 属性は 1 にする必要があります</span><span class="sxs-lookup"><span data-stu-id="b2ffa-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="b2ffa-225">(値 0 は使用できません)。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-225">(A value of 0 is not allowed).</span></span>

- <span data-ttu-id="b2ffa-226">`<xs:sequence>`内で発生し、コレクション データ コントラクトのデータ メンバーを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="b2ffa-227">この場合、 `maxOccurs` 属性は 2 以上の値か、"unbounded" にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>

- <span data-ttu-id="b2ffa-228">`<xs:schema>` 内で GED (グローバル要素宣言) として発生します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="b2ffa-229">\<xs: sequence > (データメンバー) 内で maxOccurs = 1 を持つ xs: element > を \<します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>

|<span data-ttu-id="b2ffa-230">属性</span><span class="sxs-lookup"><span data-stu-id="b2ffa-230">Attribute</span></span>|<span data-ttu-id="b2ffa-231">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-231">Schema</span></span>|
|---------------|------------|
|`ref`|<span data-ttu-id="b2ffa-232">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-232">Forbidden.</span></span>|
|`name`|<span data-ttu-id="b2ffa-233">サポートされます。データ メンバー名にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-233">Supported, maps to the data member name.</span></span>|
|`type`|<span data-ttu-id="b2ffa-234">サポートされます。データ メンバー型にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="b2ffa-235">詳細については、「型/プリミティブのマッピング」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="b2ffa-236">指定しない場合 (および要素に匿名型が含まれていない場合) は、 `xs:anyType` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|
|`block`|<span data-ttu-id="b2ffa-237">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-237">Ignored.</span></span>|
|`default`|<span data-ttu-id="b2ffa-238">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-238">Forbidden.</span></span>|
|`fixed`|<span data-ttu-id="b2ffa-239">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-239">Forbidden.</span></span>|
|`form`|<span data-ttu-id="b2ffa-240">修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-240">Must be qualified.</span></span> <span data-ttu-id="b2ffa-241">この属性は、 `elementFormDefault` の `xs:schema`を通じて設定できます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|
|`id`|<span data-ttu-id="b2ffa-242">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-242">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="b2ffa-243">1</span><span class="sxs-lookup"><span data-stu-id="b2ffa-243">1</span></span>|
|`minOccurs`|<span data-ttu-id="b2ffa-244">データ メンバーの <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> プロパティにマッピングされます (`IsRequired` が 1 の場合、 `minOccurs` は true です)。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|
|`nillable`|<span data-ttu-id="b2ffa-245">型のマッピングに影響します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-245">Affects type mapping.</span></span> <span data-ttu-id="b2ffa-246">「型/プリミティブのマッピング」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-246">See Type/primitive mapping.</span></span>|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="b2ffa-247">\<xs: sequence > (Collections) 内の maxOccurs > 1 で、xs: element > を \<します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>

- <span data-ttu-id="b2ffa-248"><xref:System.Runtime.Serialization.CollectionDataContractAttribute>にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>

- <span data-ttu-id="b2ffa-249">コレクションの型では、xs:sequence 内で xs:element を 1 つしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>

 <span data-ttu-id="b2ffa-250">コレクションは次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-250">Collections can be of the following types:</span></span>

- <span data-ttu-id="b2ffa-251">標準コレクション (配列など)。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-251">Regular collections (for example, arrays).</span></span>

- <span data-ttu-id="b2ffa-252">ディクショナリ コレクション (1 つの値を別の値にマッピングする、 <xref:System.Collections.Hashtable>など)。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>

- <span data-ttu-id="b2ffa-253">ディクショナリとキー/値ペアの配列の種類との唯一の相違は、生成されるプログラミング モデルにあります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="b2ffa-254">特定の種類がディクショナリ コレクションであることを示すには、スキーマ注釈機構を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>

<span data-ttu-id="b2ffa-255">`ref`、 `block`、 `default`、 `fixed`、 `form`、および `id` の各属性に対するルールは、コレクション以外の場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="b2ffa-256">その他に、次の表に示す属性があります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-256">Other attributes include those in the following table.</span></span>

|<span data-ttu-id="b2ffa-257">属性</span><span class="sxs-lookup"><span data-stu-id="b2ffa-257">Attribute</span></span>|<span data-ttu-id="b2ffa-258">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-258">Schema</span></span>|
|---------------|------------|
|`name`|<span data-ttu-id="b2ffa-259">サポートされます。 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> 属性の `CollectionDataContractAttribute` プロパティにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|
|`type`|<span data-ttu-id="b2ffa-260">サポートされます。コレクションに格納されている型にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-260">Supported, maps to the type stored in the collection.</span></span>|
|`maxOccurs`|<span data-ttu-id="b2ffa-261">2 以上または "unbounded"。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="b2ffa-262">DC スキーマでは、"unbounded" を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-262">The DC schema should use "unbounded".</span></span>|
|`minOccurs`|<span data-ttu-id="b2ffa-263">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-263">Ignored.</span></span>|
|`nillable`|<span data-ttu-id="b2ffa-264">型のマッピングに影響します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-264">Affects type mapping.</span></span> <span data-ttu-id="b2ffa-265">この属性は、ディクショナリ コレクションでは無視されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-265">This attribute is ignored for dictionary collections.</span></span>|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="b2ffa-266">xs: schema > グローバル要素宣言の \<内で xs: element > を \<</span><span class="sxs-lookup"><span data-stu-id="b2ffa-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>

- <span data-ttu-id="b2ffa-267">スキーマ内の型と同じ名前および名前空間を持つか、それ自体の内部で匿名型を定義するグローバル要素宣言 (GED) は、型に関連付けられていると言います。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>

- <span data-ttu-id="b2ffa-268">スキーマのエクスポート : 単純型と複合型の両方で、生成された型ごとに関連 GED が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>

- <span data-ttu-id="b2ffa-269">逆シリアル化/シリアル化 : 関連 GED が、該当する型のルート要素として使用されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>

- <span data-ttu-id="b2ffa-270">スキーマのインポート : 次のルールに従う場合、関連 GED は不要となり無視されます (ただし、それが型を定義する場合を除きます)。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>

|<span data-ttu-id="b2ffa-271">属性</span><span class="sxs-lookup"><span data-stu-id="b2ffa-271">Attribute</span></span>|<span data-ttu-id="b2ffa-272">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-272">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="b2ffa-273">関連 GED では false のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-273">Must be false for associated GEDs.</span></span>|
|`block`|<span data-ttu-id="b2ffa-274">関連 GED では禁止です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-274">Forbidden in associated GEDs.</span></span>|
|`default`|<span data-ttu-id="b2ffa-275">関連 GED では禁止です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-275">Forbidden in associated GEDs.</span></span>|
|`final`|<span data-ttu-id="b2ffa-276">関連 GED では false のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-276">Must be false for associated GEDs.</span></span>|
|`fixed`|<span data-ttu-id="b2ffa-277">関連 GED では禁止です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-277">Forbidden in associated GEDs.</span></span>|
|`id`|<span data-ttu-id="b2ffa-278">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-278">Ignored.</span></span>|
|`name`|<span data-ttu-id="b2ffa-279">サポートあり。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-279">Supported.</span></span> <span data-ttu-id="b2ffa-280">関連 GED の定義を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-280">See the definition of associated GEDs.</span></span>|
|`nillable`|<span data-ttu-id="b2ffa-281">関連 GED では true のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-281">Must be true for associated GEDs.</span></span>|
|`substitutionGroup`|<span data-ttu-id="b2ffa-282">関連 GED では禁止です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-282">Forbidden in associated GEDs.</span></span>|
|`type`|<span data-ttu-id="b2ffa-283">サポートされます。関連 GED に関連付けられた型に一致させる必要があります (ただし、要素に匿名型が含まれている場合を除きます)。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|

### <a name="xselement-contents"></a><span data-ttu-id="b2ffa-284">\<xs: element >: contents</span><span class="sxs-lookup"><span data-stu-id="b2ffa-284">\<xs:element>: contents</span></span>

|<span data-ttu-id="b2ffa-285">目次</span><span class="sxs-lookup"><span data-stu-id="b2ffa-285">Contents</span></span>|<span data-ttu-id="b2ffa-286">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-286">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="b2ffa-287">サポートされています。\*</span><span class="sxs-lookup"><span data-stu-id="b2ffa-287">Supported.\*</span></span>|
|`complexType`|<span data-ttu-id="b2ffa-288">サポートされています。\*</span><span class="sxs-lookup"><span data-stu-id="b2ffa-288">Supported.\*</span></span>|
|`unique`|<span data-ttu-id="b2ffa-289">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-289">Ignored.</span></span>|
|`key`|<span data-ttu-id="b2ffa-290">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-290">Ignored.</span></span>|
|`keyref`|<span data-ttu-id="b2ffa-291">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-291">Ignored.</span></span>|
|<span data-ttu-id="b2ffa-292">(空白)</span><span class="sxs-lookup"><span data-stu-id="b2ffa-292">(blank)</span></span>|<span data-ttu-id="b2ffa-293">サポートあり。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-293">Supported.</span></span>|

<span data-ttu-id="b2ffa-294">匿名型に対して `simpleType` と `complexType,` のマッピングを使用する場合は、匿名型のデータコントラクトが存在しない点を除き、匿名型の場合と同じように \* します。これにより、名前付きデータコントラクトが作成され、要素名から派生した名前が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="b2ffa-295">匿名型のルールは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-295">The rules for anonymous types are in the following list:</span></span>

- <span data-ttu-id="b2ffa-296">WCF 実装の詳細: `xs:element` 名にピリオドが含まれていない場合、匿名型は外部データコントラクト型の内部型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-296">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="b2ffa-297">名前にピリオドが含まれている場合、結果のデータ コントラクト型は、内部型ではなく、独立した型になります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>

- <span data-ttu-id="b2ffa-298">内部型の生成されたデータ コントラクト名は、外部型のデータ コントラクト名の後にピリオド、要素の名前、および文字列 "Type" が付いたものになります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>

- <span data-ttu-id="b2ffa-299">そのような名前を持つデータ コントラクトが既に存在する場合は、"1"、"2"、"3" などの番号が付加されて一意の名前になります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>

## <a name="simple-types---xssimpletype"></a><span data-ttu-id="b2ffa-300">Simple Types - \<xs:simpleType></span><span class="sxs-lookup"><span data-stu-id="b2ffa-300">Simple Types - \<xs:simpleType></span></span>

### <a name="xssimpletype-attributes"></a><span data-ttu-id="b2ffa-301">\<xs: simpleType >: attributes</span><span class="sxs-lookup"><span data-stu-id="b2ffa-301">\<xs:simpleType>: attributes</span></span>

|<span data-ttu-id="b2ffa-302">属性</span><span class="sxs-lookup"><span data-stu-id="b2ffa-302">Attribute</span></span>|<span data-ttu-id="b2ffa-303">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-303">Schema</span></span>|
|---------------|------------|
|`final`|<span data-ttu-id="b2ffa-304">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-304">Ignored.</span></span>|
|`id`|<span data-ttu-id="b2ffa-305">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-305">Ignored.</span></span>|
|`name`|<span data-ttu-id="b2ffa-306">サポートされます。データ コントラクト名にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-306">Supported, maps to the data contract name.</span></span>|

### <a name="xssimpletype-contents"></a><span data-ttu-id="b2ffa-307">\<xs: simpleType >: contents</span><span class="sxs-lookup"><span data-stu-id="b2ffa-307">\<xs:simpleType>: contents</span></span>

|<span data-ttu-id="b2ffa-308">目次</span><span class="sxs-lookup"><span data-stu-id="b2ffa-308">Contents</span></span>|<span data-ttu-id="b2ffa-309">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-309">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="b2ffa-310">サポートあり。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-310">Supported.</span></span> <span data-ttu-id="b2ffa-311">列挙データ コントラクトにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="b2ffa-312">列挙パターンに一致しない場合、この属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="b2ffa-313">`xs:simpleType` の制限のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-313">See the `xs:simpleType` restrictions section.</span></span>|
|`list`|<span data-ttu-id="b2ffa-314">サポートあり。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-314">Supported.</span></span> <span data-ttu-id="b2ffa-315">フラグ列挙データ コントラクトにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="b2ffa-316">`xs:simpleType` の一覧のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-316">See the `xs:simpleType` lists section.</span></span>|
|`union`|<span data-ttu-id="b2ffa-317">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-317">Forbidden.</span></span>|

### <a name="xsrestriction"></a><span data-ttu-id="b2ffa-318">\<xs:restriction></span><span class="sxs-lookup"><span data-stu-id="b2ffa-318">\<xs:restriction></span></span>

- <span data-ttu-id="b2ffa-319">複合型制限は、base="`xs:anyType`" の場合のみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>

- <span data-ttu-id="b2ffa-320">`xs:string` 以外の制限ファセットを持たない `xs:enumeration` の単純型制限は、列挙データ コントラクトにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>

- <span data-ttu-id="b2ffa-321">その他すべての単純型制限は、それぞれが制限する型にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="b2ffa-322">たとえば、 `xs:int` の制限は、 `xs:int` 自体と同様に整数にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="b2ffa-323">プリミティブ型のマッピングの詳細については、「型/プリミティブのマッピング」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-323">For more information about primitive type mapping, see Type/primitive mapping.</span></span>

### <a name="xsrestriction-attributes"></a><span data-ttu-id="b2ffa-324">\<xs: restriction >: attributes</span><span class="sxs-lookup"><span data-stu-id="b2ffa-324">\<xs:restriction>: attributes</span></span>

|<span data-ttu-id="b2ffa-325">属性</span><span class="sxs-lookup"><span data-stu-id="b2ffa-325">Attribute</span></span>|<span data-ttu-id="b2ffa-326">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-326">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="b2ffa-327">サポートされている単純型または `xs:anyType`のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-327">Must be a supported simple type or `xs:anyType`.</span></span>|
|`id`|<span data-ttu-id="b2ffa-328">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-328">Ignored.</span></span>|

### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="b2ffa-329">\<xs: restriction > (その他すべての場合): 内容</span><span class="sxs-lookup"><span data-stu-id="b2ffa-329">\<xs:restriction> for all other cases: contents</span></span>

|<span data-ttu-id="b2ffa-330">目次</span><span class="sxs-lookup"><span data-stu-id="b2ffa-330">Contents</span></span>|<span data-ttu-id="b2ffa-331">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-331">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="b2ffa-332">存在する場合、サポートされているプリミティブ型から派生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-332">If present, must be derived from a supported primitive type.</span></span>|
|`minExclusive`|<span data-ttu-id="b2ffa-333">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-333">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="b2ffa-334">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-334">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="b2ffa-335">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-335">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="b2ffa-336">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-336">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="b2ffa-337">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-337">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="b2ffa-338">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-338">Ignored.</span></span>|
|`length`|<span data-ttu-id="b2ffa-339">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-339">Ignored.</span></span>|
|`minLength`|<span data-ttu-id="b2ffa-340">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-340">Ignored.</span></span>|
|`maxLength`|<span data-ttu-id="b2ffa-341">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-341">Ignored.</span></span>|
|`enumeration`|<span data-ttu-id="b2ffa-342">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-342">Ignored.</span></span>|
|`whiteSpace`|<span data-ttu-id="b2ffa-343">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-343">Ignored.</span></span>|
|`pattern`|<span data-ttu-id="b2ffa-344">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-344">Ignored.</span></span>|
|<span data-ttu-id="b2ffa-345">(空白)</span><span class="sxs-lookup"><span data-stu-id="b2ffa-345">(blank)</span></span>|<span data-ttu-id="b2ffa-346">サポートあり。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-346">Supported.</span></span>|

## <a name="enumeration"></a><span data-ttu-id="b2ffa-347">列挙体</span><span class="sxs-lookup"><span data-stu-id="b2ffa-347">Enumeration</span></span>

### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="b2ffa-348">列挙型の xs: restriction > の \<: 属性</span><span class="sxs-lookup"><span data-stu-id="b2ffa-348">\<xs:restriction> for enumerations: attributes</span></span>

|<span data-ttu-id="b2ffa-349">属性</span><span class="sxs-lookup"><span data-stu-id="b2ffa-349">Attribute</span></span>|<span data-ttu-id="b2ffa-350">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-350">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="b2ffa-351">存在する場合、 `xs:string`のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-351">If present, must be `xs:string`.</span></span>|
|`id`|<span data-ttu-id="b2ffa-352">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-352">Ignored.</span></span>|

### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="b2ffa-353">列挙型の \<xs: restriction >: 内容</span><span class="sxs-lookup"><span data-stu-id="b2ffa-353">\<xs:restriction> for enumerations: contents</span></span>

|<span data-ttu-id="b2ffa-354">目次</span><span class="sxs-lookup"><span data-stu-id="b2ffa-354">Contents</span></span>|<span data-ttu-id="b2ffa-355">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-355">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="b2ffa-356">存在する場合、データ コントラクトによってサポートされている列挙体制限 (このセクション) のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|
|`minExclusive`|<span data-ttu-id="b2ffa-357">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-357">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="b2ffa-358">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-358">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="b2ffa-359">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-359">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="b2ffa-360">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-360">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="b2ffa-361">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-361">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="b2ffa-362">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-362">Ignored.</span></span>|
|`length`|<span data-ttu-id="b2ffa-363">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-363">Forbidden.</span></span>|
|`minLength`|<span data-ttu-id="b2ffa-364">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-364">Forbidden.</span></span>|
|`maxLength`|<span data-ttu-id="b2ffa-365">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-365">Forbidden.</span></span>|
|`enumeration`|<span data-ttu-id="b2ffa-366">サポートあり。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-366">Supported.</span></span> <span data-ttu-id="b2ffa-367">列挙体 "id" は無視され、"値" が列挙データ コントラクトの値の名前にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|
|`whiteSpace`|<span data-ttu-id="b2ffa-368">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-368">Forbidden.</span></span>|
|`pattern`|<span data-ttu-id="b2ffa-369">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-369">Forbidden.</span></span>|
|<span data-ttu-id="b2ffa-370">(空)</span><span class="sxs-lookup"><span data-stu-id="b2ffa-370">(empty)</span></span>|<span data-ttu-id="b2ffa-371">サポートされます。空の列挙型にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-371">Supported, maps to empty enumeration type.</span></span>|

 <span data-ttu-id="b2ffa-372">次のコードは、C# の列挙クラスを示しています。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-372">The following code shows a C# enumeration class.</span></span>

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

<span data-ttu-id="b2ffa-373">このクラスは `DataContractSerializer`により、次のスキーマにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-373">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="b2ffa-374">列挙値が 1 から始まる場合、 `xs:annotation` ブロックは生成されません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-374">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>

```xml
<xs:simpleType name="MyEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="first">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          3
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
    <xs:enumeration value="second">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          4
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
  </xs:restriction>
</xs:simpleType>
```

### <a name="xslist"></a><span data-ttu-id="b2ffa-375">\<xs:list></span><span class="sxs-lookup"><span data-stu-id="b2ffa-375">\<xs:list></span></span>

<span data-ttu-id="b2ffa-376">`DataContractSerializer` は、 `System.FlagsAttribute` によってマークされた列挙型を、 `xs:list` から派生した `xs:string`にマッピングします。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-376">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="b2ffa-377">これ以外の `xs:list` のバリエーションはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-377">No other `xs:list` variations are supported.</span></span>

### <a name="xslist-attributes"></a><span data-ttu-id="b2ffa-378">\<xs: list >: attributes</span><span class="sxs-lookup"><span data-stu-id="b2ffa-378">\<xs:list>: attributes</span></span>

|<span data-ttu-id="b2ffa-379">属性</span><span class="sxs-lookup"><span data-stu-id="b2ffa-379">Attribute</span></span>|<span data-ttu-id="b2ffa-380">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-380">Schema</span></span>|
|---------------|------------|
|`itemType`|<span data-ttu-id="b2ffa-381">禁止。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-381">Forbidden.</span></span>|
|`id`|<span data-ttu-id="b2ffa-382">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-382">Ignored.</span></span>|

### <a name="xslist-contents"></a><span data-ttu-id="b2ffa-383">\<xs: list >: contents</span><span class="sxs-lookup"><span data-stu-id="b2ffa-383">\<xs:list>: contents</span></span>

|<span data-ttu-id="b2ffa-384">目次</span><span class="sxs-lookup"><span data-stu-id="b2ffa-384">Contents</span></span>|<span data-ttu-id="b2ffa-385">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-385">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="b2ffa-386">`xs:string` ファセットを使用する `xs:enumeration` からの制限のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-386">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|

<span data-ttu-id="b2ffa-387">列挙値が 2 の累乗の数列 (フラグの既定) に従わない場合、値は `xs:annotation/xs:appInfo/ser:EnumerationValue` 要素に格納されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-387">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>

<span data-ttu-id="b2ffa-388">たとえば、次のコードは列挙型をフラグとして処理します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-388">For example, the following code flags an enumeration type.</span></span>

```csharp
[Flags]
public enum AuthFlags
{
  AuthAnonymous = 1,
  AuthBasic = 2,
  AuthNTLM = 4,
  AuthMD5 = 16,
  AuthWindowsLiveID = 64,
}
```

<span data-ttu-id="b2ffa-389">この列挙型は次のスキーマにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-389">This type maps to the following schema.</span></span>

```xml
<xs:simpleType name="AuthFlags">
    <xs:list>
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="AuthAnonymous" />
          <xs:enumeration value="AuthBasic" />
          <xs:enumeration value="AuthNTLM" />
          <xs:enumeration value="AuthMD5">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
          <xs:enumeration value="AuthWindowsLiveID">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
        </xs:restriction>
      </xs:simpleType>
    </xs:list>
  </xs:simpleType>
```

## <a name="inheritance"></a><span data-ttu-id="b2ffa-390">継承</span><span class="sxs-lookup"><span data-stu-id="b2ffa-390">Inheritance</span></span>

### <a name="general-rules"></a><span data-ttu-id="b2ffa-391">一般ルール</span><span class="sxs-lookup"><span data-stu-id="b2ffa-391">General rules</span></span>

<span data-ttu-id="b2ffa-392">データ コントラクトは、別のデータ コントラクトを継承できます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-392">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="b2ffa-393">このようなデータ コントラクトは base にマッピングされ、 `<xs:extension>` XML スキーマ コントラクトを使用する拡張型によって派生されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-393">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>

<span data-ttu-id="b2ffa-394">データ コントラクトは、コレクション データ コントラクトを継承できません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-394">A data contract cannot inherit from a collection data contract.</span></span>

<span data-ttu-id="b2ffa-395">データ コントラクトの例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-395">For example, the following code is a data contract.</span></span>

```csharp
[DataContract]
public class Person
{
  [DataMember]
  public string Name;
}
[DataContract]
public class Employee : Person
{
  [DataMember]
  public int ID;
}
```

<span data-ttu-id="b2ffa-396">このデータ コントラクトは次の XML スキーマ型の宣言にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-396">This data contract maps to the following XML Schema type declaration.</span></span>

```xml
<xs:complexType name="Employee">
 <xs:complexContent mixed="false">
  <xs:extension base="tns:Person">
   <xs:sequence>
    <xs:element minOccurs="0" name="ID" type="xs:int"/>
   </xs:sequence>
  </xs:extension>
 </xs:complexContent>
</xs:complexType>
<xs:complexType name="Person">
 <xs:sequence>
  <xs:element minOccurs="0" name="Name"
    nillable="true" type="xs:string"/>
 </xs:sequence>
</xs:complexType>
```

### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="b2ffa-397">\<xs: complexContent >: attributes</span><span class="sxs-lookup"><span data-stu-id="b2ffa-397">\<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="b2ffa-398">属性</span><span class="sxs-lookup"><span data-stu-id="b2ffa-398">Attribute</span></span>|<span data-ttu-id="b2ffa-399">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-399">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="b2ffa-400">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-400">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="b2ffa-401">false のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-401">Must be false.</span></span>|

### <a name="xscomplexcontent-contents"></a><span data-ttu-id="b2ffa-402">\<xs: complexContent >: コンテンツ</span><span class="sxs-lookup"><span data-stu-id="b2ffa-402">\<xs:complexContent>: contents</span></span>

|<span data-ttu-id="b2ffa-403">目次</span><span class="sxs-lookup"><span data-stu-id="b2ffa-403">Contents</span></span>|<span data-ttu-id="b2ffa-404">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-404">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="b2ffa-405">禁止ですが、base="`xs:anyType`" の場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-405">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="b2ffa-406">後者は、 `xs:restriction` のコンテナーの下に `xs:complexContent`のコンテンツを直接配置するのと同じです。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-406">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|
|`extension`|<span data-ttu-id="b2ffa-407">サポートあり。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-407">Supported.</span></span> <span data-ttu-id="b2ffa-408">データ コントラクトの継承にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-408">Maps to data contract inheritance.</span></span>|

### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="b2ffa-409">xs: complexContent >: 属性での xs: extension > \<の \<</span><span class="sxs-lookup"><span data-stu-id="b2ffa-409">\<xs:extension> in \<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="b2ffa-410">属性</span><span class="sxs-lookup"><span data-stu-id="b2ffa-410">Attribute</span></span>|<span data-ttu-id="b2ffa-411">Schema</span><span class="sxs-lookup"><span data-stu-id="b2ffa-411">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="b2ffa-412">無視。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-412">Ignored.</span></span>|
|`base`|<span data-ttu-id="b2ffa-413">サポートあり。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-413">Supported.</span></span> <span data-ttu-id="b2ffa-414">この型が継承する基本データ コントラクト型にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-414">Maps to the base data contract type that this type inherits from.</span></span>|

### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="b2ffa-415">xs: complexContent >: contents \<の \<xs: extension ></span><span class="sxs-lookup"><span data-stu-id="b2ffa-415">\<xs:extension> in \<xs:complexContent>: contents</span></span>

<span data-ttu-id="b2ffa-416">`<xs:complexType>` コンテンツと同じルールです。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-416">The rules are the same as for `<xs:complexType>` contents.</span></span>

<span data-ttu-id="b2ffa-417">`<xs:sequence>` を指定した場合は、そのメンバー要素が、派生データ コントラクトに存在する追加のデータ メンバーにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-417">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>

<span data-ttu-id="b2ffa-418">基本型の要素と同じ名前を持つ要素が派生型に含まれている場合は、重複する要素宣言が、一意のものとして生成される名前を持つデータ メンバーにマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-418">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="b2ffa-419">データ メンバーの名前には、一意の名前が見つかるまで正の整数が付加されます ("member1"、"member2" など)。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-419">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="b2ffa-420">これに対して、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-420">Conversely:</span></span>

- <span data-ttu-id="b2ffa-421">基本データ コントラクトのデータ メンバーと同じ名前および型を持つデータ メンバーが派生データ コントラクトに存在する場合、 `DataContractSerializer` は、これに対応する要素を派生型で生成します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-421">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>

- <span data-ttu-id="b2ffa-422">基本データ コントラクトのデータ メンバーと名前は同じでも型が異なるデータ メンバーが派生データ コントラクトに存在する場合、 `DataContractSerializer` は、 `xs:anyType` 型の要素を含むスキーマを、基本型と派生型の両方の宣言にインポートします。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-422">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="b2ffa-423">元の型名は、 `xs:annotations/xs:appInfo/ser:ActualType/@Name`に保持されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-423">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>

<span data-ttu-id="b2ffa-424">それぞれのデータ メンバーの順序によっては、これら両方のバリエーションにより、あいまいなコンテンツ モデルを含むスキーマが生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-424">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>

## <a name="typeprimitive-mapping"></a><span data-ttu-id="b2ffa-425">型/プリミティブのマッピング</span><span class="sxs-lookup"><span data-stu-id="b2ffa-425">Type/primitive mapping</span></span>

<span data-ttu-id="b2ffa-426">`DataContractSerializer` は、XML スキーマのプリミティブ型で次のマッピングを使用します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-426">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>

|<span data-ttu-id="b2ffa-427">XSD 型</span><span class="sxs-lookup"><span data-stu-id="b2ffa-427">XSD type</span></span>|<span data-ttu-id="b2ffa-428">.NET 型</span><span class="sxs-lookup"><span data-stu-id="b2ffa-428">.NET type</span></span>|
|--------------|---------------|
|`anyType`|<span data-ttu-id="b2ffa-429"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-429"><xref:System.Object>.</span></span>|
|`anySimpleType`|<span data-ttu-id="b2ffa-430"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-430"><xref:System.String>.</span></span>|
|`duration`|<span data-ttu-id="b2ffa-431"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-431"><xref:System.TimeSpan>.</span></span>|
|`dateTime`|<span data-ttu-id="b2ffa-432"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-432"><xref:System.DateTime>.</span></span>|
|`dateTimeOffset`|<span data-ttu-id="b2ffa-433">オフセットの<xref:System.DateTime> および <xref:System.TimeSpan> 。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-433"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="b2ffa-434">後の「DateTimeOffset のシリアル化」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-434">See DateTimeOffset Serialization below.</span></span>|
|`time`|<span data-ttu-id="b2ffa-435"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-435"><xref:System.String>.</span></span>|
|`date`|<span data-ttu-id="b2ffa-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-436"><xref:System.String>.</span></span>|
|`gYearMonth`|<span data-ttu-id="b2ffa-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-437"><xref:System.String>.</span></span>|
|`gYear`|<span data-ttu-id="b2ffa-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-438"><xref:System.String>.</span></span>|
|`gMonthDay`|<span data-ttu-id="b2ffa-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-439"><xref:System.String>.</span></span>|
|`gDay`|<span data-ttu-id="b2ffa-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-440"><xref:System.String>.</span></span>|
|`gMonth`|<span data-ttu-id="b2ffa-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-441"><xref:System.String>.</span></span>|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<span data-ttu-id="b2ffa-442"><xref:System.Byte> 配列</span><span class="sxs-lookup"><span data-stu-id="b2ffa-442"><xref:System.Byte> array.</span></span>|
|`hexBinary`|<span data-ttu-id="b2ffa-443"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-443"><xref:System.String>.</span></span>|
|`float`|<span data-ttu-id="b2ffa-444"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-444"><xref:System.Single>.</span></span>|
|`double`|<span data-ttu-id="b2ffa-445"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-445"><xref:System.Double>.</span></span>|
|`anyURI`|<span data-ttu-id="b2ffa-446"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-446"><xref:System.Uri>.</span></span>|
|`QName`|<span data-ttu-id="b2ffa-447"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-447"><xref:System.Xml.XmlQualifiedName>.</span></span>|
|`string`|<span data-ttu-id="b2ffa-448"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-448"><xref:System.String>.</span></span>|
|`normalizedString`|<span data-ttu-id="b2ffa-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-449"><xref:System.String>.</span></span>|
|`token`|<span data-ttu-id="b2ffa-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-450"><xref:System.String>.</span></span>|
|`language`|<span data-ttu-id="b2ffa-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-451"><xref:System.String>.</span></span>|
|`Name`|<span data-ttu-id="b2ffa-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-452"><xref:System.String>.</span></span>|
|`NCName`|<span data-ttu-id="b2ffa-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-453"><xref:System.String>.</span></span>|
|`ID`|<span data-ttu-id="b2ffa-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-454"><xref:System.String>.</span></span>|
|`IDREF`|<span data-ttu-id="b2ffa-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-455"><xref:System.String>.</span></span>|
|`IDREFS`|<span data-ttu-id="b2ffa-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-456"><xref:System.String>.</span></span>|
|`ENTITY`|<span data-ttu-id="b2ffa-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-457"><xref:System.String>.</span></span>|
|`ENTITIES`|<span data-ttu-id="b2ffa-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-458"><xref:System.String>.</span></span>|
|`NMTOKEN`|<span data-ttu-id="b2ffa-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-459"><xref:System.String>.</span></span>|
|`NMTOKENS`|<span data-ttu-id="b2ffa-460"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-460"><xref:System.String>.</span></span>|
|`decimal`|<span data-ttu-id="b2ffa-461"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-461"><xref:System.Decimal>.</span></span>|
|`integer`|<span data-ttu-id="b2ffa-462"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-462"><xref:System.Int64>.</span></span>|
|`nonPositiveInteger`|<span data-ttu-id="b2ffa-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-463"><xref:System.Int64>.</span></span>|
|`negativeInteger`|<span data-ttu-id="b2ffa-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-464"><xref:System.Int64>.</span></span>|
|`long`|<span data-ttu-id="b2ffa-465"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-465"><xref:System.Int64>.</span></span>|
|`int`|<span data-ttu-id="b2ffa-466"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-466"><xref:System.Int32>.</span></span>|
|`short`|<span data-ttu-id="b2ffa-467"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-467"><xref:System.Int16>.</span></span>|
|`Byte`|<span data-ttu-id="b2ffa-468"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-468"><xref:System.SByte>.</span></span>|
|`nonNegativeInteger`|<span data-ttu-id="b2ffa-469"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-469"><xref:System.Int64>.</span></span>|
|`unsignedLong`|<span data-ttu-id="b2ffa-470"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-470"><xref:System.UInt64>.</span></span>|
|`unsignedInt`|<span data-ttu-id="b2ffa-471"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-471"><xref:System.UInt32>.</span></span>|
|`unsignedShort`|<span data-ttu-id="b2ffa-472"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-472"><xref:System.UInt16>.</span></span>|
|`unsignedByte`|<span data-ttu-id="b2ffa-473"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-473"><xref:System.Byte>.</span></span>|
|`positiveInteger`|<span data-ttu-id="b2ffa-474"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b2ffa-474"><xref:System.Int64>.</span></span>|

## <a name="iserializable-types-mapping"></a><span data-ttu-id="b2ffa-475">ISerializable 型のマッピング</span><span class="sxs-lookup"><span data-stu-id="b2ffa-475">ISerializable types mapping</span></span>

<span data-ttu-id="b2ffa-476">.NET Framework バージョン1.0 では、永続化またはデータ転送のためにオブジェクトをシリアル化するための一般的なメカニズムとして <xref:System.Runtime.Serialization.ISerializable> が導入されました。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-476">In .NET Framework version 1.0, <xref:System.Runtime.Serialization.ISerializable> was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="b2ffa-477">`ISerializable` を実装し、アプリケーション間で渡される .NET Framework 型は多数あります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-477">There are many .NET Framework types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="b2ffa-478"><xref:System.Runtime.Serialization.DataContractSerializer> は、当然ながら `ISerializable` クラスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-478"><xref:System.Runtime.Serialization.DataContractSerializer> naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="b2ffa-479">`DataContractSerializer` は、型の QName (修飾名) のみが異なり、事実上プロパティ コレクションである `ISerializable` 実装スキーマ型をマッピングします。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-479">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="b2ffa-480">たとえば、`DataContractSerializer`マップ<xref:System.Exception>で次の XSD 型を `http://schemas.datacontract.org/2004/07/System` 名前空間。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-480">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

<span data-ttu-id="b2ffa-481">データ コントラクトのシリアル化スキーマで宣言されたオプションの属性 `ser:FactoryType` は、型を逆シリアル化できるファクトリ クラスを参照します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-481">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="b2ffa-482">ファクトリ クラスは、使用する `DataContractSerializer` インスタンスの既知の型コレクションの一部である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-482">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="b2ffa-483">既知の型の詳細については、「[データコントラクトの既知の型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-483">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>

## <a name="datacontract-serialization-schema"></a><span data-ttu-id="b2ffa-484">DataContract のシリアル化スキーマ</span><span class="sxs-lookup"><span data-stu-id="b2ffa-484">DataContract Serialization Schema</span></span>

<span data-ttu-id="b2ffa-485">`DataContractSerializer` によってエクスポートされたいくつかのスキーマでは、次の特別なデータ コントラクト シリアル化名前空間の型、要素、および属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-485">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>

`http://schemas.microsoft.com/2003/10/Serialization`

<span data-ttu-id="b2ffa-486">データ コントラクト シリアル化スキーマの完全な宣言を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-486">The following is a complete Data Contract Serialization schema declaration.</span></span>

```xml
<xs:schema attributeFormDefault="qualified"
   elementFormDefault="qualified"
   targetNamespace =
    "http://schemas.microsoft.com/2003/10/Serialization/"
   xmlns:xs="http://www.w3.org/2001/XMLSchema"
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">

 <!-- Top-level elements for primitive types. -->
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>
 <xs:element name="base64Binary"
       nillable="true" type="xs:base64Binary"/>
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>
 <xs:element name="byte" nillable="true" type="xs:byte"/>
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>
 <xs:element name="double" nillable="true" type="xs:double"/>
 <xs:element name="float" nillable="true" type="xs:float"/>
 <xs:element name="int" nillable="true" type="xs:int"/>
 <xs:element name="long" nillable="true" type="xs:long"/>
 <xs:element name="QName" nillable="true" type="xs:QName"/>
 <xs:element name="short" nillable="true" type="xs:short"/>
 <xs:element name="string" nillable="true" type="xs:string"/>
 <xs:element name="unsignedByte"
       nillable="true" type="xs:unsignedByte"/>
 <xs:element name="unsignedInt"
       nillable="true" type="xs:unsignedInt"/>
 <xs:element name="unsignedLong"
       nillable="true" type="xs:unsignedLong"/>
 <xs:element name="unsignedShort"
       nillable="true" type="xs:unsignedShort"/>

 <!-- Primitive types introduced for certain .NET simple types. -->
 <xs:element name="char" nillable="true" type="tns:char"/>
 <xs:simpleType name="char">
  <xs:restriction base="xs:int"/>
 </xs:simpleType>

 <!-- xs:duration is restricted to an ordered value space,
    to map to System.TimeSpan -->
 <xs:element name="duration" nillable="true" type="tns:duration"/>
 <xs:simpleType name="duration">
  <xs:restriction base="xs:duration">
   <xs:pattern
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>
  </xs:restriction>
 </xs:simpleType>

 <xs:element name="guid" nillable="true" type="tns:guid"/>
 <xs:simpleType name="guid">
  <xs:restriction base="xs:string">
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>
  </xs:restriction>
 </xs:simpleType>

 <!-- This is used for schemas exported from ISerializable type. -->
 <xs:attribute name="FactoryType" type="xs:QName"/>
</xs:schema>
```

<span data-ttu-id="b2ffa-487">ここで次の点に注意します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-487">The following should be noted:</span></span>

- <span data-ttu-id="b2ffa-488">`ser:char` を導入して、型 <xref:System.Char>の Unicode 文字を表現します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-488">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>

- <span data-ttu-id="b2ffa-489">`valuespace` の `xs:duration` を順序付きセットに縮小し、 <xref:System.TimeSpan>にマッピングできるようにします。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-489">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>

- <span data-ttu-id="b2ffa-490">`FactoryType` から派生した型からエクスポートされたスキーマで <xref:System.Runtime.Serialization.ISerializable>を使用します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-490">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>

## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="b2ffa-491">非 DataContract スキーマのインポート</span><span class="sxs-lookup"><span data-stu-id="b2ffa-491">Importing non-DataContract schemas</span></span>

<span data-ttu-id="b2ffa-492">`DataContractSerializer` には、 `ImportXmlTypes` XSD プロファイルに準拠しないスキーマのインポートを可能にする `DataContractSerializer` オプションがあります (「 <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> プロパティ」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-492">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="b2ffa-493">このオプションを `true` に設定すると、非準拠スキーマ型を受け入れ、それを次の実装 ( <xref:System.Xml.Serialization.IXmlSerializable> の配列をラップする <xref:System.Xml.XmlNode> ) にマッピングできるようになります (クラス名のみ異なります)。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-493">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>

```csharp
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]
public partial class Person : object, IXmlSerializable
{
  private XmlNode[] nodesField;
  private static XmlQualifiedName typeName =
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");
  public XmlNode[] Nodes
  {
    get {return this.nodesField;}
    set {this.nodesField = value;}
  }
  public void ReadXml(XmlReader reader)
  {
    this.nodesField = XmlSerializableServices.ReadNodes(reader);
  }
  public void WriteXml(XmlWriter writer)
  {
    XmlSerializableServices.WriteNodes(writer, this.Nodes);
  }
  public System.Xml.Schema.XmlSchema GetSchema()
  {
    return null;
  }
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)
  {
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);
    return typeName;
  }
}
```

## <a name="datetimeoffset-serialization"></a><span data-ttu-id="b2ffa-494">DateTimeOffset のシリアル化</span><span class="sxs-lookup"><span data-stu-id="b2ffa-494">DateTimeOffset Serialization</span></span>

<span data-ttu-id="b2ffa-495"><xref:System.DateTimeOffset> はプリミティブ型としては扱われません。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-495">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="b2ffa-496">その代わりに、2 つの部分から成る複合型要素としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-496">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="b2ffa-497">最初の部分は日時を表し、2 番目の部分は日時からのオフセットを表します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-497">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="b2ffa-498">次のコード例に、シリアル化された DateTimeOffset 値を示します。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-498">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>

```xml
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">
  <DateTime i:type="b:dateTime" xmlns=""
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00
  </DateTime>
  <OffsetMinutes i:type="b:short" xmlns=""
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480
   </OffsetMinutes>
</OffSet>
```

<span data-ttu-id="b2ffa-499">スキーマは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b2ffa-499">The schema is as follows.</span></span>

```xml
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">
   <xs:complexType name="DateTimeOffset">
      <xs:sequence minOccurs="1" maxOccurs="1">
         <xs:element name="DateTime" type="xs:dateTime"
         minOccurs="1" maxOccurs="1" />
         <xs:element name="OffsetMinutes" type="xs:short"
         minOccurs="1" maxOccurs="1" />
      </xs:sequence>
   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a><span data-ttu-id="b2ffa-500">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2ffa-500">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [<span data-ttu-id="b2ffa-501">データ コントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="b2ffa-501">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
