---
title: ワークフロー ソリューションでのサービス参照の追加
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 577026249e00b528cf5c6e7ccd9527e02cb22a28
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597671"
---
# <a name="add-a-service-reference-in-a-workflow-solution"></a><span data-ttu-id="687aa-102">ワークフローソリューションでのサービス参照の追加</span><span class="sxs-lookup"><span data-stu-id="687aa-102">Add a Service Reference in a Workflow Solution</span></span>

<span data-ttu-id="687aa-103">ワークフロー アプリケーションでのサービス参照の追加は、通常の WCF アプリケーションとは動作が少し異なります。</span><span class="sxs-lookup"><span data-stu-id="687aa-103">Adding a service reference in a workflow application works a little differently than a regular WCF application.</span></span> <span data-ttu-id="687aa-104">[サービス参照の**追加**] を選択し、サービスの URL を指定すると、  >  **Service Reference**メタデータがダウンロードされ、カスタムアクティビティが生成されます。これにより、wcf サービスまたは wcf ワークフローサービスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="687aa-104">When you select **Add** > **Service Reference** and specify the URL to the service, the metadata is downloaded and custom activities are generated that allow you to call that WCF service or WCF workflow service.</span></span> <span data-ttu-id="687aa-105">サービス参照を追加した後、生成されたアクティビティがビルドされるように、ソリューションを再ビルドします。</span><span class="sxs-lookup"><span data-stu-id="687aa-105">After adding a service reference, rebuild the solution so the generated activities are built.</span></span> <span data-ttu-id="687aa-106">これにより、アクティビティがワークフロー デザイナー ツールボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="687aa-106">They will then appear in the workflow designer toolbox.</span></span> <span data-ttu-id="687aa-107">これは、ワークフローソリューション内にサービス参照を追加する場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="687aa-107">This will only work if you are adding a service reference within a workflow solution.</span></span> <span data-ttu-id="687aa-108">次の web キャストは、他の種類のプロジェクトにサービス参照を追加する方法を示しています。 [Web プロジェクトのワークフローから WCF サービスを呼び出し](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)ます。</span><span class="sxs-lookup"><span data-stu-id="687aa-108">The following web cast shows how to add a service reference in other types of projects: [Calling a WCF Service from a Workflow in a Web Project](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).</span></span>

<span data-ttu-id="687aa-109">同じ操作名が含まれるサービスへのサービス参照を複数追加すると、問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="687aa-109">Adding two or more service references to services that contain the same operation name will cause a problem.</span></span> <span data-ttu-id="687aa-110">生成されたアクティビティは最初のサービス操作しか呼び出しません。</span><span class="sxs-lookup"><span data-stu-id="687aa-110">The generated activities will call only the first service operation.</span></span> <span data-ttu-id="687aa-111">この問題を回避するには、サービス操作の名前を変更するか、生成された各アクティビティ内のエンドポイント構成名を変更します。</span><span class="sxs-lookup"><span data-stu-id="687aa-111">To work around this issue, rename the service operations so they are different, or change the endpoint configuration name within each generated activity.</span></span>

## <a name="see-also"></a><span data-ttu-id="687aa-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="687aa-112">See also</span></span>

- [<span data-ttu-id="687aa-113">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="687aa-113">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="687aa-114">Web プロジェクトでのワークフローからの WCF サービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="687aa-114">Calling a WCF Service from a Workflow in a Web Project</span></span>](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
