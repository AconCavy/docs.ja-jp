---
title: Azure での F# の使用
description: F# での Azure サービスの使用に関するガイド
author: sylvanc
ms.date: 09/22/2016
ms.openlocfilehash: f074ac192f6dedbadf8132430cf27dc5865e6371
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501821"
---
# <a name="using-f-on-azure"></a><span data-ttu-id="efe1d-103">Azure での F# の使用</span><span class="sxs-lookup"><span data-stu-id="efe1d-103">Using F# on Azure</span></span>

<span data-ttu-id="efe1d-104">F# は卓越したクラウド プログラミング言語であり、Web アプリケーション、クラウド サービス、クラウドでホストされるマイクロ サービスの作成、および拡張性の高いデータの処理に頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-104">F# is a superb language for cloud programming and is frequently used to write web applications, cloud services, cloud-hosted microservices, and for scalable data processing.</span></span>

<span data-ttu-id="efe1d-105">次のセクションでは、広範囲の Azure サービスで F# を使用する方法に関するリソースを紹介します。</span><span class="sxs-lookup"><span data-stu-id="efe1d-105">In the following sections, you will find resources on how to use a range of Azure services with F#.</span></span>

> [!NOTE]
> <span data-ttu-id="efe1d-106">特定の Azure サービスがこのドキュメント セットに記載されていない場合、そのサービスの Azure Functions または .NET のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe1d-106">If a particular Azure service isn't in this documentation set, please consult either the Azure Functions or .NET documentation for that service.</span></span> <span data-ttu-id="efe1d-107">言語に依存しない言語固有のドキュメントを必要としない一部の Azure サービスはここに記載されていません。</span><span class="sxs-lookup"><span data-stu-id="efe1d-107">Some Azure services are language-independent and require no language-specific documentation and are not listed here.</span></span>

## <a name="using-azure-virtual-machines-with-f"></a><span data-ttu-id="efe1d-108">F\# での Azure Virtual Machines の使用</span><span class="sxs-lookup"><span data-stu-id="efe1d-108">Using Azure Virtual Machines with F\#</span></span>

