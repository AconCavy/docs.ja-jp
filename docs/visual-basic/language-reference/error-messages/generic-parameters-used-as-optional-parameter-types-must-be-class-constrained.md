---
title: 省略可能なパラメーター型として使用されるジェネリック パラメーターは、クラスの制約がある型でなければなりません。
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 11cf4f8d9457ebff385a601786dc97334f274324
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662068"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="7ff59-102">省略可能なパラメーター型として使用されるジェネリック パラメーターは、クラスの制約がある型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="7ff59-102">Generic parameters used as optional parameter types must be class constrained</span></span>
<span data-ttu-id="7ff59-103">プロシージャは、参照型に制限されていない型パラメーターを使用する省略可能なパラメーターで、宣言します。</span><span class="sxs-lookup"><span data-stu-id="7ff59-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="7ff59-104">省略可能な各パラメーターには、常に既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ff59-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="7ff59-105">パラメーターが参照型の場合、省略可能な値は `Nothing` である必要があります。これはすべての参照型に有効な値です。</span><span class="sxs-lookup"><span data-stu-id="7ff59-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="7ff59-106">ただし、パラメーターが値型の場合、その型は Visual Basic によって事前に定義された基本データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ff59-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="7ff59-107">これは、ユーザー定義構造体などの複合値型に有効な既定値がないためです。</span><span class="sxs-lookup"><span data-stu-id="7ff59-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="7ff59-108">省略可能なパラメーターに型パラメーターを使用する場合は、有効な既定値を持たない値型の可能性を回避するために、それが参照型であることを保証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ff59-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="7ff59-109">つまり、`Class` キーワードまたは特定のクラスの名前のいずれかによって、型パラメーターを制約する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ff59-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="7ff59-110">**エラー ID:** BC32124</span><span class="sxs-lookup"><span data-stu-id="7ff59-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7ff59-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="7ff59-111">To correct this error</span></span>  
  
- <span data-ttu-id="7ff59-112">参照型のみを受け入れるように型パラメーターを制約するか、または省略可能なパラメーターにそれを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7ff59-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff59-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ff59-113">See also</span></span>

- [<span data-ttu-id="7ff59-114">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ff59-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="7ff59-115">型リスト</span><span class="sxs-lookup"><span data-stu-id="7ff59-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="7ff59-116">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="7ff59-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="7ff59-117">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="7ff59-117">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="7ff59-118">構造体</span><span class="sxs-lookup"><span data-stu-id="7ff59-118">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="7ff59-119">Nothing</span><span class="sxs-lookup"><span data-stu-id="7ff59-119">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
