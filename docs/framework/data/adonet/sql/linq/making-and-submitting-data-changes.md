---
title: データの変更と変更の送信
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 18468c9a2018a28e85d87155d98b0853854013fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792971"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="d3255-102">データの変更と変更の送信</span><span class="sxs-lookup"><span data-stu-id="d3255-102">Making and Submitting Data Changes</span></span>

<span data-ttu-id="d3255-103">このセクションのトピックでは、データベースを変更し、その変更を送信する方法と、オプティミスティック コンカレンシーの競合を処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3255-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>

> [!NOTE]
> <span data-ttu-id="d3255-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の `Insert`、`Update`、および `Delete` の既定のデータベース操作メソッドはオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="d3255-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="d3255-105">詳細については、「[挿入、更新、および削除の各操作のカスタマイズ](customizing-insert-update-and-delete-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3255-105">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="d3255-106">Visual Studio を使用している開発者は、オブジェクト リレーショナル デザイナーを使用して、同じ用途のストアド プロシージャを開発できます。</span><span class="sxs-lookup"><span data-stu-id="d3255-106">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d3255-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d3255-107">In This Section</span></span>

<span data-ttu-id="d3255-108">[方法: 行をデータベースに挿入する](how-to-insert-rows-into-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="d3255-108">[How to: Insert Rows Into the Database](how-to-insert-rows-into-the-database.md) </span></span>\
<span data-ttu-id="d3255-109">オブジェクト モデルにオブジェクトを追加することにより、データベースに行を挿入する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3255-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>

<span data-ttu-id="d3255-110">[方法: データベースの行を更新する](how-to-update-rows-in-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="d3255-110">[How to: Update Rows in the Database](how-to-update-rows-in-the-database.md) </span></span>\
<span data-ttu-id="d3255-111">オブジェクト モデルのオブジェクトを更新することにより、データベースの行を更新する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3255-111">Describes how to update rows in the database by updating objects in the object model.</span></span>

<span data-ttu-id="d3255-112">[方法: 行をデータベースから削除する](how-to-delete-rows-from-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="d3255-112">[How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md) </span></span>\
<span data-ttu-id="d3255-113">オブジェクト モデルのオブジェクトを削除することにより、データベースの行を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3255-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>

<span data-ttu-id="d3255-114">[方法: データベースに変更内容を送信する](how-to-submit-changes-to-the-database.md) </span><span class="sxs-lookup"><span data-stu-id="d3255-114">[How to: Submit Changes to the Database](how-to-submit-changes-to-the-database.md) </span></span>\
<span data-ttu-id="d3255-115">オブジェクト モデルに対する変更をデータベースに送信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3255-115">Describes how to send object-model changes to the database.</span></span>

<span data-ttu-id="d3255-116">[方法: データ送信をトランザクションで囲む](how-to-bracket-data-submissions-by-using-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="d3255-116">[How to: Bracket Data Submissions by Using Transactions](how-to-bracket-data-submissions-by-using-transactions.md) </span></span>\
<span data-ttu-id="d3255-117">トランザクションに操作を含める方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3255-117">Describes how to include operations in a transaction.</span></span>

<span data-ttu-id="d3255-118">[方法: データベースを動的に作成する](how-to-dynamically-create-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="d3255-118">[How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md) </span></span>\
<span data-ttu-id="d3255-119">動的にデータベースを生成する方法と、この方法を使用する一般的なシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d3255-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>

<span data-ttu-id="d3255-120">[方法: 変更の競合を管理する](how-to-manage-change-conflicts.md) </span><span class="sxs-lookup"><span data-stu-id="d3255-120">[How to: Manage Change Conflicts](how-to-manage-change-conflicts.md) </span></span>\
<span data-ttu-id="d3255-121">オプティミスティック コンカレンシーの問題に対処する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3255-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
