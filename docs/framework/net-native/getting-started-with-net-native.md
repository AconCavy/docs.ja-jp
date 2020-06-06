---
title: .NET ネイティブの概要
ms.date: 03/30/2017
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
ms.openlocfilehash: 1c0c25ddf379c31a9c7b4437d36e7e0cbf1bb2f3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128409"
---
# <a name="getting-started-with-net-native"></a><span data-ttu-id="61d47-102">.NET ネイティブの概要</span><span class="sxs-lookup"><span data-stu-id="61d47-102">Getting Started with .NET Native</span></span>

<span data-ttu-id="61d47-103">Windows 10 用に新しい Windows アプリを作成する場合も、既存の Windows ストア アプリを移行する場合も、次に示す同じ手順を実行することになります。</span><span class="sxs-lookup"><span data-stu-id="61d47-103">Whether you are writing a new Windows app for Windows 10 or you are migrating an existing Windows Store app, you can follow the same set of procedures.</span></span> <span data-ttu-id="61d47-104">.NET ネイティブアプリを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="61d47-104">To create a .NET Native app, follow these steps:</span></span>

1. <span data-ttu-id="61d47-105">[Windows 10 を対象とするユニバーサル Windows プラットフォーム (UWP) ストア アプリを開発](#Step1)し、アプリのデバッグ ビルドをテストして、そのアプリが適切に動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="61d47-105">[Develop a Universal Windows Platform (UWP) app that targets Windows 10](#Step1), and test the debug builds of your app to ensure that it works properly.</span></span>

2. <span data-ttu-id="61d47-106">[追加のリフレクションおよびシリアル化の使用を処理](#Step2)します。</span><span class="sxs-lookup"><span data-stu-id="61d47-106">[Handle additional reflection and serialization usage](#Step2).</span></span>

3. <span data-ttu-id="61d47-107">[リリース ビルドのアプリを展開して、テストします](#Step3)。</span><span class="sxs-lookup"><span data-stu-id="61d47-107">[Deploy and test the release builds of your app](#Step3).</span></span>

4. <span data-ttu-id="61d47-108">[メタデータの欠落を手動で解決し](#Step4)、すべての問題が解決されるまで [手順 3](#Step3) を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="61d47-108">[Manually resolve missing metadata](#Step4), and repeat [step 3](#Step3) until all issues are resolved.</span></span>

> [!NOTE]
> <span data-ttu-id="61d47-109">既存の Windows ストアアプリを .NET ネイティブに移行する場合は、「 [Windows ストアアプリの .NET ネイティブへの移行](migrating-your-windows-store-app-to-net-native.md)」を必ず確認してください。</span><span class="sxs-lookup"><span data-stu-id="61d47-109">If you are migrating an existing Windows Store app to .NET Native, be sure to review [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

<a name="Step1"></a>

## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a><span data-ttu-id="61d47-110">手順 1: UWP アプリのデバッグ ビルドを開発してテストする</span><span class="sxs-lookup"><span data-stu-id="61d47-110">Step 1: Develop and test debug builds of your UWP app</span></span>

<span data-ttu-id="61d47-111">新しいアプリを開発するか既存のアプリを移行するかに関係なく、Windows アプリについては同じ手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="61d47-111">Whether you are developing a new app or migrating an existing one, you follow the same process as for any Windows app.</span></span>

1. <span data-ttu-id="61d47-112">Visual C# または Visual Basic のユニバーサル Windows アプリ テンプレートを使用して、Visual Studio で新しい UWP プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="61d47-112">Create a new UWP project in Visual Studio by using the Universal Windows app template for Visual C# or Visual Basic.</span></span> <span data-ttu-id="61d47-113">既定では、すべての UWP アプリケーションは CoreCLR を対象としていて、.NET ネイティブ ツール チェーンを使用してリリース ビルドがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="61d47-113">By default, all UWP applications target the CoreCLR and their release builds are compiled by using the .NET Native tool chain.</span></span>

2. <span data-ttu-id="61d47-114">UWP アプリ プロジェクトのコンパイルに .NET ネイティブ ツール チェーンを使用する場合と使用しない場合では、両者の間に既知の互換性問題がある点にご注意ください。</span><span class="sxs-lookup"><span data-stu-id="61d47-114">Note that there are some known compatibility issues between compiling UWP app projects with the .NET Native tool chain and without it.</span></span> <span data-ttu-id="61d47-115">詳細については、 [移行ガイド](migrating-your-windows-store-app-to-net-native.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61d47-115">Refer to the [migration guide](migrating-your-windows-store-app-to-net-native.md) for more information.</span></span>

<span data-ttu-id="61d47-116">ローカルシステム (またはシミュレーター) で実行される .NET ネイティブの領域に対して C# または Visual Basic コードを記述できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="61d47-116">You can now write C# or Visual Basic code against the .NET Native surface area that runs on the local system (or in the simulator).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="61d47-117">アプリを開発するときに、コードでのシリアル化またはリフレクションを使用する場合は注意してください。</span><span class="sxs-lookup"><span data-stu-id="61d47-117">As you develop your app, note any use of serialization or reflection in your code.</span></span>

<span data-ttu-id="61d47-118">既定では、デバッグビルドは、F5 を使用した迅速な配置を可能にするために JIT でコンパイルされますが、リリースビルドは .NET ネイティブプリコンパイルテクノロジを使用してコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="61d47-118">By default, debug builds are JIT-compiled to enable rapid F5 deployment, while release builds are compiled by using the .NET Native pre-compilation technology.</span></span> <span data-ttu-id="61d47-119">つまり、アプリのデバッグ ビルドが正常に動作するようにするには、.NET ネイティブ ツール チェーンでコンパイルする前に、これをビルドしてテストする必要があるということです。</span><span class="sxs-lookup"><span data-stu-id="61d47-119">This means you should build and test the debug builds of your app to ensure that they work normally before compiling them with the .NET Native tool chain.</span></span>

<a name="Step2"></a>

## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a><span data-ttu-id="61d47-120">手順 2: 追加のリフレクションおよびシリアル化の使用を処理する</span><span class="sxs-lookup"><span data-stu-id="61d47-120">Step 2: Handle additional reflection and serialization usage</span></span>

<span data-ttu-id="61d47-121">プロジェクト作成時に Default.rd.xml という名前のランタイム ディレクティブ ファイルがプロジェクトに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="61d47-121">A runtime directives file, Default.rd.xml, is automatically added to your project when you create it.</span></span> <span data-ttu-id="61d47-122">C# で開発する場合、このファイルはプロジェクトの **Properties** フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="61d47-122">If you develop in C#, it is found in your project's **Properties** folder.</span></span> <span data-ttu-id="61d47-123">Visual Basic で開発する場合、このファイルはプロジェクトの **My Project** フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="61d47-123">If you develop in Visual Basic, it is found in your project's **My Project** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="61d47-124">ランタイム ディレクティブ ファイルが必要となる理由の背景を含む .NET ネイティブのコンパイルの概要については、「 [.NET ネイティブとコンパイル](net-native-and-compilation.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="61d47-124">For an overview of the .NET Native compilation process that provides background on why a runtime directives file is needed, see [.NET Native and Compilation](net-native-and-compilation.md).</span></span>

<span data-ttu-id="61d47-125">ランタイム ディレクティブ ファイルは、アプリの実行時に必要なメタデータを定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="61d47-125">The runtime directives file is used to define the metadata that your app needs at run time.</span></span> <span data-ttu-id="61d47-126">この既定バージョンのファイルで十分な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="61d47-126">In some cases, the default version of the file may be adequate.</span></span> <span data-ttu-id="61d47-127">ただし、シリアル化やリフレクションに依存するコードには、ランタイム ディレクティブ ファイルに追加のエントリが必要になるものがあります。</span><span class="sxs-lookup"><span data-stu-id="61d47-127">However, some code that relies on serialization or reflection may require additional entries in the runtime directives file.</span></span>

<span data-ttu-id="61d47-128">**シリアル化**</span><span class="sxs-lookup"><span data-stu-id="61d47-128">**Serialization**</span></span>

<span data-ttu-id="61d47-129">シリアライザーには 2 つのカテゴリがあり、これらはいずれもランタイム ディレクティブ ファイルに追加エントリを必要とする場合があります。</span><span class="sxs-lookup"><span data-stu-id="61d47-129">There are two categories of serializers, and both may require additional entries in the runtime directives file:</span></span>

- <span data-ttu-id="61d47-130">非リフレクション ベースのシリアライザー。</span><span class="sxs-lookup"><span data-stu-id="61d47-130">Non-reflection based serializers.</span></span> <span data-ttu-id="61d47-131"><xref:System.Runtime.Serialization.DataContractSerializer>、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>、および <xref:System.Xml.Serialization.XmlSerializer> クラスなど、.NET Framework クラス ライブラリ内にあるシリアライザーは、リフレクションに依存しません。</span><span class="sxs-lookup"><span data-stu-id="61d47-131">The serializers found in the .NET Framework class library, such as the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes, do not rely on reflection.</span></span> <span data-ttu-id="61d47-132">ただし、これらのシリアライザーでは、シリアル化または逆シリアル化されるオブジェクトに基づいてコードが生成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="61d47-132">However, they do require that code be generated based on the object to be serialized or deserialized.</span></span>  <span data-ttu-id="61d47-133">詳しくは、「 [シリアル化とメタデータ](serialization-and-metadata.md)」の「Microsoft のシリアライザー」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="61d47-133">For more information, see the "Microsoft Serializers" section in [Serialization and Metadata](serialization-and-metadata.md).</span></span>

- <span data-ttu-id="61d47-134">サードパーティ シリアライザー。</span><span class="sxs-lookup"><span data-stu-id="61d47-134">Third-party serializers.</span></span> <span data-ttu-id="61d47-135">サードパーティ製のシリアル化ライブラリ (最も一般的なものは Newtonsoft JSON シリアライザー) であり、一般的にリフレクションに基づいており、 \* オブジェクトのシリアル化と逆シリアル化をサポートするために、.xml ファイルのエントリが必要です。</span><span class="sxs-lookup"><span data-stu-id="61d47-135">Third-party serialization libraries, the most common of which is the Newtonsoft JSON serializer, are generally reflection-based and require entries in the \*.rd.xml file to support object serialization and deserialization.</span></span> <span data-ttu-id="61d47-136">詳しくは、「 [Serialization and Metadata](serialization-and-metadata.md)」の「サードパーティ シリアライザー」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="61d47-136">For more information, see the "Third-Party Serializers" section in [Serialization and Metadata](serialization-and-metadata.md).</span></span>

<span data-ttu-id="61d47-137">**リフレクションに依存するメソッド**</span><span class="sxs-lookup"><span data-stu-id="61d47-137">**Methods that rely on reflection**</span></span>

<span data-ttu-id="61d47-138">コードでのリフレクションの使用は明確ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="61d47-138">In some cases, the use of reflection in code is not obvious.</span></span> <span data-ttu-id="61d47-139">一般的な API やプログラミング パターンの中には、リフレクション API の一部とは見なされないが、正常な実行にリフレクションを必要とするものがあります。</span><span class="sxs-lookup"><span data-stu-id="61d47-139">Some common APIs or programming patterns aren't considered part of the reflection API but rely on reflection to execute successfully.</span></span> <span data-ttu-id="61d47-140">これには、次のような型インスタンス化およびメソッド作成方法があります。</span><span class="sxs-lookup"><span data-stu-id="61d47-140">This includes the following type instantiation and method construction methods:</span></span>

- <span data-ttu-id="61d47-141"><xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> メソッド</span><span class="sxs-lookup"><span data-stu-id="61d47-141">The <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method</span></span>

- <span data-ttu-id="61d47-142"><xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> メソッドと <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> メソッド</span><span class="sxs-lookup"><span data-stu-id="61d47-142">The <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> and <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> methods</span></span>

- <span data-ttu-id="61d47-143"><xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> メソッド。</span><span class="sxs-lookup"><span data-stu-id="61d47-143">The <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="61d47-144">詳細については、「 [リフレクションに依存する API](apis-that-rely-on-reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61d47-144">For more information, see [APIs That Rely on Reflection](apis-that-rely-on-reflection.md).</span></span>

> [!NOTE]
> <span data-ttu-id="61d47-145">ランタイム ディレクティブ ファイルで使用される型名は完全修飾である必要があります。</span><span class="sxs-lookup"><span data-stu-id="61d47-145">Type names used in runtime directives files must be fully qualified.</span></span> <span data-ttu-id="61d47-146">たとえば、ファイルでは "String" ではなく "System.String" を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61d47-146">For example, the file must specify "System.String" instead of "String".</span></span>

<a name="Step3"></a>

## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a><span data-ttu-id="61d47-147">手順 3: リリース ビルドのアプリを展開してテストする</span><span class="sxs-lookup"><span data-stu-id="61d47-147">Step 3: Deploy and test the release builds of your app</span></span>

<span data-ttu-id="61d47-148">ランタイム ディレクティブ ファイルを更新したら、アプリのリリース ビルドを再ビルドして配置できます。</span><span class="sxs-lookup"><span data-stu-id="61d47-148">After you’ve updated the runtime directives file, you can rebuild and deploy release builds of your app.</span></span> <span data-ttu-id="61d47-149">.NET ネイティブバイナリは、プロジェクトの [**プロパティ**] ダイアログボックスの [**コンパイル**] タブにある [**ビルド出力パス**] テキストボックスで指定されたディレクトリの ILC サブディレクトリに配置されます。このフォルダーにないバイナリは、.NET ネイティブではコンパイルされていません。</span><span class="sxs-lookup"><span data-stu-id="61d47-149">.NET Native binaries are placed in the ILC.out subdirectory of the directory specified in the **Build output path** text box of  the project's **Properties** dialog box, **Compile** tab. Binaries that aren't in this folder haven't been compiled with .NET Native.</span></span> <span data-ttu-id="61d47-150">ターゲット プラットフォームごとに、アプリを十分にテストし、失敗シナリオを含むすべてのシナリオをテストします。</span><span class="sxs-lookup"><span data-stu-id="61d47-150">Test your app thoroughly, and test all scenarios, including failure scenarios, on each of its target platforms.</span></span>

<span data-ttu-id="61d47-151">アプリが正常に動作しない場合 (特に実行時に [MissingMetadataException](missingmetadataexception-class-net-native.md) 例外または [MissingInteropDataException](missinginteropdataexception-class-net-native.md) 例外をスローする場合)、次のセクション「[手順 4: メタデータの欠落を手動で解決する](#Step4)」の手順を実行してください。</span><span class="sxs-lookup"><span data-stu-id="61d47-151">If your app doesn’t work properly (particularly in cases where it throws [MissingMetadataException](missingmetadataexception-class-net-native.md) or [MissingInteropDataException](missinginteropdataexception-class-net-native.md) exceptions at run time), follow the instructions in the next section, [Step 4: Manually resolve missing metadata](#Step4).</span></span> <span data-ttu-id="61d47-152">初回例外を有効にすると、このようなバグの検出に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="61d47-152">Enabling first-chance exceptions may help you find these bugs.</span></span>

<span data-ttu-id="61d47-153">アプリのデバッグビルドをテストしてデバッグし、 [MissingMetadataException](missingmetadataexception-class-net-native.md)例外と[MissingInteropDataException](missinginteropdataexception-class-net-native.md)例外を削除したことが確実な場合は、アプリを最適化された .NET ネイティブアプリとしてテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="61d47-153">When you’ve tested and debugged the debug builds of your app and you’re confident that you’ve eliminated the [MissingMetadataException](missingmetadataexception-class-net-native.md) and [MissingInteropDataException](missinginteropdataexception-class-net-native.md) exceptions, you should test your app as an optimized .NET Native app.</span></span> <span data-ttu-id="61d47-154">これを行うには、アクティブ プロジェクトの構成を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="61d47-154">To do this, change your active project configuration from **Debug** to **Release**.</span></span>

<a name="Step4"></a>

## <a name="step-4-manually-resolve-missing-metadata"></a><span data-ttu-id="61d47-155">手順 4: メタデータの欠落を手動で解決する</span><span class="sxs-lookup"><span data-stu-id="61d47-155">Step 4: Manually resolve missing metadata</span></span>

<span data-ttu-id="61d47-156">デスクトップでは発生しない .NET ネイティブで発生する最も一般的なエラーは、ランタイムの[MissingMetadataException](missingmetadataexception-class-net-native.md)、 [MissingInteropDataException](missinginteropdataexception-class-net-native.md)、または[誤 singruntimeartifactexception](missingruntimeartifactexception-class-net-native.md)例外です。</span><span class="sxs-lookup"><span data-stu-id="61d47-156">The most common failure you'll encounter with .NET Native that you don't encounter on the desktop is a runtime [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), or [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="61d47-157">メタデータの欠落は、予期しない動作やアプリの失敗によって判明することもあります。</span><span class="sxs-lookup"><span data-stu-id="61d47-157">In some cases, the absence of metadata can manifest itself in unpredictable behavior or even in app failures.</span></span> <span data-ttu-id="61d47-158">このセクションでは、ランタイム ディレクティブ ファイルにディレクティブを追加することによって、これらの例外をデバッグして解決する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="61d47-158">This section discusses how you can debug and resolve these exceptions by adding directives to the runtime directives file.</span></span> <span data-ttu-id="61d47-159">ランタイム ディレクティブの形式については、「[ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](runtime-directives-rd-xml-configuration-file-reference.md)」を参照してださい。</span><span class="sxs-lookup"><span data-stu-id="61d47-159">For information about the format of runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="61d47-160">ランタイム ディレクティブを追加したら、もう一度 [アプリを配置およびテスト](#Step3) して、例外が発生しなくなるまで新しい [MissingMetadataException](missingmetadataexception-class-net-native.md)、 [MissingInteropDataException](missinginteropdataexception-class-net-native.md)、および  [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 例外を解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61d47-160">After you’ve added runtime directives, you should [deploy and test your app](#Step3) again and resolve any new [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and  [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions until you encounter no more exceptions.</span></span>

> [!TIP]
> <span data-ttu-id="61d47-161">高いレベルでランタイム ディレクティブを指定して、アプリがコードの変更に対応できるようにします。</span><span class="sxs-lookup"><span data-stu-id="61d47-161">Specify the runtime directives at a high level to enable your app to be resilient to code changes.</span></span>  <span data-ttu-id="61d47-162">メンバー レベルではなく、名前空間レベルおよび型レベルでランタイム ディレクティブを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="61d47-162">We recommend adding runtime directives at the namespace and type levels rather than the member level.</span></span> <span data-ttu-id="61d47-163">回復性と、バイナリを大きくすることに伴うコンパイル時間の延長の間にはトレードオフがある場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="61d47-163">Note that there may be a tradeoff between resiliency and larger binaries with longer compile times.</span></span>

<span data-ttu-id="61d47-164">メタデータの欠落例外に対応する場合は、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="61d47-164">When addressing a missing metadata exception, consider these issues:</span></span>

- <span data-ttu-id="61d47-165">例外が発生する前にアプリが何を実行しようとしていたか。</span><span class="sxs-lookup"><span data-stu-id="61d47-165">What was the app trying to do before the exception?</span></span>

  - <span data-ttu-id="61d47-166">たとえば、データ バインド、シリアル化または逆シリアル化を行っていたか、またはリフレクション API を直接使用していましたか。</span><span class="sxs-lookup"><span data-stu-id="61d47-166">For example, was it data binding, serializing or deserializing data, or directly using the reflection API?</span></span>

- <span data-ttu-id="61d47-167">これは特殊なケースか、または他の型でも同じ問題が発生すると考えられるか。</span><span class="sxs-lookup"><span data-stu-id="61d47-167">Is this an isolated case, or do you believe you'll encounter the same issue for other types?</span></span>

  - <span data-ttu-id="61d47-168">たとえば、 [MissingMetadataException](missingmetadataexception-class-net-native.md) 例外は、アプリのオブジェクト モデル内の型をシリアル化するときにスローされます。</span><span class="sxs-lookup"><span data-stu-id="61d47-168">For example, a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception is thrown when serializing a type in the app’s object model.</span></span>  <span data-ttu-id="61d47-169">シリアル化されるその他の型がわかっている場合は、それらの型 (または、コードがどの程度構造的に作成されているかによって、それを含む名前空間) に同時にランタイム ディレクティブを追加できます。</span><span class="sxs-lookup"><span data-stu-id="61d47-169">If you know other types that will be serialized, you can add runtime directives for those types (or for their containing namespaces, depending on how well the code is organized) at the same time.</span></span>

- <span data-ttu-id="61d47-170">リフレクションを使用しないようにコードを書き換えることができるか。</span><span class="sxs-lookup"><span data-stu-id="61d47-170">Can you rewrite the code so it doesn’t use reflection?</span></span>

  - <span data-ttu-id="61d47-171">たとえば、予期される型がわかっている場合に、コードで `dynamic` キーワードが使用されていますか。</span><span class="sxs-lookup"><span data-stu-id="61d47-171">For example, does the code use the `dynamic` keyword when you know what type to expect?</span></span>

  - <span data-ttu-id="61d47-172">より適切な他の方法を使用できる場合に、リフレクションに依存するメソッドをコードで呼び出していますか。</span><span class="sxs-lookup"><span data-stu-id="61d47-172">Does the code call a method that depends on reflection when some better alternative is available?</span></span>

> [!NOTE]
> <span data-ttu-id="61d47-173">リフレクションの違い、およびデスクトップアプリと .NET ネイティブでのメタデータの可用性に起因する問題の処理の詳細については、「[リフレクションに依存する api](apis-that-rely-on-reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61d47-173">For additional information about handling problems that stem from differences in reflection and the availability of metadata in desktop apps and .NET Native, see [APIs That Rely on Reflection](apis-that-rely-on-reflection.md).</span></span>

<span data-ttu-id="61d47-174">アプリのテスト時に発生する例外およびその他の問題の処理に関する具体的な例については、次のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="61d47-174">For some specific examples of handling exceptions and other issues that occur when testing your app, see:</span></span>

- [<span data-ttu-id="61d47-175">例:データ バインド時の例外の処理</span><span class="sxs-lookup"><span data-stu-id="61d47-175">Example: Handling Exceptions When Binding Data</span></span>](example-handling-exceptions-when-binding-data.md)

- [<span data-ttu-id="61d47-176">例:動的プログラミングのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="61d47-176">Example: Troubleshooting Dynamic Programming</span></span>](example-troubleshooting-dynamic-programming.md)

- [<span data-ttu-id="61d47-177">.NET ネイティブ アプリでのランタイム例外</span><span class="sxs-lookup"><span data-stu-id="61d47-177">Runtime Exceptions in .NET Native Apps</span></span>](runtime-exceptions-in-net-native-apps.md)

## <a name="see-also"></a><span data-ttu-id="61d47-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="61d47-178">See also</span></span>

- [<span data-ttu-id="61d47-179">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="61d47-179">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- <span data-ttu-id="61d47-180">[.NET ネイティブのセットアップおよび構成](https://docs.microsoft.com/previous-versions/dn600164(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="61d47-180">[.NET Native Setup and Configuration](https://docs.microsoft.com/previous-versions/dn600164(v=vs.110))</span></span>
- [<span data-ttu-id="61d47-181">.NET Native とコンパイル</span><span class="sxs-lookup"><span data-stu-id="61d47-181">.NET Native and Compilation</span></span>](net-native-and-compilation.md)
- [<span data-ttu-id="61d47-182">リフレクションおよび .NET ネイティブ</span><span class="sxs-lookup"><span data-stu-id="61d47-182">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
- [<span data-ttu-id="61d47-183">リフレクションに依存する API</span><span class="sxs-lookup"><span data-stu-id="61d47-183">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)
- [<span data-ttu-id="61d47-184">シリアル化とメタデータ</span><span class="sxs-lookup"><span data-stu-id="61d47-184">Serialization and Metadata</span></span>](serialization-and-metadata.md)
- [<span data-ttu-id="61d47-185">Windows ストア アプリの .NET ネイティブへの移行</span><span class="sxs-lookup"><span data-stu-id="61d47-185">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)
