---
title: DLL 関数の呼び出し
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
ms.openlocfilehash: 14589544e05f6c59f4f58f7723fef40e75af9823
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123712"
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="15cd7-102">DLL 関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="15cd7-102">Calling a DLL Function</span></span>
<span data-ttu-id="15cd7-103">アンマネージド DLL 関数の呼び出しは、他のマネージド コードの呼び出しとほとんど同じですが、最初のうちは DLL 関数がわかりづらいと感じる違いがあります。</span><span class="sxs-lookup"><span data-stu-id="15cd7-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="15cd7-104">ここでは、通常とは異なる呼び出しに関連するいくつかの問題について説明しているトピックを紹介します。</span><span class="sxs-lookup"><span data-stu-id="15cd7-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="15cd7-105">プラットフォーム呼び出しから返される構造体は、マネージド コードとアンマネージド コードで同じ表現のデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="15cd7-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="15cd7-106">このような型のことは *blittable 型*と呼ばれます。これは、会話が必要ではないためです (「[Blittable and Non-Blittable Types](blittable-and-non-blittable-types.md)」(blittable 型と非 blittable 型) を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="15cd7-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="15cd7-107">戻り値の型が非 blittable 構造体の関数を呼び出すには、非 blittable 型と同じサイズの blittable ヘルパー型を定義し、関数からデータが返された後にそのデータを変換します。</span><span class="sxs-lookup"><span data-stu-id="15cd7-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15cd7-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="15cd7-108">In This Section</span></span>  
 [<span data-ttu-id="15cd7-109">構造体の受け渡し</span><span class="sxs-lookup"><span data-stu-id="15cd7-109">Passing Structures</span></span>](passing-structures.md)  
 <span data-ttu-id="15cd7-110">事前に定義されたレイアウトを使用して、データ構造体の受け渡しに関する問題を特定します。</span><span class="sxs-lookup"><span data-stu-id="15cd7-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="15cd7-111">コールバック関数</span><span class="sxs-lookup"><span data-stu-id="15cd7-111">Callback Functions</span></span>](callback-functions.md)  
 <span data-ttu-id="15cd7-112">コールバック関数に関する基本情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="15cd7-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="15cd7-113">方法: コールバック関数を実装する</span><span class="sxs-lookup"><span data-stu-id="15cd7-113">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)  
 <span data-ttu-id="15cd7-114">マネージド コードにコールバック関数を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="15cd7-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="15cd7-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="15cd7-115">Related Sections</span></span>  
 [<span data-ttu-id="15cd7-116">アンマネージ DLL 関数の処理</span><span class="sxs-lookup"><span data-stu-id="15cd7-116">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="15cd7-117">プラットフォーム呼び出しを使用して、アンマネージ DLL 関数を呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="15cd7-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="15cd7-118">プラットフォーム呼び出しによるデータのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="15cd7-118">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="15cd7-119">メソッドのパラメーターを宣言してアンマネージ ライブラリによってエクスポートされた関数に引数を渡す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="15cd7-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
