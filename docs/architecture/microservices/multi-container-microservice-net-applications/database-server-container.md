---
title: コンテナーとして実行するデータベース サーバーの使用
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 開発のためだけにコンテナーとして実行するデータベース サーバーを使用していますか。 理由を理解します。
ms.date: 10/02/2018
ms.openlocfilehash: 371d622dc39681edb0b52e723faccbf611b7797c
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568431"
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="452c7-104">コンテナーとして実行するデータベース サーバーの使用</span><span class="sxs-lookup"><span data-stu-id="452c7-104">Using a database server running as a container</span></span>

<span data-ttu-id="452c7-105">データベース (SQL Server、PostgreSQL、MySQL など) は、通常のスタンドアロン サーバー上、オンプレミス クラスター内、または Azure SQL DB などのクラウド内の PaaS サービスとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="452c7-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="452c7-106">ただし、開発およびテスト環境では、データベースをコンテナーとして実行すると便利です。これは、外部の依存関係がなく、`docker-compose up` コマンドを実行するだけで、アプリケーション全体が起動するためです。</span><span class="sxs-lookup"><span data-stu-id="452c7-106">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="452c7-107">それらのデータベースをコンテナーとして使用することは、統合テストにも有効です。これは、データベースがコンテナー内で起動され、常に同じサンプル データが格納されるので、テストの予測精度が向上するためです。</span><span class="sxs-lookup"><span data-stu-id="452c7-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="452c7-108">マイクロサービスに関連するデータベースを含むコンテナーとして実行している SQL Server</span><span class="sxs-lookup"><span data-stu-id="452c7-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="452c7-109">eShopOnContainers には、[docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) ファイルで定義される sql.data というコンテナーがあり、これが Linux 用 SQL Server とマイクロサービスに必要なすべての SQL Server データベースを実行します</span><span class="sxs-lookup"><span data-stu-id="452c7-109">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="452c7-110">(各データベース用に 1 つの SQL Server コンテナーを使用することもできますが、より多くのメモリを Docker に割り当てる必要があります)。マイクロサービスで重要な点は、各マイクロサービスが関連するデータを所有し、そのためこのケースでは、SQL データベースに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="452c7-110">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="452c7-111">しかし、データベースは任意の場所に置くことができます。</span><span class="sxs-lookup"><span data-stu-id="452c7-111">But the databases can be anywhere.</span></span>

<span data-ttu-id="452c7-112">サンプル アプリケーションの SQL Server コンテナーは、docker-compose.yml ファイル内で次の YAML コードで構成され、`docker-compose up` を実行したときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="452c7-112">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="452c7-113">YAML コードは、汎用の docker compose.yml ファイルと docker compose.override.yml ファイルから構成情報を統合されていることに注意してください</span><span class="sxs-lookup"><span data-stu-id="452c7-113">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="452c7-114">(通常は、SQL Server イメージに関連する基本情報または静的情報から、環境の設定を分離します)。</span><span class="sxs-lookup"><span data-stu-id="452c7-114">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="452c7-115">同様の方法で、`docker-compose` を使用する代わりに、次の `docker run` コマンドでそのコンテナーを実行できます。</span><span class="sxs-lookup"><span data-stu-id="452c7-115">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```console
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

<span data-ttu-id="452c7-116">ただし、eShopOnContainers などのマルチコンテナー アプリケーションを展開する場合は、アプリケーションに必要なすべてのコンテナーを展開する `docker-compose up` コマンドを使う方が便利です。</span><span class="sxs-lookup"><span data-stu-id="452c7-116">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="452c7-117">初めてこの SQL Server のコンテナーを起動するときに、コンテナーが、指定したパスワードを使用して SQL Server を初期化します。</span><span class="sxs-lookup"><span data-stu-id="452c7-117">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="452c7-118">SQL Server がコンテナーとして実行されたら、SQL Server Management Studio、Visual Studio、C\# コードなどの通常の SQL 接続を介して接続することでデータベースを更新できます。</span><span class="sxs-lookup"><span data-stu-id="452c7-118">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="452c7-119">eShopOnContainers アプリケーションは、次のセクションで説明するように、起動時にデータをシードすることにより、各マイクロサービス データベースをサンプル データで初期化します。</span><span class="sxs-lookup"><span data-stu-id="452c7-119">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="452c7-120">SQL Server のコンテナーとしての実行は、SQL Server のインスタンスにアクセスできない場合があるデモに役に立つだけではありません。</span><span class="sxs-lookup"><span data-stu-id="452c7-120">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="452c7-121">説明したように、新しいサンプル データをシードすることによってクリーンな SQL Server イメージと既知のデータから統合テストを簡単に実行できるので開発やテストの環境にも有効です。</span><span class="sxs-lookup"><span data-stu-id="452c7-121">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="452c7-122">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="452c7-122">Additional resources</span></span>

- <span data-ttu-id="452c7-123">**Linux、Mac、Windows で SQL Server Docker イメージを実行する** </span><span class="sxs-lookup"><span data-stu-id="452c7-123">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- <span data-ttu-id="452c7-124">**Linux で sqlcmd を使用して SQL Server に接続してクエリする** </span><span class="sxs-lookup"><span data-stu-id="452c7-124">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="452c7-125">Web アプリケーションの起動時のテスト データのシード処理</span><span class="sxs-lookup"><span data-stu-id="452c7-125">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="452c7-126">アプリケーションの起動時にデータベースにデータを追加するには、Web API プロジェクトのスタートアップ クラス内の構成メソッドに次のようにコードを追加できます。</span><span class="sxs-lookup"><span data-stu-id="452c7-126">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code...
    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure code...
        // Seed data through our custom class
        CatalogContextSeed.SeedAsync(app)
            .Wait();
        // Other Configure code...
    }
}
```

