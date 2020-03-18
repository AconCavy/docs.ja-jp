---
title: マイクロサービス アーキテクチャ
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | マイクロサービス アーキテクチャの 30.000 フィート ビュー
ms.date: 09/20/2018
ms.openlocfilehash: d1c58d218be9e5f8c0ae8ae732f9bdd06674a2c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834383"
---
# <a name="microservices-architecture"></a><span data-ttu-id="09125-103">マイクロサービス アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="09125-103">Microservices architecture</span></span>

<span data-ttu-id="09125-104">名前が示すように、マイクロサービス アーキテクチャは、一連の小さなサービスとしてサーバー アプリケーションを構築するアプローチです。</span><span class="sxs-lookup"><span data-stu-id="09125-104">As the name implies, a microservices architecture is an approach to building a server application as a set of small services.</span></span> <span data-ttu-id="09125-105">つまり、アプローチはフロント エンドにも使用されますが、マイクロサービス アーキテクチャは主にバックエンド向けです。</span><span class="sxs-lookup"><span data-stu-id="09125-105">That means a microservices architecture is mainly oriented to the back-end, although the approach is also being used for the front end.</span></span> <span data-ttu-id="09125-106">各サービスは独自のプロセスで実行され、HTTP/HTTPS、WebSockets、[AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) などのプロトコルを使用して他のプロセスと通信します。</span><span class="sxs-lookup"><span data-stu-id="09125-106">Each service runs in its own process and communicates with other processes using protocols such as HTTP/HTTPS, WebSockets, or [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).</span></span> <span data-ttu-id="09125-107">各マイクロサービスは、特定のコンテキスト境界内で特定のエンドツーエンドのドメインまたはビジネス機能を実装します。個々のマイクロサービスを自律的に開発し、独立して展開可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="09125-107">Each microservice implements a specific end-to-end domain or business capability within a certain context boundary, and each must be developed autonomously and be deployable independently.</span></span> <span data-ttu-id="09125-108">最後に、各マイクロサービスは関連するドメイン データ モデルとドメイン ロジック (管轄と分散データ管理) を所有する必要があり、異なるデータ ストレージ テクノロジ (SQL、NoSQL) や異なるプログラミング言語に基づいてる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="09125-108">Finally, each microservice should own its related domain data model and domain logic (sovereignty and decentralized data management) and could be based on different data storage technologies (SQL, NoSQL) and different programming languages.</span></span>

<span data-ttu-id="09125-109">マイクロサービスはどのくらいのサイズにすべきでしょうか。</span><span class="sxs-lookup"><span data-stu-id="09125-109">What size should a microservice be?</span></span> <span data-ttu-id="09125-110">マイクロサービスを開発する場合、サイズは重要なポイントではありません。</span><span class="sxs-lookup"><span data-stu-id="09125-110">When developing a microservice, size shouldn't be the important point.</span></span> <span data-ttu-id="09125-111">その代わり、弱く結合されたサービスを作成して、サービスごとに開発、展開、およびスケールの自律性を持たせることが重要です。</span><span class="sxs-lookup"><span data-stu-id="09125-111">Instead, the important point should be to create loosely coupled services so you have autonomy of development, deployment, and scale, for each service.</span></span> <span data-ttu-id="09125-112">当然ながら、マイクロサービスを特定して設計する場合は、他のマイクロサービスとの直接の依存関係が多くなりすぎない限り、できるだけマイクロサービスを小さくするようにします。</span><span class="sxs-lookup"><span data-stu-id="09125-112">Of course, when identifying and designing microservices, you should try to make them as small as possible as long as you don't have too many direct dependencies with other microservices.</span></span> <span data-ttu-id="09125-113">マイクロサービスのサイズよりも重要な点は、必要な内部の凝集度と、他のサービスからの独立性です。</span><span class="sxs-lookup"><span data-stu-id="09125-113">More important than the size of the microservice is the internal cohesion it must have and its independence from other services.</span></span>

