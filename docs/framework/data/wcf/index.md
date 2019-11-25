---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 1ce152b84f17a35982a75f54b5418623ba39210f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975233"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="50f7d-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="50f7d-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="50f7d-103">WCF Data Services (旧称 "ADO.NET Data Services" と呼ばれていた) は、 [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)のセマンティクスを使用して、Web またはイントラネット上のデータを公開および使用するための Open Data Protocol (OData) を使用するサービスを作成できるようにする、.NET Framework のコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="50f7d-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span></span> <span data-ttu-id="50f7d-104">OData は、URI でアドレス指定できるリソースとしてデータを公開します。</span><span class="sxs-lookup"><span data-stu-id="50f7d-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="50f7d-105">標準的な HTTP 動詞である GET、PUT、POST、および DELETE を使用してデータにアクセスし、変更できます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="50f7d-106">OData は、 [Entity Data Model](../adonet/entity-data-model.md)のエンティティとリレーションシップの規則を使用して、アソシエーションによって関連付けられたエンティティのセットとしてリソースを公開します。</span><span class="sxs-lookup"><span data-stu-id="50f7d-106">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="50f7d-107">WCF Data Services は、OData プロトコルを使用してリソースのアドレス指定と更新を行います。</span><span class="sxs-lookup"><span data-stu-id="50f7d-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="50f7d-108">このようにして、OData をサポートする任意のクライアントからこれらのサービスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="50f7d-109">OData を使用すると、一般的な転送形式 (Atom、データを XML として交換および更新するための標準のセット)、および AJAX で幅広く使用されるテキストベースのデータ交換形式である JavaScript Object Notation (JSON) を使用して、リソースにデータを要求して書き込むことができます。プログラム.</span><span class="sxs-lookup"><span data-stu-id="50f7d-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="50f7d-110">WCF Data Services は、さまざまなソースから送信されたデータを OData フィードとして公開できます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="50f7d-111">Visual Studio tools を使用すると、ADO.NET Entity Framework データモデルを使用して、OData ベースのサービスを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="50f7d-112">また、共通言語ランタイム (CLR) クラスに基づいて OData フィードを作成したり、遅延バインディングまたは型指定されていないデータを作成したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="50f7d-113">WCF Data Services には、一般的な .NET Framework クライアントアプリケーション用と Silverlight ベースのアプリケーション用のクライアントライブラリのセットも含まれています。</span><span class="sxs-lookup"><span data-stu-id="50f7d-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="50f7d-114">これらのクライアントライブラリは、.NET Framework や Silverlight などの環境から OData フィードにアクセスするときに、オブジェクトベースのプログラミングモデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="50f7d-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="50f7d-115">開始すべき場所</span><span class="sxs-lookup"><span data-stu-id="50f7d-115">Where Should I Start?</span></span>

<span data-ttu-id="50f7d-116">興味に応じて、次のトピックのいずれかで WCF Data Services の使用を開始することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="50f7d-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="50f7d-117">すぐに使用を開始する…</span><span class="sxs-lookup"><span data-stu-id="50f7d-117">I want to jump right in...</span></span>

