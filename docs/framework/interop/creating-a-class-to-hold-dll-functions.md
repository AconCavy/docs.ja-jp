---
title: DLL 関数を保持するクラスの作成
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
ms.openlocfilehash: 765d4344553a6e65b930a7bf586a41144d220fc6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123621"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="ba29b-102">DLL 関数を保持するクラスの作成</span><span class="sxs-lookup"><span data-stu-id="ba29b-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="ba29b-103">マネージド クラス内の頻繁に使用される DLL 関数をラップすることは、プラットフォームの機能をカプセル化するための効果的な方法です。</span><span class="sxs-lookup"><span data-stu-id="ba29b-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="ba29b-104">これはすべてのケースで必須であるわけではありませんが、DLL 関数の定義には手間がかかり、エラーが発生しやすくなるため、クラス ラッパーを用意しておくと便利です。</span><span class="sxs-lookup"><span data-stu-id="ba29b-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="ba29b-105">Visual Basic や C# でプログラミングしている場合は、DLL 関数をクラスまたは Visual Basic モジュール内で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba29b-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="ba29b-106">クラス内では、呼び出す DLL 関数ごとに静的メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="ba29b-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="ba29b-107">この定義には、メソッド引数を渡すときに使用される呼び出し規則や文字セットなどの追加情報を含めることができます。この情報を省略すると、既定の設定が選択されます。</span><span class="sxs-lookup"><span data-stu-id="ba29b-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="ba29b-108">宣言のオプションと、既定の設定の完全なリストについては、「[Creating Prototypes in Managed Code](creating-prototypes-in-managed-code.md)」(マネージド コードでのプロトタイプの作成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba29b-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="ba29b-109">ラッピングが完了すると、他のクラスで静的メソッドを呼び出す場合と同じように、クラスでメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ba29b-109">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="ba29b-110">プラットフォーム呼び出しでは、基になるエクスポートされた関数が自動的に処理されます。</span><span class="sxs-lookup"><span data-stu-id="ba29b-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="ba29b-111">プラットフォーム呼び出しのためにマネージド クラスをデザインする場合は、クラスと DLL 関数との関係を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="ba29b-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="ba29b-112">たとえば、次のように操作できます。</span><span class="sxs-lookup"><span data-stu-id="ba29b-112">For example, you can:</span></span>  
  
- <span data-ttu-id="ba29b-113">既存のクラス内で DLL 関数を宣言する。</span><span class="sxs-lookup"><span data-stu-id="ba29b-113">Declare DLL functions within an existing class.</span></span>  
  
- <span data-ttu-id="ba29b-114">関数を分離し、検索しやすくするために、DLL 関数ごとに別のクラスを作成する。</span><span class="sxs-lookup"><span data-stu-id="ba29b-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
- <span data-ttu-id="ba29b-115">論理的なグループを形成し、オーバーヘッドを減らすため、一連の関連する DLL 関数に対して 1 つのクラスを作成する。</span><span class="sxs-lookup"><span data-stu-id="ba29b-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="ba29b-116">クラスおよびそのメソッドには、任意の名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="ba29b-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="ba29b-117">プラットフォーム呼び出しで使用する .NET ベースの宣言を作成する方法を示す例については、「[プラットフォーム呼び出しによるデータのマーシャリング](marshaling-data-with-platform-invoke.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba29b-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba29b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba29b-118">See also</span></span>

- [<span data-ttu-id="ba29b-119">アンマネージ DLL 関数の処理</span><span class="sxs-lookup"><span data-stu-id="ba29b-119">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="ba29b-120">DLL 内の関数の識別</span><span class="sxs-lookup"><span data-stu-id="ba29b-120">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="ba29b-121">マネージド コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="ba29b-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="ba29b-122">DLL 関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="ba29b-122">Calling a DLL Function</span></span>](calling-a-dll-function.md)
