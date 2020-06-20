---
title: '方法: 発行者ポリシーを作成する'
description: アセンブリベンダーが、.NET でアップグレードされたアセンブリを使用して発行者ポリシーファイルを作成し、アプリケーションが新しいバージョンを使用する必要があることを規定する方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 23e9d8144ec5742e0371d566b7af59dc9dd30c9b
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105404"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="20cd1-103">方法: 発行者ポリシーを作成する</span><span class="sxs-lookup"><span data-stu-id="20cd1-103">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="20cd1-104">アセンブリのベンダーは、アップグレードされたアセンブリに発行者ポリシーファイルを含めることによって、アプリケーションが新しいバージョンのアセンブリを使用する必要があることを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="20cd1-104">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="20cd1-105">発行者ポリシーファイルは、アセンブリリダイレクトとコードベース設定を指定し、アプリケーション構成ファイルと同じ形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="20cd1-105">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="20cd1-106">発行者ポリシーファイルは、アセンブリにコンパイルされ、グローバルアセンブリキャッシュに配置されます。</span><span class="sxs-lookup"><span data-stu-id="20cd1-106">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="20cd1-107">発行者ポリシーを作成するには、次の3つの手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="20cd1-107">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="20cd1-108">発行者ポリシーファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="20cd1-108">Create a publisher policy file.</span></span>

