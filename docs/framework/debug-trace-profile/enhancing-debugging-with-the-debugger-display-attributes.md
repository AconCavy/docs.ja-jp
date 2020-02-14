---
title: デバッガー表示属性によるデバッグ機能の拡張
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- debugger, display attributes
- DebuggerTypeProxyAttribute attribute
- debugging [.NET Framework], debugger display attributes
- DebuggerDisplayAttribute attribute
- display attributes for debugger
- DebuggerBrowsableAttribute attribute
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
ms.openlocfilehash: ca118bffb045a0e7e3a5084916a0ff8020ebda90
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216492"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="73704-102">デバッガー表示属性によるデバッグ機能の拡張</span><span class="sxs-lookup"><span data-stu-id="73704-102">Enhancing Debugging with the Debugger Display Attributes</span></span>

<span data-ttu-id="73704-103">デバッガー表示属性は、型を指定し、その型の実行時の動作を最もよく理解している型の開発者が、デバッガーで表示されたときに、その型がどのように見えるかも指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="73704-103">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="73704-104">さらに、`Target` プロパティを提供するデバッガー表示属性は、ソース コードの知識がなくても、ユーザーがアセンブリ レベルで適用することができます。</span><span class="sxs-lookup"><span data-stu-id="73704-104">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="73704-105"><xref:System.Diagnostics.DebuggerDisplayAttribute> 属性は、デバッガーの変数ウィンドウで型やメンバーを表示する方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="73704-105">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="73704-106"><xref:System.Diagnostics.DebuggerBrowsableAttribute> 属性は、デバッガーの変数ウィンドウにフィールドまたはプロパティを表示するかどうか、および表示方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="73704-106">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="73704-107"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> 属性は、型に対して代理の型 (プロキシ) を指定し、その型をデバッガー ウィンドウで表示する方法を変更します。</span><span class="sxs-lookup"><span data-stu-id="73704-107">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="73704-108">プロキシまたは代替の種類を持つ変数を表示すると、プロキシは、デバッガーの表示ウィンドウで元の型を表します。</span><span class="sxs-lookup"><span data-stu-id="73704-108">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="73704-109">デバッガーの変数ウィンドウには、プロキシ型のパブリック メンバーのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="73704-109">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="73704-110">プライベート メンバーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="73704-110">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="73704-111">DebuggerDisplayAttribute の使用</span><span class="sxs-lookup"><span data-stu-id="73704-111">Using the DebuggerDisplayAttribute</span></span>  

<span data-ttu-id="73704-112"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> コンストラクターには引数が 1 つあり、それは、型のインスタンスの値列に表示される文字列です。</span><span class="sxs-lookup"><span data-stu-id="73704-112">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="73704-113">この文字列には、中かっこ ({ と }) を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="73704-113">This string can contain braces ({ and }).</span></span> <span data-ttu-id="73704-114">かっこ内のテキストは、式として評価されます。</span><span class="sxs-lookup"><span data-stu-id="73704-114">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="73704-115">たとえば、次の C# コードでは、`MyHashtable` のインスタンスのデバッガー表示を展開するプラス記号 (+) が選択された場合に、"Count = 4" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="73704-115">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

<span data-ttu-id="73704-116">式で参照されるプロパティに適用される属性は処理されません。</span><span class="sxs-lookup"><span data-stu-id="73704-116">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="73704-117">C# コンパイラでは、対象の型の現在のインスタンスへのこの参照に対し、暗黙的なアクセスのみを持つ一般的な式が許可されています。</span><span class="sxs-lookup"><span data-stu-id="73704-117">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="73704-118">この式は制限されており、エイリアス、ローカル、またはポインターに対するアクセスはありません。</span><span class="sxs-lookup"><span data-stu-id="73704-118">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="73704-119">C# コードでは、対象となる型の現在のインスタンスのみの `this` ポインターに暗黙的にアクセスする一般的な式をかっこ内で使用できます。</span><span class="sxs-lookup"><span data-stu-id="73704-119">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>

<span data-ttu-id="73704-120">たとえば、C# オブジェクトにオーバーライドされた `ToString()` がある場合、デバッガーはそのオーバーライドを呼び出し、標準の `{<typeName>}.` ではなく、その結果を表示します。したがって、オーバーライドされた `ToString()` がある場合、<xref:System.Diagnostics.DebuggerDisplayAttribute> を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="73704-120">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="73704-121">両方を使用すると、<xref:System.Diagnostics.DebuggerDisplayAttribute> 属性が `ToString()` オーバーライドよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="73704-121">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>

## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="73704-122">DebuggerBrowsableAttribute の使用</span><span class="sxs-lookup"><span data-stu-id="73704-122">Using the DebuggerBrowsableAttribute</span></span>
 <span data-ttu-id="73704-123"><xref:System.Diagnostics.DebuggerBrowsableAttribute> をフィールドまたはプロパティに適用して、デバッガー ウィンドウにフィールドまたはプロパティを表示する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="73704-123">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="73704-124">この属性のコンストラクターは、次の状態のいずれかを指定する <xref:System.Diagnostics.DebuggerBrowsableState> 列挙値を 1 つ取得します。</span><span class="sxs-lookup"><span data-stu-id="73704-124">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>

