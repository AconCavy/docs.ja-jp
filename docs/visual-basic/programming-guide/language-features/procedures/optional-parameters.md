---
title: 省略可能なパラメーター
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
ms.openlocfilehash: 4e07b75c94b4aea681e6e862e161bda80b2833fc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364332"
---
# <a name="optional-parameters-visual-basic"></a><span data-ttu-id="6f143-102">省略可能なパラメーター (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f143-102">Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="6f143-103">プロシージャのパラメーターを省略可能にすると、呼び出し時に引数を指定する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="6f143-103">You can specify that a procedure parameter is optional and no argument has to be supplied for it when the procedure is called.</span></span> <span data-ttu-id="6f143-104">"*省略可能なパラメーター*" は、プロシージャ定義で `Optional` キーワードによって示されます。</span><span class="sxs-lookup"><span data-stu-id="6f143-104">*Optional parameters* are indicated by the `Optional` keyword in the procedure definition.</span></span> <span data-ttu-id="6f143-105">次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="6f143-105">The following rules apply:</span></span>  
  
- <span data-ttu-id="6f143-106">プロシージャ定義のすべての省略可能なパラメーターについて、既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f143-106">Every optional parameter in the procedure definition must specify a default value.</span></span>  
  
- <span data-ttu-id="6f143-107">省略可能なパラメーターの既定値には、定数式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f143-107">The default value for an optional parameter must be a constant expression.</span></span>  
  
