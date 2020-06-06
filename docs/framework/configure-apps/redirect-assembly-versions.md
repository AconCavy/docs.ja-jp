---
title: アセンブリ バージョンのリダイレクト
ms.date: 03/30/2017
helpviewer_keywords:
- assembly binding, redirection
- redirecting assembly binding to earlier version
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], binding redirection
ms.assetid: 88fb1a17-6ac9-4b57-8028-193aec1f727c
ms.openlocfilehash: 0d55171e37ec056b3470d238a60bc32f2feb04fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "81646044"
---
# <a name="redirecting-assembly-versions"></a><span data-ttu-id="bb05f-102">アセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="bb05f-102">Redirecting Assembly Versions</span></span>

<span data-ttu-id="bb05f-103">コンパイル時のバインド参照のリダイレクト先として、.NET Framework アセンブリ、サードパーティ製のアセンブリ、または独自のアプリのアセンブリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-103">You can redirect compile-time binding references to .NET Framework assemblies, third-party assemblies, or your own app's assemblies.</span></span> <span data-ttu-id="bb05f-104">アプリで別のバージョンのアセンブリを使用するようにリダイレクトするには、発行者ポリシーを使用する、アプリ構成ファイルを使用する、コンピューター構成ファイルを使用するなど、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="bb05f-104">You can redirect your app to use a different version of an assembly in a number of ways: through publisher policy, through an app configuration file; or through the machine configuration file.</span></span> <span data-ttu-id="bb05f-105">ここでは、.NET Framework でのアセンブリ バインドの動作の仕組みと、構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-105">This article discusses how assembly binding works in the .NET Framework and how it can be configured.</span></span>

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a><span data-ttu-id="bb05f-106">アセンブリの統一と既定のバインド</span><span class="sxs-lookup"><span data-stu-id="bb05f-106">Assembly unification and default binding</span></span>
 <span data-ttu-id="bb05f-107">.NET Framework アセンブリへのバインドは、 *アセンブリの統一*というプロセスによってリダイレクトされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bb05f-107">Bindings to .NET Framework assemblies are sometimes redirected through a process called *assembly unification*.</span></span> <span data-ttu-id="bb05f-108">.NET Framework は、1 つのバージョンの共通言語ランタイムと、型ライブラリを構成する 24 個前後の .NET Framework アセンブリで構成されています。</span><span class="sxs-lookup"><span data-stu-id="bb05f-108">The .NET Framework consists of a version of the common language runtime and about two dozen .NET Framework assemblies that make up the type library.</span></span> <span data-ttu-id="bb05f-109">これらの .NET Framework アセンブリは、ランタイムによって単一のユニットとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-109">These .NET Framework assemblies are treated by the runtime as a single unit.</span></span> <span data-ttu-id="bb05f-110">既定では、アプリを起動するとき、ランタイムによって実行されるコード内の型のすべての参照が、プロセスに読み込まれたランタイムと同じバージョン番号を持つ .NET Framework アセンブリにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-110">By default, when an app is launched, all references to types in code run by the runtime are directed to .NET Framework assemblies that have the same version number as the runtime that is loaded in a process.</span></span> <span data-ttu-id="bb05f-111">このモデルで発生するリダイレクトは、ランタイムの既定の動作となります。</span><span class="sxs-lookup"><span data-stu-id="bb05f-111">The redirections that occur with this model are the default behavior for the runtime.</span></span>

 <span data-ttu-id="bb05f-112">たとえば、アプリが SYSTEM.XML 名前空間の型を参照し、.NET Framework 4.5 を使用してビルドされた場合、ランタイムバージョン4.5 に付属する SYSTEM.XML アセンブリへの静的参照が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bb05f-112">For example, if your app references types in the System.XML namespace and was built by using the .NET Framework 4.5, it contains static references to the System.XML assembly that ships with runtime version 4.5.</span></span> <span data-ttu-id="bb05f-113">ここで、.NET Framework 4 と共に出荷された System.XML アセンブリを指すようにバインド参照をリダイレクトする場合は、リダイレクト情報をアプリ構成ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-113">If you want to redirect the binding reference to point to the System.XML assembly that ship with the .NET Framework 4, you can put redirect information in the app configuration file.</span></span> <span data-ttu-id="bb05f-114">構成ファイルで、統一された .NET Framework アセンブリに対するバインド リダイレクトを設定すると、このアセンブリの統一が取り消されます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-114">A binding redirection in a configuration file for a unified .NET Framework assembly cancels the unification for that assembly.</span></span>

 <span data-ttu-id="bb05f-115">また、使用できる複数のバージョンがある場合は、サードパーティ アセンブリのアセンブリ バインドを手動でリダイレクトすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-115">In addition, you may want to manually redirect assembly binding for third-party assemblies if there are multiple versions available.</span></span>

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a><span data-ttu-id="bb05f-116">発行者ポリシーを使用したアセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="bb05f-116">Redirecting assembly versions by using publisher policy</span></span>
 <span data-ttu-id="bb05f-117">アセンブリの販売元は、新しいアセンブリに発行者ポリシー ファイルを含めることにより、より新しいバージョンのアセンブリにアプリをリダイレクトできます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-117">Vendors of assemblies can direct apps to a newer version of an assembly by including a publisher policy file with the new assembly.</span></span> <span data-ttu-id="bb05f-118">発行者ポリシー ファイルは、グローバル アセンブリ キャッシュに配置され、アセンブリ リダイレクトの設定が格納されます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-118">The publisher policy file, which is located in the global assembly cache, contains assembly redirection settings.</span></span>

 <span data-ttu-id="bb05f-119">アセンブリの *major*.*minor* バージョンごとに、独自の発行者ポリシー ファイルが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-119">Each *major*.*minor* version of an assembly has its own publisher policy file.</span></span> <span data-ttu-id="bb05f-120">たとえば、バージョン 2.0.2.222 から 2.0.3.000 へのリダイレクトと、バージョン 2.0.2.321 から 2.0.3.000 へのリダイレクトは、いずれもバージョン 2.0 に関連付けられているため、両方とも同じファイルに記述します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-120">For example, redirections from version 2.0.2.222 to 2.0.3.000 and from version 2.0.2.321 to version 2.0.3.000 both go into the same file, because they are associated with version 2.0.</span></span> <span data-ttu-id="bb05f-121">ただし、バージョン 3.0.0.999 から 4.0.0.000 へのリダイレクトは、バージョン 3.0.999 のファイルに記述します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-121">However, a redirection from version 3.0.0.999 to version 4.0.0.000 goes into the file for version 3.0.999.</span></span> <span data-ttu-id="bb05f-122">.NET Framework のメジャー バージョンごとに、独自の発行者ポリシー ファイルが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-122">Each major version of the .NET Framework has its own publisher policy file.</span></span>

 <span data-ttu-id="bb05f-123">アセンブリの発行者ポリシー ファイルが存在する場合、ランタイムは、アセンブリのマニフェストとアプリ構成ファイルをチェックした後で、発行者ポリシー ファイルをチェックします。</span><span class="sxs-lookup"><span data-stu-id="bb05f-123">If a publisher policy file exists for an assembly, the runtime checks this file after checking the assembly's manifest and app configuration file.</span></span> <span data-ttu-id="bb05f-124">販売元は、新しいアセンブリがリダイレクト元のアセンブリとの下位互換性を維持している場合にだけ、発行者ポリシー ファイルを使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="bb05f-124">Vendors should use publisher policy files only when the new assembly is backward compatible with the assembly being redirected.</span></span>

 <span data-ttu-id="bb05f-125">「 [発行者ポリシーの省略](#bypass_PP)」で説明するように、アプリ構成ファイルで設定を指定することによって、アプリの発行者ポリシーを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-125">You can bypass publisher policy for your app by specifying settings in the app configuration file, as discussed in the [Bypassing publisher policy section](#bypass_PP).</span></span>

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a><span data-ttu-id="bb05f-126">アプリ レベルでのアセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="bb05f-126">Redirecting assembly versions at the app level</span></span>
 <span data-ttu-id="bb05f-127">アプリ構成ファイルを通じてアプリのバインド動作を変更するには、いくつかの手法があります。手動でのファイルの編集、自動バインド リダイレクトの利用、発行者ポリシーの省略によるバインド動作の指定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-127">There are a few different techniques for changing the binding behavior for your app through the app configuration file: you can manually edit the file, you can rely on automatic binding redirection, or you can specify binding behavior by bypassing publisher policy.</span></span>

### <a name="manually-editing-the-app-config-file"></a><span data-ttu-id="bb05f-128">手動でのアプリ構成ファイルの編集</span><span class="sxs-lookup"><span data-stu-id="bb05f-128">Manually editing the app config file</span></span>
 <span data-ttu-id="bb05f-129">手動でアプリ構成ファイルを編集して、アセンブリの問題を解決できます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-129">You can manually edit the app configuration file to resolve assembly issues.</span></span> <span data-ttu-id="bb05f-130">たとえば、販売元が、アプリで使用しているアセンブリの新しいバージョンをリリースしたが、下位互換性を保証していないために、発行者ポリシーを提供しない場合でも、次のように、アプリ構成ファイルにアセンブリ バインド情報を記述することによって、アプリで新しいバージョンのアセンブリを使用するように指示できます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-130">For example, if a vendor might release a newer version of an assembly that your app uses without supplying a publisher policy, because they do not guarantee backward compatibility, you can direct your app to use the newer version of the assembly by putting assembly binding information in your app's configuration file as follows.</span></span>

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a><span data-ttu-id="bb05f-131">自動バインド リダイレクトの利用</span><span class="sxs-lookup"><span data-stu-id="bb05f-131">Relying on automatic binding redirection</span></span>

<span data-ttu-id="bb05f-132">.NET Framework 4.5.1 以降のバージョンを対象とするデスクトップアプリを Visual Studio で作成すると、アプリは自動バインドリダイレクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-132">When you create a desktop app in Visual Studio that targets the .NET Framework 4.5.1 or a later version, the app uses automatic binding redirection.</span></span> <span data-ttu-id="bb05f-133">これは、2 つのコンポーネントが同じ厳密な名前付きアセンブリの異なるバージョンを参照する場合、ランタイムは出力するアプリ構成ファイル (app.config) に新しいバージョンのアセンブリへのバインド リダイレクトを自動的に追加することを意味します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-133">This means that if two components reference different versions of the same strong-named assembly, the runtime automatically adds a binding redirection to the newer version of the assembly in the output app configuration (app.config) file.</span></span> <span data-ttu-id="bb05f-134">このリダイレクトは、別の方法で発生する可能性があるアセンブリの統一をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="bb05f-134">This redirection overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="bb05f-135">ソース app.config ファイルは変更されません。</span><span class="sxs-lookup"><span data-stu-id="bb05f-135">The source app.config file is not modified.</span></span> <span data-ttu-id="bb05f-136">たとえば、アプリがアウトオブバンド .NET Framework コンポーネントを直接参照する場合に、同じコンポーネントの旧バージョンを対象とするサードパーティのライブラリを使用しているとします。</span><span class="sxs-lookup"><span data-stu-id="bb05f-136">For example, let's say that your app directly references an out-of-band .NET Framework component but uses a third-party library that targets an older version of the same component.</span></span> <span data-ttu-id="bb05f-137">このアプリをコンパイルすると、出力されるアプリ構成ファイルは、新しいバージョンのコンポーネントへのバインド リダイレクトを含むように変更されます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-137">When you compile the app, the output app configuration file is modified to contain a binding redirection to the newer version of the component.</span></span> <span data-ttu-id="bb05f-138">Web アプリを作成すると、バインドの競合に関するビルドの警告が表示され、ソース Web 構成ファイルに必要なバインド リダイレクトを追加するためオプションが示されます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-138">If you create a web app, you receive a build warning regarding the binding conflict, which in turn, gives you the option to add the necessary binding redirect to the source web configuration file.</span></span>

<span data-ttu-id="bb05f-139">手動でソース app.config ファイルにバインドリダイレクトを追加すると、コンパイル時に、追加したバインドリダイレクトに基づいてアセンブリの統合が試行されます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-139">If you manually add binding redirects to the source app.config file, at compile time, Visual Studio tries to unify the assemblies based on the binding redirects you added.</span></span> <span data-ttu-id="bb05f-140">たとえば、アセンブリの次のバインド リダイレクトを挿入するとします。</span><span class="sxs-lookup"><span data-stu-id="bb05f-140">For example, let's say you insert the following binding redirect for an assembly:</span></span>

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

<span data-ttu-id="bb05f-141">アプリ内の別のプロジェクトが同じアセンブリのバージョン 1.0.0.0 を参照する場合、自動バインド リダイレクトは、アプリがこのアセンブリのバージョン 2.0.0.0 で統一されるように、出力 app.config ファイルに次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-141">If another project in your app references version 1.0.0.0 of the same assembly, automatic binding redirection adds the following entry to the output app.config file so that the app is unified on version 2.0.0.0 of this assembly:</span></span>

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

<span data-ttu-id="bb05f-142">アプリが古いバージョンの .NET Framework を対象としている場合は、自動バインドリダイレクトを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-142">You can enable automatic binding redirection if your app targets older versions of the .NET Framework.</span></span> <span data-ttu-id="bb05f-143">この既定の動作をオーバーライドするには、任意のアセンブリの app.config ファイルにバインドリダイレクト情報を指定するか、バインドリダイレクト機能をオフにします。</span><span class="sxs-lookup"><span data-stu-id="bb05f-143">You can override this default behavior by providing binding redirection information in the app.config file for any assembly, or by turning off the binding redirection feature.</span></span> <span data-ttu-id="bb05f-144">この機能を有効または無効にする方法については、「[方法: 自動バインドリダイレクトを有効](how-to-enable-and-disable-automatic-binding-redirection.md)または無効にする」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb05f-144">For information about how to turn this feature on or off, see [How to: Enable and Disable Automatic Binding Redirection](how-to-enable-and-disable-automatic-binding-redirection.md).</span></span>

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a><span data-ttu-id="bb05f-145">発行者ポリシーの省略</span><span class="sxs-lookup"><span data-stu-id="bb05f-145">Bypassing publisher policy</span></span>
 <span data-ttu-id="bb05f-146">アプリの構成ファイルの発行者ポリシーを必要に応じてオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-146">You can override publisher policy in the app configuration file if necessary.</span></span> <span data-ttu-id="bb05f-147">たとえば、下位互換性を維持しているとされる新しいアセンブリ バージョンでも、アプリを破壊する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bb05f-147">For example, new versions of assemblies that claim to be backward compatible can still break an app.</span></span> <span data-ttu-id="bb05f-148">発行者ポリシーを省略する場合は、 [\<publisherPolicy>](./file-schema/runtime/publisherpolicy-element.md) アプリ構成ファイルの要素に要素を追加 [\<dependentAssembly>](./file-schema/runtime/dependentassembly-element.md) し、 **apply**属性を**no**に設定します。これにより、前の **[はい]** 設定が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-148">If you want to bypass publisher policy, add a [\<publisherPolicy>](./file-schema/runtime/publisherpolicy-element.md) element to the [\<dependentAssembly>](./file-schema/runtime/dependentassembly-element.md) element in the app configuration file, and set the **apply** attribute to **no**, which overrides any previous **yes** settings.</span></span>

 `<publisherPolicy apply="no" />`

 <span data-ttu-id="bb05f-149">発行者ポリシーを省略することにより、アプリの実行を続行できますが、必ず、問題点をアセンブリの販売元に報告してください。</span><span class="sxs-lookup"><span data-stu-id="bb05f-149">Bypass publisher policy to keep your app running for your users, but make sure you report the problem to the assembly vendor.</span></span> <span data-ttu-id="bb05f-150">アセンブリに発行者ポリシー ファイルを提供した場合、販売元はそのアセンブリが下位互換性を維持していること、およびクライアントが可能な限り新バージョンを使用できることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb05f-150">If an assembly has a publisher policy file, the vendor should make sure that the assembly is backward compatible and that clients can use the new version as much as possible.</span></span>

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a><span data-ttu-id="bb05f-151">コンピューター レベルでのアセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="bb05f-151">Redirecting assembly versions at the machine level</span></span>
 <span data-ttu-id="bb05f-152">コンピューター管理者が 1 台のコンピューター上のすべてのアプリで特定のアセンブリ バージョンを使用する場合も、まれにあります。</span><span class="sxs-lookup"><span data-stu-id="bb05f-152">There might be rare cases when a machine administrator wants all apps on a computer to use a specific version of an assembly.</span></span> <span data-ttu-id="bb05f-153">たとえば、セキュリティ ホールを修復するために、すべてのアプリで特定のアセンブリ バージョンを使用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="bb05f-153">For example, the administrator might want every app to use a particular assembly version, because that version fixes a security hole.</span></span> <span data-ttu-id="bb05f-154">コンピューターの構成ファイル内でアセンブリをリダイレクトした場合は、そのコンピューターで旧バージョンを使用しているすべてのアプリが新バージョンを使用するようになります。</span><span class="sxs-lookup"><span data-stu-id="bb05f-154">If an assembly is redirected in the machine's configuration file, all apps on that machine that use the old version will be directed to use the new version.</span></span> <span data-ttu-id="bb05f-155">コンピューター構成ファイルは、アプリ構成ファイルおよび発行者ポリシー ファイルよりもオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-155">The machine configuration file overrides the app configuration file and the publisher policy file.</span></span> <span data-ttu-id="bb05f-156">このファイルは、%*runtime install path*%\Config ディレクトリに含まれています。</span><span class="sxs-lookup"><span data-stu-id="bb05f-156">This file is located in the %*runtime install path*%\Config directory.</span></span> <span data-ttu-id="bb05f-157">通常、.NET Framework は %drive%\Windows\Microsoft.NET\Framework ディレクトリにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-157">Typically, the .NET Framework is installed in the %drive%\Windows\Microsoft.NET\Framework directory.</span></span>

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a><span data-ttu-id="bb05f-158">構成ファイル内でのアセンブリ バインドの指定</span><span class="sxs-lookup"><span data-stu-id="bb05f-158">Specifying assembly binding in configuration files</span></span>
 <span data-ttu-id="bb05f-159">アプリ構成ファイル、コンピューター構成ファイル、発行者ポリシー ファイルのいずれの場合も、同じ XML 形式を使用してバインド リダイレクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-159">You use the same XML format to specify binding redirects whether it’s in the app configuration file, the machine configuration file, or the publisher policy file.</span></span> <span data-ttu-id="bb05f-160">あるアセンブリバージョンを別のバージョンにリダイレクトするには、要素を使用し [\<bindingRedirect>](./file-schema/runtime/bindingredirect-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-160">To redirect one assembly version to another, use the [\<bindingRedirect>](./file-schema/runtime/bindingredirect-element.md) element.</span></span> <span data-ttu-id="bb05f-161">**oldVersion** 属性では、1 つのアセンブリ バージョンまたはバージョンの範囲を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-161">The **oldVersion** attribute can specify a single assembly version or a range of versions.</span></span> <span data-ttu-id="bb05f-162">`newVersion` 属性では、1 つのバージョンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb05f-162">The `newVersion` attribute should specify a single version.</span></span>  <span data-ttu-id="bb05f-163">たとえば、 `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` は、アセンブリ バージョン 1.1.0.0 ～ 1.2.0.0 の代わりにバージョン 2.0.0.0 を使用するようにランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-163">For example, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` specifies that the runtime should use version 2.0.0.0 instead of the assembly versions between 1.1.0.0 and 1.2.0.0.</span></span>

 <span data-ttu-id="bb05f-164">次のコード例は、さまざまなバインディング リダイレクトのシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="bb05f-164">The following code example demonstrates a variety of binding redirect scenarios.</span></span> <span data-ttu-id="bb05f-165">この例では、 `myAssembly`のバージョンの範囲に対するリダイレクトと、 `mySecondAssembly`の単一のバインド リダイレクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-165">The example specifies a redirect for a range of versions for `myAssembly`, and a single binding redirect for `mySecondAssembly`.</span></span> <span data-ttu-id="bb05f-166">この例では、発行者ポリシー ファイルによって `myThirdAssembly`のバインド リダイレクトがオーバーライドされないことも指定しています。</span><span class="sxs-lookup"><span data-stu-id="bb05f-166">The example also specifies that publisher policy file will not override the binding redirects for `myThirdAssembly`.</span></span>

 <span data-ttu-id="bb05f-167">アセンブリをバインドするには、タグに**xmlns**属性を指定して文字列 "urn: schema-microsoft-com: asm: v1" を指定する必要があり [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) ます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-167">To bind an assembly, you must specify the string "urn:schemas-microsoft-com:asm.v1" with the **xmlns** attribute in the [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) tag.</span></span>

```xml
<configuration>
  <runtime>
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
      <dependentAssembly>
        <assemblyIdentity name="myAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
        <!-- Assembly versions can be redirected in app,
          publisher policy, or machine configuration files. -->
        <bindingRedirect oldVersion="1.0.0.0-2.0.0.0" newVersion="3.0.0.0" />
      </dependentAssembly>
      <dependentAssembly>
        <assemblyIdentity name="mySecondAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
             <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />
      </dependentAssembly>
      <dependentAssembly>
      <assemblyIdentity name="myThirdAssembly"
        publicKeyToken="32ab4ba45e0a69a1"
        culture="en-us" />
        <!-- Publisher policy can be set only in the app
          configuration file. -->
        <publisherPolicy apply="no" />
      </dependentAssembly>
    </assemblyBinding>
  </runtime>
</configuration>
```

### <a name="limiting-assembly--bindings-to-a-specific-version"></a><span data-ttu-id="bb05f-168">特定のバージョンへのアセンブリ バインドの制限</span><span class="sxs-lookup"><span data-stu-id="bb05f-168">Limiting assembly  bindings to a specific version</span></span>
 <span data-ttu-id="bb05f-169">アプリ構成ファイルの要素で**appliesTo**属性を使用して [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) 、アセンブリバインディング参照を特定のバージョンの .NET Framework にリダイレクトできます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-169">You can use the **appliesTo** attribute on the [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) element in an app configuration file to redirect assembly binding references to a specific version of the .NET Framework.</span></span> <span data-ttu-id="bb05f-170">このオプションの属性では、.NET Framework バージョン番号を使用して、適用するバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-170">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="bb05f-171">**AppliesTo**属性が指定されていない場合、 [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) 要素は .NET Framework のすべてのバージョンに適用されます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-171">If no **appliesTo** attribute is specified, the [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) element applies to all versions of the .NET Framework.</span></span>

 <span data-ttu-id="bb05f-172">たとえば、.NET Framework 3.5 アセンブリのアセンブリ バインドをリダイレクトするには、アプリ構成ファイルに次の XML コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-172">For example, to redirect assembly binding for a .NET Framework 3.5 assembly, you would include the following XML code in your app configuration file.</span></span>

```xml
<runtime>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"
    appliesTo="v3.5">
    <dependentAssembly>
      <!-- assembly information goes here -->
    </dependentAssembly>
  </assemblyBinding>
</runtime>
```

 <span data-ttu-id="bb05f-173">バージョンの順序でリダイレクト情報を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb05f-173">You should enter redirection information in version order.</span></span> <span data-ttu-id="bb05f-174">たとえば、.NET Framework 3.5 アセンブリのアセンブリ バインド リダイレクト情報を入力し、次に .NET Framework 4.5 アセンブリの情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-174">For example, enter assembly binding redirection information for .NET Framework 3.5 assemblies followed by .NET Framework 4.5 assemblies.</span></span> <span data-ttu-id="bb05f-175">最後に、 **appliesTo** 属性を使用せず、すべてのバージョンの .NET Framework に適用される .NET Framework アセンブリ リダイレクトのアセンブリ バインディング リダイレクト情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-175">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="bb05f-176">リダイレクトで競合が発生した場合は、構成ファイル内で最初に一致したリダイレクト ステートメントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="bb05f-176">If there is a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>

 <span data-ttu-id="bb05f-177">たとえば、ある参照を .NET Framework 3.5 のアセンブリにリダイレクトし、別の参照を .NET Framework 4 のアセンブリにリダイレクトするには、次の擬似コードに示すパターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb05f-177">For example, to redirect one reference to a .NET Framework 3.5 assembly and another reference to a .NET Framework 4 assembly, use the pattern shown in the following pseudocode.</span></span>

```xml
<assemblyBinding xmlns="..." appliesTo="v3.5 ">
  <!--.NET Framework version 3.5 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="..." appliesTo="v4.0.30319">
  <!--.NET Framework version 4.0 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="...">
  <!-- redirects meant for all versions of the runtime -->
</assemblyBinding>
```

## <a name="see-also"></a><span data-ttu-id="bb05f-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb05f-178">See also</span></span>

- [<span data-ttu-id="bb05f-179">方法: 自動バインディング リダイレクトを有効/無効にする</span><span class="sxs-lookup"><span data-stu-id="bb05f-179">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="bb05f-180">\<bindingRedirect>Element</span><span class="sxs-lookup"><span data-stu-id="bb05f-180">\<bindingRedirect> Element</span></span>](./file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="bb05f-181">アセンブリ バインディング リダイレクトのセキュリティ アクセス許可</span><span class="sxs-lookup"><span data-stu-id="bb05f-181">Assembly Binding Redirection Security Permission</span></span>](assembly-binding-redirection-security-permission.md)
- [<span data-ttu-id="bb05f-182">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="bb05f-182">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="bb05f-183">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="bb05f-183">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="bb05f-184">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="bb05f-184">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="bb05f-185">アプリの構成</span><span class="sxs-lookup"><span data-stu-id="bb05f-185">Configuring Apps</span></span>](index.md)
- [<span data-ttu-id="bb05f-186">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="bb05f-186">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="bb05f-187">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="bb05f-187">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="bb05f-188">方法: 発行者ポリシーを作成する</span><span class="sxs-lookup"><span data-stu-id="bb05f-188">How to: Create a Publisher Policy</span></span>](how-to-create-a-publisher-policy.md)
