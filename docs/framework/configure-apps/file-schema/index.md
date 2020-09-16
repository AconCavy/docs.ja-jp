---
title: .NET Framework の構成ファイル スキーマ
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: ab6f12be01899f5b7e54a7ec2d9675d502d88bc3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555134"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="65821-102">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="65821-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="65821-103">構成ファイルは、設定を変更し、アプリのポリシーを設定するために使用できる標準 XML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="65821-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="65821-104">.NET Framework の構成スキーマは、アプリの動作を制御するために構成ファイルで使用できる要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="65821-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="65821-105">このセクションの目次は、スキーマ、起動時の階層、ランタイム、ネットワーク、およびその他の種類の構成設定を反映しています。</span><span class="sxs-lookup"><span data-stu-id="65821-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="65821-106">構成ファイルの種類、形式、および場所の詳細については、「 [アプリの構成](../index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65821-106">For information about the types, format, and location of configuration files, see [Configure apps](../index.md).</span></span> <span data-ttu-id="65821-107">構成ファイルを直接編集する場合は、XML に関する知識が必要です。</span><span class="sxs-lookup"><span data-stu-id="65821-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65821-108">構成ファイルの XML タグおよび属性では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="65821-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="65821-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="65821-109">In this section</span></span>

<span data-ttu-id="65821-110">[**\<configuration>** Element](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="65821-110">[**\<configuration>** Element](configuration-element.md)</span></span>\
<span data-ttu-id="65821-111">すべての構成ファイルの最上位要素。</span><span class="sxs-lookup"><span data-stu-id="65821-111">The top-level element for all configuration files.</span></span>

<span data-ttu-id="65821-112">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="65821-112">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="65821-113">構成レベルでのアセンブリ バインディング ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="65821-113">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="65821-114">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="65821-114">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span></span>\
<span data-ttu-id="65821-115">インクルードする構成ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="65821-115">Specifies a configuration file to include.</span></span>

<span data-ttu-id="65821-116">[スタートアップ設定スキーマ](./startup/index.md)</span><span class="sxs-lookup"><span data-stu-id="65821-116">[Startup Settings Schema](./startup/index.md)</span></span>\
<span data-ttu-id="65821-117">使用する共通言語ランタイムのバージョンを指定する要素。</span><span class="sxs-lookup"><span data-stu-id="65821-117">Elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="65821-118">[ランタイム設定スキーマ](./runtime/index.md)</span><span class="sxs-lookup"><span data-stu-id="65821-118">[Runtime Settings Schema](./runtime/index.md)</span></span>\
<span data-ttu-id="65821-119">アセンブリバインディングとランタイム動作を構成する要素。</span><span class="sxs-lookup"><span data-stu-id="65821-119">Elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="65821-120">[ネットワーク設定スキーマ](./network/index.md)</span><span class="sxs-lookup"><span data-stu-id="65821-120">[Network Settings Schema](./network/index.md)</span></span>\
<span data-ttu-id="65821-121">.NET Framework がインターネットに接続する方法を指定する要素。</span><span class="sxs-lookup"><span data-stu-id="65821-121">Elements that specify how the .NET Framework connects to the internet.</span></span>

<span data-ttu-id="65821-122">[暗号化設定スキーマ](./cryptography/index.md)</span><span class="sxs-lookup"><span data-stu-id="65821-122">[Cryptography Settings Schema](./cryptography/index.md)</span></span>\
<span data-ttu-id="65821-123">アルゴリズムのフレンドリ名を、暗号化アルゴリズムを実装するクラスにマップする要素。</span><span class="sxs-lookup"><span data-stu-id="65821-123">Elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="65821-124">[構成セクションのスキーマ](configuration-sections-schema.md)</span><span class="sxs-lookup"><span data-stu-id="65821-124">[Configuration Sections Schema](configuration-sections-schema.md)</span></span>\
<span data-ttu-id="65821-125">カスタム設定の構成セクションを作成して使用するために使用される要素。</span><span class="sxs-lookup"><span data-stu-id="65821-125">Elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="65821-126">[トレースおよびデバッグ設定のスキーマ](./trace-debug/index.md)</span><span class="sxs-lookup"><span data-stu-id="65821-126">[Trace and Debug Settings Schema](./trace-debug/index.md)</span></span>\
<span data-ttu-id="65821-127">トレーススイッチとリスナーを指定する要素。</span><span class="sxs-lookup"><span data-stu-id="65821-127">Elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="65821-128">[コンパイラおよび言語プロバイダー設定スキーマ](./compiler/index.md)</span><span class="sxs-lookup"><span data-stu-id="65821-128">[Compiler and Language Provider Settings Schema](./compiler/index.md)</span></span>\
<span data-ttu-id="65821-129">使用可能な言語プロバイダーのコンパイラ構成を指定する要素。</span><span class="sxs-lookup"><span data-stu-id="65821-129">Elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="65821-130">[アプリケーション設定スキーマ](application-settings-schema.md)</span><span class="sxs-lookup"><span data-stu-id="65821-130">[Application Settings Schema](application-settings-schema.md)</span></span>\
<span data-ttu-id="65821-131">Windows フォームまたは ASP.NET アプリケーションで、アプリケーションスコープの設定とユーザースコープの設定を格納および取得できるようにする要素。</span><span class="sxs-lookup"><span data-stu-id="65821-131">Elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="65821-132">[アプリ設定スキーマ](./appsettings/index.md)</span><span class="sxs-lookup"><span data-stu-id="65821-132">[App Settings Schema](./appsettings/index.md)</span></span>\
<span data-ttu-id="65821-133">ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="65821-133">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="65821-134">[Web 設定スキーマ](./web/index.md)</span><span class="sxs-lookup"><span data-stu-id="65821-134">[Web Settings Schema](./web/index.md)</span></span>\
<span data-ttu-id="65821-135">IIS などのホストアプリケーションで ASP.NET がどのように動作するかを構成するための要素。</span><span class="sxs-lookup"><span data-stu-id="65821-135">Elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="65821-136">*Aspnet.config* ファイルで使用します。</span><span class="sxs-lookup"><span data-stu-id="65821-136">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="65821-137">[Windows フォーム構成スキーマ](winforms/index.md)</span><span class="sxs-lookup"><span data-stu-id="65821-137">[Windows Forms Configuration Schema](winforms/index.md)</span></span>\
<span data-ttu-id="65821-138">Windows フォームアプリケーション構成セクション内のすべての要素。マルチモニターや高 DPI のサポートなどのカスタマイズが含まれます。</span><span class="sxs-lookup"><span data-stu-id="65821-138">All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high-DPI support.</span></span>

<span data-ttu-id="65821-139">[WCF 構成スキーマ](./wcf/index.md)</span><span class="sxs-lookup"><span data-stu-id="65821-139">[WCF Configuration Schema](./wcf/index.md)</span></span>\
<span data-ttu-id="65821-140">WCF サービスおよびクライアントアプリケーションを構成できるすべての要素。</span><span class="sxs-lookup"><span data-stu-id="65821-140">All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="65821-141">[WCF ディレクティブの構文](./wcf-directive/index.md)</span><span class="sxs-lookup"><span data-stu-id="65821-141">[WCF Directive Syntax](./wcf-directive/index.md)</span></span>\
<span data-ttu-id="65821-142">`@ServiceHost`.Svc コンパイラによって使用されるページ固有の属性を定義するディレクティブについて説明します。</span><span class="sxs-lookup"><span data-stu-id="65821-142">Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="65821-143">[WIF 構成スキーマ](windows-identity-foundation/index.md)</span><span class="sxs-lookup"><span data-stu-id="65821-143">[WIF Configuration Schema](windows-identity-foundation/index.md)</span></span>\
<span data-ttu-id="65821-144">Windows Identity Foundation (WIF) 構成スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="65821-144">All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="65821-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="65821-145">Related sections</span></span>

<span data-ttu-id="65821-146">[リモート処理設定スキーマ](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="65821-146">[Remoting Settings Schema](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span>\
<span data-ttu-id="65821-147">リモート処理を実装するクライアント アプリケーションとサーバー アプリケーションを構成する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="65821-147">Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="65821-148">[ASP.NET 設定スキーマ](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="65821-148">[ASP.NET Settings Schema](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span>\
<span data-ttu-id="65821-149">ASP.NET Web アプリケーションの動作を制御する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="65821-149">Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="65821-150">[Web サービス設定スキーマ](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="65821-150">[Web Services Settings Schema](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span>\
<span data-ttu-id="65821-151">ASP.NET Web サービス、およびそれらのクライアントの動作を制御する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="65821-151">Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="65821-152">[.NET Framework アプリの構成](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="65821-152">[Configuring .NET Framework Apps](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span></span>\
<span data-ttu-id="65821-153">セキュリティ、アセンブリのバインディング、および .NET Framework のリモート処理を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="65821-153">Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