<span data-ttu-id="efe1d-109">Azure では、さまざまな仮想マシン (VM) の構成をサポートします。[Linux および Windows の仮想マシン](https://azure.microsoft.com/services/virtual-machines/)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe1d-109">Azure supports a wide range of virtual machine (VM) configurations, see [Linux and Azure Virtual Machines](https://azure.microsoft.com/services/virtual-machines/).</span></span>

<span data-ttu-id="efe1d-110">実行、コンパイル、スクリプト作成のために F# を仮想マシンにインストールするには、「[Using F# on Linux](https://fsharp.org/use/linux)」(Linux での F# の使用) および「[Using F# on Windows](https://fsharp.org/use/windows)」(Windows での F# の使用) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe1d-110">To install F# on a virtual machine for execution, compilation and/or scripting see [Using F# on Linux](https://fsharp.org/use/linux) and [Using F# on Windows](https://fsharp.org/use/windows).</span></span>

## <a name="using-azure-functions-with-f"></a><span data-ttu-id="efe1d-111">F\#での Azure Functions の使用</span><span class="sxs-lookup"><span data-stu-id="efe1d-111">Using Azure Functions with F\#</span></span>

<span data-ttu-id="efe1d-112">[Azure Functions](https://azure.microsoft.com/services/functions/) を使用すると、クラウドで小さなコードの集まりまたは "関数" を簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-112">[Azure Functions](https://azure.microsoft.com/services/functions/) is a solution for easily running small pieces of code, or "functions," in the cloud.</span></span> <span data-ttu-id="efe1d-113">問題を解決するために必要なコードのみを手元で作成することができます。アプリケーション全体またはコードを実行するためのインフラストラクチャについて心配する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="efe1d-113">You can write just the code you need for the problem at hand, without worrying about a whole application or the infrastructure to run it.</span></span> <span data-ttu-id="efe1d-114">関数は、Azure ストレージおよびその他のクラウドでホストされるリソースでイベントに接続されます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-114">Your functions are connected to events in Azure storage and other cloud-hosted resources.</span></span> <span data-ttu-id="efe1d-115">データは、関数の引数を使用して F# 関数に渡されます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-115">Data flows into your F# functions via function arguments.</span></span> <span data-ttu-id="efe1d-116">必要に応じて任意の開発言語を使用し、スケールを Azure に任せることができます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-116">You can use your development language of choice, trusting Azure to scale as needed.</span></span>

<span data-ttu-id="efe1d-117">Azure Functions は、F# を第一級の言語としてサポートし、F# コードを効率と拡張性に優れた方法で事後対応型で実行します。</span><span class="sxs-lookup"><span data-stu-id="efe1d-117">Azure Functions support F# as a first-class language with efficient, reactive, scalable execution of F# code.</span></span> <span data-ttu-id="efe1d-118">Azure Functions で F# を使用する方法のリファレンス ドキュメントについては、「[Azure Functions F# 開発者向けリファレンス](/azure/azure-functions/functions-reference-fsharp)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe1d-118">See the [Azure Functions F# Developer Reference](/azure/azure-functions/functions-reference-fsharp) for reference documentation on how to use F# with Azure Functions.</span></span>

<span data-ttu-id="efe1d-119">Azure Functions と F# の使用に関する他のリソース:</span><span class="sxs-lookup"><span data-stu-id="efe1d-119">Other resources for using Azure Functions and F#:</span></span>

* [<span data-ttu-id="efe1d-120">Suave を使用した F# での Azure Functions のスケールアップ</span><span class="sxs-lookup"><span data-stu-id="efe1d-120">Scale Up Azure Functions in F# Using Suave</span></span>](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [<span data-ttu-id="efe1d-121">F# で Azure 関数を作成する方法</span><span class="sxs-lookup"><span data-stu-id="efe1d-121">How to create Azure function in F#</span></span>](https://www.mnie.me/azurefunctions)
* [<span data-ttu-id="efe1d-122">Azure Functions での Azure 型プロバイダーの使用</span><span class="sxs-lookup"><span data-stu-id="efe1d-122">Using the Azure Type Provider with Azure Functions</span></span>](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a><span data-ttu-id="efe1d-123">F\#での Azure Storage の使用</span><span class="sxs-lookup"><span data-stu-id="efe1d-123">Using Azure Storage with F\#</span></span>

<span data-ttu-id="efe1d-124">Azure Storage は、顧客のニーズに合う耐久性、可用性、スケーラビリティを必要とする最新のアプリケーション向けのストレージ サービスの基本階層です。</span><span class="sxs-lookup"><span data-stu-id="efe1d-124">Azure Storage is a base layer of storage services for modern applications that rely on durability, availability, and scalability to meet the needs of customers.</span></span> <span data-ttu-id="efe1d-125">F# プログラムは、次の記事で説明されている方法を使用して、Azure Storage サービスと直接やり取りできます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-125">F# programs can interact directly with Azure storage services, using the techniques described in the following articles.</span></span>

* [<span data-ttu-id="efe1d-126">F# を使用した Azure Blob Storage の概要</span><span class="sxs-lookup"><span data-stu-id="efe1d-126">Get started with Azure Blob storage using F#</span></span>](blob-storage.md)
* [<span data-ttu-id="efe1d-127">F# を使用した Azure File Storage の概要</span><span class="sxs-lookup"><span data-stu-id="efe1d-127">Get started with Azure File storage using F#</span></span>](file-storage.md)
* [<span data-ttu-id="efe1d-128">F# を使用した Azure Queue Storage の概要</span><span class="sxs-lookup"><span data-stu-id="efe1d-128">Get started with Azure Queue storage using F#</span></span>](queue-storage.md)
* [<span data-ttu-id="efe1d-129">F# を使用した Azure Table Storage の概要</span><span class="sxs-lookup"><span data-stu-id="efe1d-129">Get started with Azure Table storage using F#</span></span>](table-storage.md)

<span data-ttu-id="efe1d-130">Azure Storage は、明示的な API 呼び出しではなく、宣言型の構成を使って Azure Functions と組み合わせても使用できます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-130">Azure Storage can also be used in conjunction with Azure Functions through declarative configuration rather than explicit API calls.</span></span> <span data-ttu-id="efe1d-131">F# の例を含む「[Azure Functions における Storage BLOB のバインド](/azure/azure-functions/functions-bindings-storage)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe1d-131">See [Azure Functions triggers and bindings for Azure Storage](/azure/azure-functions/functions-bindings-storage) which includes F# examples.</span></span>

## <a name="using-azure-app-service-with-f"></a><span data-ttu-id="efe1d-132">F\#での Azure App Service の使用</span><span class="sxs-lookup"><span data-stu-id="efe1d-132">Using Azure App Service with F\#</span></span>

<span data-ttu-id="efe1d-133">[Azure App Service](https://azure.microsoft.com/services/app-service/) は、クラウドまたはオンプレミスでどこにでもデータに接続する強力な Web アプリおよびモバイル アプリをビルドするためのクラウド プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="efe1d-133">[Azure App Service](https://azure.microsoft.com/services/app-service/) is a cloud platform to build powerful web and mobile apps that connect to data anywhere, in the cloud or on-premises.</span></span>

* [<span data-ttu-id="efe1d-134">F# Azure Web API の例</span><span class="sxs-lookup"><span data-stu-id="efe1d-134">F# Azure Web API example</span></span>](https://github.com/fsprojects/azure-webapi-example)
* [<span data-ttu-id="efe1d-135">Azure 上の web アプリケーションでの F# のホスト</span><span class="sxs-lookup"><span data-stu-id="efe1d-135">Hosting F# in a web application on Azure</span></span>](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a><span data-ttu-id="efe1d-136">Azure HDInsight と F# での Apache Spark の使用</span><span class="sxs-lookup"><span data-stu-id="efe1d-136">Using Apache Spark with F# with Azure HDInsight</span></span>

<span data-ttu-id="efe1d-137">[Apache Spark for Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) は、大規模なデータ分析アプリケーションを実行するオープン ソースの処理のフレームワークです。</span><span class="sxs-lookup"><span data-stu-id="efe1d-137">[Apache Spark for Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) is an open source processing framework that runs large-scale data analytics applications.</span></span> <span data-ttu-id="efe1d-138">Azure では、Apache Spark は簡単かつ低コストで展開できます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-138">Azure makes Apache Spark easy and cost effective to deploy.</span></span> <span data-ttu-id="efe1d-139">F# で、Spark 用の .NET API である [Mobius](https://github.com/Microsoft/Mobius) を使用して、Spark アプリケーションを開発します。</span><span class="sxs-lookup"><span data-stu-id="efe1d-139">Develop your Spark application in F# using [Mobius](https://github.com/Microsoft/Mobius), a .NET API for Spark.</span></span>

* [<span data-ttu-id="efe1d-140">Mobius を使用した F# での Spark アプリケーションの実装</span><span class="sxs-lookup"><span data-stu-id="efe1d-140">Implementing Spark Apps in F# using Mobius</span></span>](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [<span data-ttu-id="efe1d-141">Mobius を使用する F# Spark アプリケーションの例</span><span class="sxs-lookup"><span data-stu-id="efe1d-141">Example F# Spark Apps using Mobius</span></span>](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-cosmos-db-with-f"></a><span data-ttu-id="efe1d-142">F\# での Azure Cosmos DB の使用</span><span class="sxs-lookup"><span data-stu-id="efe1d-142">Using Azure Cosmos DB with F\#</span></span>

<span data-ttu-id="efe1d-143">[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) は、可用性が高く世界各地に分散されたアプリ向けの NoSQL サービスです。</span><span class="sxs-lookup"><span data-stu-id="efe1d-143">[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) is a NoSQL service for highly available, globally distributed apps.</span></span>

<span data-ttu-id="efe1d-144">Azure Cosmos DB は、2 つの方法で F# で使用できます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-144">Azure Cosmos DB can be used with F# in two ways:</span></span>

1. <span data-ttu-id="efe1d-145">Azure Cosmos DB コレクションに対する変更に反応するか変更を発生させる F# Azure Functions を作成する。</span><span class="sxs-lookup"><span data-stu-id="efe1d-145">Through the creation of F# Azure Functions which react to or cause changes to Azure Cosmos DB collections.</span></span> <span data-ttu-id="efe1d-146">「[Azure Functions の Azure Cosmos DB バインド](/azure/azure-functions/functions-bindings-cosmosdb)」を参照してください。または</span><span class="sxs-lookup"><span data-stu-id="efe1d-146">See [Azure Cosmos DB bindings for Azure Functions](/azure/azure-functions/functions-bindings-cosmosdb), or</span></span>
2. <span data-ttu-id="efe1d-147">[Azure Cosmos DB .NET SDK for SQL API](/azure/cosmos-db/sql-api-sdk-dotnet) を使用する。</span><span class="sxs-lookup"><span data-stu-id="efe1d-147">By using the [Azure Cosmos DB .NET SDK for SQL API](/azure/cosmos-db/sql-api-sdk-dotnet).</span></span> <span data-ttu-id="efe1d-148">関連するサンプルが C# であります。</span><span class="sxs-lookup"><span data-stu-id="efe1d-148">The related samples are in C#.</span></span>

## <a name="using-azure-event-hubs-with-f"></a><span data-ttu-id="efe1d-149">F\# での Azure Event Hubs の使用</span><span class="sxs-lookup"><span data-stu-id="efe1d-149">Using Azure Event Hubs with F\#</span></span>

<span data-ttu-id="efe1d-150">[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) は、Web サイト、アプリケーション、およびデバイスからのクラウド スケール テレメトリの取り込みを提供します。</span><span class="sxs-lookup"><span data-stu-id="efe1d-150">[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) provide cloud-scale telemetry ingestion from websites, apps, and devices.</span></span>

<span data-ttu-id="efe1d-151">Azure Event Hubs は、2 つの方法で F# で使用できます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-151">Azure Event Hubs can be used with F# in two ways:</span></span>

1. <span data-ttu-id="efe1d-152">イベントによってトリガーされる F# Azure Functions を作成します。</span><span class="sxs-lookup"><span data-stu-id="efe1d-152">Through the creation of F# Azure Functions which are triggered by events.</span></span> <span data-ttu-id="efe1d-153">「[Azure Functions における Event Hub のバインド](/azure/azure-functions/functions-bindings-event-hubs)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe1d-153">See [Azure Function triggers for Event Hubs](/azure/azure-functions/functions-bindings-event-hubs), or</span></span>
2. <span data-ttu-id="efe1d-154">または、[.NET SDK for Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted) を使用します。</span><span class="sxs-lookup"><span data-stu-id="efe1d-154">By using the [.NET SDK for Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted).</span></span> <span data-ttu-id="efe1d-155">これらの例は C# であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="efe1d-155">Note these examples are in C#.</span></span>

## <a name="using-azure-notification-hubs-with-f"></a><span data-ttu-id="efe1d-156">F\# での Azure Notification Hubs の使用</span><span class="sxs-lookup"><span data-stu-id="efe1d-156">Using Azure Notification Hubs with F\#</span></span>

<span data-ttu-id="efe1d-157">[Azure Notification Hubs](/azure/notification-hubs/) は、任意のバックエンド (クラウドまたはオンプレミス) から任意のモバイル プラットフォームにモバイル プッシュ通知を送信するためのマルチプラット フォームに対応するスケール アウト プッシュ インフラストラクチャです。</span><span class="sxs-lookup"><span data-stu-id="efe1d-157">[Azure Notification Hubs](/azure/notification-hubs/) are multiplatform, scaled-out push infrastructure that enable you to send mobile push notifications from any backend (in the cloud or on-premises) to any mobile platform.</span></span>

<span data-ttu-id="efe1d-158">Azure Notification Hubs は、2 つの方法で F# で使用できます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-158">Azure Notification Hubs can be used with F# in two ways:</span></span>

1. <span data-ttu-id="efe1d-159">通知ハブに結果を送信する F# Azure Functions を作成します。</span><span class="sxs-lookup"><span data-stu-id="efe1d-159">Through the creation of F# Azure Functions which send results to a notification hub.</span></span> <span data-ttu-id="efe1d-160">「[Azure Functions における通知ハブの出力バインド](/azure/azure-functions/functions-bindings-notification-hubs)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe1d-160">See [Azure Function output triggers for Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs), or</span></span>
2. <span data-ttu-id="efe1d-161">または、[.NET SDK for Azure](https://docs.microsoft.com/archive/blogs/azuremobile/push-notifications-using-notification-hub-and-net-backend) を使用します。</span><span class="sxs-lookup"><span data-stu-id="efe1d-161">By using the [.NET SDK for Azure](https://docs.microsoft.com/archive/blogs/azuremobile/push-notifications-using-notification-hub-and-net-backend).</span></span> <span data-ttu-id="efe1d-162">これらの例は C# であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="efe1d-162">Note these examples are in C#.</span></span>

## <a name="implementing-webhooks-on-azure-with-f"></a><span data-ttu-id="efe1d-163">Azure と F\# での Webhook の実装</span><span class="sxs-lookup"><span data-stu-id="efe1d-163">Implementing WebHooks on Azure with F\#</span></span>

<span data-ttu-id="efe1d-164">[Webhook](https://en.wikipedia.org/wiki/Webhook)は、Web 要求によってトリガーされるコールバックです。</span><span class="sxs-lookup"><span data-stu-id="efe1d-164">A [Webhook](https://en.wikipedia.org/wiki/Webhook) is a callback triggered via a web request.</span></span> <span data-ttu-id="efe1d-165">Webhook は、GitHub などのサイトでイベントを通知するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-165">Webhooks are used by sites such as GitHub to signal events.</span></span>

<span data-ttu-id="efe1d-166">[Azure Function F# と Webhook バインド](/azure/azure-functions/functions-bindings-http-webhook)を使用して、Webhook を F# で実装し、Azure でホストすることができます。します。</span><span class="sxs-lookup"><span data-stu-id="efe1d-166">Webhooks can be implemented in F# and hosted on Azure via an [Azure Function in F# with a Webhook Binding](/azure/azure-functions/functions-bindings-http-webhook).</span></span>

## <a name="using-webjobs-with-f"></a><span data-ttu-id="efe1d-167">F\# での Webjobs の使用</span><span class="sxs-lookup"><span data-stu-id="efe1d-167">Using Webjobs with F\#</span></span>

<span data-ttu-id="efe1d-168">[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) は、オンデマンド、継続的、またはスケジュール指定の 3 つの方法で App Service Web アプリで実行できるプログラムです。</span><span class="sxs-lookup"><span data-stu-id="efe1d-168">[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) are programs you can run in your App Service web app in three ways: on demand, continuously, or on a schedule.</span></span>

[<span data-ttu-id="efe1d-169">F# Webjob の例</span><span class="sxs-lookup"><span data-stu-id="efe1d-169">Example F# Webjob</span></span>](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a><span data-ttu-id="efe1d-170">Azure と F\# でのタイマーの実装</span><span class="sxs-lookup"><span data-stu-id="efe1d-170">Implementing Timers on Azure with F\#</span></span>

<span data-ttu-id="efe1d-171">タイマーは、スケジュールに従って、1 回または定期的に呼び出し関数をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="efe1d-171">Timer triggers call functions based on a schedule, one time or recurring.</span></span>

<span data-ttu-id="efe1d-172">[Azure Function F# とタイマー トリガー](/azure/azure-functions/functions-bindings-timer)を使用して、タイマーを F# で実装し、Azure でホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-172">Timers can be implemented in F# and hosted on Azure via an [Azure Function in F# with a Timer Trigger](/azure/azure-functions/functions-bindings-timer).</span></span>

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a><span data-ttu-id="efe1d-173">F# スクリプトを使用した Azure リソースの展開と管理</span><span class="sxs-lookup"><span data-stu-id="efe1d-173">Deploying and Managing Azure Resources with F# Scripts</span></span>

<span data-ttu-id="efe1d-174">Azure VM はプログラムで展開し、Microsoft.Azure.Management パッケージと API を使用して、F# スクリプトから管理します。</span><span class="sxs-lookup"><span data-stu-id="efe1d-174">Azure VMs may be programmatically deployed and managed from F# scripts by using the Microsoft.Azure.Management packages and APIs.</span></span> <span data-ttu-id="efe1d-175">例については、「[.NET の管理ライブラリの概要](https://msdn.microsoft.com/library/dn722415.aspx)」と[Azure Resource Manager の使用](/azure/azure-resource-manager/resource-manager-deployment-model)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe1d-175">For example, see [Get Started with the Management Libraries for .NET](https://msdn.microsoft.com/library/dn722415.aspx) and [Using Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).</span></span>

<span data-ttu-id="efe1d-176">同様に、他の Azure リソースも同じコンポーネントを使用して、F# スクリプトから展開および管理できます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-176">Likewise, other Azure resources may also be deployed and managed from F# scripts using the same components.</span></span> <span data-ttu-id="efe1d-177">たとえば、F# スクリプトからプログラム的に、ストレージ アカウントの作成、Azure Cloud Services のデプロイ、Azure Cosmos DB インスタンスの作成、Azure Notifcation Hubs の管理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-177">For example, you can create storage accounts, deploy Azure Cloud Services, create Azure Cosmos DB instances and manage Azure Notifcation Hubs programmatically from F# scripts.</span></span>

<span data-ttu-id="efe1d-178">F# スクリプトを使用したリソースの展開および管理は、通常必要はありません。</span><span class="sxs-lookup"><span data-stu-id="efe1d-178">Using F# scripts to deploy and manage resources is not normally necessary.</span></span> <span data-ttu-id="efe1d-179">たとえば、Azure リソースは JSON テンプレートの説明から直接デプロイすることもでき、これをパラメーター化できます。</span><span class="sxs-lookup"><span data-stu-id="efe1d-179">For example, Azure resources may also be deployed directly from JSON template descriptions, which can be parameterized.</span></span> <span data-ttu-id="efe1d-180">[Azure クイック スタート テンプレート](https://azure.microsoft.com/resources/templates/)などの例を含む[Azure Resource Manager テンプレート](/azure/azure-resource-manager/resource-manager-template-best-practices)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efe1d-180">See [Azure Resource Manager Templates](/azure/azure-resource-manager/resource-manager-template-best-practices) including examples such as the [Azure Quickstart Templates](https://azure.microsoft.com/resources/templates/).</span></span>

## <a name="other-resources"></a><span data-ttu-id="efe1d-181">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="efe1d-181">Other resources</span></span>

* [<span data-ttu-id="efe1d-182">すべての Azure サービスのドキュメント</span><span class="sxs-lookup"><span data-stu-id="efe1d-182">Full documentation on all Azure services</span></span>](/azure/)
