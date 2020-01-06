---
title: モジュール、ハンドラー、ミドルウェア
description: モジュール、ハンドラー、およびミドルウェアを使用した HTTP 要求の処理について説明します。
author: danroth27
ms.author: daroth
ms.date: 10/11/2019
ms.openlocfilehash: 3ecc109c54f88b5b06a1474f7c6e262d426a78a9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337473"
---
# <a name="modules-handlers-and-middleware"></a><span data-ttu-id="bbe79-103">モジュール、ハンドラー、ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="bbe79-103">Modules, handlers, and middleware</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="bbe79-104">ASP.NET Core アプリは一連の*ミドルウェア*に基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="bbe79-104">An ASP.NET Core app is built upon a series of *middleware*.</span></span> <span data-ttu-id="bbe79-105">ミドルウェアは、要求と応答を処理するためにパイプラインに配置されるハンドラーです。</span><span class="sxs-lookup"><span data-stu-id="bbe79-105">Middleware is handlers that are arranged into a pipeline to handle requests and responses.</span></span> <span data-ttu-id="bbe79-106">Web フォームアプリでは、HTTP ハンドラーとモジュールは同様の問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="bbe79-106">In a Web Forms app, HTTP handlers and modules solve similar problems.</span></span> <span data-ttu-id="bbe79-107">ASP.NET Core では、モジュール、ハンドラー、 *Global.asax.cs*、およびアプリのライフサイクルはミドルウェアに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="bbe79-107">In ASP.NET Core, modules, handlers, *Global.asax.cs*, and the app life cycle are replaced with middleware.</span></span> <span data-ttu-id="bbe79-108">この章では、Blazor アプリのコンテキストでのミドルウェアについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bbe79-108">In this chapter, you'll learn what middleware in the context of a Blazor app.</span></span>

## <a name="overview"></a><span data-ttu-id="bbe79-109">の概要</span><span class="sxs-lookup"><span data-stu-id="bbe79-109">Overview</span></span>

<span data-ttu-id="bbe79-110">ASP.NET Core 要求パイプラインは、順番に呼び出される一連の要求デリゲートで構成されています。</span><span class="sxs-lookup"><span data-stu-id="bbe79-110">The ASP.NET Core request pipeline consists of a sequence of request delegates, called one after the other.</span></span> <span data-ttu-id="bbe79-111">次の図は、その概念を示しています。</span><span class="sxs-lookup"><span data-stu-id="bbe79-111">The following diagram demonstrates the concept.</span></span> <span data-ttu-id="bbe79-112">実行のスレッドは黒い矢印をたどります。</span><span class="sxs-lookup"><span data-stu-id="bbe79-112">The thread of execution follows the black arrows.</span></span>

![パイプライン](media/middleware/request-delegate-pipeline.png)

<span data-ttu-id="bbe79-114">上の図には、ライフサイクルイベントの概念がありません。</span><span class="sxs-lookup"><span data-stu-id="bbe79-114">The preceding diagram lacks a concept of lifecycle events.</span></span> <span data-ttu-id="bbe79-115">この概念は、ASP.NET Web フォーム要求がどのように処理されるかについての基礎となります。</span><span class="sxs-lookup"><span data-stu-id="bbe79-115">This concept is foundational to how ASP.NET Web Forms requests are handled.</span></span> <span data-ttu-id="bbe79-116">このシステムにより、どのようなプロセスが発生しているかがわかりやすくなり、ミドルウェアをいつでも挿入できるようになります。</span><span class="sxs-lookup"><span data-stu-id="bbe79-116">This system makes it easier to reason about what process is occurring and allows middleware to be inserted at any point.</span></span> <span data-ttu-id="bbe79-117">ミドルウェアは、要求パイプラインに追加された順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="bbe79-117">Middleware executes in the order in which it's added to the request pipeline.</span></span> <span data-ttu-id="bbe79-118">また、構成ファイルではなくコードに追加されています (通常は*Startup.cs*)。</span><span class="sxs-lookup"><span data-stu-id="bbe79-118">They're also added in code instead of configuration files, usually in *Startup.cs*.</span></span>

