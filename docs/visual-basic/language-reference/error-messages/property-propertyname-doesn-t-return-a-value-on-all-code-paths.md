---
title: プロパティ '<propertyname>' は、すべてのコードのパスでは値を返しません。
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 21a1c4dbab6e26cd1cb848e270bbda9a544c2a67
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400423"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="8e6d5-102">プロパティ '\<propertyname>' は、すべてのコードのパスでは値を返しません。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-102">Property '\<propertyname>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="8e6d5-103">プロパティ '\<propertyname>' は、すべてのコードのパスでは値を返しません。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="8e6d5-104">この結果が使用されると、実行時に Null 参照例外が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="8e6d5-105">プロパティ `Get` プロシージャのコードには、値を返さないパスが少なくとも 1 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="8e6d5-106">次のいずれかの方法で、プロパティ `Get` プロシージャから値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="8e6d5-107">プロパティ名に値を代入して、`Exit Property` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
- <span data-ttu-id="8e6d5-108">プロパティ名に値を代入して、`End Get` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
- <span data-ttu-id="8e6d5-109">[return ステートメント](../statements/return-statement.md)に値を含めます。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-109">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="8e6d5-110">制御が `Exit Property` または `End Get` に渡され、プロパティ名に何も値を代入していない場合、`Get` プロシージャでは、プロパティのデータ型の既定値が返されます。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="8e6d5-111">詳細については、「[Function ステートメント](../statements/function-statement.md)」の "動作" に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="8e6d5-112">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-112">By default, this message is a warning.</span></span> <span data-ttu-id="8e6d5-113">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="8e6d5-114">**エラー ID:** BC42107</span><span class="sxs-lookup"><span data-stu-id="8e6d5-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8e6d5-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8e6d5-115">To correct this error</span></span>  
  
- <span data-ttu-id="8e6d5-116">制御フロー ロジックをチェックし、戻り値を返すすべてのステートメントの前に値を代入してください。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="8e6d5-117">常に `Return` ステートメントを使用すれば、プロシージャからのすべての戻り値で、値が返されることを簡単に保証できます。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="8e6d5-118">これを実行する場合、`End Get` の前の最後のステートメントは、`Return` ステートメントでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="8e6d5-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e6d5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e6d5-119">See also</span></span>

- [<span data-ttu-id="8e6d5-120">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="8e6d5-120">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="8e6d5-121">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="8e6d5-121">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="8e6d5-122">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="8e6d5-122">Get Statement</span></span>](../statements/get-statement.md)
