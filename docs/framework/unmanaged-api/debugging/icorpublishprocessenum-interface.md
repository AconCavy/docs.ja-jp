---
title: ICorPublishProcessEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 657d2d638a419ba88d4cf7152f4505de1bd23706
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421073"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="da610-102">ICorPublishProcessEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da610-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="da610-103">[ICorPublishProcess](icorpublishprocess-interface.md)オブジェクトのコレクションを走査するメソッドを提供する[ICorPublishEnum](icorpublishenum-interface.md)インターフェイスのサブクラス。</span><span class="sxs-lookup"><span data-stu-id="da610-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da610-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="da610-104">Methods</span></span>  
  
|<span data-ttu-id="da610-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="da610-105">Method</span></span>|<span data-ttu-id="da610-106">説明</span><span class="sxs-lookup"><span data-stu-id="da610-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da610-107">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="da610-107">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="da610-108">現在の位置から開始して、指定した数の `ICorPublishProcess` インスタンスをコレクションから取得します。</span><span class="sxs-lookup"><span data-stu-id="da610-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da610-109">解説</span><span class="sxs-lookup"><span data-stu-id="da610-109">Remarks</span></span>  
 <span data-ttu-id="da610-110">インターフェイスは、 `ICorPublishProcessEnum` 抽象インターフェイス[ICorPublishEnum](icorpublishenum-interface.md)のメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="da610-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="da610-111">`ICorPublishProcessEnum`インスタンスは、 [ICorPublish:: EnumProcesses](icorpublish-enumprocesses-method.md)メソッドによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="da610-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="da610-112">オブジェクトのコレクションの走査 `ICorPublishProcess` は、インスタンスの作成時に指定されたフィルター条件に基づいてい `ICorPublishProcessEnum` ます。</span><span class="sxs-lookup"><span data-stu-id="da610-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da610-113">要件</span><span class="sxs-lookup"><span data-stu-id="da610-113">Requirements</span></span>  
 <span data-ttu-id="da610-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da610-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da610-115">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="da610-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="da610-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da610-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da610-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da610-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da610-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="da610-118">See also</span></span>

- [<span data-ttu-id="da610-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="da610-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="da610-120">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="da610-120">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