<span data-ttu-id="09125-114">マイクロサービス アーキテクチャを選ぶ理由は何でしょうか。</span><span class="sxs-lookup"><span data-stu-id="09125-114">Why a microservices architecture?</span></span> <span data-ttu-id="09125-115">短く説明すると、長期的な機敏性を実現するためです。</span><span class="sxs-lookup"><span data-stu-id="09125-115">In short, it provides long-term agility.</span></span> <span data-ttu-id="09125-116">マイクロサービスを使用すると、個々が細かい自律的なライフサイクルを持つ、多数の独立して展開可能なサービスに基づいてアプリケーションを作成できるので、複雑で大規模で高度にスケーラブルなシステムの保守性を向上することができます。</span><span class="sxs-lookup"><span data-stu-id="09125-116">Microservices enable better maintainability in complex, large, and highly-scalable systems by letting you create applications based on many independently deployable services that each have granular and autonomous lifecycles.</span></span>

<span data-ttu-id="09125-117">また、個別にスケールアウトできることもマイクロサービスのメリットです。</span><span class="sxs-lookup"><span data-stu-id="09125-117">As an additional benefit, microservices can scale out independently.</span></span> <span data-ttu-id="09125-118">1 つのモノリシックなアプリケーションを 1 ユニットとしてスケールアウトするのではなく、特定のマイクロサービスをスケールアウトできます。</span><span class="sxs-lookup"><span data-stu-id="09125-118">Instead of having a single monolithic application that you must scale out as a unit, you can instead scale out specific microservices.</span></span> <span data-ttu-id="09125-119">その結果、需要に応えるために多くの処理能力やネットワーク帯域幅を必要とする機能領域だけをスケールアウトでき、スケールアウトする必要のない機能領域までスケールアウトすることはありません。</span><span class="sxs-lookup"><span data-stu-id="09125-119">That way, you can scale just the functional area that needs more processing power or network bandwidth to support demand, rather than scaling out other areas of the application that don't need to be scaled.</span></span> <span data-ttu-id="09125-120">つまり、必要なハードウェア数が少ないため、コストを削減できます。</span><span class="sxs-lookup"><span data-stu-id="09125-120">That means cost savings because you need less hardware.</span></span>

![2 つのデプロイ方法の違いの図。](./media/microservices-architecture/monolith-deployment-vs-microservice-approach.png)

<span data-ttu-id="09125-122">**図 4-6**</span><span class="sxs-lookup"><span data-stu-id="09125-122">**Figure 4-6**.</span></span> <span data-ttu-id="09125-123">モノリシック展開とマイクロサービス アプローチ</span><span class="sxs-lookup"><span data-stu-id="09125-123">Monolithic deployment versus the microservices approach</span></span>

<span data-ttu-id="09125-124">図 4-6 に示すように、従来のモノリシック アプローチでは、複数のサーバー/VM 上のアプリ全体を複製することで、アプリケーションがスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="09125-124">As Figure 4-6 shows, in the traditional monolithic approach, the application scales by cloning the whole app in several servers/VM.</span></span> <span data-ttu-id="09125-125">マイクロサービス アプローチでは、機能はより小さいサービスに分離されるため、それぞれのサービスで個別にスケーリングできます。</span><span class="sxs-lookup"><span data-stu-id="09125-125">In the microservices approach, functionality is segregated in smaller services, so each service can scale independently.</span></span> <span data-ttu-id="09125-126">マイクロサービス アプローチを使用すると、複雑で大規模でスケーラブルなアプリケーションの特定の小さな領域を変更できるため、各マイクロサービスの柔軟な変更と迅速な繰り返しが可能になります。</span><span class="sxs-lookup"><span data-stu-id="09125-126">The microservices approach allows agile changes and rapid iteration of each microservice, because you can change specific, small areas of complex, large, and scalable applications.</span></span>

<span data-ttu-id="09125-127">細かいマイクロサービスベースのアプリケーションを設計することで、継続的な統合と継続的デリバリーの方法を実現できます。</span><span class="sxs-lookup"><span data-stu-id="09125-127">Architecting fine-grained microservices-based applications enables continuous integration and continuous delivery practices.</span></span> <span data-ttu-id="09125-128">また、短期間でアプリケーションに新しい関数を配信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="09125-128">It also accelerates delivery of new functions into the application.</span></span> <span data-ttu-id="09125-129">細かいアプリケーションの構成にすることで、マイクロサービスを単独で実行してテストし、マイクロサービス間の明確なコントラクトを維持しながら自律的に進化させることもできます。</span><span class="sxs-lookup"><span data-stu-id="09125-129">Fine-grained composition of applications also allows you to run and test microservices in isolation, and to evolve them autonomously while maintaining clear contracts between them.</span></span> <span data-ttu-id="09125-130">インターフェイスまたはコントラクトを変更しない限り、任意のマイクロサービスの内部実装を変更することや、他のマイクロサービスを中断することなく新機能を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="09125-130">As long as you don't change the interfaces or contracts, you can change the internal implementation of any microservice or add new functionality without breaking other microservices.</span></span>