- [<span data-ttu-id="50f7d-118">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="50f7d-118">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="50f7d-119">はじめに</span><span class="sxs-lookup"><span data-stu-id="50f7d-119">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

- [<span data-ttu-id="50f7d-120">Silverlight クイックスタート</span><span class="sxs-lookup"><span data-stu-id="50f7d-120">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

- [<span data-ttu-id="50f7d-121">Windows Phone 開発用の Silverlight クイック スタート</span><span class="sxs-lookup"><span data-stu-id="50f7d-121">Silverlight Quickstart for Windows Phone Development</span></span>](https://go.microsoft.com/fwlink/?LinkID=214535)

<span data-ttu-id="50f7d-122">コードを表示するだけです...</span><span class="sxs-lookup"><span data-stu-id="50f7d-122">Just show me some code...</span></span>

- [<span data-ttu-id="50f7d-123">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="50f7d-123">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="50f7d-124">方法: データ サービス クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="50f7d-124">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="50f7d-125">方法: Windows Presentation Foundation 要素にデータをバインドする</span><span class="sxs-lookup"><span data-stu-id="50f7d-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="50f7d-126">OData の詳細を知りたい...</span><span class="sxs-lookup"><span data-stu-id="50f7d-126">I want to know more about OData...</span></span>

- [<span data-ttu-id="50f7d-127">ホワイト ペーパー: OData の概要</span><span class="sxs-lookup"><span data-stu-id="50f7d-127">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- [<span data-ttu-id="50f7d-128">Open Data Protocol Web サイト</span><span class="sxs-lookup"><span data-stu-id="50f7d-128">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

- [<span data-ttu-id="50f7d-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="50f7d-129">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

- [<span data-ttu-id="50f7d-130">OData: よく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="50f7d-130">OData: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/?LinkId=185867)

<span data-ttu-id="50f7d-131">ビデオを見ています...</span><span class="sxs-lookup"><span data-stu-id="50f7d-131">I want to watch some videos...</span></span>

- [<span data-ttu-id="50f7d-132">WCF Data Services のビギナーズ ガイド</span><span class="sxs-lookup"><span data-stu-id="50f7d-132">Beginner's Guide to WCF Data Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=220864)

- [<span data-ttu-id="50f7d-133">WCF Data Services 開発者用ビデオ</span><span class="sxs-lookup"><span data-stu-id="50f7d-133">WCF Data Services Developer Videos</span></span>](https://go.microsoft.com/fwlink/?LinkId=220861)

- [<span data-ttu-id="50f7d-134">OData: 開発者 Web サイト</span><span class="sxs-lookup"><span data-stu-id="50f7d-134">OData: Developers Web site</span></span>](https://go.microsoft.com/fwlink/?LinkId=185866)

<span data-ttu-id="50f7d-135">エンドツーエンドのサンプルを確認するには...</span><span class="sxs-lookup"><span data-stu-id="50f7d-135">I want to see end-to-end samples...</span></span>

- [<span data-ttu-id="50f7d-136">MSDN サンプル ギャラリーの WCF Data Services ドキュメントのサンプル</span><span class="sxs-lookup"><span data-stu-id="50f7d-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkID=220865)

- [<span data-ttu-id="50f7d-137">MSDN サンプル ギャラリーのその他の WCF Data Services サンプル</span><span class="sxs-lookup"><span data-stu-id="50f7d-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkId=220866)

- [<span data-ttu-id="50f7d-138">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="50f7d-138">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

<span data-ttu-id="50f7d-139">Visual Studio との統合について知りたい</span><span class="sxs-lookup"><span data-stu-id="50f7d-139">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="50f7d-140">データ サービス クライアント ライブラリの生成</span><span class="sxs-lookup"><span data-stu-id="50f7d-140">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="50f7d-141">データ サービスの作成</span><span class="sxs-lookup"><span data-stu-id="50f7d-141">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="50f7d-142">Entity Framework プロバイダー</span><span class="sxs-lookup"><span data-stu-id="50f7d-142">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="50f7d-143">何に使用できるかを知りたい</span><span class="sxs-lookup"><span data-stu-id="50f7d-143">What can I do with it?</span></span>

- [<span data-ttu-id="50f7d-144">概要</span><span class="sxs-lookup"><span data-stu-id="50f7d-144">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="50f7d-145">ホワイト ペーパー: OData の概要</span><span class="sxs-lookup"><span data-stu-id="50f7d-145">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- [<span data-ttu-id="50f7d-146">アプリケーション シナリオ</span><span class="sxs-lookup"><span data-stu-id="50f7d-146">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="50f7d-147">Silverlight を使用するには...</span><span class="sxs-lookup"><span data-stu-id="50f7d-147">I want to use Silverlight...</span></span>

- [<span data-ttu-id="50f7d-148">Silverlight クイックスタート</span><span class="sxs-lookup"><span data-stu-id="50f7d-148">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

- [<span data-ttu-id="50f7d-149">WCF Data Services (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="50f7d-149">WCF Data Services (Silverlight)</span></span>](https://go.microsoft.com/fwlink/?LinkID=143149)

- [<span data-ttu-id="50f7d-150">Silverlight について</span><span class="sxs-lookup"><span data-stu-id="50f7d-150">Getting Started with Silverlight</span></span>](https://go.microsoft.com/fwlink/?LinkId=148366)

<span data-ttu-id="50f7d-151">LINQ...</span><span class="sxs-lookup"><span data-stu-id="50f7d-151">I want to use LINQ...</span></span>

- [<span data-ttu-id="50f7d-152">データ サービスに対するクエリ</span><span class="sxs-lookup"><span data-stu-id="50f7d-152">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="50f7d-153">LINQ に関する留意点</span><span class="sxs-lookup"><span data-stu-id="50f7d-153">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="50f7d-154">方法: データ サービス クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="50f7d-154">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="50f7d-155">まだいくつかの情報が必要です...</span><span class="sxs-lookup"><span data-stu-id="50f7d-155">I still need some more information...</span></span>

- [<span data-ttu-id="50f7d-156">WCF Data Services チームのブログ</span><span class="sxs-lookup"><span data-stu-id="50f7d-156">WCF Data Services Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=150511)

- [<span data-ttu-id="50f7d-157">リソース</span><span class="sxs-lookup"><span data-stu-id="50f7d-157">Resources</span></span>](wcf-data-services-resources.md)

- [<span data-ttu-id="50f7d-158">WCF Data Services デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="50f7d-158">WCF Data Services Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=220868)

- [<span data-ttu-id="50f7d-159">Open Data Protocol Web サイト</span><span class="sxs-lookup"><span data-stu-id="50f7d-159">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a><span data-ttu-id="50f7d-160">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="50f7d-160">In This Section</span></span>

[<span data-ttu-id="50f7d-161">概要</span><span class="sxs-lookup"><span data-stu-id="50f7d-161">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="50f7d-162">WCF Data Services で使用できる機能の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="50f7d-162">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="50f7d-163">[WCF Data Services 5.0 の新機能](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="50f7d-163">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="50f7d-164">WCF Data Services の新機能と、新しい OData 機能のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="50f7d-164">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="50f7d-165">はじめに</span><span class="sxs-lookup"><span data-stu-id="50f7d-165">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="50f7d-166">WCF Data Services を使用して OData フィードを公開および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="50f7d-166">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="50f7d-167">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="50f7d-167">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="50f7d-168">OData フィードを公開するデータサービスを作成および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="50f7d-168">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="50f7d-169">WCF Data Services クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="50f7d-169">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="50f7d-170">クライアントライブラリを使用して、.NET Framework クライアントアプリケーションから OData フィードを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="50f7d-170">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="50f7d-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="50f7d-171">See also</span></span>

- [<span data-ttu-id="50f7d-172">Representational State Transfer (REST)</span><span class="sxs-lookup"><span data-stu-id="50f7d-172">Representational State Transfer (REST)</span></span>](https://go.microsoft.com/fwlink/?LinkId=113919)
