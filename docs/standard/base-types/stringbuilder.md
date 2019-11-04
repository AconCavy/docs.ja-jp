---
title: .NET の StringBuilder クラスを使用する
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Remove method
- strings [.NET Framework], capacities
- StringBuilder object
- Replace method
- AppendFormat method
- Append method
- Insert method
- strings [.NET Framework], StringBuilder object
ms.assetid: 5c14867c-9a99-45bc-ae7f-2686700d377a
ms.openlocfilehash: 19ee90f3300e3b610eeefd4949baa2759b834a60
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121673"
---
# <a name="using-the-stringbuilder-class-in-net"></a><span data-ttu-id="0247d-102">.NET の StringBuilder クラスを使用する</span><span class="sxs-lookup"><span data-stu-id="0247d-102">Using the StringBuilder Class in .NET</span></span>
<span data-ttu-id="0247d-103"><xref:System.String> オブジェクトは、変更できません。</span><span class="sxs-lookup"><span data-stu-id="0247d-103">The <xref:System.String> object is immutable.</span></span> <span data-ttu-id="0247d-104"><xref:System.String?displayProperty=nameWithType> クラスのメソッドのいずれかを使用するたびに、新しい文字列オブジェクトをメモリ内に作成します。その際、その新しいオブジェクトに対して領域を新たに割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="0247d-104">Every time you use one of the methods in the <xref:System.String?displayProperty=nameWithType> class, you create a new string object in memory, which requires a new allocation of space for that new object.</span></span> <span data-ttu-id="0247d-105">文字列に対して何度も変更を実行する必要がある場合、新しい <xref:System.String> オブジェクトの作成に関連したオーバーヘッドが高コストになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0247d-105">In situations where you need to perform repeated modifications to a string, the overhead associated with creating a new <xref:System.String> object can be costly.</span></span> <span data-ttu-id="0247d-106">新しいオブジェクトを作成せずに文字列を変更したい場合は、<xref:System.Text.StringBuilder?displayProperty=nameWithType> クラスを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0247d-106">The <xref:System.Text.StringBuilder?displayProperty=nameWithType> class can be used when you want to modify a string without creating a new object.</span></span> <span data-ttu-id="0247d-107">たとえば、ループで多数の文字列を連結する場合に、<xref:System.Text.StringBuilder> クラスを使用してパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="0247d-107">For example, using the <xref:System.Text.StringBuilder> class can boost performance when concatenating many strings together in a loop.</span></span>  
  