- <span data-ttu-id="6f143-108">プロシージャ定義で省略可能なパラメーターの後に続くパラメーターは、すべて省略可能であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="6f143-108">Every parameter following an optional parameter in the procedure definition must also be optional.</span></span>  
  
 <span data-ttu-id="6f143-109">次の構文は、省略可能なパラメーターを含むプロシージャ宣言を示しています。</span><span class="sxs-lookup"><span data-stu-id="6f143-109">The following syntax shows a procedure declaration with an optional parameter:</span></span>  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a><span data-ttu-id="6f143-110">省略可能なパラメーターを使ったプロシージャ呼び出し</span><span class="sxs-lookup"><span data-stu-id="6f143-110">Calling Procedures with Optional Parameters</span></span>  
 <span data-ttu-id="6f143-111">省略可能なパラメーターを使ってプロシージャを呼び出すときには、引数を指定するかどうかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="6f143-111">When you call a procedure with an optional parameter, you can choose whether to supply the argument.</span></span> <span data-ttu-id="6f143-112">引数を指定しない場合は、そのパラメーターに対して宣言されている既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6f143-112">If you do not, the procedure uses the default value declared for that parameter.</span></span>  
  
 <span data-ttu-id="6f143-113">引数リストで省略可能な引数を省略する場合は、コンマを続けて、省略する引数の位置を表します。</span><span class="sxs-lookup"><span data-stu-id="6f143-113">When you omit one or more optional arguments in the argument list, you use successive commas to mark their positions.</span></span> <span data-ttu-id="6f143-114">次の例では、1 番目と 4 番目の引数は指定されていますが、2 番目と 3 番目の引数は省略されています。</span><span class="sxs-lookup"><span data-stu-id="6f143-114">The following example call supplies the first and fourth arguments but not the second or third:</span></span>  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 <span data-ttu-id="6f143-115">次の例では、`MsgBox` 関数を数回呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6f143-115">The following example makes several calls to the `MsgBox` function.</span></span> <span data-ttu-id="6f143-116">`MsgBox` には、必須パラメーター 1 つと省略可能なパラメーターが 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="6f143-116">`MsgBox` has one required parameter and two optional parameters.</span></span>  
  
 <span data-ttu-id="6f143-117">`MsgBox` の最初の呼び出しでは、`MsgBox` で定義された順番で 3 つの引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f143-117">The first call to `MsgBox` supplies all three arguments in the order that `MsgBox` defines them.</span></span> <span data-ttu-id="6f143-118">2 番目の呼び出しでは、必須の引数だけを指定します。</span><span class="sxs-lookup"><span data-stu-id="6f143-118">The second call supplies only the required argument.</span></span> <span data-ttu-id="6f143-119">3 番目と 4 番目の呼び出しでは、1 つ目と 3 つ目の引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f143-119">The third and fourth calls supply the first and third arguments.</span></span> <span data-ttu-id="6f143-120">3 番目の呼び出しでは引数を位置で指定し、4 番目の呼び出しでは引数を名前で指定します。</span><span class="sxs-lookup"><span data-stu-id="6f143-120">The third call does this by position, and the fourth call does it by name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#47)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a><span data-ttu-id="6f143-121">省略可能な引数があるかどうかの確認</span><span class="sxs-lookup"><span data-stu-id="6f143-121">Determining Whether an Optional Argument Is Present</span></span>  
 <span data-ttu-id="6f143-122">引数が省略されているのか、呼び出し元のコードで既定値が明示的に指定されているのかについて、プロシージャで実行時に検出することはできません。</span><span class="sxs-lookup"><span data-stu-id="6f143-122">A procedure cannot detect at run time whether a given argument has been omitted or the calling code has explicitly supplied the default value.</span></span> <span data-ttu-id="6f143-123">この区別が必要な場合は、ありそうにない値を既定値に設定します。</span><span class="sxs-lookup"><span data-stu-id="6f143-123">If you need to make this distinction, you can set an unlikely value as the default.</span></span> <span data-ttu-id="6f143-124">次のプロシージャでは、省略可能なパラメーター `office` を定義し、その既定値 `QJZ` をテストして、呼び出しで省略されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="6f143-124">The following procedure defines the optional parameter `office`, and tests for its default value, `QJZ`, to see if it has been omitted in the call:</span></span>  
  
 [!code-vb[VbVbcnProcedures#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#46)]  
  
 <span data-ttu-id="6f143-125">省略可能なパラメーターが `String` などの参照型の場合は、`Nothing` を既定値として使用できます。ただし、 が引数の値として使用されることが予想される場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="6f143-125">If the optional parameter is a reference type such as a `String`, you can use `Nothing` as the default value, provided this is not an expected value for the argument.</span></span>  
  
## <a name="optional-parameters-and-overloading"></a><span data-ttu-id="6f143-126">省略可能なパラメーターとオーバーロード</span><span class="sxs-lookup"><span data-stu-id="6f143-126">Optional Parameters and Overloading</span></span>  
 <span data-ttu-id="6f143-127">省略可能なパラメーターを持つプロシージャを定義するには、オーバーロードを使用する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="6f143-127">Another way to define a procedure with optional parameters is to use overloading.</span></span> <span data-ttu-id="6f143-128">省略可能なパラメーターが 1 つあるとすると、パラメーターを受け取る場合と受け取らない場合の、2 つのオーバーロードされたバージョンのプロシージャを定義できます。</span><span class="sxs-lookup"><span data-stu-id="6f143-128">If you have one optional parameter, you can define two overloaded versions of the procedure, one accepting the parameter and one without it.</span></span> <span data-ttu-id="6f143-129">この方法は、省略可能なパラメーターの数が増えるにつれて複雑になります。</span><span class="sxs-lookup"><span data-stu-id="6f143-129">This approach becomes more complicated as the number of optional parameters increases.</span></span> <span data-ttu-id="6f143-130">しかし、それぞれの省略可能な引数が呼び出しプログラムによって指定されているかどうかを確実に把握できるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="6f143-130">However, its advantage is that you can be absolutely sure whether the calling program supplied each optional argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f143-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f143-131">See also</span></span>

- [<span data-ttu-id="6f143-132">手順</span><span class="sxs-lookup"><span data-stu-id="6f143-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="6f143-133">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="6f143-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6f143-134">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="6f143-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="6f143-135">位置と名前による引数渡し</span><span class="sxs-lookup"><span data-stu-id="6f143-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="6f143-136">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="6f143-136">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="6f143-137">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="6f143-137">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="6f143-138">Optional</span><span class="sxs-lookup"><span data-stu-id="6f143-138">Optional</span></span>](../../../language-reference/modifiers/optional.md)
- [<span data-ttu-id="6f143-139">ParamArray</span><span class="sxs-lookup"><span data-stu-id="6f143-139">ParamArray</span></span>](../../../language-reference/modifiers/paramarray.md)
