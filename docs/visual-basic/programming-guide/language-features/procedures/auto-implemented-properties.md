---
title: 自動実装プロパティ
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: b322bd2215c95298be0a33ace1f3590a63878e24
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350382"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="036d0-102">自動実装プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="036d0-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="036d0-103">*自動実装プロパティ*を使用すると、`Get` するコードを記述したり、プロパティを `Set` したりせずに、クラスのプロパティをすばやく指定できます。</span><span class="sxs-lookup"><span data-stu-id="036d0-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="036d0-104">自動実装プロパティのコードを記述する場合、Visual Basic コンパイラでは、関連付けられた `Get` プロシージャおよび `Set` プロシージャが作成されるだけでなく、プロパティの変数を格納するためのプライベート フィールドが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="036d0-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="036d0-105">自動実装プロパティを使用することで、プロパティを既定値も含めて 1 つの行で宣言できます。</span><span class="sxs-lookup"><span data-stu-id="036d0-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="036d0-106">次に、プロパティ宣言の 3 つの例を示します。</span><span class="sxs-lookup"><span data-stu-id="036d0-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 <span data-ttu-id="036d0-107">自動実装プロパティは、プライベート フィールドにプロパティ値が格納されたプロパティに相当します。</span><span class="sxs-lookup"><span data-stu-id="036d0-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="036d0-108">自動実装プロパティを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="036d0-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 <span data-ttu-id="036d0-109">次のコード例は、前の自動実装プロパティの例で示したコードと同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="036d0-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 <span data-ttu-id="036d0-110">次のコードは、読み取り専用プロパティの実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="036d0-110">The following code show implementing readonly properties:</span></span>  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="036d0-111">例で示されているように、初期化式でプロパティに割り当てることができます。また、含む型のコンストラクター内でプロパティに割り当てることもできます。</span><span class="sxs-lookup"><span data-stu-id="036d0-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="036d0-112">任意の時点で読み取り専用プロパティのバッキング フィールドに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="036d0-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="036d0-113">バッキング フィールド</span><span class="sxs-lookup"><span data-stu-id="036d0-113">Backing Field</span></span>  
 <span data-ttu-id="036d0-114">自動実装プロパティを宣言すると、Visual Basic によって、プロパティ値を格納する*バッキングフィールド*と呼ばれる非表示のプライベートフィールドが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="036d0-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="036d0-115">バッキング フィールド名は、自動実装プロパティ名の前にアンダースコア (_) が付いた名前になります。</span><span class="sxs-lookup"><span data-stu-id="036d0-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="036d0-116">たとえば、`ID` という名前の自動実装プロパティを宣言した場合は、バッキング フィールド名は `_ID` になります。</span><span class="sxs-lookup"><span data-stu-id="036d0-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="036d0-117">同じ `_ID` という名前のクラスのメンバーを含めた場合、名前の競合が発生し、Visual Basic でコンパイル エラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="036d0-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="036d0-118">また、バッキング フィールドには、次の特性もあります。</span><span class="sxs-lookup"><span data-stu-id="036d0-118">The backing field also has the following characteristics:</span></span>  
  