<span data-ttu-id="452c7-127">カスタムの CatalogContextSeed クラスの次のコードはデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="452c7-127">The following code in the custom CatalogContextSeed class populates the data.</span></span>

```csharp
public class CatalogContextSeed
{
    public static async Task SeedAsync(IApplicationBuilder applicationBuilder)
    {
        var context = (CatalogContext)applicationBuilder
            .ApplicationServices.GetService(typeof(CatalogContext));
        using (context)
        {
            context.Database.Migrate();
            if (!context.CatalogBrands.Any())
            {
                context.CatalogBrands.AddRange(
                    GetPreconfiguredCatalogBrands());
                await context.SaveChangesAsync();
            }
            if (!context.CatalogTypes.Any())
            {
                context.CatalogTypes.AddRange(
                    GetPreconfiguredCatalogTypes());
                await context.SaveChangesAsync();
            }
        }
    }

    static IEnumerable<CatalogBrand> GetPreconfiguredCatalogBrands()
    {
        return new List<CatalogBrand>()
       {
           new CatalogBrand() { Brand = "Azure"},
           new CatalogBrand() { Brand = ".NET" },
           new CatalogBrand() { Brand = "Visual Studio" },
           new CatalogBrand() { Brand = "SQL Server" }
       };
    }

    static IEnumerable<CatalogType> GetPreconfiguredCatalogTypes()
    {
        return new List<CatalogType>()
        {
            new CatalogType() { Type = "Mug"},
            new CatalogType() { Type = "T-Shirt" },
            new CatalogType() { Type = "Backpack" },
            new CatalogType() { Type = "USB Memory Stick" }
        };
    }
}
```

