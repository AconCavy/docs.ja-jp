---
title: CorValidatorModuleType 列挙型
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
ms.openlocfilehash: 038e2ec20e5fd01edf9835080e0f7a15ec862fd9
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008938"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="2243d-102">CorValidatorModuleType 列挙型</span><span class="sxs-lookup"><span data-stu-id="2243d-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="2243d-103">モジュールの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="2243d-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2243d-104">構文</span><span class="sxs-lookup"><span data-stu-id="2243d-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a><span data-ttu-id="2243d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="2243d-105">Members</span></span>  
  
|<span data-ttu-id="2243d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2243d-106">Member</span></span>|<span data-ttu-id="2243d-107">説明</span><span class="sxs-lookup"><span data-stu-id="2243d-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="2243d-108">モジュールの型が無効です。</span><span class="sxs-lookup"><span data-stu-id="2243d-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="2243d-109">列挙型の最小値 `CorValidatorModuleType` 。</span><span class="sxs-lookup"><span data-stu-id="2243d-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="2243d-110">モジュールは、移植可能な実行可能 (PE) ファイルです。</span><span class="sxs-lookup"><span data-stu-id="2243d-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="2243d-111">モジュールは .obj ファイルです。</span><span class="sxs-lookup"><span data-stu-id="2243d-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="2243d-112">モジュールは、エディットコンティニュのデバッガーセッションです。</span><span class="sxs-lookup"><span data-stu-id="2243d-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="2243d-113">モジュールは、インクリメンタルビルドされたモジュールです。</span><span class="sxs-lookup"><span data-stu-id="2243d-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="2243d-114">列挙型の最大値 `CorValidatorModuleType` 。</span><span class="sxs-lookup"><span data-stu-id="2243d-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2243d-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="2243d-115">Requirements</span></span>  
 <span data-ttu-id="2243d-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2243d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2243d-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="2243d-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2243d-118">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2243d-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2243d-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2243d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2243d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="2243d-120">See also</span></span>

- [<span data-ttu-id="2243d-121">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="2243d-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
