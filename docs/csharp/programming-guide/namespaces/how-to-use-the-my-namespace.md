---
title: My 名前空間を使用する方法 - C# プログラミング ガイド
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 268543980ba891b0b30f393ee8982f2863ba9a71
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241943"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="639d2-102">My 名前空間を使用する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="639d2-102">How to use the My namespace (C# Programming Guide)</span></span>

<span data-ttu-id="639d2-103"><xref:Microsoft.VisualBasic.MyServices> 名前空間 (Visual Basic では `My`) を使用すると、いくつもの .NET クラスに簡単かつ直感的にアクセスでき、コンピューター、アプリケーション、設定、リソースなどと対話するコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="639d2-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="639d2-104">`MyServices` 名前空間は、もともとは Visual Basic で使用するものとして設計されましたが、C# アプリケーションでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="639d2-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="639d2-105">Visual Basic で `MyServices` 名前空間を使用する方法の詳細については、[My を使用した開発](../../../visual-basic/developing-apps/development-with-my/index.md) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="639d2-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="add-a-reference"></a><span data-ttu-id="639d2-106">参照を追加する</span><span class="sxs-lookup"><span data-stu-id="639d2-106">Add a reference</span></span>

 <span data-ttu-id="639d2-107">`MyServices` クラスをソリューションで使用する前に、Visual Basic ライブラリへの参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="639d2-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
### <a name="add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="639d2-108">Visual Basic ライブラリへの参照を追加する</span><span class="sxs-lookup"><span data-stu-id="639d2-108">Add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="639d2-109">**ソリューション エクスプローラー**で、 **[参照設定]** ノードを右クリックし、 **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="639d2-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="639d2-110">**[参照設定]** ダイアログ ボックスが表示されたら、一覧を下にスクロールし、Microsoft.VisualBasic.dll を選択します。</span><span class="sxs-lookup"><span data-stu-id="639d2-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="639d2-111">プログラムの先頭の `using` セクションに次の行を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="639d2-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="639d2-112">例</span><span class="sxs-lookup"><span data-stu-id="639d2-112">Example</span></span>  
 <span data-ttu-id="639d2-113">次の例では、`MyServices` 名前空間に含まれているさまざまな静的メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="639d2-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="639d2-114">このコードをコンパイルするには、Microsoft.VisualBasic.DLL への参照をプロジェクトに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="639d2-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="639d2-115">`MyServices` 名前空間のクラスの中には C# アプリケーションから呼び出すことができないクラスもあります。たとえば、<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> クラスは、C# と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="639d2-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="639d2-116">そのような場合は、同様に VisualBasic.dll に含まれている <xref:Microsoft.VisualBasic.FileIO.FileSystem> を構成する静的メソッドを代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="639d2-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="639d2-117">このようなメソッドを使用してディレクトリを複製する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="639d2-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="639d2-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="639d2-118">See also</span></span>

- [<span data-ttu-id="639d2-119">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="639d2-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="639d2-120">名前空間</span><span class="sxs-lookup"><span data-stu-id="639d2-120">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="639d2-121">名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="639d2-121">Using Namespaces</span></span>](./using-namespaces.md)