<span data-ttu-id="09125-131">マイクロサービスベースのシステムを含む実稼働環境への移行を成功させるには、次の点が重要です。</span><span class="sxs-lookup"><span data-stu-id="09125-131">The following are important aspects to enable success in going into production with a microservices-based system:</span></span>

- <span data-ttu-id="09125-132">サービスとインフラストラクチャの監視と正常性検査。</span><span class="sxs-lookup"><span data-stu-id="09125-132">Monitoring and health checks of the services and infrastructure.</span></span>

- <span data-ttu-id="09125-133">サービス (つまり、クラウドとオーケストレーター) のスケーラブルなインフラストラクチャ。</span><span class="sxs-lookup"><span data-stu-id="09125-133">Scalable infrastructure for the services (that is, cloud and orchestrators).</span></span>

- <span data-ttu-id="09125-134">複数レベルのセキュリティ設計と実装: 認証、承認、シークレット管理、セキュリティで保護された通信など。</span><span class="sxs-lookup"><span data-stu-id="09125-134">Security design and implementation at multiple levels: authentication, authorization, secrets management, secure communication, etc.</span></span>

- <span data-ttu-id="09125-135">高速なアプリケーション配信。通常は、チームによって異なるマイクロサービスに集中します。</span><span class="sxs-lookup"><span data-stu-id="09125-135">Rapid application delivery, usually with different teams focusing on different microservices.</span></span>

- <span data-ttu-id="09125-136">DevOps および CI/CD のプラクティスとインフラストラクチャ。</span><span class="sxs-lookup"><span data-stu-id="09125-136">DevOps and CI/CD practices and infrastructure.</span></span>

<span data-ttu-id="09125-137">このガイドでは最初の 3 つのみを扱い、紹介しています。</span><span class="sxs-lookup"><span data-stu-id="09125-137">Of these, only the first three are covered or introduced in this guide.</span></span> <span data-ttu-id="09125-138">アプリケーションのライフサイクルに関連する残り 2 つの点については、「[Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook)」(Microsoft プラットフォームとツールを使用してコンテナー化された Docker アプリケーションのライフサイクル) の電子書籍を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09125-138">The last two points, which are related to application lifecycle, are covered in the additional [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) e-book.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="09125-139">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="09125-139">Additional resources</span></span>

- <span data-ttu-id="09125-140">**Mark Russinovich。マイクロサービス:クラウドによって強化されるアプリケーションの革命** </span><span class="sxs-lookup"><span data-stu-id="09125-140">**Mark Russinovich. Microservices: An application revolution powered by the cloud** </span></span>\
  <https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/>

- <span data-ttu-id="09125-141">**Martin Fowler。マイクロサービス** </span><span class="sxs-lookup"><span data-stu-id="09125-141">**Martin Fowler. Microservices** </span></span>\
  <https://www.martinfowler.com/articles/microservices.html>

- <span data-ttu-id="09125-142">**Martin Fowler。マイクロサービスの前提条件** </span><span class="sxs-lookup"><span data-stu-id="09125-142">**Martin Fowler. Microservice Prerequisites** </span></span>\
  <https://martinfowler.com/bliki/MicroservicePrerequisites.html>

- <span data-ttu-id="09125-143">**Jimmy Nilsson。チャンク クラウド コンピューティング** </span><span class="sxs-lookup"><span data-stu-id="09125-143">**Jimmy Nilsson. Chunk Cloud Computing** </span></span>\
  <https://www.infoq.com/articles/CCC-Jimmy-Nilsson>

- <span data-ttu-id="09125-144">**Cesar de la Torre。Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル** (ダウンロード可能な e-book) </span><span class="sxs-lookup"><span data-stu-id="09125-144">**Cesar de la Torre. Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) </span></span>\
  <https://aka.ms/dockerlifecycleebook>

>[!div class="step-by-step"]
><span data-ttu-id="09125-145">[前へ](service-oriented-architecture.md)
>[次へ](data-sovereignty-per-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="09125-145">[Previous](service-oriented-architecture.md)
[Next](data-sovereignty-per-microservice.md)</span></span>