## <a name="importing-the-systemtext-namespace"></a><span data-ttu-id="0247d-108">System.Text 名前空間のインポート</span><span class="sxs-lookup"><span data-stu-id="0247d-108">Importing the System.Text Namespace</span></span>  
 <span data-ttu-id="0247d-109"><xref:System.Text.StringBuilder> クラスは、<xref:System.Text> 名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="0247d-109">The <xref:System.Text.StringBuilder> class is found in the <xref:System.Text> namespace.</span></span>  <span data-ttu-id="0247d-110">完全修飾型名をコードに指定しなくてもすむように、<xref:System.Text> 名前空間をインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="0247d-110">To avoid having to provide a fully qualified type name in your code,  you can import the <xref:System.Text> namespace:</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a><span data-ttu-id="0247d-111">StringBuilder オブジェクトのインスタンス化</span><span class="sxs-lookup"><span data-stu-id="0247d-111">Instantiating a StringBuilder Object</span></span>  
 <span data-ttu-id="0247d-112">以下の例に示すように、オーバーロードされたコンストラクター メソッドの 1 つで変数を初期化することにより、<xref:System.Text.StringBuilder> クラスの新しいインスタンスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="0247d-112">You can create a new instance of the <xref:System.Text.StringBuilder> class by initializing your variable with one of the overloaded constructor methods, as illustrated in the following example.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a><span data-ttu-id="0247d-113">容量と長さの設定</span><span class="sxs-lookup"><span data-stu-id="0247d-113">Setting the Capacity and Length</span></span>  
 <span data-ttu-id="0247d-114"><xref:System.Text.StringBuilder> は、カプセル化する文字列内の文字数を拡張できるようにする動的オブジェクトですが、保持可能な最大文字数の値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="0247d-114">Although the <xref:System.Text.StringBuilder> is a dynamic object that allows you to expand the number of characters in the string that it encapsulates, you can specify a value for the maximum number of characters that it can hold.</span></span> <span data-ttu-id="0247d-115">この値を、オブジェクトの容量と呼びます。これを現行の <xref:System.Text.StringBuilder> が保持する文字列の長さと混同すべきではありません。</span><span class="sxs-lookup"><span data-stu-id="0247d-115">This value is called the capacity of the object and should not be confused with the length of the string that the current <xref:System.Text.StringBuilder> holds.</span></span> <span data-ttu-id="0247d-116">たとえば、"Hello" という長さ 5 の文字列を持つ <xref:System.Text.StringBuilder> クラスの新しいインスタンスを作成するときに、オブジェクトの最大容量として 25 を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="0247d-116">For example, you might create a new instance of the <xref:System.Text.StringBuilder> class with the string "Hello", which has a length of 5, and you might specify that the object has a maximum capacity of 25.</span></span> <span data-ttu-id="0247d-117"><xref:System.Text.StringBuilder> を変更する際、容量に達するまでは、自動再割り当ては発生しません。</span><span class="sxs-lookup"><span data-stu-id="0247d-117">When you modify the <xref:System.Text.StringBuilder>, it does not reallocate size for itself until the capacity is reached.</span></span> <span data-ttu-id="0247d-118">容量に達すると、新しい領域が自動的に割り当てられ、容量が 2 倍になります。</span><span class="sxs-lookup"><span data-stu-id="0247d-118">When this occurs, the new space is allocated automatically and the capacity is doubled.</span></span> <span data-ttu-id="0247d-119">オーバーロードされたコンストラクターのいずれかを使用して、<xref:System.Text.StringBuilder> クラスの容量を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="0247d-119">You can specify the capacity of the <xref:System.Text.StringBuilder> class using one of the overloaded constructors.</span></span> <span data-ttu-id="0247d-120">次の例は、`myStringBuilder` オブジェクトを最大 25 の領域に拡張できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="0247d-120">The following example specifies that the `myStringBuilder` object can be expanded to a maximum of 25 spaces.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 <span data-ttu-id="0247d-121">また、<xref:System.Text.StringBuilder.Capacity%2A> の読み取り/書き込みプロパティを使用して、オブジェクトの最大長を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="0247d-121">Additionally, you can use the read/write <xref:System.Text.StringBuilder.Capacity%2A> property to set the maximum length of your object.</span></span> <span data-ttu-id="0247d-122">次の例では、**Capacity** プロパティを使用して、オブジェクトの最大長を定義しています。</span><span class="sxs-lookup"><span data-stu-id="0247d-122">The following example uses the **Capacity** property to define the maximum object length.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <span data-ttu-id="0247d-123"><xref:System.Text.StringBuilder.EnsureCapacity%2A> メソッドを使用して、現行 **StringBuilder** の容量を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="0247d-123">The <xref:System.Text.StringBuilder.EnsureCapacity%2A> method can be used to check the capacity of the current **StringBuilder**.</span></span> <span data-ttu-id="0247d-124">容量が渡された値よりも大きい場合、変更は行われません。しかし、容量が渡された値より小さい場合は、渡された値と一致するよう現行の容量が変更されます。</span><span class="sxs-lookup"><span data-stu-id="0247d-124">If the capacity is greater than the passed value, no change is made; however, if the capacity is smaller than the passed value, the current capacity is changed to match the passed value.</span></span>  
  
 <span data-ttu-id="0247d-125"><xref:System.Text.StringBuilder.Length%2A> プロパティを表示または設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="0247d-125">The <xref:System.Text.StringBuilder.Length%2A> property can also be viewed or set.</span></span> <span data-ttu-id="0247d-126">**Length** プロパティを、**Capacity** プロパティより大きな値に設定する場合、**Capacity** プロパティは **Length** プロパティと同じ値に自動的に変更されます。</span><span class="sxs-lookup"><span data-stu-id="0247d-126">If you set the **Length** property to a value that is greater than the **Capacity** property, the **Capacity** property is automatically changed to the same value as the **Length** property.</span></span> <span data-ttu-id="0247d-127">**Length** プロパティを、現行の **StringBuilder** 内の文字列の長さより小さい値に設定すると、文字列は短縮されます。</span><span class="sxs-lookup"><span data-stu-id="0247d-127">Setting the **Length** property to a value that is less than the length of the string within the current **StringBuilder** shortens the string.</span></span>  
  