## <a name="katana"></a><span data-ttu-id="bbe79-119">Katana</span><span class="sxs-lookup"><span data-stu-id="bbe79-119">Katana</span></span>

<span data-ttu-id="bbe79-120">Katana に慣れている読者は、ASP.NET Core に慣れることができます。</span><span class="sxs-lookup"><span data-stu-id="bbe79-120">Readers familiar with Katana will feel comfortable in ASP.NET Core.</span></span> <span data-ttu-id="bbe79-121">実際、Katana は、ASP.NET Core が派生するフレームワークです。</span><span class="sxs-lookup"><span data-stu-id="bbe79-121">In fact, Katana is a framework from which ASP.NET Core derives.</span></span> <span data-ttu-id="bbe79-122">ASP.NET 4.x 用の同様のミドルウェアとパイプラインパターンが導入されました。</span><span class="sxs-lookup"><span data-stu-id="bbe79-122">It introduced similar middleware and pipeline patterns for ASP.NET 4.x.</span></span> <span data-ttu-id="bbe79-123">Katana 向けに設計されたミドルウェアは、ASP.NET Core パイプラインで動作するように調整できます。</span><span class="sxs-lookup"><span data-stu-id="bbe79-123">Middleware designed for Katana can be adapted to work with the ASP.NET Core pipeline.</span></span>

## <a name="common-middleware"></a><span data-ttu-id="bbe79-124">共通ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="bbe79-124">Common middleware</span></span>

<span data-ttu-id="bbe79-125">ASP.NET 4.x には多数のモジュールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bbe79-125">ASP.NET 4.x includes many modules.</span></span> <span data-ttu-id="bbe79-126">同様に、ASP.NET Core にも多くのミドルウェアコンポーネントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="bbe79-126">In a similar fashion, ASP.NET Core has many middleware components available as well.</span></span> <span data-ttu-id="bbe79-127">IIS モジュールは、ASP.NET Core がある場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbe79-127">IIS modules may be used in some cases with ASP.NET Core.</span></span> <span data-ttu-id="bbe79-128">それ以外の場合は、ネイティブ ASP.NET Core ミドルウェアを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbe79-128">In other cases, native ASP.NET Core middleware may be available.</span></span>

<span data-ttu-id="bbe79-129">次の表に、ASP.NET Core の代替ミドルウェアとコンポーネントの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="bbe79-129">The following table lists replacement middleware and components in ASP.NET Core.</span></span>

