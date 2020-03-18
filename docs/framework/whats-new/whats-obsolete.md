---
title: .NET Framework で互換性のために残されている機能
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: 7cfebfde859a95495e9d2d5e42bd034ad5d55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "79143136"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a><span data-ttu-id="244a7-102">クラス ライブラリ内にある旧版のもの</span><span class="sxs-lookup"><span data-stu-id="244a7-102">What's obsolete in the .NET Framework class library</span></span>

<span data-ttu-id="244a7-103">.NET の変化の推移。</span><span class="sxs-lookup"><span data-stu-id="244a7-103">.NET changes over time.</span></span> <span data-ttu-id="244a7-104">バージョンが新しくなるたびに、新しい機能を提供する新しい型と新しいメンバーが追加されています。</span><span class="sxs-lookup"><span data-stu-id="244a7-104">Each new version adds new types and type members that provide new functionality.</span></span> <span data-ttu-id="244a7-105">既存の型とそのメンバーも変更されています。</span><span class="sxs-lookup"><span data-stu-id="244a7-105">Existing types and their members also change over time.</span></span> <span data-ttu-id="244a7-106">たとえば、一部の型は、その型がサポートするテクノロジが新しいテクノロジに置き換えられることで重要度が下がり、一部のメソッドは、何らかの形で優れた新しいメソッドに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="244a7-106">For example, some types become less important as the technology they support is replaced by a new technology, and some methods are superseded by newer methods that are superior in some way.</span></span>

<span data-ttu-id="244a7-107">.NET Framework と共通言語ランタイムでは、下位互換性をサポートするように努めています (.NET Framework の特定のバージョンで開発したアプリケーションを、.NET Framework の次期バージョンで実行できるようにするためです)。</span><span class="sxs-lookup"><span data-stu-id="244a7-107">.NET Framework and the common language runtime strive to support backward compatibility (allowing applications that were developed with one version of .NET Framework to run on the next version of .NET Framework).</span></span> <span data-ttu-id="244a7-108">そのため、型または型のメンバーを単純に削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="244a7-108">This makes it difficult to simply remove a type or a type member.</span></span> <span data-ttu-id="244a7-109">そこで、.NET では、型または型のメンバーが使用されなくなったことを示すために、その型またはメンバーを旧式 (互換性のために残されている) または非推奨として指定しています。</span><span class="sxs-lookup"><span data-stu-id="244a7-109">Instead, .NET indicates that a type or a type member should no longer be used by marking it as obsolete or deprecated.</span></span> <span data-ttu-id="244a7-110">型またはメンバーを非推奨とする場合は、開発者がその型またはメンバーが削除予定であることを認識してその削除に対応できるように、指定を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="244a7-110">Deprecating a type or a member involves marking it so that developers are aware it will go away and have time to respond to its removal.</span></span> <span data-ttu-id="244a7-111">ただし、そのような型またはメンバーを使用する既存のコードは、.NET の次期バージョンで引き続き実行できます。</span><span class="sxs-lookup"><span data-stu-id="244a7-111">However, existing code that uses the type or member continues to run in the new version of .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="244a7-112">"*旧式 (互換性のために残されている)* " という用語と "*非推奨*" という用語は、.NET の型とメンバーに対して使用する場合は同じ意味です。</span><span class="sxs-lookup"><span data-stu-id="244a7-112">The terms *obsolete* and *deprecated* have the same meaning when applied to .NET types and members.</span></span>

## <a name="the-obsoleteattribute-attribute"></a><span data-ttu-id="244a7-113">ObsoleteAttribute 属性</span><span class="sxs-lookup"><span data-stu-id="244a7-113">The ObsoleteAttribute attribute</span></span>

<span data-ttu-id="244a7-114">.NET Framework では、型または型のメンバーが旧式であることを示すために、その型またはメンバーに <xref:System.ObsoleteAttribute> 属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="244a7-114">The .NET Framework indicates that a type or type member is obsolete by marking it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="244a7-115">この属性が型またはメンバーに適用されている場合、その型またはメンバーは .NET Framework の将来のバージョンで削除される予定であることを意味します。ただし、そのメンバーを使用するコンパイル済みコードに影響はありません。</span><span class="sxs-lookup"><span data-stu-id="244a7-115">Applying the attribute to a type or member indicates that type or member will be removed in some future version of the .NET Framework without breaking compiled code that uses that member.</span></span>

<span data-ttu-id="244a7-116">型または型のメンバーが旧式であることを示す以外に、<xref:System.ObsoleteAttribute> は、その型またはメンバーが含まれているソース コードをコンパイラで処理する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="244a7-116">In addition to indicating that a type or a type member is obsolete, <xref:System.ObsoleteAttribute> defines how the compiler handles source code that includes that type or member.</span></span> <span data-ttu-id="244a7-117">コードをコンパイルするが警告メッセージを出力するようにすることも、旧式の型またはメンバーの使用をエラーとして扱うこともできます。</span><span class="sxs-lookup"><span data-stu-id="244a7-117">The compiler can compile the code but emit a warning message, or it can treat the use of the type or member as an error.</span></span> <span data-ttu-id="244a7-118">前者の場合、コードを正常にコンパイルできますが、警告メッセージによって型またはメンバーが旧式であることが示されます。</span><span class="sxs-lookup"><span data-stu-id="244a7-118">In the first case, the code can successfully compile, but a warning message indicates that the type or member is obsolete.</span></span> <span data-ttu-id="244a7-119">後者の場合、コンパイルは失敗します。</span><span class="sxs-lookup"><span data-stu-id="244a7-119">In the second case, compilation fails.</span></span>