- <span data-ttu-id="036d0-119">バッキング フィールドのアクセス修飾子は、そのプロパティ自体に `Private` などの別のアクセス レベルがある場合でも、常に `Public` です。</span><span class="sxs-lookup"><span data-stu-id="036d0-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
- <span data-ttu-id="036d0-120">プロパティ フィールドが `Shared` としてマークされている場合は、バッキング フィールドも共有になります。</span><span class="sxs-lookup"><span data-stu-id="036d0-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
- <span data-ttu-id="036d0-121">プロパティに指定された属性は、バッキング フィールドには適用されません。</span><span class="sxs-lookup"><span data-stu-id="036d0-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
- <span data-ttu-id="036d0-122">バッキング フィールドは、クラス内のコードや、ウォッチ ウィンドウなどのデバッグ ツールからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="036d0-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="036d0-123">ただし、バッキング フィールドは IntelliSense の単語補完リストには表示されません。</span><span class="sxs-lookup"><span data-stu-id="036d0-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="036d0-124">自動実装プロパティの初期化</span><span class="sxs-lookup"><span data-stu-id="036d0-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="036d0-125">フィールドの初期化に使用する式は、すべて自動実装プロパティの初期化にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="036d0-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="036d0-126">自動実装プロパティを初期化する場合、その式は評価され、そのプロパティの `Set` プロシージャに渡されます。</span><span class="sxs-lookup"><span data-stu-id="036d0-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="036d0-127">次のコード例は、初期値を持ついくつかの自動実装プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="036d0-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 <span data-ttu-id="036d0-128">`Interface` のメンバーである自動実装プロパティ、または `MustOverride` としてマークされた自動実装プロパティを初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="036d0-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="036d0-129">自動実装プロパティを `Structure` のメンバーとして宣言した場合、自動実装プロパティを `Shared` としてマークした場合にのみ初期化できます。</span><span class="sxs-lookup"><span data-stu-id="036d0-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="036d0-130">自動実装プロパティを配列として宣言した場合、明示的な配列の範囲は指定できません。</span><span class="sxs-lookup"><span data-stu-id="036d0-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="036d0-131">しかし、次の例に示すように、配列初期化子を使用して値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="036d0-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="036d0-132">標準構文を必要とするプロパティ定義</span><span class="sxs-lookup"><span data-stu-id="036d0-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="036d0-133">自動実装プロパティは使いやすく、多くのプログラミング シナリオに対応します。</span><span class="sxs-lookup"><span data-stu-id="036d0-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="036d0-134">ただし、自動実装プロパティを使用することはできず、代わりに標準または*拡張*されたプロパティの構文を使用する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="036d0-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="036d0-135">次のいずれかを実行する場合は、展開されたプロパティ定義構文を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="036d0-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
- <span data-ttu-id="036d0-136">`Get` プロシージャで受信した値を検証するコードなどのコードを、プロパティの `Set` プロシージャまたは `Set` プロシージャに追加する。</span><span class="sxs-lookup"><span data-stu-id="036d0-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="036d0-137">たとえば、電話番号を示す文字列のプロパティ値を設定する前に、その文字列に必要な数の数字が含まれていることを検証する場合です。</span><span class="sxs-lookup"><span data-stu-id="036d0-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
- <span data-ttu-id="036d0-138">`Get` プロシージャと `Set` プロシージャに異なるアクセシビリティを指定する。</span><span class="sxs-lookup"><span data-stu-id="036d0-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="036d0-139">たとえば、`Set` プロシージャを `Private` にし、`Get` プロシージャを `Public` にする場合です。</span><span class="sxs-lookup"><span data-stu-id="036d0-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
- <span data-ttu-id="036d0-140">`WriteOnly` のプロパティを作成する。</span><span class="sxs-lookup"><span data-stu-id="036d0-140">Create properties that are `WriteOnly`.</span></span>  
  
- <span data-ttu-id="036d0-141">パラメーター化されたプロパティ (`Default` プロパティなど) を使用する。</span><span class="sxs-lookup"><span data-stu-id="036d0-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="036d0-142">プロパティのパラメーターを指定するか、`Set` プロシージャに追加のパラメーターを指定するには、展開されたプロパティを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="036d0-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
- <span data-ttu-id="036d0-143">バッキング フィールドに属性を指定するか、バッキング フィールドのアクセス レベルを変更する。</span><span class="sxs-lookup"><span data-stu-id="036d0-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
- <span data-ttu-id="036d0-144">バッキング フィールドに XML コメントを指定する。</span><span class="sxs-lookup"><span data-stu-id="036d0-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="036d0-145">自動実装プロパティの展開</span><span class="sxs-lookup"><span data-stu-id="036d0-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="036d0-146">自動実装プロパティを `Get` プロシージャまたは `Set` プロシージャを含む展開されたプロパティに変換する必要がある場合、Visual Basic コード エディターを使用すると、`Get` プロシージャおよび `Set` プロシージャと、そのプロパティの `End Property` ステートメントを自動的に生成できます。</span><span class="sxs-lookup"><span data-stu-id="036d0-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="036d0-147">このコードは、`Property` ステートメントの後の空白行にカーソルを置くと、`G` (`Get`) または `S` (`Set`の場合) を入力し、enter キーを押すと生成されます。</span><span class="sxs-lookup"><span data-stu-id="036d0-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="036d0-148">`Get` ステートメントの最後で Enter キーを押すと、読み取り専用のプロパティおよび書き込み専用のプロパティの `Set` プロシージャまたは `Property` プロシージャが Visual Basic コード エディターで自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="036d0-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="036d0-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="036d0-149">See also</span></span>

- [<span data-ttu-id="036d0-150">方法: Visual Basic で既定のプロパティを宣言して呼び出す</span><span class="sxs-lookup"><span data-stu-id="036d0-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="036d0-151">方法 : 複数のアクセス レベルを持つプロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="036d0-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="036d0-152">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="036d0-152">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="036d0-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="036d0-153">ReadOnly</span></span>](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="036d0-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="036d0-154">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="036d0-155">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="036d0-155">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