- <span data-ttu-id="73704-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> は、データ ウィンドウにメンバーが表示されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="73704-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="73704-126">たとえば、この値をフィールドで <xref:System.Diagnostics.DebuggerBrowsableAttribute> に使用すると、そのフィールドが階層から削除され、型のインスタンスのプラス記号 (+) をクリックして囲む型を展開したときに、そのフィールドが表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="73704-126">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>

- <span data-ttu-id="73704-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> は、メンバーが表示されますが、既定で展開されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="73704-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="73704-128">これは既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="73704-128">This is the default behavior.</span></span>

- <span data-ttu-id="73704-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> は、メンバー自体は表示されませんが、メンバーが配列またはコレクションである場合は、その構成オブジェクトが表示されることを示します。</span><span class="sxs-lookup"><span data-stu-id="73704-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>

> [!NOTE]
> <span data-ttu-id="73704-130">.NET Framework version 2.0 では、<xref:System.Diagnostics.DebuggerBrowsableAttribute> は Visual Basic でサポートされません。</span><span class="sxs-lookup"><span data-stu-id="73704-130">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>

<span data-ttu-id="73704-131">次のコード例は、<xref:System.Diagnostics.DebuggerBrowsableAttribute> を使用して、それに続くプロパティがクラスのデバッグ ウィンドウに表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="73704-131">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="73704-132">DebuggerTypeProxy の使用</span><span class="sxs-lookup"><span data-stu-id="73704-132">Using the DebuggerTypeProxy</span></span>
 <span data-ttu-id="73704-133"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> 属性は、型のデバッグ ビューを大幅かつ根本的に変更する必要があるものの、型そのものは変えない場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="73704-133">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="73704-134"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> 属性は、開発者が型の表示を調整できるように、型の表示プロキシを指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="73704-134">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="73704-135"><xref:System.Diagnostics.DebuggerDisplayAttribute> と同様に、この属性は、アセンブリ レベルで使用できます。この場合、<xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> プロパティは、プロキシが使用される型を指定します。</span><span class="sxs-lookup"><span data-stu-id="73704-135">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="73704-136">推奨される使用法は、この属性が、属性が適用される型の中で発生するプライベートの入れ子にされた型を指定することです。</span><span class="sxs-lookup"><span data-stu-id="73704-136">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="73704-137">型ビューアーをサポートする式エバリュエーターが、型が表示されるときに、この属性をチェックします。</span><span class="sxs-lookup"><span data-stu-id="73704-137">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="73704-138">属性が見つかると、式エバリュエーターは、属性が適用される型の代わりに表示プロキシ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="73704-138">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>

 <span data-ttu-id="73704-139"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> が存在する場合は、デバッガーの変数ウィンドウには、プロキシ型のパブリック メンバーのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="73704-139">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="73704-140">プライベート メンバーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="73704-140">Private members are not displayed.</span></span> <span data-ttu-id="73704-141">データ ウィンドウの動作は、属性拡張ビューでは変更されません。</span><span class="sxs-lookup"><span data-stu-id="73704-141">The behavior of the data window is not changed by attribute-enhanced views.</span></span>

 <span data-ttu-id="73704-142">不要なパフォーマンスの低下を避けるため、データ ウィンドウでユーザーが型の横にあるプラス記号 (+) をクリックするか、<xref:System.Diagnostics.DebuggerBrowsableAttribute> 属性の適用により、オブジェクトが展開されるまで、表示プロキシの属性は処理されません。</span><span class="sxs-lookup"><span data-stu-id="73704-142">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="73704-143">そのため、表示型に属性を適用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="73704-143">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="73704-144">属性は、表示型の本体内で適用でき、また適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73704-144">Attributes can and should be applied within the body of the display type.</span></span>

 <span data-ttu-id="73704-145">次のコード例は、<xref:System.Diagnostics.DebuggerTypeProxyAttribute> を使用してデバッガーの表示プロキシとして使用する型を指定します。</span><span class="sxs-lookup"><span data-stu-id="73704-145">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>

```csharp
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable : Hashtable
{
    private const string TestString =
        "This should not appear in the debug window.";

    internal class HashtableDebugView
    {
        private Hashtable hashtable;
        public const string TestStringProxy =
            "This should appear in the debug window.";

        // The constructor for the type proxy class must have a
        // constructor that takes the target type as a parameter.
        public HashtableDebugView(Hashtable hashtable)
        {
            this.hashtable = hashtable;
        }
    }
}
```

## <a name="example"></a><span data-ttu-id="73704-146">例</span><span class="sxs-lookup"><span data-stu-id="73704-146">Example</span></span>

### <a name="description"></a><span data-ttu-id="73704-147">説明</span><span class="sxs-lookup"><span data-stu-id="73704-147">Description</span></span>

<span data-ttu-id="73704-148">次のコード例を Visual Studio で表示すると、<xref:System.Diagnostics.DebuggerDisplayAttribute>、<xref:System.Diagnostics.DebuggerBrowsableAttribute>、および <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 属性を適用した結果を確認できます。</span><span class="sxs-lookup"><span data-stu-id="73704-148">The following code example can be viewed in Visual Studio to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>

### <a name="code"></a><span data-ttu-id="73704-149">コード</span><span class="sxs-lookup"><span data-stu-id="73704-149">Code</span></span>

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="73704-150">参照</span><span class="sxs-lookup"><span data-stu-id="73704-150">See also</span></span>

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
