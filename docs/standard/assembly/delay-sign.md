---
title: アセンブリへの遅延署名
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 113df1ad3fc3ac1e27ebfef572494c1f15a3dbb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733161"
---
# <a name="delay-sign-an-assembly"></a><span data-ttu-id="96839-102">アセンブリへの遅延署名</span><span class="sxs-lookup"><span data-stu-id="96839-102">Delay-sign an assembly</span></span>

<span data-ttu-id="96839-103">組織には、開発者が日常的にアクセスできない厳重に保護されたキーのペアがある場合があります。</span><span class="sxs-lookup"><span data-stu-id="96839-103">An organization can have a closely guarded key pair that developers can't access on a daily basis.</span></span> <span data-ttu-id="96839-104">公開キーは広く使用可能ですが、秘密キーへのアクセスは少数のユーザーに限定されます。</span><span class="sxs-lookup"><span data-stu-id="96839-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="96839-105">厳密な名前のアセンブリを開発すると、厳密な名前のターゲット アセンブリを参照する各アセンブリに、そのターゲット アセンブリに厳密な名前を指定するために使用する公開キーのトークンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="96839-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="96839-106">この場合、開発プロセスで、公開キーを使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="96839-106">This requires that the public key be available during the development process.</span></span>

<span data-ttu-id="96839-107">ビルド時に遅延署名または部分署名を使用することで、厳密な名前の署名のためにポータブル実行可能 (PE) ファイルに領域を確保し、少し後の段階、通常はアセンブリが出荷される直前まで、実際の署名を遅らせることができます。</span><span class="sxs-lookup"><span data-stu-id="96839-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage, usually just before shipping the assembly.</span></span>

<span data-ttu-id="96839-108">アセンブリへの遅延署名を行うには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="96839-108">To delay-sign an assembly:</span></span>

1. <span data-ttu-id="96839-109">最終的な署名を行う組織のキー ペアの公開キー部分を取得します。</span><span class="sxs-lookup"><span data-stu-id="96839-109">Get the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="96839-110">通常、このキーは、Windows SDK により提供される[厳密名ツール (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) を使って作成できる *.snk* ファイルの形式です。</span><span class="sxs-lookup"><span data-stu-id="96839-110">Typically this key is in the form of an *.snk* file, which can be created using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) provided by the Windows SDK.</span></span>

2. <span data-ttu-id="96839-111"><xref:System.Reflection> から次の 2 つのカスタム属性を含むアセンブリのソース コードに注釈を付けます。</span><span class="sxs-lookup"><span data-stu-id="96839-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>

   - <span data-ttu-id="96839-112">公開キーをパラメーターとして含むファイルの名前を、そのコンストラクターに渡す <xref:System.Reflection.AssemblyKeyFileAttribute>。</span><span class="sxs-lookup"><span data-stu-id="96839-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>

   - <span data-ttu-id="96839-113">その遅延署名がパラメーターとして **true** をそのコンストラクターに渡すことで使用されていることを示す <xref:System.Reflection.AssemblyDelaySignAttribute>。</span><span class="sxs-lookup"><span data-stu-id="96839-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span>

   <span data-ttu-id="96839-114">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="96839-114">For example:</span></span>

   ```cpp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")];
   [assembly:AssemblyDelaySignAttribute(true)];
   ```

   ```csharp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")]
   [assembly:AssemblyDelaySignAttribute(true)]
   ```

   ```vb
   <Assembly:AssemblyKeyFileAttribute("myKey.snk")>
   <Assembly:AssemblyDelaySignAttribute(True)>
   ```

3. <span data-ttu-id="96839-115">コンパイラは、アセンブリ マニフェストに公開キーを挿入し、完全に厳密な名前の署名のために PE ファイルの領域を確保します。</span><span class="sxs-lookup"><span data-stu-id="96839-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="96839-116">このアセンブリを参照する他のアセンブリがキーを取得して自身のアセンブリ参照に格納できるように、アセンブリのビルド中に実際の公開キーが格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="96839-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>