## <a name="modifying-the-stringbuilder-string"></a><span data-ttu-id="0247d-128">StringBuilder 文字列の変更</span><span class="sxs-lookup"><span data-stu-id="0247d-128">Modifying the StringBuilder String</span></span>  
 <span data-ttu-id="0247d-129">**StringBuilder** の内容の変更に使用できるメソッドを次の表に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="0247d-129">The following table lists the methods you can use to modify the contents of a **StringBuilder**.</span></span>  
  
|<span data-ttu-id="0247d-130">メソッド名</span><span class="sxs-lookup"><span data-stu-id="0247d-130">Method name</span></span>|<span data-ttu-id="0247d-131">使用</span><span class="sxs-lookup"><span data-stu-id="0247d-131">Use</span></span>|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|<span data-ttu-id="0247d-132">現行の **StringBuilder** の末尾に情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="0247d-132">Appends information to the end of the current **StringBuilder**.</span></span>|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<span data-ttu-id="0247d-133">文字列に渡される書式指定子を、書式設定されたテキスト文字列で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0247d-133">Replaces a format specifier passed in a string with formatted text.</span></span>|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="0247d-134">現行の **StringBuilder** の指定されたインデックスに、文字列またはオブジェクトを挿入します。</span><span class="sxs-lookup"><span data-stu-id="0247d-134">Inserts a string or object into the specified index of the current **StringBuilder**.</span></span>|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="0247d-135">現行の **StringBuilder** から、指定された文字数を削除します。</span><span class="sxs-lookup"><span data-stu-id="0247d-135">Removes a specified number of characters from the current **StringBuilder**.</span></span>|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|<span data-ttu-id="0247d-136">指定されたインデックスで、指定された文字を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0247d-136">Replaces a specified character at a specified index.</span></span>|  
  
