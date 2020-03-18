---
title: XML ファイルの処理 - C# プログラミング ガイド
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: bc72cade9ce6edddb88d741a3424405bba0a7ad8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793391"
---
# <a name="processing-the-xml-file-c-programming-guide"></a><span data-ttu-id="4d7a0-102">XML ファイルの処理 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="4d7a0-102">Processing the XML file (C# programming guide)</span></span>

<span data-ttu-id="4d7a0-103">コンパイラは、ドキュメントを生成するためにタグ付けされたコードのコンストラクトごとに、ID 文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="4d7a0-104">(コードをタグ付けする方法については、[ドキュメント コメント用の推奨タグ](./recommended-tags-for-documentation-comments.md)に関するページを参照してください。)ID 文字列によって、コンストラクトは一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-104">(For information about how to tag your code, see [Recommended Tags for Documentation Comments](./recommended-tags-for-documentation-comments.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="4d7a0-105">XML ファイルを処理するプログラムは、ID 文字列を使用して、対応する .NET Framework のメタデータまたはドキュメントを適用するリフレクション項目を識別できます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-105">Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item that the documentation applies to.</span></span>

<span data-ttu-id="4d7a0-106">XML ファイルは、コードの階層表現ではなく、要素ごとに生成された ID のフラット リストです。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-106">The XML file is not a hierarchical representation of your code; it is a flat list that has a generated ID for each element.</span></span>

<span data-ttu-id="4d7a0-107">コンパイラは、次の規則に基づいて ID 文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-107">The compiler observes the following rules when it generates the ID strings:</span></span>

- <span data-ttu-id="4d7a0-108">文字列に空白文字は含まれません。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-108">No white space is in the string.</span></span>

- <span data-ttu-id="4d7a0-109">ID 文字列の最初の部分は、単一の文字とそれに続くコロンで識別されるメンバー種類を示します。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-109">The first part of the ID string identifies the kind of member being identified, by way of a single character followed by a colon.</span></span> <span data-ttu-id="4d7a0-110">使用されるメンバー型は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-110">The following member types are used:</span></span>

    |<span data-ttu-id="4d7a0-111">文字</span><span class="sxs-lookup"><span data-stu-id="4d7a0-111">Character</span></span>|<span data-ttu-id="4d7a0-112">説明</span><span class="sxs-lookup"><span data-stu-id="4d7a0-112">Description</span></span>|
    |---------------|-----------------|
    |<span data-ttu-id="4d7a0-113">N</span><span class="sxs-lookup"><span data-stu-id="4d7a0-113">N</span></span>|<span data-ttu-id="4d7a0-114">名前空間</span><span class="sxs-lookup"><span data-stu-id="4d7a0-114">namespace</span></span><br /><br /> <span data-ttu-id="4d7a0-115">ドキュメント コメントを名前空間に追加することはできませんが、名前空間への cref 参照を行うことはできます (サポートされている場合)。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-115">You cannot add documentation comments to a namespace, but you can make cref references to them, where supported.</span></span>|
    |<span data-ttu-id="4d7a0-116">T</span><span class="sxs-lookup"><span data-stu-id="4d7a0-116">T</span></span>|<span data-ttu-id="4d7a0-117">型: クラス、インターフェイス、構造体、列挙型、またはデリゲート</span><span class="sxs-lookup"><span data-stu-id="4d7a0-117">type: class, interface, struct, enum, or delegate</span></span>|
    |<span data-ttu-id="4d7a0-118">F</span><span class="sxs-lookup"><span data-stu-id="4d7a0-118">F</span></span>|<span data-ttu-id="4d7a0-119">フィールド</span><span class="sxs-lookup"><span data-stu-id="4d7a0-119">field</span></span>|
    |<span data-ttu-id="4d7a0-120">P</span><span class="sxs-lookup"><span data-stu-id="4d7a0-120">P</span></span>|<span data-ttu-id="4d7a0-121">プロパティ (インデクサーまたはその他のインデックス付きプロパティを含む)</span><span class="sxs-lookup"><span data-stu-id="4d7a0-121">property (including indexers or other indexed properties)</span></span>|
    |<span data-ttu-id="4d7a0-122">M</span><span class="sxs-lookup"><span data-stu-id="4d7a0-122">M</span></span>|<span data-ttu-id="4d7a0-123">メソッド (コンストラクター、演算子などの特殊なメソッドを含む)</span><span class="sxs-lookup"><span data-stu-id="4d7a0-123">method (including such special methods as constructors, operators, and so forth)</span></span>|
    |<span data-ttu-id="4d7a0-124">E</span><span class="sxs-lookup"><span data-stu-id="4d7a0-124">E</span></span>|<span data-ttu-id="4d7a0-125">イベント</span><span class="sxs-lookup"><span data-stu-id="4d7a0-125">event</span></span>|
    |<span data-ttu-id="4d7a0-126">!</span><span class="sxs-lookup"><span data-stu-id="4d7a0-126">!</span></span>|<span data-ttu-id="4d7a0-127">エラー文字列</span><span class="sxs-lookup"><span data-stu-id="4d7a0-127">error string</span></span><br /><br /> <span data-ttu-id="4d7a0-128">あとに続く文字列で、エラーの情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="4d7a0-129">C# コンパイラは、解決できないリンクのエラー情報を生成します。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-129">The C# compiler generates error information for links that cannot be resolved.</span></span>|

