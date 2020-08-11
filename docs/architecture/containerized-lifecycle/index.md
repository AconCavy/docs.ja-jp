---
title: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
description: Docker および Microsoft のプラットフォームとツールでコンテナー化されたアプリケーションを開発およびデプロイするための、開発とデプロイのプロセスの概要を説明します。
ms.date: 07/30/2020
ms.openlocfilehash: d8055315b25f73d7b0b355026ab6b2c4767f9d89
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915151"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a><span data-ttu-id="5be0c-103">Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル</span><span class="sxs-lookup"><span data-stu-id="5be0c-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools</span></span>

![本の表紙](./media/devops-book-cover-large-we.png)

<span data-ttu-id="5be0c-105">**エディション v3.1** - ASP.NET Core 3.1 に更新</span><span class="sxs-lookup"><span data-stu-id="5be0c-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="5be0c-106">このガイドは、Microsoft のプラットフォームとツールを使用して、コンテナー化された ASP.NET Core アプリケーションを Docker で開発およびデプロイするための一般的な概要です。</span><span class="sxs-lookup"><span data-stu-id="5be0c-106">This guide is a general overview for developing and deploying containerized ASP.NET Core applications with Docker, using the Microsoft platform and tools.</span></span> <span data-ttu-id="5be0c-107">このガイドには、CI/CD パイプラインを実装するための Azure DevOps の概要、Azure Container Registry (ACR)、デプロイ用の Azure Kubernetes Services AKS が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5be0c-107">The guide includes a high-level introduction to Azure DevOps, for implementing CI/CD pipelines, as well as Azure Container Registry (ACR), and Azure Kubernetes Services AKS for deployment.</span></span>

