---
title: 事前バインディングと遅延バインディング
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: ce74498225fb7947c92f2f4f61ec46e6b2594151
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086011"
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="218af-102">事前バインディングと遅延バインディング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="218af-102">Early and Late Binding (Visual Basic)</span></span>

<span data-ttu-id="218af-103">Visual Basic コンパイラは、オブジェクトがオブジェクト変数に代入されるときに `binding` と呼ばれる処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="218af-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="218af-104">オブジェクトが特定のオブジェクト型として宣言された変数に代入される場合、オブジェクトは*事前バインディング*されます。</span><span class="sxs-lookup"><span data-stu-id="218af-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="218af-105">事前バインディングされたオブジェクトを使用すると、コンパイラは、アプリケーションを実行する前に、メモリの割り当てとその他の最適化を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="218af-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="218af-106">たとえば、次のコードは、<xref:System.IO.FileStream> 型の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="218af-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <span data-ttu-id="218af-107"><xref:System.IO.FileStream> は特定のオブジェクト型であるため、`FS` に代入されるインスタンスは事前バインディングされます。</span><span class="sxs-lookup"><span data-stu-id="218af-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="218af-108">対照的に、オブジェクトが `Object` 型として宣言された変数に代入される場合、オブジェクトは*遅延バインディング*されます。</span><span class="sxs-lookup"><span data-stu-id="218af-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="218af-109">この型のオブジェクトは、任意のオブジェクトへの参照を保持できますが、事前バインディングされたオブジェクトが持っている多くの利点を欠いています。</span><span class="sxs-lookup"><span data-stu-id="218af-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="218af-110">たとえば、次のコードは、`CreateObject` 関数によって返されたオブジェクトを保持するオブジェクト変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="218af-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="218af-111">事前バインディングの利点</span><span class="sxs-lookup"><span data-stu-id="218af-111">Advantages of Early Binding</span></span>  

 <span data-ttu-id="218af-112">コンパイラが効率の高いアプリケーションを生成するための重要な最適化を行うことができるため、可能であれば、事前バインディングされたオブジェクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="218af-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="218af-113">事前バインディングされたオブジェクトは遅延バインディング オブジェクトよりもはるかに高速であり、使用されるオブジェクトの種類を正確に記述することでコードを読みやすくして管理を容易にします。</span><span class="sxs-lookup"><span data-stu-id="218af-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="218af-114">事前バインディングのもう 1 つの利点は、自動コード補完機能やダイナミック ヘルプなどの便利な機能を有効にできることです。これは、Visual Basic 統合開発環境 (IDE) では、コードの編集時に作業中のオブジェクトの種類を正確に判断できるためです。</span><span class="sxs-lookup"><span data-stu-id="218af-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="218af-115">事前バインディングを使用すると、コンパイラがプログラムのコンパイル時にエラーを報告できるため、ランタイム エラーの数が減少し、重大度が低下します。</span><span class="sxs-lookup"><span data-stu-id="218af-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="218af-116">遅延バインディングは、`Public` として宣言されている型メンバーにアクセスするためにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="218af-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="218af-117">`Friend` または `Protected Friend` として宣言されているメンバーにアクセスすると、ランタイム エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="218af-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="218af-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="218af-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="218af-119">オブジェクトの有効期間:オブジェクトの作成と破棄</span><span class="sxs-lookup"><span data-stu-id="218af-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="218af-120">Object 型</span><span class="sxs-lookup"><span data-stu-id="218af-120">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
