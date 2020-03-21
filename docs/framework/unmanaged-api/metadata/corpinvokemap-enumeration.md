---
title: CorPinvokeMap 列挙型
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: 8216dc3030b18428ab52fbf8385d392f81057aa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176150"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="98c35-102">CorPinvokeMap 列挙型</span><span class="sxs-lookup"><span data-stu-id="98c35-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="98c35-103">PInvoke 呼び出しのオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="98c35-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98c35-104">構文</span><span class="sxs-lookup"><span data-stu-id="98c35-104">Syntax</span></span>  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a><span data-ttu-id="98c35-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="98c35-105">Members</span></span>  
  
|<span data-ttu-id="98c35-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="98c35-106">Member</span></span>|<span data-ttu-id="98c35-107">説明</span><span class="sxs-lookup"><span data-stu-id="98c35-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="98c35-108">各メンバー名を指定どおりに使用します。</span><span class="sxs-lookup"><span data-stu-id="98c35-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="98c35-109">予約済み。</span><span class="sxs-lookup"><span data-stu-id="98c35-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="98c35-110">予約済み。</span><span class="sxs-lookup"><span data-stu-id="98c35-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="98c35-111">マルチバイト文字として文字列をマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="98c35-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="98c35-112">Unicode 2 バイト文字として文字列をマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="98c35-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="98c35-113">対象オペレーティング システムに適するように、自動的に文字列をマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="98c35-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="98c35-114">デフォルトは、Windows NT、Windows 2000、Windows XP、および Windows Server 2003 ファミリのユニコードです。デフォルトは、Windows 98 および Windows Me の ANSI です。</span><span class="sxs-lookup"><span data-stu-id="98c35-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="98c35-115">予約済み。</span><span class="sxs-lookup"><span data-stu-id="98c35-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="98c35-116">ANSI 文字セットで完全に一致しない Unicode 文字の最適なマッピングを実行します。</span><span class="sxs-lookup"><span data-stu-id="98c35-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="98c35-117">Unicode 文字の最適なマッピングを実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="98c35-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="98c35-118">この場合、すべてのマップできない文字は'?' に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="98c35-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="98c35-119">予約済み。</span><span class="sxs-lookup"><span data-stu-id="98c35-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="98c35-120">予約済み。</span><span class="sxs-lookup"><span data-stu-id="98c35-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="98c35-121">相互運用マーシャラーがマップできない文字を検出したときに例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="98c35-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="98c35-122">相互運用マーシャラーがマップできない文字を検出した場合は、例外をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="98c35-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="98c35-123">予約済み</span><span class="sxs-lookup"><span data-stu-id="98c35-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="98c35-124">呼び出し先が、属性付きメソッド`SetLastError`から戻る前に Win32 関数を呼び出すことを許可します。</span><span class="sxs-lookup"><span data-stu-id="98c35-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="98c35-125">予約済み</span><span class="sxs-lookup"><span data-stu-id="98c35-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="98c35-126">既定のプラットフォーム呼び出し規約を使用します。</span><span class="sxs-lookup"><span data-stu-id="98c35-126">Use the default platform calling convention.</span></span> <span data-ttu-id="98c35-127">たとえば、Windows では既定の設定`StdCall`が、Windows CE .NET`Cdecl`では .</span><span class="sxs-lookup"><span data-stu-id="98c35-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="98c35-128">呼び`Cdecl`出し規約を使用します。</span><span class="sxs-lookup"><span data-stu-id="98c35-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="98c35-129">この場合、呼び出し元はスタックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="98c35-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="98c35-130">これにより、関数の呼`varargs`び出し (可変個のパラメーターを受け取る関数) が可能になります。</span><span class="sxs-lookup"><span data-stu-id="98c35-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="98c35-131">呼び`StdCall`出し規約を使用します。</span><span class="sxs-lookup"><span data-stu-id="98c35-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="98c35-132">この場合、呼び出し先はスタックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="98c35-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="98c35-133">これは、プラットフォーム呼び出しでアンマネージ関数を呼び出すための既定の規約です。</span><span class="sxs-lookup"><span data-stu-id="98c35-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="98c35-134">呼び`ThisCall`出し規約を使用します。</span><span class="sxs-lookup"><span data-stu-id="98c35-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="98c35-135">この場合、最初のパラメータは`this`ポインタであり、レジスタECXに格納されます。</span><span class="sxs-lookup"><span data-stu-id="98c35-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="98c35-136">その他のパラメーターは、スタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="98c35-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="98c35-137">呼`ThisCall`び出し規約は、アンマネージ DLL からエクスポートされたクラスのメソッドを呼び出すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="98c35-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="98c35-138">予約済み。</span><span class="sxs-lookup"><span data-stu-id="98c35-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="98c35-139">予約済み。</span><span class="sxs-lookup"><span data-stu-id="98c35-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98c35-140">必要条件</span><span class="sxs-lookup"><span data-stu-id="98c35-140">Requirements</span></span>  
 <span data-ttu-id="98c35-141">**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98c35-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98c35-142">**ヘッダー:** コルドル.h</span><span class="sxs-lookup"><span data-stu-id="98c35-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="98c35-143">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98c35-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98c35-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="98c35-144">See also</span></span>

- [<span data-ttu-id="98c35-145">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="98c35-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
