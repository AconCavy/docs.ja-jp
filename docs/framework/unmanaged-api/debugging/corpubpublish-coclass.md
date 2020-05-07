---
title: CorpubPublish コクラス
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
ms.openlocfilehash: e33029e8244fdfa180a79aa4a5b05b07f594d928
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860908"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="fedaa-102">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="fedaa-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="fedaa-103">アプリケーション ドメインとプロセスに関する情報を発行するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="fedaa-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fedaa-104">構文</span><span class="sxs-lookup"><span data-stu-id="fedaa-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="fedaa-105">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fedaa-105">Interfaces</span></span>  
  
|<span data-ttu-id="fedaa-106">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fedaa-106">Interface</span></span>|<span data-ttu-id="fedaa-107">説明</span><span class="sxs-lookup"><span data-stu-id="fedaa-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="fedaa-108">ICorPublish インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fedaa-108">ICorPublish Interface</span></span>](icorpublish-interface.md)|<span data-ttu-id="fedaa-109">プロセスおよびプロセス内のアプリケーションドメインに関する情報を公開するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="fedaa-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="fedaa-110">ICorPublishAppDomain インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fedaa-110">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)|<span data-ttu-id="fedaa-111">プロセス内のアプリケーションドメインに関する情報を表し、提供します。</span><span class="sxs-lookup"><span data-stu-id="fedaa-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="fedaa-112">ICorPublishAppDomainEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fedaa-112">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)|<span data-ttu-id="fedaa-113">プロセス内に現在存在するアプリケーションドメインのコレクションを走査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="fedaa-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="fedaa-114">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fedaa-114">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)|<span data-ttu-id="fedaa-115">コンピューター上で実行されているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="fedaa-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="fedaa-116">ICorPublishProcessEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fedaa-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)|<span data-ttu-id="fedaa-117">コンピューター上で実行されているプロセスのコレクションを走査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="fedaa-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fedaa-118">解説</span><span class="sxs-lookup"><span data-stu-id="fedaa-118">Remarks</span></span>  
 <span data-ttu-id="fedaa-119">一般的な発行シナリオでは、開発者がアプリケーションドメイン内のコンピューターで実行されているマネージコードをデバッグする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fedaa-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="fedaa-120">ホスト環境で、プロセス内で複数のアプリケーションドメインが実行されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fedaa-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="fedaa-121">開発者は、コンピューター上で実行されているすべてのプロセスを一覧表示し、特定のプロセスを選択するために、グラフィカルユーザーインターフェイスまたはその他の方法を使用したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="fedaa-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="fedaa-122">この一覧には、マネージコードを実行しているプロセス内のすべてのアプリケーションドメインが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fedaa-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="fedaa-123">開発者は、特定のアプリケーションドメインを特定し、そのドメインにデバッガーをアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="fedaa-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fedaa-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="fedaa-124">Requirements</span></span>  
 <span data-ttu-id="fedaa-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fedaa-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fedaa-126">**ヘッダー:** CorPub .idl</span><span class="sxs-lookup"><span data-stu-id="fedaa-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="fedaa-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fedaa-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fedaa-128">**.NET Framework のバージョン:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fedaa-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fedaa-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="fedaa-129">See also</span></span>

- [<span data-ttu-id="fedaa-130">デバッグ</span><span class="sxs-lookup"><span data-stu-id="fedaa-130">Debugging</span></span>](index.md)