<span data-ttu-id="452c7-128">統合テストを実行するときには、統合テストと一貫性のあるデータを生成する方法があると便利です。</span><span class="sxs-lookup"><span data-stu-id="452c7-128">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="452c7-129">コンテナーで実行されている SQL Server のインスタンスを含む、すべてのものを新規に作成できると、テスト環境に非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="452c7-129">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="452c7-130">EF Core InMemory データベースとコンテナーとして実行される SQL Server</span><span class="sxs-lookup"><span data-stu-id="452c7-130">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="452c7-131">テストの実行時に適した別の選択肢として、Entity Framework InMemory データベース プロバイダーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="452c7-131">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="452c7-132">Web API プロジェクトのスタートアップ クラスの ConfigureServices メソッドでその構成を指定できます。</span><span class="sxs-lookup"><span data-stu-id="452c7-132">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code ...
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IConfiguration>(Configuration);
        // DbContext using an InMemory database provider
        services.AddDbContext<CatalogContext>(opt => opt.UseInMemoryDatabase());
        //(Alternative: DbContext using a SQL Server provider
        //services.AddDbContext<CatalogContext>(c =>
        //{
            // c.UseSqlServer(Configuration["ConnectionString"]);
            //
        //});
    }
  
    // Other Startup code ...
}
```

<span data-ttu-id="452c7-133">ただし、重要な落とし穴があります。</span><span class="sxs-lookup"><span data-stu-id="452c7-133">There is an important catch, though.</span></span> <span data-ttu-id="452c7-134">メモリ内データベースは、特定のデータベースに固有な多くの制約をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="452c7-134">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="452c7-135">たとえば、EF Core モデルで列に一意のインデックスを追加し、重複する値の追加を許可しないことを確認するためのテストをインメモリ データベースに対して記述する場合があります。</span><span class="sxs-lookup"><span data-stu-id="452c7-135">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="452c7-136">しかし、メモリ内データベースを使用している場合は、列で一意のインデックスを処理することはできません。</span><span class="sxs-lookup"><span data-stu-id="452c7-136">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="452c7-137">そのため、メモリ内データベースは、実際の SQL Server データベースとまったく同じようには動作せず、データベース固有の制約をエミュレートしません。</span><span class="sxs-lookup"><span data-stu-id="452c7-137">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="452c7-138">それでも、テストやプロトタイプ作成にはメモリ内データベースが依然として役立ちます。</span><span class="sxs-lookup"><span data-stu-id="452c7-138">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="452c7-139">特定のデータベースの実装の動作を考慮する正確な統合テストを作成する場合は、SQL Server のような実際のデータベースを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="452c7-139">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="452c7-140">その目的のために、コンテナー内での SQL Server の実行は優れた選択肢であり、EF Core InMemory データベース プロバイダーよりも正確です。</span><span class="sxs-lookup"><span data-stu-id="452c7-140">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="452c7-141">コンテナーで実行されている Redis キャッシュ サービスの使用</span><span class="sxs-lookup"><span data-stu-id="452c7-141">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="452c7-142">特に開発およびテストや概念実証のシナリオで、Redis をコンテナー上で実行できます。</span><span class="sxs-lookup"><span data-stu-id="452c7-142">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="452c7-143">このシナリオは、ローカルの開発用コンピューターだけでなく、CI/CD パイプラインのテスト環境向けにも、コンテナーですべての依存関係を実行できるので便利です。</span><span class="sxs-lookup"><span data-stu-id="452c7-143">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="452c7-144">ただし、実稼働環境で Redis を実行するときは、PaaS (サービスとしてのプラットフォーム) として実行される Redis Microsoft Azure のような高可用性ソリューションを探すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="452c7-144">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="452c7-145">コード内で、接続文字列だけを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="452c7-145">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="452c7-146">Redis は、Redis と共に Docker イメージを提供します。</span><span class="sxs-lookup"><span data-stu-id="452c7-146">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="452c7-147">そのイメージは、次の URL での Docker Hub から入手できます。</span><span class="sxs-lookup"><span data-stu-id="452c7-147">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="452c7-148">コマンド プロンプトで次の Docker CLI コマンドを実行することによって、Docker Redis コンテナーを直接実行できます。</span><span class="sxs-lookup"><span data-stu-id="452c7-148">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="452c7-149">Redis イメージには expose:6379 (Redis によって使用されるポート) が含まれているので、標準のコンテナーのリンクを、リンクされたコンテナーが自動的に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="452c7-149">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="452c7-150">eShopOnContainers で、basket.api マイクロサービスが、コンテナーとして実行されている Redis キャッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="452c7-150">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="452c7-151">basket.data コンテナーは、次の例で示すように、マルチコンテナー docker compose.yml ファイルの一部として定義されます。</span><span class="sxs-lookup"><span data-stu-id="452c7-151">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="452c7-152">Docker compose.yml のこのコードは、redis イメージに基づいて basket.data という名前のコンテナーを定義し、ポート 6379 を内部的に公開します。これは、Docker ホスト内で実行されている他のコンテナーからのみアクセスできることを意味します。</span><span class="sxs-lookup"><span data-stu-id="452c7-152">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="452c7-153">最後に、docker compose.override.yml ファイル内の eShopOnContainers サンプルの basket.api マイクロサービスが、その Redis コンテナーに使用する接続文字列を定義します。</span><span class="sxs-lookup"><span data-stu-id="452c7-153">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="452c7-154">前述のように、マイクロサービスの名前 "basket.data" は、docker の内部ネットワーク DNS によって解決されます。</span><span class="sxs-lookup"><span data-stu-id="452c7-154">As mentioned before, the name of the microservice "basket.data" is resolved by docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="452c7-155">[前へ](multi-container-applications-docker-compose.md)
>[次へ](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="452c7-155">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