<span data-ttu-id="244a7-120">コンパイルで警告メッセージではなくエラーが生成される場合でも、<xref:System.ObsoleteAttribute> は実行時の動作には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="244a7-120">Even if compilation produces an error instead of a warning message, <xref:System.ObsoleteAttribute> does not affect run-time behavior.</span></span> <span data-ttu-id="244a7-121">つまり、旧式の型またはメンバーを使用しているが正常にコンパイルされたアプリケーションは、常に正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="244a7-121">That is, applications that use the type or member and that have compiled successfully will always run successfully.</span></span> <span data-ttu-id="244a7-122">旧式の型またはメンバーを使用するアプリケーションを再コンパイルしようとした場合にのみ失敗します。</span><span class="sxs-lookup"><span data-stu-id="244a7-122">Only the attempt to recompile an application that uses the type or member fails.</span></span>

## <a name="how-to-handle-obsolete-types-and-members"></a><span data-ttu-id="244a7-123">旧式の型とメンバーを処理する方法</span><span class="sxs-lookup"><span data-stu-id="244a7-123">How to handle obsolete types and members</span></span>

<span data-ttu-id="244a7-124">既存のコードをアップグレードし、再コンパイルする場合に、コンパイラの警告を生成する旧式の型またはメンバーをアプリケーションで使用しても、まったく問題ありません。</span><span class="sxs-lookup"><span data-stu-id="244a7-124">When you upgrade and recompile existing code, using an obsolete type or member that produces a compiler warning in your application is perfectly acceptable.</span></span> <span data-ttu-id="244a7-125">ただし、コンパイラの警告メッセージを確認して、アプリケーション コードを変更する必要があるかどうか判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="244a7-125">However, you should review the compiler warning message to determine whether you should change your application code.</span></span> <span data-ttu-id="244a7-126">代わりとなる適切な方法がメッセージに示されていない場合は、次のいずれかの操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="244a7-126">If the message does not point to a suitable alternative, you should do either of the following:</span></span>

- <span data-ttu-id="244a7-127">可能であれば、コードを変更して旧式の型またはメンバーの使用を止めます。</span><span class="sxs-lookup"><span data-stu-id="244a7-127">Change your code by removing the use of the type or member, if possible.</span></span>

     <span data-ttu-id="244a7-128">\- または -</span><span class="sxs-lookup"><span data-stu-id="244a7-128">-or-</span></span>

- <span data-ttu-id="244a7-129">このテクノロジ分野に関するドキュメントを確認して、非推奨の機能の使用に対する対応方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="244a7-129">Review the documentation for this technology area to determine how to respond to the deprecation.</span></span>

<span data-ttu-id="244a7-130">既存のコードは、.NET Framework の新しいバージョンに対して再コンパイルすることはできません。</span><span class="sxs-lookup"><span data-stu-id="244a7-130">You may choose not to recompile existing code against a later version of the .NET Framework.</span></span> <span data-ttu-id="244a7-131">代わりに、既存のコンパイル済みコードの実行対象である .NET Framework のバージョンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="244a7-131">Instead, you can specify the version of the .NET Framework against which your existing compiled code runs.</span></span> <span data-ttu-id="244a7-132">たとえば、.NET Framework 3.5 に対してコンパイルされた app1.exe というアプリケーションがあるものの、このアプリケーションを .NET Framework 4.5 に対して実行する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="244a7-132">For example, suppose that you have an application named app1.exe that was compiled against the .NET Framework 3.5, but you want the application to run against the .NET Framework 4.5.</span></span> <span data-ttu-id="244a7-133">この場合、次の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="244a7-133">This requires the following steps:</span></span>

1. <span data-ttu-id="244a7-134">メイン実行可能ファイルの構成ファイルを作成し、その名前を *appName*.exe.config にします。*appName* は、アプリケーションの実行可能ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="244a7-134">Create a configuration file for your main executable and name it *appName*.exe.config, where *appName* is the name of the application executable.</span></span> <span data-ttu-id="244a7-135">このトピックの例の *app1.exe* というアプリケーションの場合は、*app1.exe.config* という名前の構成ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="244a7-135">For the application named *app1.exe* in our example, you would create a configuration file named *app1.exe.config*.</span></span>

2. <span data-ttu-id="244a7-136">次のコードを構成ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="244a7-136">Add the following to the configuration file.</span></span>

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

<span data-ttu-id="244a7-137">.NET Framework の特定のバージョンを対象とするには、次の文字列値のいずれかを `version` 属性に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="244a7-137">To target a specific version of .NET Framework, assign one of the following string values to the `version` attribute:</span></span>