4. <span data-ttu-id="96839-117">アセンブリには有効な厳密な名前の署名がないため、その署名の検証をオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="96839-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="96839-118">これは、厳密な名前ツールで **–Vr** オプションを使用して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="96839-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>

     <span data-ttu-id="96839-119">次の例では、*myAssembly.dll* と呼ばれるアセンブリの検証をオフにしています。</span><span class="sxs-lookup"><span data-stu-id="96839-119">The following example turns off verification for an assembly called *myAssembly.dll*.</span></span>

   ```console
   sn –Vr myAssembly.dll
   ```

   <span data-ttu-id="96839-120">厳密な名前ツールを実行できない Advanced RISC Machine (ARM) マイクロプロセッサなどのプラットフォームで検証をオフにするには、 **–Vk** オプションを使用してレジストリ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="96839-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="96839-121">検証をオフにするコンピューターのレジストリにこのレジストリ ファイルをインポートします。</span><span class="sxs-lookup"><span data-stu-id="96839-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="96839-122">次の例では、`myAssembly.dll` にレジストリ ファイルを作成しています。</span><span class="sxs-lookup"><span data-stu-id="96839-122">The following example creates a registry file for `myAssembly.dll`.</span></span>

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   <span data-ttu-id="96839-123">**–Vr** または **–Vk** のどちらかのオプションでは、テスト キー署名のための *.snk* ファイルを任意で含めることができます。</span><span class="sxs-lookup"><span data-stu-id="96839-123">With either the **–Vr** or **–Vk** option, you can optionally include an *.snk* file for test key signing.</span></span>

   > [!WARNING]
   > <span data-ttu-id="96839-124">セキュリティに関しては、厳格な名前に依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="96839-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="96839-125">厳格な名前は、一意の ID を提供するだけです。</span><span class="sxs-lookup"><span data-stu-id="96839-125">They provide a unique identity only.</span></span>

   > [!NOTE]
   > <span data-ttu-id="96839-126">64 ビット コンピューターの Visual Studio を使用した開発中に、遅延署名を使用して、**Any CPU** のアセンブリをコンパイルする場合は、 **-Vr** オプションを 2 回適用しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="96839-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="96839-127">(Visual Studio では、**Any CPU** は**プラットフォーム ターゲット**のビルド プロパティの値です。コマンド ラインからコンパイルする場合は、これが既定です。)コマンド ラインまたはファイル エクスプローラーからアプリケーションを実行する場合は、64 ビット バージョンの [Sn.exe (厳密な名前ツール)](../../framework/tools/sn-exe-strong-name-tool.md) を使用して、アセンブリに **-Vr** オプションを適用します。</span><span class="sxs-lookup"><span data-stu-id="96839-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="96839-128">設計時に Visual Studio にアセンブリを読み込む (たとえば、アプリケーションの他のアセンブリで使用されているコンポーネントがアセンブリに含まれている) 場合は、32 ビット バージョンの厳密な名前ツールを使用してください。</span><span class="sxs-lookup"><span data-stu-id="96839-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="96839-129">これは、Just-In-Time (JIT) コンパイラが、コマンド ラインからアセンブリを実行する場合には 64 ビットのネイティブ コードに、設計時の環境にアセンブリを読み込む場合には 32 ビットのネイティブ コードにアセンブリをコンパイルするためです。</span><span class="sxs-lookup"><span data-stu-id="96839-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>

5. <span data-ttu-id="96839-130">後ほど (通常は出荷の直前)、厳密な名前ツールで **–R** オプションを使用して実際に厳密な名前の署名を行うため、組織の署名機関にアセンブリを送信します。</span><span class="sxs-lookup"><span data-stu-id="96839-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>

   <span data-ttu-id="96839-131">キー ペア *sgKey.snk* を使用して厳密な名前で *myAssembly.dll* というアセンブリに署名する例を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="96839-131">The following example signs an assembly called *myAssembly.dll* with a strong name using the *sgKey.snk* key pair.</span></span>

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a><span data-ttu-id="96839-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="96839-132">See also</span></span>

- [<span data-ttu-id="96839-133">アセンブリを作成する</span><span class="sxs-lookup"><span data-stu-id="96839-133">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="96839-134">方法: 公開キーと秘密キーのキー ペアを作成する</span><span class="sxs-lookup"><span data-stu-id="96839-134">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="96839-135">Sn.exe (厳密名ツール)</span><span class="sxs-lookup"><span data-stu-id="96839-135">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
