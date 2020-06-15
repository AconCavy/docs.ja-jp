---
title: '方法: プロパティを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: fa220998d12206e620c242b9b39df3dc1b639d29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388259"
---
# <a name="how-to-create-a-property-visual-basic"></a><span data-ttu-id="42285-102">方法: プロパティを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42285-102">How to: Create a Property (Visual Basic)</span></span>
<span data-ttu-id="42285-103">プロパティ定義は、`Property` ステートメントと `End Property` ステートメントで囲みます。</span><span class="sxs-lookup"><span data-stu-id="42285-103">You enclose a property definition between a `Property` statement and an `End Property` statement.</span></span> <span data-ttu-id="42285-104">この定義内で、`Get` プロシージャ、`Set` プロシージャ、またはその両方を定義します。</span><span class="sxs-lookup"><span data-stu-id="42285-104">Within this definition you define a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="42285-105">プロパティのすべてのコードは、これらのプロシージャ内にあります。</span><span class="sxs-lookup"><span data-stu-id="42285-105">All the property's code lies within these procedures.</span></span>  
  
 <span data-ttu-id="42285-106">`Get` プロシージャ はプロパティの値を取得し、`Set` プロシージャは値を格納します。</span><span class="sxs-lookup"><span data-stu-id="42285-106">The `Get` procedure retrieves the property's value, and the `Set` procedure stores a value.</span></span> <span data-ttu-id="42285-107">プロパティに読み取り/書き込みアクセスが必要な場合は、両方のプロシージャを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42285-107">If you want the property to have read/write access, you must define both procedures.</span></span> <span data-ttu-id="42285-108">読み取り専用プロパティでは `Get` のみを定義し、書き込み専用プロパティでは `Set` のみを定義します。</span><span class="sxs-lookup"><span data-stu-id="42285-108">For a read-only property, you define only `Get`, and for a write-only property, you define only `Set`.</span></span>  
  
### <a name="to-create-a-property"></a><span data-ttu-id="42285-109">プロパティを作成するには</span><span class="sxs-lookup"><span data-stu-id="42285-109">To create a property</span></span>  
  
1. <span data-ttu-id="42285-110">任意のプロパティまたはプロシージャの外部で、[ Property ステートメント ](../../../language-reference/statements/property-statement.md) を使用し、その後に `End Property` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="42285-110">Outside any property or procedure, use a [Property Statement](../../../language-reference/statements/property-statement.md), followed by an `End Property` statement.</span></span>  
  
2. <span data-ttu-id="42285-111">プロパティがパラメーターを受け取る場合は、`Property` キーワードの後にプロシージャの名前を指定し、その後にかっこで囲んだパラメーター リストを指定します。</span><span class="sxs-lookup"><span data-stu-id="42285-111">If the property takes parameters, follow the `Property` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="42285-112">かっこの後に `As` 句を入力して、プロパティの値のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="42285-112">Follow the parentheses with an `As` clause to specify the data type of the property's value.</span></span> <span data-ttu-id="42285-113">書き込み専用プロパティでもデータ型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42285-113">You must specify the data type even for a write-only property.</span></span>  
  
4. <span data-ttu-id="42285-114">必要に応じて、`Get` および `Set` プロシージャを追加します。</span><span class="sxs-lookup"><span data-stu-id="42285-114">Add `Get` and `Set` procedures, as appropriate.</span></span> <span data-ttu-id="42285-115">以降の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42285-115">See the following directions.</span></span>  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a><span data-ttu-id="42285-116">プロパティ値を取得する Get プロシージャを作成するには</span><span class="sxs-lookup"><span data-stu-id="42285-116">To create a Get procedure that retrieves a property value</span></span>  
  
1. <span data-ttu-id="42285-117">`Property` ステートメントと `End Property` ステートメントの間に、[Get ステートメント](../../../language-reference/statements/get-statement.md)を記述し、その後に `End Get` ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="42285-117">Between the `Property` and `End Property` statements, write a [Get Statement](../../../language-reference/statements/get-statement.md), followed by an `End Get` statement.</span></span> <span data-ttu-id="42285-118">`Get` プロシージャのパラメーターを定義する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="42285-118">You do not need to define any parameters for the `Get` procedure.</span></span>  
  
2. <span data-ttu-id="42285-119">`Get` ステートメントと `End Get` ステートメントの間に、プロパティの値を取得するコード ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="42285-119">Place the code statements to retrieve the property's value between the `Get` and `End Get` statements.</span></span> <span data-ttu-id="42285-120">このコードでは、プロパティの値を生成して返すだけでなく、他の計算やデータ操作も含めることができます。</span><span class="sxs-lookup"><span data-stu-id="42285-120">This code can include other calculations and data manipulations in addition to generating and returning the property's value.</span></span>  
  
3. <span data-ttu-id="42285-121">`Return` ステートメントを使用して、プロパティの値を呼び出し元のコードに返します。</span><span class="sxs-lookup"><span data-stu-id="42285-121">Use a `Return` statement to return the property's value to the calling code.</span></span>  
  
 <span data-ttu-id="42285-122">読み取り/書き込みプロパティと読み取り専用プロパティの `Get` プロシージャを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42285-122">You must write a `Get` procedure for a read-write property and for a read-only property.</span></span> <span data-ttu-id="42285-123">書き込み専用プロパティの `Get` プロシージャを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="42285-123">You must not define a `Get` procedure for a write-only property.</span></span>  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a><span data-ttu-id="42285-124">プロパティの値を書き込む Set プロシージャを作成するには</span><span class="sxs-lookup"><span data-stu-id="42285-124">To create a Set procedure that writes a property's value</span></span>  
  
