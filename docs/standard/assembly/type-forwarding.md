---
title: 共通言語ランタイムでの型の転送
description: 型の転送を使用すると、別の .NET アセンブリに型を移動する際に、元のアセンブリを使用するアプリケーションを再コンパイルする必要がありません。
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: f0be61bd4ce88569e22a350a9ea9490d67e74ff3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378592"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="cdbc1-103">共通言語ランタイムでの型の転送</span><span class="sxs-lookup"><span data-stu-id="cdbc1-103">Type forwarding in the common language runtime</span></span>
<span data-ttu-id="cdbc1-104">型の転送を使用すると、別のアセンブリに型を移動する際に、元のアセンブリを使用するアプリケーションを再コンパイルする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-104">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="cdbc1-105">たとえば、*Utility.dll* というアセンブリ内の `Example` クラスをアプリケーションが使用しているとします。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-105">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll*.</span></span> <span data-ttu-id="cdbc1-106">その場合、*Utility.dll* の開発者がアセンブリをリファクタリングすることになった際には、その過程で `Example` クラスが別のアセンブリに移動される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-106">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="cdbc1-107">*Utility.dll* の旧バージョンが *Utility.dll* の新バージョンとそのコンパニオン アセンブリに置き換えられると、`Example` クラスを使用するアプリケーションは、新しいバージョンの *Utility.dll* で `Example` クラスを見つけられないために失敗します。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-107">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll*.</span></span>  
  
 <span data-ttu-id="cdbc1-108">*Utility.dll* の開発者は、<xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 属性を使用して、`Example` クラスの要求を転送することで、この問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-108">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="cdbc1-109">この属性が新バージョンの *Utility.dll* に適用されている場合、`Example` クラスに対する要求は、現在このクラスを含んでいるアセンブリに転送されます。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-109">If the attribute has been applied to the new version of *Utility.dll*, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="cdbc1-110">既存のアプリケーションは、再コンパイルを必要とすることなく正常に機能し続けます。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-110">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdbc1-111">.NET Framework Version 2.0 では、Visual Basic で記述されたアセンブリから型を転送することはできません。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-111">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="cdbc1-112">ただし、Visual Basic で記述されたアプリケーションで、転送された型を使用することはできます。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-112">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="cdbc1-113">つまり、アプリケーションで使用しているアセンブリが C# または C++ でコーディングされていれば、そのアセンブリの型が別のアセンブリに転送されても、転送された型をVisual Basic アプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-113">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forward-types"></a><span data-ttu-id="cdbc1-114">転送型</span><span class="sxs-lookup"><span data-stu-id="cdbc1-114">Forward types</span></span>  
 <span data-ttu-id="cdbc1-115">型の転送は 4 つの手順で行います。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-115">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="cdbc1-116">型のソース コードを、元のアセンブリから転送先のアセンブリに移動します。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-116">Move the source code for the type from the original assembly to the destination assembly.</span></span>  

2. <span data-ttu-id="cdbc1-117">配置に使用される型のアセンブリで、移動された型の <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> を追加します。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-117">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="cdbc1-118">次のコードは、移動された `Example` という型の属性を示しています。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-118">The following code shows the attribute for a type named `Example` that was moved.</span></span>  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. <span data-ttu-id="cdbc1-119">型の現在の場所であるアセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-119">Compile the assembly that now contains the type.</span></span>  

4. <span data-ttu-id="cdbc1-120">型の現在の場所であるアセンブリへの参照を指定して、型の元の場所であるアセンブリを再コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-120">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="cdbc1-121">たとえば、C# ファイルをコマンド ラインからコンパイルする場合は、[-reference (C# コンパイラ オプション)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) オプションを使用して、型の現在の場所であるアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-121">For example, if you are compiling a C# file from the command line, use the [-reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="cdbc1-122">C++ では、ソース ファイルで [#using](/cpp/preprocessor/hash-using-directive-cpp) ディレクティブを使用して、型の現在の場所であるアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="cdbc1-122">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdbc1-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="cdbc1-123">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="cdbc1-124">型の転送 (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="cdbc1-124">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="cdbc1-125">#using ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="cdbc1-125">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