- <span data-ttu-id="4d7a0-130">文字列の 2 番目の部分は、項目の完全修飾名で、名前空間のルートから始まります。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-130">The second part of the string is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="4d7a0-131">項目の名前、それを囲む型、名前空間は、ピリオドで区切られます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-131">The name of the item, its enclosing type(s), and namespace are separated by periods.</span></span> <span data-ttu-id="4d7a0-132">項目の名前自体にピリオドがある場合、名前のピリオドはハッシュ記号 ('#') に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-132">If the name of the item itself has periods, they are replaced by the hash-sign ('#').</span></span> <span data-ttu-id="4d7a0-133">項目の名前には、ハッシュ記号がないことが前提です。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-133">It is assumed that no item has a hash-sign directly in its name.</span></span> <span data-ttu-id="4d7a0-134">たとえば、String コンストラクターの完全修飾名は "System.String.#ctor" です。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-134">For example, the fully qualified name of the String constructor would be "System.String.#ctor".</span></span>

- <span data-ttu-id="4d7a0-135">プロパティおよびメソッドについては、メソッドに引数がある場合は、引数のリストをかっこで囲み、メソッドに続けて指定します。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="4d7a0-136">引数がない場合は、かっこはありません。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="4d7a0-137">引数はコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-137">The arguments are separated by commas.</span></span> <span data-ttu-id="4d7a0-138">各引数のエンコードは、次に示す .NET Framework のシグネチャでの引数のエンコーディング方法にそのまま従います。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-138">The encoding of each argument follows directly how it is encoded in a .NET Framework signature:</span></span>

  - <span data-ttu-id="4d7a0-139">基本データ型。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-139">Base types.</span></span> <span data-ttu-id="4d7a0-140">通常の型 (ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE) は、型の完全修飾名で表されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-140">Regular types (ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE) are represented as the fully qualified name of the type.</span></span>

  - <span data-ttu-id="4d7a0-141">(ELEMENT_TYPE_I4、ELEMENT_TYPE_OBJECT、ELEMENT_TYPE_STRING、ELEMENT_TYPE_TYPEDBYREF、および ELEMENT_TYPE_VOID などの) 組み込み型は、対応する完全な型の完全修飾名で表されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-141">Intrinsic types (for example, ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF, and ELEMENT_TYPE_VOID) are represented as the fully qualified name of the corresponding full type.</span></span> <span data-ttu-id="4d7a0-142">たとえば、System.Int32 や System.TypedReference です。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-142">For example, System.Int32 or System.TypedReference.</span></span>

  - <span data-ttu-id="4d7a0-143">ELEMENT_TYPE_PTR は、修飾される型に続けて '\*' と表されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-143">ELEMENT_TYPE_PTR is represented as a '\*' following the modified type.</span></span>

  - <span data-ttu-id="4d7a0-144">ELEMENT_TYPE_BYREF は、修飾される型に続けて '\@' と表されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-144">ELEMENT_TYPE_BYREF is represented as a '\@' following the modified type.</span></span>

  - <span data-ttu-id="4d7a0-145">ELEMENT_TYPE_PINNED は、修飾される型に続けて '^' と表されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-145">ELEMENT_TYPE_PINNED is represented as a '^' following the modified type.</span></span> <span data-ttu-id="4d7a0-146">これは C# コンパイラでは生成されません。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-146">The C# compiler never generates this.</span></span>

  - <span data-ttu-id="4d7a0-147">ELEMENT_TYPE_CMOD_REQ は、修飾される型に続けて "&#124;" と修飾子クラスの完全修飾名で表されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-147">ELEMENT_TYPE_CMOD_REQ is represented as a '&#124;' and the fully qualified name of the modifier class, following the modified type.</span></span> <span data-ttu-id="4d7a0-148">これは C# コンパイラでは生成されません。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-148">The C# compiler never generates this.</span></span>

  - <span data-ttu-id="4d7a0-149">ELEMENT_TYPE_CMOD_OPT は、修飾される型に続けて "!" と修飾子クラスの完全修飾名で表されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-149">ELEMENT_TYPE_CMOD_OPT is represented as a '!' and the fully qualified name of the modifier class, following the modified type.</span></span>

  - <span data-ttu-id="4d7a0-150">ELEMENT_TYPE_SZARRAY は、配列の要素型に続けて "[]" と表されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-150">ELEMENT_TYPE_SZARRAY is represented as "[]" following the element type of the array.</span></span>

  - <span data-ttu-id="4d7a0-151">ELEMENT_TYPE_GENERICARRAY は、配列の要素型に続けて "[?]" と表されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-151">ELEMENT_TYPE_GENERICARRAY is represented as "[?]" following the element type of the array.</span></span> <span data-ttu-id="4d7a0-152">これは C# コンパイラでは生成されません。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-152">The C# compiler never generates this.</span></span>

  - <span data-ttu-id="4d7a0-153">ELEMENT_TYPE_ARRAY は、[*lowerbound*:`size`,*lowerbound*:`size`] の形式で表されます。ここで、コンマの個数はランク -1 個であり、各次元の下限とサイズは明らかな場合は、10 進数で表されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-153">ELEMENT_TYPE_ARRAY is represented as [*lowerbound*:`size`,*lowerbound*:`size`] where the number of commas is the rank - 1, and the lower bounds and size of each dimension, if known, are represented in decimal.</span></span> <span data-ttu-id="4d7a0-154">下限またはサイズの指定がない場合は省略されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-154">If a lower bound or size is not specified, it is simply omitted.</span></span> <span data-ttu-id="4d7a0-155">特定の次元で下限およびサイズが省略されている場合は、':' も省略されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-155">If the lower bound and size for a particular dimension are omitted, the ':' is omitted as well.</span></span> <span data-ttu-id="4d7a0-156">たとえば、ある 2 次元配列の下限が 1 で、サイズの指定がない場合は、[1:,1:] と表されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-156">For example, a 2-dimensional array with 1 as the lower bounds and unspecified sizes is [1:,1:].</span></span>

  - <span data-ttu-id="4d7a0-157">ELEMENT_TYPE_FNPTR は、"=FUNC:`type`(*signature*)" と表されます。ここで、`type` は戻り値の型であり、*signature* はメソッドの引数です。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-157">ELEMENT_TYPE_FNPTR is represented as "=FUNC:`type`(*signature*)", where `type` is the return type, and *signature* is the arguments of the method.</span></span> <span data-ttu-id="4d7a0-158">引数がない場合、かっこは省略されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-158">If there are no arguments, the parentheses are omitted.</span></span> <span data-ttu-id="4d7a0-159">これは C# コンパイラでは生成されません。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-159">The C# compiler never generates this.</span></span>

    <span data-ttu-id="4d7a0-160">次に示すシグネチャ コンポーネントは、オーバーロードされるメソッドの区別には使用されることがないため、表されません。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-160">The following signature components are not represented because they are never used for differentiating overloaded methods:</span></span>

  - <span data-ttu-id="4d7a0-161">呼び出し規則</span><span class="sxs-lookup"><span data-stu-id="4d7a0-161">calling convention</span></span>

  - <span data-ttu-id="4d7a0-162">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="4d7a0-162">return type</span></span>

  - <span data-ttu-id="4d7a0-163">ELEMENT_TYPE_SENTINEL</span><span class="sxs-lookup"><span data-stu-id="4d7a0-163">ELEMENT_TYPE_SENTINEL</span></span>