|<span data-ttu-id="bbe79-130">Module</span><span class="sxs-lookup"><span data-stu-id="bbe79-130">Module</span></span>                 |<span data-ttu-id="bbe79-131">ASP.NET 4.x モジュール</span><span class="sxs-lookup"><span data-stu-id="bbe79-131">ASP.NET 4.x module</span></span>           |<span data-ttu-id="bbe79-132">ASP.NET Core オプション</span><span class="sxs-lookup"><span data-stu-id="bbe79-132">ASP.NET Core option</span></span>|
|-----------------------|-----------------------------|-------------------|
|<span data-ttu-id="bbe79-133">HTTP エラー</span><span class="sxs-lookup"><span data-stu-id="bbe79-133">HTTP errors</span></span>            |`CustomErrorModule`          |[<span data-ttu-id="bbe79-134">状態コード ページ ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="bbe79-134">Status Code Pages Middleware</span></span>](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|<span data-ttu-id="bbe79-135">既定のドキュメント</span><span class="sxs-lookup"><span data-stu-id="bbe79-135">Default document</span></span>       |`DefaultDocumentModule`      |[<span data-ttu-id="bbe79-136">既定のファイル ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="bbe79-136">Default Files Middleware</span></span>](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|<span data-ttu-id="bbe79-137">ディレクトリの参照</span><span class="sxs-lookup"><span data-stu-id="bbe79-137">Directory browsing</span></span>     |`DirectoryListingModule`     |[<span data-ttu-id="bbe79-138">ディレクトリ参照ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="bbe79-138">Directory Browsing Middleware</span></span>](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|<span data-ttu-id="bbe79-139">動的圧縮</span><span class="sxs-lookup"><span data-stu-id="bbe79-139">Dynamic compression</span></span>    |`DynamicCompressionModule`   |[<span data-ttu-id="bbe79-140">応答圧縮ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="bbe79-140">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="bbe79-141">失敗した要求のトレース</span><span class="sxs-lookup"><span data-stu-id="bbe79-141">Failed requests tracing</span></span>|`FailedRequestsTracingModule`|[<span data-ttu-id="bbe79-142">ASP.NET Core のログ</span><span class="sxs-lookup"><span data-stu-id="bbe79-142">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|<span data-ttu-id="bbe79-143">ファイルのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="bbe79-143">File caching</span></span>           |`FileCacheModule`            |[<span data-ttu-id="bbe79-144">応答キャッシュ ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="bbe79-144">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="bbe79-145">HTTP キャッシュ</span><span class="sxs-lookup"><span data-stu-id="bbe79-145">HTTP caching</span></span>           |`HttpCacheModule`            |[<span data-ttu-id="bbe79-146">応答キャッシュ ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="bbe79-146">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="bbe79-147">HTTP ログ</span><span class="sxs-lookup"><span data-stu-id="bbe79-147">HTTP logging</span></span>           |`HttpLoggingModule`          |[<span data-ttu-id="bbe79-148">ASP.NET Core のログ</span><span class="sxs-lookup"><span data-stu-id="bbe79-148">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index)|
|<span data-ttu-id="bbe79-149">HTTP リダイレクト</span><span class="sxs-lookup"><span data-stu-id="bbe79-149">HTTP redirection</span></span>       |`HttpRedirectionModule`      |[<span data-ttu-id="bbe79-150">ミドルウェアの URL リライト</span><span class="sxs-lookup"><span data-stu-id="bbe79-150">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="bbe79-151">ISAPI フィルター</span><span class="sxs-lookup"><span data-stu-id="bbe79-151">ISAPI filters</span></span>          |`IsapiFilterModule`          |[<span data-ttu-id="bbe79-152">ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="bbe79-152">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="bbe79-153">ISAPI</span><span class="sxs-lookup"><span data-stu-id="bbe79-153">ISAPI</span></span>                  |`IsapiModule`                |[<span data-ttu-id="bbe79-154">ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="bbe79-154">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="bbe79-155">要求のフィルター処理</span><span class="sxs-lookup"><span data-stu-id="bbe79-155">Request filtering</span></span>      |`RequestFilteringModule`     |[<span data-ttu-id="bbe79-156">URL リライトミドルウェア IRule</span><span class="sxs-lookup"><span data-stu-id="bbe79-156">URL Rewriting Middleware IRule</span></span>](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|<span data-ttu-id="bbe79-157">URL の書き換え&#8224;</span><span class="sxs-lookup"><span data-stu-id="bbe79-157">URL rewriting&#8224;</span></span>   |`RewriteModule`              |[<span data-ttu-id="bbe79-158">ミドルウェアの URL リライト</span><span class="sxs-lookup"><span data-stu-id="bbe79-158">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="bbe79-159">静的な圧縮</span><span class="sxs-lookup"><span data-stu-id="bbe79-159">Static compression</span></span>     |`StaticCompressionModule`    |[<span data-ttu-id="bbe79-160">応答圧縮ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="bbe79-160">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="bbe79-161">静的コンテンツ</span><span class="sxs-lookup"><span data-stu-id="bbe79-161">Static content</span></span>         |`StaticFileModule`           |[<span data-ttu-id="bbe79-162">静的ファイル ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="bbe79-162">Static File Middleware</span></span>](/aspnet/core/fundamentals/static-files)|
|<span data-ttu-id="bbe79-163">URL 承認</span><span class="sxs-lookup"><span data-stu-id="bbe79-163">URL authorization</span></span>      |`UrlAuthorizationModule`     |[<span data-ttu-id="bbe79-164">ASP.NET Core ID</span><span class="sxs-lookup"><span data-stu-id="bbe79-164">ASP.NET Core Identity</span></span>](/aspnet/core/security/authentication/identity)|

<span data-ttu-id="bbe79-165">このリストは完全なものではありませんが、2つのフレームワーク間にどのようなマッピングが存在するのかを把握する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbe79-165">This list isn't exhaustive but should give an idea of what mapping exists between the two frameworks.</span></span> <span data-ttu-id="bbe79-166">詳細な一覧については、「 [ASP.NET Core を使用した IIS モジュール](/aspnet/core/host-and-deploy/iis/modules)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbe79-166">For a more detailed list, see [IIS modules with ASP.NET Core](/aspnet/core/host-and-deploy/iis/modules).</span></span>

## <a name="custom-middleware"></a><span data-ttu-id="bbe79-167">カスタムミドルウェア</span><span class="sxs-lookup"><span data-stu-id="bbe79-167">Custom middleware</span></span>

<span data-ttu-id="bbe79-168">組み込みのミドルウェアでは、アプリに必要なすべてのシナリオを処理することはできません。</span><span class="sxs-lookup"><span data-stu-id="bbe79-168">Built-in middleware may not handle all scenarios needed for an app.</span></span> <span data-ttu-id="bbe79-169">このような場合は、独自のミドルウェアを作成するのが理にかなっています。</span><span class="sxs-lookup"><span data-stu-id="bbe79-169">In such cases, it makes sense to create your own middleware.</span></span> <span data-ttu-id="bbe79-170">ミドルウェアを定義する方法は複数ありますが、最も単純なのは単純なデリゲートです。</span><span class="sxs-lookup"><span data-stu-id="bbe79-170">There are multiple ways of defining middleware, with the simplest being a simple delegate.</span></span> <span data-ttu-id="bbe79-171">クエリ文字列からカルチャ要求を受け取る次のミドルウェアを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="bbe79-171">Consider the following middleware, which accepts a culture request from a query string:</span></span>

```csharp
public class Startup
{
    public void Configure(IApplicationBuilder app)
    {
        app.Use(async (context, next) =>
        {
            var cultureQuery = context.Request.Query["culture"];

            if (!string.IsNullOrWhiteSpace(cultureQuery))
            {
                var culture = new CultureInfo(cultureQuery);

                CultureInfo.CurrentCulture = culture;
                CultureInfo.CurrentUICulture = culture;
            }

            // Call the next delegate/middleware in the pipeline
            await next();
        });

        app.Run(async (context) =>
            await context.Response.WriteAsync(
                $"Hello {CultureInfo.CurrentCulture.DisplayName}"));
    }
}
```

<span data-ttu-id="bbe79-172">ミドルウェアは、`IMiddleware` インターフェイスを実装するか、次のミドルウェア規則に従って、クラスとして定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="bbe79-172">Middleware can also be defined as class, either by implementing the `IMiddleware` interface or by following middleware convention.</span></span> <span data-ttu-id="bbe79-173">詳細については、「[カスタム ASP.NET Core ミドルウェアを作成](/aspnet/core/fundamentals/middleware/write)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbe79-173">For more information, see [Write custom ASP.NET Core middleware](/aspnet/core/fundamentals/middleware/write).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bbe79-174">[前へ](data.md)
>[次へ](config.md)</span><span class="sxs-lookup"><span data-stu-id="bbe79-174">[Previous](data.md)
[Next](config.md)</span></span>
