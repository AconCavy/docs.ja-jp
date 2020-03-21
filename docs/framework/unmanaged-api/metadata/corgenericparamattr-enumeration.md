---
title: CorGenericParamAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
ms.openlocfilehash: bf0008ce9429671f0c156df4256bed0b2aaee184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176176"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="d9164-102">CorGenericParamAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="d9164-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="d9164-103">[:D ジェネリック](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)型の<xref:System.Type>パラメーターを記述する値を含みます。</span><span class="sxs-lookup"><span data-stu-id="d9164-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9164-104">構文</span><span class="sxs-lookup"><span data-stu-id="d9164-104">Syntax</span></span>  
  
```cpp  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="d9164-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="d9164-105">Members</span></span>  
  
|<span data-ttu-id="d9164-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d9164-106">Member</span></span>|<span data-ttu-id="d9164-107">説明</span><span class="sxs-lookup"><span data-stu-id="d9164-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="d9164-108">パラメーターの分散は、インターフェイスとデリゲートのジェネリック パラメーターにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="d9164-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="d9164-109">差異がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="d9164-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="d9164-110">共分散を示します。</span><span class="sxs-lookup"><span data-stu-id="d9164-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="d9164-111">反変性を示します。</span><span class="sxs-lookup"><span data-stu-id="d9164-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="d9164-112">任意<xref:System.Type>のパラメータに特殊な制約を適用できます。</span><span class="sxs-lookup"><span data-stu-id="d9164-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="d9164-113"><xref:System.Type>パラメーターに制約が適用されなくなっています。</span><span class="sxs-lookup"><span data-stu-id="d9164-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="d9164-114">パラメーターが<xref:System.Type>参照型である必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="d9164-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="d9164-115">パラメーターが<xref:System.Type>null 値にできない値型である必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="d9164-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="d9164-116">パラメーターにパラメーター<xref:System.Type>を受け取らない既定のパブリック コンストラクターが必要であることを示します。</span><span class="sxs-lookup"><span data-stu-id="d9164-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9164-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="d9164-117">Requirements</span></span>  
 <span data-ttu-id="d9164-118">**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9164-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9164-119">**ヘッダー:** コルドル.h</span><span class="sxs-lookup"><span data-stu-id="d9164-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d9164-120">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9164-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9164-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9164-121">See also</span></span>

- [<span data-ttu-id="d9164-122">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="d9164-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
