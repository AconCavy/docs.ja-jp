---
title: COM クラスの例 - C# プログラミング ガイド
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 6af85d0314a44acbde0996cecbe6dad82cdcc8db
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712079"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="6d9d7-102">COM クラスの例 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="6d9d7-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="6d9d7-103">ここでは、COM オブジェクトとして公開されるクラスの例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="6d9d7-104">このコードを .cs ファイルに保存して、プロジェクトに追加したあと、 **[COM の相互運用機能に登録]** プロパティを **[True]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="6d9d7-105">詳細については、[コンポーネントを COM 相互運用機能に登録する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100))」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-105">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="6d9d7-106">Visual C# オブジェクトを COM に公開するには、クラス インターフェイス、イベント インターフェイス (必要な場合)、クラス自体を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="6d9d7-107">クラスのメンバーを COM で参照するには、次の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-107">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="6d9d7-108">クラスはパブリックであること。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-108">The class must be public.</span></span>  
  
- <span data-ttu-id="6d9d7-109">プロパティ、メソッド、およびイベントがパブリックであること。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-109">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="6d9d7-110">プロパティとメソッドがクラス インターフェイスで宣言されていること。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-110">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="6d9d7-111">イベントがイベント インターフェイスで宣言されていること。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="6d9d7-112">これらのインターフェイスで宣言されていない、クラス内の他のパブリック メンバーは、COM から参照されませんが、他の .NET Framework オブジェクトからは参照されます。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="6d9d7-113">プロパティとメソッドを COM に公開するには、それらをクラス インターフェイスで宣言し、`DispId` 属性でマークを付けて、クラスに実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="6d9d7-114">メンバーをインターフェイスで宣言する順序は、COM vtable で使用される順序になります。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="6d9d7-115">クラスのイベントを公開するには、それらをイベント インターフェイスで宣言し、`DispId` 属性でマークを付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="6d9d7-116">クラスでこのインターフェイスを実装しないでください。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="6d9d7-117">クラスでは、クラス インターフェイスが実装されます。複数のインターフェイスを実装できますが、最初に実装されるのは、既定のクラス インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="6d9d7-118">ここで、COM に対して公開するプロパティとメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="6d9d7-119">プロパティとメソッドは、パブリックとしてマークされており、クラス インターフェイスの宣言と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="6d9d7-120">また、ここでクラスから発生するイベントを宣言します。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="6d9d7-121">イベントは、パブリックとしてマークされており、イベント インターフェイスの宣言と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9d7-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d9d7-122">例</span><span class="sxs-lookup"><span data-stu-id="6d9d7-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="6d9d7-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d9d7-123">See also</span></span>

- [<span data-ttu-id="6d9d7-124">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="6d9d7-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6d9d7-125">相互運用性</span><span class="sxs-lookup"><span data-stu-id="6d9d7-125">Interoperability</span></span>](./index.md)
- <span data-ttu-id="6d9d7-126">[[ビルド] ページ (プロジェクト デザイナー) (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)</span><span class="sxs-lookup"><span data-stu-id="6d9d7-126">[Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)</span></span>