- <span data-ttu-id="4d7a0-164">変換演算子 (op_Implicit および op_Explicit) だけは、上記のエンコードと同様に、メソッドの戻り値が ”~” としてエンコードされ、それに続けて戻り値の型が表されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-164">For conversion operators only (op_Implicit and op_Explicit), the return value of the method is encoded as a '~' followed by the return type, as encoded above.</span></span>

- <span data-ttu-id="4d7a0-165">ジェネリック型では、型の名前の後に、バックチック、ジェネリック型パラメーターの数を示す数値が順に続きます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-165">For generic types, the name of the type is followed by a backtick and then a number that indicates the number of generic type parameters.</span></span> <span data-ttu-id="4d7a0-166">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-166">For example:</span></span>

     <span data-ttu-id="4d7a0-167">``<member name="T:SampleClass`2">`` は、`public class SampleClass<T, U>` として定義されている型のタグです。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-167">``<member name="T:SampleClass`2">`` is the tag for a type that is defined as `public class SampleClass<T, U>`.</span></span>

     <span data-ttu-id="4d7a0-168">パラメーターとしてジェネリック型を受け取るメソッドでは、ジェネリック型パラメーターは、バックチック付きの数値 (\`0、\`1 など) として指定されます。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-168">For methods taking generic types as parameters, the generic type parameters are specified as numbers prefaced with backticks (for example \`0,\`1).</span></span> <span data-ttu-id="4d7a0-169">各数値は、型のジェネリック パラメーターに対する、0 から始まる配列表記を表しています。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-169">Each number representing a zero-based array notation for the type's generic parameters.</span></span>

## <a name="examples"></a><span data-ttu-id="4d7a0-170">使用例</span><span class="sxs-lookup"><span data-stu-id="4d7a0-170">Examples</span></span>

<span data-ttu-id="4d7a0-171">次の例は、クラスおよびそのメンバーの ID 文字列を生成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4d7a0-171">The following examples show how the ID strings for a class and its members would be generated:</span></span>

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a><span data-ttu-id="4d7a0-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d7a0-172">See also</span></span>

- [<span data-ttu-id="4d7a0-173">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="4d7a0-173">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="4d7a0-174">-doc (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="4d7a0-174">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="4d7a0-175">XML ドキュメント コメント</span><span class="sxs-lookup"><span data-stu-id="4d7a0-175">XML documentation comments</span></span>](./index.md)