|<span data-ttu-id="244a7-138">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="244a7-138">.NET Framework version</span></span>|<span data-ttu-id="244a7-139">`version` 文字列</span><span class="sxs-lookup"><span data-stu-id="244a7-139">`version` string</span></span>|
|-|-|
|<span data-ttu-id="244a7-140">4.8</span><span class="sxs-lookup"><span data-stu-id="244a7-140">4.8</span></span>|<span data-ttu-id="244a7-141">v4.0</span><span class="sxs-lookup"><span data-stu-id="244a7-141">v4.0</span></span>|
|<span data-ttu-id="244a7-142">4.7 (4.7.1 と 4.7.2 を含む)</span><span class="sxs-lookup"><span data-stu-id="244a7-142">4.7 (including 4.7.1 and 4.7.2)</span></span>|<span data-ttu-id="244a7-143">v4.0</span><span class="sxs-lookup"><span data-stu-id="244a7-143">v4.0</span></span>|
|<span data-ttu-id="244a7-144">4.6 (4.6.1 と 4.6.2 を含む)</span><span class="sxs-lookup"><span data-stu-id="244a7-144">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="244a7-145">v4.0</span><span class="sxs-lookup"><span data-stu-id="244a7-145">v4.0</span></span>|
|<span data-ttu-id="244a7-146">4.5 (4.5.1 および 4.5.2 を含む)</span><span class="sxs-lookup"><span data-stu-id="244a7-146">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="244a7-147">v4.0</span><span class="sxs-lookup"><span data-stu-id="244a7-147">v4.0</span></span>|
|<span data-ttu-id="244a7-148">4</span><span class="sxs-lookup"><span data-stu-id="244a7-148">4</span></span>|<span data-ttu-id="244a7-149">v4.0</span><span class="sxs-lookup"><span data-stu-id="244a7-149">v4.0</span></span>|
|<span data-ttu-id="244a7-150">3.5</span><span class="sxs-lookup"><span data-stu-id="244a7-150">3.5</span></span>|<span data-ttu-id="244a7-151">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="244a7-151">v2.0.50727</span></span>|
|<span data-ttu-id="244a7-152">2.0</span><span class="sxs-lookup"><span data-stu-id="244a7-152">2.0</span></span>|<span data-ttu-id="244a7-153">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="244a7-153">v2.0.50727</span></span>|
|<span data-ttu-id="244a7-154">1.1</span><span class="sxs-lookup"><span data-stu-id="244a7-154">1.1</span></span>|<span data-ttu-id="244a7-155">v1.1.4322</span><span class="sxs-lookup"><span data-stu-id="244a7-155">v1.1.4322</span></span>|
|<span data-ttu-id="244a7-156">1</span><span class="sxs-lookup"><span data-stu-id="244a7-156">1.0</span></span>|<span data-ttu-id="244a7-157">v1.0.3705</span><span class="sxs-lookup"><span data-stu-id="244a7-157">v1.0.3705</span></span>|

## <a name="obsolete-apis-for-net-framework-45-and-later-versions"></a><span data-ttu-id="244a7-158">.NET Framework 4.5 以降のバージョンの互換性のために残されている API</span><span class="sxs-lookup"><span data-stu-id="244a7-158">Obsolete APIs for .NET Framework 4.5 and later versions</span></span>

- [<span data-ttu-id="244a7-159">旧版の .NET Framework の型</span><span class="sxs-lookup"><span data-stu-id="244a7-159">Obsolete Types</span></span>](obsolete-types.md)
- [<span data-ttu-id="244a7-160">互換性のために残されているメンバー</span><span class="sxs-lookup"><span data-stu-id="244a7-160">Obsolete Members</span></span>](obsolete-members.md)

## <a name="obsolete-apis-for-previous-versions"></a><span data-ttu-id="244a7-161">以前のバージョンの互換性のために残されている API</span><span class="sxs-lookup"><span data-stu-id="244a7-161">Obsolete APIs for previous versions</span></span>

- <span data-ttu-id="244a7-162">[.NET Framework 4 で互換性のために残されている型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="244a7-162">[Obsolete Types in .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span></span>
- <span data-ttu-id="244a7-163">[.NET Framework 4 で互換性のために残されているメンバー](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="244a7-163">[Obsolete Members in .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span></span>
- <span data-ttu-id="244a7-164">[.NET Framework 3.5 Obsolete List (.NET Framework 3.5 の互換性のために残されている機能の一覧)](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="244a7-164">[.NET Framework 3.5 Obsolete List](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span></span>
- <span data-ttu-id="244a7-165">[.NET Framework 2.0 Obsolete List (.NET Framework 2.0 の互換性のために残されている機能の一覧)](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="244a7-165">[.NET Framework 2.0 Obsolete List](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="244a7-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="244a7-166">See also</span></span>

- [<span data-ttu-id="244a7-167">\<supportedRuntime> 要素</span><span class="sxs-lookup"><span data-stu-id="244a7-167">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
