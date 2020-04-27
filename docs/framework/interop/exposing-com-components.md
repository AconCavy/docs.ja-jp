---
title: .NET Framework への COM コンポーネントの公開
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
ms.openlocfilehash: 914f72b5e4840555541943620ca2df1f629b0604
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123525"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="3a8e5-102">.NET Framework への COM コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="3a8e5-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="3a8e5-103">このセクションでは、既存の COM コンポーネントをマネージド コードに公開するために必要なプロセスをまとめています。</span><span class="sxs-lookup"><span data-stu-id="3a8e5-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="3a8e5-104">.NET Framework と緊密に統合される COM サーバーの詳細については、「[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))」(相互運用のためのデザインの考慮事項) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a8e5-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="3a8e5-105">既存の COM コンポーネントは、中間層のビジネス アプリケーション、または独立した機能として、マネージド コードでの貴重なリソースです。</span><span class="sxs-lookup"><span data-stu-id="3a8e5-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="3a8e5-106">理想的なコンポーネントは、プライマリ相互運用機能アセンブリがあり、COM で課せられるプログラミング標準に厳密に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="3a8e5-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="3a8e5-107">.NET Framework に COM コンポーネントを公開するには</span><span class="sxs-lookup"><span data-stu-id="3a8e5-107">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="3a8e5-108">[タイプ ライブラリをアセンブリとしてインポートする](importing-a-type-library-as-an-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="3a8e5-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="3a8e5-109">共通言語ランタイムでは、COM 型を含め、すべてのタイプにメタデータが必要です。</span><span class="sxs-lookup"><span data-stu-id="3a8e5-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="3a8e5-110">メタデータとしてインポートされた COM 型を含むアセンブリを取得するには、複数の方法があります。</span><span class="sxs-lookup"><span data-stu-id="3a8e5-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="3a8e5-111">[マネージド コード内で COM 型を使用する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="3a8e5-111">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="3a8e5-112">任意のマネージド型で行うのと同じ方法で、COM オブジェクトで COM 型の検査、インスタンスのアクティブ化、およびメソッドの呼び出しができます。</span><span class="sxs-lookup"><span data-stu-id="3a8e5-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="3a8e5-113">[相互運用プロジェクトをコンパイルする](compiling-an-interop-project.md)。</span><span class="sxs-lookup"><span data-stu-id="3a8e5-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="3a8e5-114">Windows SDK には、共通言語仕様 (CLS) に準拠するいくつかの言語 (Visual Basic、C#、C++ など) のコンパイラが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3a8e5-114">The Windows SDK provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="3a8e5-115">[相互運用アプリケーションを展開する](deploying-an-interop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="3a8e5-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="3a8e5-116">相互運用アプリケーションは、[厳密な名前を付けた](../../standard/assembly/strong-named.md)、署名されたアセンブリとして、グローバル アセンブリ キャッシュに最適に展開されます。</span><span class="sxs-lookup"><span data-stu-id="3a8e5-116">Interop applications are best deployed as [strong-named](../../standard/assembly/strong-named.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a8e5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a8e5-117">See also</span></span>

- [<span data-ttu-id="3a8e5-118">アンマネージ コードとの相互運用</span><span class="sxs-lookup"><span data-stu-id="3a8e5-118">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="3a8e5-119">[相互運用のためのデザインの考慮事項](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3a8e5-119">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="3a8e5-120">COM 相互運用機能のサンプル: .NET クライアントおよび COM サーバー</span><span class="sxs-lookup"><span data-stu-id="3a8e5-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="3a8e5-121">言語への非依存性、および言語非依存コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3a8e5-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="3a8e5-122">Gacutil.exe (グローバル アセンブリ キャッシュ ツール)</span><span class="sxs-lookup"><span data-stu-id="3a8e5-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
