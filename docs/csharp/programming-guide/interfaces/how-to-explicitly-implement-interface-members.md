---
title: インターフェイス メンバーを明示的に実装する方法 - C# プログラミング ガイド
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: d006db2a7501a3273f5cd11e82bc589b21e1ce9f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712092"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="b7362-102">インターフェイス メンバーを明示的に実装する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b7362-102">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="b7362-103">この例では[インターフェイス](../../language-reference/keywords/interface.md)、`IDimensions`、およびクラス `Box` を宣言します。これは、インターフェイス メンバーの `getLength` と `getWidth` を明示的に実装します。</span><span class="sxs-lookup"><span data-stu-id="b7362-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="b7362-104">メンバーには、インターフェイス インスタンス `dimensions` を介してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="b7362-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7362-105">例</span><span class="sxs-lookup"><span data-stu-id="b7362-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b7362-106">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="b7362-106">Robust Programming</span></span>  
  
- <span data-ttu-id="b7362-107">`Main` メソッドでは、次の行はコメントアウトされます。これらの行でコンパイル エラーが発生するためです。</span><span class="sxs-lookup"><span data-stu-id="b7362-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="b7362-108">明示的に実装されるインターフェイス メンバーに、[クラス](../../language-reference/keywords/class.md) インスタンスからアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b7362-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="b7362-109">`Main` メソッドの以下の行では、メソッドがインターフェイスのインスタンスから呼び出されるため、ボックスのサイズを正常に出力できます。</span><span class="sxs-lookup"><span data-stu-id="b7362-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="b7362-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7362-110">See also</span></span>

- [<span data-ttu-id="b7362-111">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b7362-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b7362-112">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="b7362-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="b7362-113">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7362-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="b7362-114">2 つのインターフェイスのメンバーを明示的に実装する方法</span><span class="sxs-lookup"><span data-stu-id="b7362-114">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