1. <span data-ttu-id="42285-125">`Property` ステートメントと `End Property` ステートメントの間に、[Set ステートメント](../../../language-reference/statements/set-statement.md)を記述し、その後に `End Set` ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="42285-125">Between the `Property` and `End Property` statements, write a [Set Statement](../../../language-reference/statements/set-statement.md), followed by an `End Set` statement.</span></span>  
  
2. <span data-ttu-id="42285-126">`Set` ステートメントで、`Set` キーワードの後に、かっこで囲まれたパラメーター リストを指定します。</span><span class="sxs-lookup"><span data-stu-id="42285-126">In the `Set` statement, follow the `Set` keyword with a parameter list in parentheses.</span></span> <span data-ttu-id="42285-127">このパラメーター リストには、呼び出し元のコードから渡される値の値パラメーターが少なくとも含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="42285-127">This parameter list must include at least a value parameter for the value passed by the calling code.</span></span> <span data-ttu-id="42285-128">この値パラメーターの既定の名前は `Value` ですが、必要に応じて別の名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="42285-128">The default name for this value parameter is `Value`, but you can use a different name if appropriate.</span></span> <span data-ttu-id="42285-129">値パラメーターは、プロパティ自体と同じデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="42285-129">The value parameter must have the same data type as the property itself.</span></span>  
  
3. <span data-ttu-id="42285-130">`Set` ステートメントと `End Set` ステートメントの間に、プロパティに値を格納するコード ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="42285-130">Place the code statements to store a value in the property between the `Set` and `End Set` statements.</span></span> <span data-ttu-id="42285-131">このコードでは、プロパティの値を検証して格納するだけでなく、他の計算やデータ操作も含めることができます。</span><span class="sxs-lookup"><span data-stu-id="42285-131">This code can include other calculations and data manipulations in addition to validating and storing the property's value.</span></span>  
  
4. <span data-ttu-id="42285-132">値パラメーターを使用して、呼び出し元のコードで指定された値を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="42285-132">Use the value parameter to accept the value supplied by the calling code.</span></span> <span data-ttu-id="42285-133">この値は、代入ステートメントで直接格納することも、式で使用して格納する内部値を計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="42285-133">You can either store this value directly in an assignment statement, or use it in an expression to calculate the internal value to be stored.</span></span>  
  
 <span data-ttu-id="42285-134">読み取り/書き込みプロパティと書き込み専用プロパティの `Set` プロシージャを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42285-134">You must write a `Set` procedure for a read-write property and for a write-only property.</span></span> <span data-ttu-id="42285-135">読み取り専用プロパティの `Set` プロシージャを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="42285-135">You must not define a `Set` procedure for a read-only property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42285-136">例</span><span class="sxs-lookup"><span data-stu-id="42285-136">Example</span></span>  
 <span data-ttu-id="42285-137">次の例では、フル ネームを 2 つの構成要素名 (名と姓) として格納する読み取り/書き込みプロパティを作成します。</span><span class="sxs-lookup"><span data-stu-id="42285-137">The following example creates a read/write property that stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="42285-138">呼び出し元のコードが `fullName` を読み取ると、`Get` プロシージャが 2 つの構成要素名を結合し、フル ネームを返します。</span><span class="sxs-lookup"><span data-stu-id="42285-138">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="42285-139">呼び出し元のコードが新しいフル ネームを割り当てると、`Set` プロシージャがそれを 2 つの構成要素名に分割することを試みます。</span><span class="sxs-lookup"><span data-stu-id="42285-139">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="42285-140">スペースが見つからない場合は、すべてが名として格納されます。</span><span class="sxs-lookup"><span data-stu-id="42285-140">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="42285-141">次の例は、`fullName` のプロパティ プロシージャの一般的な呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="42285-141">The following example shows typical calls to the property procedures of `fullName`.</span></span> <span data-ttu-id="42285-142">最初の呼び出しではプロパティ値を設定し、2 番目の呼び出しではそれを取得します。</span><span class="sxs-lookup"><span data-stu-id="42285-142">The first call sets the property value and the second call retrieves it.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="42285-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="42285-143">See also</span></span>

- [<span data-ttu-id="42285-144">手順</span><span class="sxs-lookup"><span data-stu-id="42285-144">Procedures</span></span>](./index.md)
- [<span data-ttu-id="42285-145">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="42285-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="42285-146">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="42285-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="42285-147">Visual Basic のプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="42285-147">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="42285-148">方法: 複数のアクセス レベルを持つプロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="42285-148">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="42285-149">方法: プロパティ プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="42285-149">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="42285-150">方法: 既定のプロパティを宣言して呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42285-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="42285-151">方法: プロパティに値を格納する</span><span class="sxs-lookup"><span data-stu-id="42285-151">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="42285-152">方法: プロパティから値を取得する</span><span class="sxs-lookup"><span data-stu-id="42285-152">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