<span data-ttu-id="5be0c-108">開発に関連した低レベルの詳細については、『[.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ](https://docs.microsoft.com/dotnet/architecture/microservices/)』 ガイドと IT 関連の参照アプリケーション [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5be0c-108">For low-level, development-related details you can see the [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/architecture/microservices/) guide and it related reference application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="5be0c-109">フィードバックをお寄せください。</span><span class="sxs-lookup"><span data-stu-id="5be0c-109">Send us your feedback!</span></span>

<span data-ttu-id="5be0c-110">このガイドは、コンテナー化されたアプリケーションと .NET のマイクロサービスのアーキテクチャの理解を促進する目的で書かれています。</span><span class="sxs-lookup"><span data-stu-id="5be0c-110">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="5be0c-111">ガイドと関連する参照アプリケーションは進化していくため、お客様のフィードバックをお待ちしています。</span><span class="sxs-lookup"><span data-stu-id="5be0c-111">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="5be0c-112">このガイドを改善する方法に関するコメントがある場合は、<https://aka.ms/ebookfeedback> にフィードバックを送信してください。</span><span class="sxs-lookup"><span data-stu-id="5be0c-112">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="5be0c-113">謝辞</span><span class="sxs-lookup"><span data-stu-id="5be0c-113">Credits</span></span>

<span data-ttu-id="5be0c-114">作成者:</span><span class="sxs-lookup"><span data-stu-id="5be0c-114">Author:</span></span>

> <span data-ttu-id="5be0c-115">**Cesar de la Torre**、Microsoft Corp.、.NET 製品チーム、シニア PM</span><span class="sxs-lookup"><span data-stu-id="5be0c-115">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>

<span data-ttu-id="5be0c-116">総合編集者:</span><span class="sxs-lookup"><span data-stu-id="5be0c-116">Acquisitions Editor:</span></span>

> <span data-ttu-id="5be0c-117">**Janine Patrick**</span><span class="sxs-lookup"><span data-stu-id="5be0c-117">**Janine Patrick**</span></span>

<span data-ttu-id="5be0c-118">監修者:</span><span class="sxs-lookup"><span data-stu-id="5be0c-118">Developmental Editor:</span></span>

> <span data-ttu-id="5be0c-119">**Bob Russell**、Microsoft、ソリューション プロフェッショナル</span><span class="sxs-lookup"><span data-stu-id="5be0c-119">**Bob Russell**, Solutions Professional at Microsoft</span></span>
>
> [<span data-ttu-id="5be0c-120">**Octal Publishing, Inc.** </span><span class="sxs-lookup"><span data-stu-id="5be0c-120">**Octal Publishing, Inc.**</span></span>](http://www.octalpub.com/)

<span data-ttu-id="5be0c-121">制作者:</span><span class="sxs-lookup"><span data-stu-id="5be0c-121">Editorial Production:</span></span>

> [<span data-ttu-id="5be0c-122">Dianne Russell</span><span class="sxs-lookup"><span data-stu-id="5be0c-122">Dianne Russell</span></span>](http://www.octalpub.com/)
>
> <span data-ttu-id="5be0c-123">**Octal Publishing, Inc.**</span><span class="sxs-lookup"><span data-stu-id="5be0c-123">**Octal Publishing, Inc.**</span></span>

<span data-ttu-id="5be0c-124">原稿整理編集者:</span><span class="sxs-lookup"><span data-stu-id="5be0c-124">Copyeditor:</span></span>

> <span data-ttu-id="5be0c-125">**Bob Russell**、Microsoft、ソリューション プロフェッショナル</span><span class="sxs-lookup"><span data-stu-id="5be0c-125">**Bob Russell**, Solutions Professional at Microsoft</span></span>

<span data-ttu-id="5be0c-126">参加者とレビュー担当者:</span><span class="sxs-lookup"><span data-stu-id="5be0c-126">Participants and reviewers:</span></span>

> <span data-ttu-id="5be0c-127">**Nish Anil**、Microsoft、.NET チーム、シニア プログラム マネージャー</span><span class="sxs-lookup"><span data-stu-id="5be0c-127">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="5be0c-128">**Miguel Veloso**、Plain Concepts のソフトウェア開発エンジニア</span><span class="sxs-lookup"><span data-stu-id="5be0c-128">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="5be0c-129">**Sumit Ghosh**、Neudesic、主席コンサルタント</span><span class="sxs-lookup"><span data-stu-id="5be0c-129">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="5be0c-130">Copyright</span><span class="sxs-lookup"><span data-stu-id="5be0c-130">Copyright</span></span>

<span data-ttu-id="5be0c-131">発行者</span><span class="sxs-lookup"><span data-stu-id="5be0c-131">PUBLISHED BY</span></span>

<span data-ttu-id="5be0c-132">Microsoft 開発部門、.NET および Visual Studio 製品チーム</span><span class="sxs-lookup"><span data-stu-id="5be0c-132">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="5be0c-133">A division of Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5be0c-133">A division of Microsoft Corporation</span></span>

<span data-ttu-id="5be0c-134">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="5be0c-134">One Microsoft Way</span></span>

<span data-ttu-id="5be0c-135">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="5be0c-135">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="5be0c-136">Copyright &copy; 2020 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5be0c-136">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="5be0c-137">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="5be0c-137">All rights reserved.</span></span> <span data-ttu-id="5be0c-138">本書のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製または伝送することを禁じます。</span><span class="sxs-lookup"><span data-stu-id="5be0c-138">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="5be0c-139">本書は "現状有姿" で提供され、著者の見解と意見を表しています。</span><span class="sxs-lookup"><span data-stu-id="5be0c-139">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="5be0c-140">URL および他の参照されているインターネットの Web サイトをはじめ、本書に記載されている見解、意見、および情報は、通知なく変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="5be0c-140">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="5be0c-141">ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。</span><span class="sxs-lookup"><span data-stu-id="5be0c-141">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="5be0c-142">実在のものとの関連性または関係性は一切ありません。</span><span class="sxs-lookup"><span data-stu-id="5be0c-142">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="5be0c-143"><https://www.microsoft.com> の "商標" Web ページに記載されている Microsoft および商標は、Microsoft グループの商標です。</span><span class="sxs-lookup"><span data-stu-id="5be0c-143">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="5be0c-144">Mac および macOS は Apple Inc. の商標です。</span><span class="sxs-lookup"><span data-stu-id="5be0c-144">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="5be0c-145">Docker のクジラのロゴは Docker, Inc. の登録商標です。許可を得て使用しています。</span><span class="sxs-lookup"><span data-stu-id="5be0c-145">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="5be0c-146">その他のすべてのマークおよびロゴは、該当する各社が所有しています。</span><span class="sxs-lookup"><span data-stu-id="5be0c-146">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="5be0c-147">次へ</span><span class="sxs-lookup"><span data-stu-id="5be0c-147">Next</span></span>](introduction-to-containers-and-docker.md)
