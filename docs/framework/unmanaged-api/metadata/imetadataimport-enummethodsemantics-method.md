---
title: IMetaDataImport::EnumMethodSemantics メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175461"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="b17d6-102">IMetaDataImport::EnumMethodSemantics メソッド</span><span class="sxs-lookup"><span data-stu-id="b17d6-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="b17d6-103">指定したメソッドが関連付けられているプロパティおよびプロパティ変更イベントを列挙します。</span><span class="sxs-lookup"><span data-stu-id="b17d6-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b17d6-104">構文</span><span class="sxs-lookup"><span data-stu-id="b17d6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b17d6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b17d6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b17d6-106">[イン、アウト]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b17d6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b17d6-107">このメソッドの最初の呼び出しでは、NULL にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b17d6-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="b17d6-108">[in]列挙のスコープを制限する MethodDef トークン。</span><span class="sxs-lookup"><span data-stu-id="b17d6-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="b17d6-109">[アウト]イベントまたはプロパティを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="b17d6-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b17d6-110">[in] `rEventProp` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="b17d6-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="b17d6-111">[アウト]で返されるイベントまたはプロパティの`rEventProp`数。</span><span class="sxs-lookup"><span data-stu-id="b17d6-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b17d6-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="b17d6-112">Return Value</span></span>  
  
|<span data-ttu-id="b17d6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b17d6-113">HRESULT</span></span>|<span data-ttu-id="b17d6-114">説明</span><span class="sxs-lookup"><span data-stu-id="b17d6-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b17d6-115">`EnumMethodSemantics`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="b17d6-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b17d6-116">列挙するイベントまたはプロパティはありません。</span><span class="sxs-lookup"><span data-stu-id="b17d6-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="b17d6-117">その場合は、`pcEventProp`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="b17d6-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b17d6-118">解説</span><span class="sxs-lookup"><span data-stu-id="b17d6-118">Remarks</span></span>  
 <span data-ttu-id="b17d6-119">多くの共通言語ランタイム型は *、プロパティ*`Changed``On`イベントとプロパティに関連する*プロパティ*`Changed`メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="b17d6-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="b17d6-120">たとえば、型は<xref:System.Windows.Forms.Control?displayProperty=nameWithType><xref:System.Windows.Forms.Control.Font%2A>プロパティ、イベント、およびメソッド<xref:System.Windows.Forms.Control.FontChanged>を定義します<xref:System.Windows.Forms.Control.OnFontChanged%2A>。</span><span class="sxs-lookup"><span data-stu-id="b17d6-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="b17d6-121">プロパティの set アクセサ<xref:System.Windows.Forms.Control.Font%2A>メソッド<xref:System.Windows.Forms.Control.OnFontChanged%2A>はメソッドを呼び出し、<xref:System.Windows.Forms.Control.FontChanged>イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="b17d6-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="b17d6-122">プロパティとイベント`EnumMethodSemantics`への参照を取得するには<xref:System.Windows.Forms.Control.OnFontChanged%2A>、 メソッド定義を<xref:System.Windows.Forms.Control.Font%2A>使用して呼<xref:System.Windows.Forms.Control.FontChanged>び出します。</span><span class="sxs-lookup"><span data-stu-id="b17d6-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b17d6-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="b17d6-123">Requirements</span></span>  
 <span data-ttu-id="b17d6-124">**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b17d6-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b17d6-125">**ヘッダー:** コル・h</span><span class="sxs-lookup"><span data-stu-id="b17d6-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b17d6-126">**ライブラリ:** MsCorEE.dll にリソースとして含まれる</span><span class="sxs-lookup"><span data-stu-id="b17d6-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b17d6-127">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b17d6-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b17d6-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="b17d6-128">See also</span></span>

- [<span data-ttu-id="b17d6-129">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b17d6-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b17d6-130">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b17d6-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
