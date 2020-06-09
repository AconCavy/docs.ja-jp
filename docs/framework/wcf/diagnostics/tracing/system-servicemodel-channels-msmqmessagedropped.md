---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 4b016f53a75d9527a5cd1bbadacacd650b7f35b0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601913"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="a0654-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="a0654-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="a0654-103">MSMQ はメッセージを破棄しました。</span><span class="sxs-lookup"><span data-stu-id="a0654-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a0654-104">説明</span><span class="sxs-lookup"><span data-stu-id="a0654-104">Description</span></span>  
 <span data-ttu-id="a0654-105">このトレースは、MSMQ メッセージが破棄されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="a0654-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="a0654-106">MSMQ メッセージは Windows Communication Foundation (WCF) (NetMsmqBinding または MsmqIntegrationBinding で使用) が処理できない場合に削除できます。</span><span class="sxs-lookup"><span data-stu-id="a0654-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="a0654-107">このようなメッセージは、有害メッセージと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a0654-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="a0654-108">有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Drop` に設定されていると破棄されます。</span><span class="sxs-lookup"><span data-stu-id="a0654-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="a0654-109">破棄されたメッセージはキューから削除され、元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="a0654-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="a0654-110">メッセージが有害になった場合の詳細、およびメッセージを適切に処理するようにサービスを構成する方法については、「[有害メッセージの処理](../../feature-details/poison-message-handling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0654-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0654-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0654-111">See also</span></span>

- [<span data-ttu-id="a0654-112">トレース</span><span class="sxs-lookup"><span data-stu-id="a0654-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="a0654-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a0654-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a0654-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="a0654-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="a0654-115">有害メッセージの処理</span><span class="sxs-lookup"><span data-stu-id="a0654-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
