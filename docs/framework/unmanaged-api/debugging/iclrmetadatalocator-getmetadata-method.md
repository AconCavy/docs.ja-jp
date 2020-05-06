---
title: ICLRMetadataLocator::GetMetadata メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
ms.openlocfilehash: ad309290319396ff4e74e30d572effeffe802d1d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859881"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="017a2-102">ICLRMetadataLocator::GetMetadata メソッド</span><span class="sxs-lookup"><span data-stu-id="017a2-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="017a2-103">イメージのメタデータを取得するために、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="017a2-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="017a2-104">構文</span><span class="sxs-lookup"><span data-stu-id="017a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="017a2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="017a2-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="017a2-106">からイメージファイルのパスを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="017a2-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="017a2-107">からイメージファイルのタイムスタンプ。</span><span class="sxs-lookup"><span data-stu-id="017a2-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="017a2-108">からイメージファイルのサイズ。</span><span class="sxs-lookup"><span data-stu-id="017a2-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="017a2-109">からイメージのグローバル一意識別子。</span><span class="sxs-lookup"><span data-stu-id="017a2-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="017a2-110">からメタデータの相対仮想アドレス (RVA)。</span><span class="sxs-lookup"><span data-stu-id="017a2-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="017a2-111">アドレスは、イメージのベースアドレスを基準としています。</span><span class="sxs-lookup"><span data-stu-id="017a2-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="017a2-112">から将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="017a2-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="017a2-113">からメタデータを格納するバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="017a2-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="017a2-114">入出力メタデータを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="017a2-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="017a2-115">入出力返されるメタデータのサイズ。</span><span class="sxs-lookup"><span data-stu-id="017a2-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="017a2-116">解説</span><span class="sxs-lookup"><span data-stu-id="017a2-116">Remarks</span></span>  
 <span data-ttu-id="017a2-117">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="017a2-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="017a2-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="017a2-118">Requirements</span></span>  
 <span data-ttu-id="017a2-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="017a2-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="017a2-120">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="017a2-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="017a2-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="017a2-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="017a2-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="017a2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="017a2-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="017a2-123">See also</span></span>

- [<span data-ttu-id="017a2-124">ICLRMetadataLocator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="017a2-124">ICLRMetadataLocator Interface</span></span>](iclrmetadatalocator-interface.md)