2. <span data-ttu-id="20cd1-109">発行者ポリシーアセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="20cd1-109">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="20cd1-110">発行者ポリシーアセンブリをグローバルアセンブリキャッシュに追加します。</span><span class="sxs-lookup"><span data-stu-id="20cd1-110">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="20cd1-111">発行元ポリシーのスキーマについては、「[アセンブリバージョンのリダイレクト](redirect-assembly-versions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20cd1-111">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="20cd1-112">次の例は、の1つのバージョンを別のバージョンにリダイレクトする発行者ポリシーファイルを示して `myAssembly` います。</span><span class="sxs-lookup"><span data-stu-id="20cd1-112">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
       <dependentAssembly>
         <assemblyIdentity name="myAssembly"
                           publicKeyToken="32ab4ba45e0a69a1"
                           culture="en-us" />
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->
         <bindingRedirect oldVersion="1.0.0.0"
                          newVersion="2.0.0.0"/>
       </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="20cd1-113">コードベースを指定する方法については、「[アセンブリの場所の指定](specify-assembly-location.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20cd1-113">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="20cd1-114">発行者ポリシーアセンブリを作成しています</span><span class="sxs-lookup"><span data-stu-id="20cd1-114">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="20cd1-115">[アセンブリリンカー (Al.exe)](../tools/al-exe-assembly-linker.md)を使用して、発行者ポリシーアセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="20cd1-115">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="20cd1-116">発行者ポリシーアセンブリを作成するには</span><span class="sxs-lookup"><span data-stu-id="20cd1-116">To create a publisher policy assembly</span></span>

<span data-ttu-id="20cd1-117">コマンド プロンプトに、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="20cd1-117">Type the following command at the command prompt:</span></span>

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

<span data-ttu-id="20cd1-118">このコマンドの説明:</span><span class="sxs-lookup"><span data-stu-id="20cd1-118">In this command:</span></span>

- <span data-ttu-id="20cd1-119">`publisherPolicyFile`引数は発行者ポリシーファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="20cd1-119">The `publisherPolicyFile` argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="20cd1-120">`publisherPolicyAssemblyFile`引数は、このコマンドの結果として生成される発行者ポリシーアセンブリの名前です。</span><span class="sxs-lookup"><span data-stu-id="20cd1-120">The `publisherPolicyAssemblyFile` argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="20cd1-121">アセンブリファイル名は、次の形式に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="20cd1-121">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="20cd1-122">'policy.majorNumber.minorNumber.mainAssemblyName.dll '</span><span class="sxs-lookup"><span data-stu-id="20cd1-122">\`policy.majorNumber.minorNumber.mainAssemblyName.dll'</span></span>

- <span data-ttu-id="20cd1-123">`keyPairFile`引数は、キーペアを含むファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="20cd1-123">The `keyPairFile` argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="20cd1-124">アセンブリと発行者ポリシーアセンブリには、同じキーペアで署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20cd1-124">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="20cd1-125">引数は、 `processorArchitecture` プロセッサ固有のアセンブリの対象となるプラットフォームを識別します。</span><span class="sxs-lookup"><span data-stu-id="20cd1-125">The `processorArchitecture` argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="20cd1-126">特定のプロセッサアーキテクチャを対象とする機能は、.NET Framework 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="20cd1-126">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="20cd1-127">特定のプロセッサアーキテクチャを対象とする機能は、.NET Framework 2.0 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="20cd1-127">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="20cd1-128">次のコマンドは、という発行者ポリシーファイルからという発行者ポリシーアセンブリを作成し `policy.1.0.myAssembly` `pub.config` 、ファイルのキーペアを使用してアセンブリに厳密な名前を割り当て、 `sgKey.snk` アセンブリが x86 プロセッサアーキテクチャを対象とすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="20cd1-128">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="20cd1-129">発行者ポリシーアセンブリは、適用されるアセンブリのプロセッサアーキテクチャと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="20cd1-129">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="20cd1-130">したがって、アセンブリの値がの場合は、 <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> <xref:System.Reflection.ProcessorArchitecture.MSIL> そのアセンブリの発行者ポリシーアセンブリをで作成する必要があり `/platform:anycpu` ます。</span><span class="sxs-lookup"><span data-stu-id="20cd1-130">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="20cd1-131">プロセッサ固有のアセンブリごとに個別の発行者ポリシーアセンブリを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20cd1-131">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="20cd1-132">このルールの結果として、アセンブリのプロセッサアーキテクチャを変更するには、バージョン番号のメジャーまたはマイナーコンポーネントを変更して、正しいプロセッサアーキテクチャを持つ新しい発行者ポリシーアセンブリを指定できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="20cd1-132">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="20cd1-133">アセンブリに異なるプロセッサアーキテクチャがある場合、古い発行者ポリシーアセンブリはアセンブリを処理できません。</span><span class="sxs-lookup"><span data-stu-id="20cd1-133">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="20cd1-134">また、バージョン2.0 リンカーを使用して、以前のバージョンの .NET Framework を使用してコンパイルされたアセンブリの発行者ポリシーアセンブリを作成することはできません。これは、常にプロセッサアーキテクチャを指定するためです。</span><span class="sxs-lookup"><span data-stu-id="20cd1-134">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="20cd1-135">発行者ポリシーアセンブリをグローバルアセンブリキャッシュに追加する</span><span class="sxs-lookup"><span data-stu-id="20cd1-135">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="20cd1-136">グローバル[アセンブリキャッシュツール (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md)を使用して、発行者ポリシーアセンブリをグローバルアセンブリキャッシュに追加します。</span><span class="sxs-lookup"><span data-stu-id="20cd1-136">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="20cd1-137">発行者ポリシーアセンブリをグローバルアセンブリキャッシュに追加するには</span><span class="sxs-lookup"><span data-stu-id="20cd1-137">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="20cd1-138">コマンド プロンプトに、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="20cd1-138">Type the following command at the command prompt:</span></span>

```console
gacutil /i publisherPolicyAssemblyFile
```

<span data-ttu-id="20cd1-139">次のコマンドは、 `policy.1.0.myAssembly.dll` をグローバルアセンブリキャッシュに追加します。</span><span class="sxs-lookup"><span data-stu-id="20cd1-139">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="20cd1-140">引数で指定された元の発行者ポリシーファイル `/link` がアセンブリと同じディレクトリにある場合を除き、発行者ポリシーアセンブリをグローバルアセンブリキャッシュに追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="20cd1-140">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file specified in the `/link` argument is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="20cd1-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="20cd1-141">See also</span></span>

- [<span data-ttu-id="20cd1-142">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="20cd1-142">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="20cd1-143">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="20cd1-143">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="20cd1-144">構成ファイルを使用してアプリを構成する方法</span><span class="sxs-lookup"><span data-stu-id="20cd1-144">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="20cd1-145">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="20cd1-145">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="20cd1-146">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="20cd1-146">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="20cd1-147">アセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="20cd1-147">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
