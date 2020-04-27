---
title: '方法: アプリケーション ドメインにアセンブリを読み込む'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
ms.openlocfilehash: c560e2c5858de67442ccbcd18c8f92b142cc178d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119894"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="db569-102">方法: アプリケーション ドメインにアセンブリを読み込む</span><span class="sxs-lookup"><span data-stu-id="db569-102">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="db569-103">アプリケーション ドメインにアセンブリを読み込むには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="db569-103">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="db569-104">推奨されているのは、<xref:System.Reflection.Assembly?displayProperty=nameWithType> クラスの `static` (Visual Basic では `Shared`) <xref:System.Reflection.Assembly.Load%2A> メソッドを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="db569-104">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="db569-105">それ以外には、以下の方法でアセンブリを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="db569-105">Other ways assemblies can be loaded include:</span></span>  
  
- <span data-ttu-id="db569-106"><xref:System.Reflection.Assembly> クラスの <xref:System.Reflection.Assembly.LoadFrom%2A> メソッドは、ファイルの場所が指定されたアセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="db569-106">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="db569-107">このメソッドでアセンブリを読み込む場合は、別の読み込みコンテキストが使用されます。</span><span class="sxs-lookup"><span data-stu-id="db569-107">Loading assemblies with this method uses a different load context.</span></span>  
  
- <span data-ttu-id="db569-108"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> メソッドと <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> メソッドは、リフレクション専用コンテキストにアセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="db569-108">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="db569-109">このコンテキストに読み込まれたアセンブリは検査できますが、実行することはできません。その結果、他のプラットフォームをターゲットにしているアセンブリを検査できます。</span><span class="sxs-lookup"><span data-stu-id="db569-109">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="db569-110">「[方法:リフレクションのみのコンテキストにアセンブリを読み込む](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db569-110">See [How to: Load Assemblies into the Reflection-Only Context](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db569-111">リフレクション専用コンテキストは、.NET Framework Version 2.0 で新たに追加されました。</span><span class="sxs-lookup"><span data-stu-id="db569-111">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
- <span data-ttu-id="db569-112"><xref:System.AppDomain> クラスの <xref:System.AppDomain.CreateInstance%2A> や <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> などのメソッドは、アプリケーション ドメインにアセンブリを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="db569-112">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
- <span data-ttu-id="db569-113"><xref:System.Type> クラスの <xref:System.Type.GetType%2A> メソッドは、アセンブリを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="db569-113">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
- <span data-ttu-id="db569-114"><xref:System.AppDomain?displayProperty=nameWithType> クラスの <xref:System.AppDomain.Load%2A> メソッドは、アセンブリを読み込むことができますが、主に COM の相互運用性のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="db569-114">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="db569-115">このメソッドの呼び出し元であるアプリケーション ドメイン以外のアプリケーション ドメインにアセンブリを読み込む場合は、このメソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="db569-115">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db569-116">.NET Framework Version 2.0 以降では、現在読み込まれているランタイムよりもバージョン番号が新しい .NET Framework のバージョンでコンパイルされたアセンブリは、ランタイムに読み込まれないようになりました。</span><span class="sxs-lookup"><span data-stu-id="db569-116">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="db569-117">これはメジャー コンポーネントとマイナー コンポーネントの組み合わせたバージョン番号に適用されます。</span><span class="sxs-lookup"><span data-stu-id="db569-117">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="db569-118">読み込まれたアセンブリの Just-In-Time (JIT) コンパイル コードがアプリケーション ドメイン間で共有される方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="db569-118">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="db569-119">詳細については、「[アプリケーション ドメインとアセンブリ](application-domains.md#application-domains-and-assemblies)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db569-119">For more information, see [Application domains and assemblies](application-domains.md#application-domains-and-assemblies).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db569-120">例</span><span class="sxs-lookup"><span data-stu-id="db569-120">Example</span></span>  
 <span data-ttu-id="db569-121">次に示すコードは、"example.exe" または "example.dll" という名前のアセンブリを現在のアプリケーション ドメインに読み込み、アセンブリから `Example` という型を取得します。さらに、その型に使用する `MethodA` というパラメーターを持たないメソッドを取得して、そのメソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="db569-121">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="db569-122">読み込まれたアセンブリから情報を取得する方法の詳細については、「[型の動的な読み込みおよび使用](../reflection-and-codedom/dynamically-loading-and-using-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db569-122">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="db569-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="db569-123">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [<span data-ttu-id="db569-124">アプリケーション ドメインを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="db569-124">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="db569-125">リフレクション</span><span class="sxs-lookup"><span data-stu-id="db569-125">Reflection</span></span>](../reflection-and-codedom/reflection.md)
- [<span data-ttu-id="db569-126">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="db569-126">Using Application Domains</span></span>](use.md)
- <span data-ttu-id="db569-127">[方法:  リフレクションのみのコンテキストにアセンブリを読み込む](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db569-127">[How to: Load Assemblies into the Reflection-Only Context](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)</span></span>
- [<span data-ttu-id="db569-128">アプリケーション ドメインとアセンブリ</span><span class="sxs-lookup"><span data-stu-id="db569-128">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