### <a name="append"></a><span data-ttu-id="0247d-137">追加</span><span class="sxs-lookup"><span data-stu-id="0247d-137">Append</span></span>  
 <span data-ttu-id="0247d-138">**Append** メソッドを使用して、現行 **StringBuilder** によって表される文字列の末尾にオブジェクトのテキストまたは文字列形式を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="0247d-138">The **Append** method can be used to add text or a string representation of an object to the end of a string represented by the current **StringBuilder**.</span></span> <span data-ttu-id="0247d-139">次の例では、**StringBuilder** を "Hello World" に初期設定し、テキストをオブジェクトの末尾に追加しています。</span><span class="sxs-lookup"><span data-stu-id="0247d-139">The following example initializes a **StringBuilder** to "Hello World" and then appends some text to the end of the object.</span></span> <span data-ttu-id="0247d-140">領域は、必要に応じて自動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="0247d-140">Space is allocated automatically as needed.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a><span data-ttu-id="0247d-141">AppendFormat</span><span class="sxs-lookup"><span data-stu-id="0247d-141">AppendFormat</span></span>  
 <span data-ttu-id="0247d-142"><xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> メソッドは、<xref:System.Text.StringBuilder> オブジェクトの末尾にテキストを追加します。</span><span class="sxs-lookup"><span data-stu-id="0247d-142">The <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> method adds text to the end of the <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="0247d-143">これは、書式設定される 1 つ以上のオブジェクトの <xref:System.IFormattable> 実装を呼び出すことにより、複合書式機能をサポートしています (詳細については、「[複合書式指定](../../../docs/standard/base-types/composite-formatting.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="0247d-143">It supports the composite formatting feature (for more information, see [Composite Formatting](../../../docs/standard/base-types/composite-formatting.md)) by calling the <xref:System.IFormattable> implementation of the object or objects to be formatted.</span></span> <span data-ttu-id="0247d-144">そのため、数値、日時、および列挙の値に対して標準書式文字列を受け取り、数値と日時の値、およびカスタム型に定義されている書式文字列に対してカスタム書式文字列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="0247d-144">Therefore, it accepts the standard format strings for numeric, date and time, and enumeration values, the custom format strings for numeric and date and time values, and the format strings defined for custom types.</span></span> <span data-ttu-id="0247d-145">(書式設定については、「[型の書式設定](../../../docs/standard/base-types/formatting-types.md)」を参照してください。)このメソッドを使用して、変数の書式をカスタマイズし、その値を <xref:System.Text.StringBuilder> に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="0247d-145">(For information about formatting, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).) You can use this method to customize the format of variables and append those values to a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="0247d-146">次の例では、<xref:System.Text.StringBuilder.AppendFormat%2A> メソッドを使用して、<xref:System.Text.StringBuilder> オブジェクトの末尾に、通貨値として書式設定されている整数値を挿入しています。</span><span class="sxs-lookup"><span data-stu-id="0247d-146">The following example uses the <xref:System.Text.StringBuilder.AppendFormat%2A> method to place an integer value formatted as a currency value at the end of a <xref:System.Text.StringBuilder> object.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a><span data-ttu-id="0247d-147">挿入</span><span class="sxs-lookup"><span data-stu-id="0247d-147">Insert</span></span>  
 <span data-ttu-id="0247d-148"><xref:System.Text.StringBuilder.Insert%2A> メソッドは、現行の <xref:System.Text.StringBuilder> オブジェクトの指定された位置に、文字列またはオブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="0247d-148">The <xref:System.Text.StringBuilder.Insert%2A> method adds a string or object to a specified position in the current <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="0247d-149">次の例では、このメソッドを使用して、<xref:System.Text.StringBuilder> オブジェクトの 6 番目の位置に単語を挿入しています。</span><span class="sxs-lookup"><span data-stu-id="0247d-149">The following example uses this method to insert a word into the sixth position of a <xref:System.Text.StringBuilder> object.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a><span data-ttu-id="0247d-150">削除</span><span class="sxs-lookup"><span data-stu-id="0247d-150">Remove</span></span>  
 <span data-ttu-id="0247d-151">**Remove** メソッドを使用して、現行の <xref:System.Text.StringBuilder> オブジェクトから指定された文字数を削除します (0 から始まる指定されたインデックスで開始します)。</span><span class="sxs-lookup"><span data-stu-id="0247d-151">You can use the **Remove** method to remove a specified number of characters from the current <xref:System.Text.StringBuilder> object, beginning at a specified zero-based index.</span></span> <span data-ttu-id="0247d-152">次の例では、**Remove** メソッドを使用して、<xref:System.Text.StringBuilder> オブジェクトを短縮しています。</span><span class="sxs-lookup"><span data-stu-id="0247d-152">The following example uses the **Remove** method to shorten a <xref:System.Text.StringBuilder> object.</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a><span data-ttu-id="0247d-153">Replace</span><span class="sxs-lookup"><span data-stu-id="0247d-153">Replace</span></span>  
 <span data-ttu-id="0247d-154">**Replace** メソッドを使用して、<xref:System.Text.StringBuilder> オブジェクト内の文字を、指定された別の文字で置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="0247d-154">The **Replace** method can be used to replace characters within the <xref:System.Text.StringBuilder> object with another specified character.</span></span> <span data-ttu-id="0247d-155">次の例では、**Replace** メソッドを使用して、感嘆符 (!) のすべてのインスタンスを求めて <xref:System.Text.StringBuilder> オブジェクトを検索し、疑問符 (?) で置き換えています。</span><span class="sxs-lookup"><span data-stu-id="0247d-155">The following example uses the **Replace** method to search a <xref:System.Text.StringBuilder> object for all instances of the exclamation point character (!) and replace them with the question mark character (?).</span></span>  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a><span data-ttu-id="0247d-156">文字列への StringBuilder オブジェクトの変換</span><span class="sxs-lookup"><span data-stu-id="0247d-156">Converting a StringBuilder Object to a String</span></span>  
 <span data-ttu-id="0247d-157"><xref:System.Text.StringBuilder> オブジェクトで表される文字列を <xref:System.String> パラメーターを持つメソッドに渡すかそれをユーザー インターフェイスに表示するには、事前に <xref:System.Text.StringBuilder> オブジェクトを <xref:System.String> オブジェクトに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0247d-157">You must convert the <xref:System.Text.StringBuilder> object to a <xref:System.String> object before you can pass the string represented by the <xref:System.Text.StringBuilder> object to a method that has a <xref:System.String> parameter or display it in the user interface.</span></span> <span data-ttu-id="0247d-158">この変換は、<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> メソッドを呼び出すことによって行います。</span><span class="sxs-lookup"><span data-stu-id="0247d-158">You do this conversion by calling the <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0247d-159">次の例では、いくつかの <xref:System.Text.StringBuilder> メソッドを呼び出し、その後、<xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> メソッドを呼び出して文字列を表示しています。</span><span class="sxs-lookup"><span data-stu-id="0247d-159">The following example calls a number of <xref:System.Text.StringBuilder> methods and then calls the <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> method to display the string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="0247d-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="0247d-160">See also</span></span>

- <xref:System.Text.StringBuilder?displayProperty=nameWithType>
- [<span data-ttu-id="0247d-161">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="0247d-161">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="0247d-162">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="0247d-162">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)
