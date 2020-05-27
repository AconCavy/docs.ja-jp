---
title: CorTypeAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
ms.openlocfilehash: b6936081ca3dbadb4f802a6856fafb53f6cef3fa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008964"
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="78611-102">CorTypeAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="78611-102">CorTypeAttr Enumeration</span></span>
<span data-ttu-id="78611-103">メタデータ型を示す値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="78611-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78611-104">構文</span><span class="sxs-lookup"><span data-stu-id="78611-104">Syntax</span></span>  
  
```cpp  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="78611-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="78611-105">Members</span></span>  
  
|<span data-ttu-id="78611-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="78611-106">Member</span></span>|<span data-ttu-id="78611-107">説明</span><span class="sxs-lookup"><span data-stu-id="78611-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="78611-108">型の可視性情報に使用されます。</span><span class="sxs-lookup"><span data-stu-id="78611-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="78611-109">型がパブリックスコープ内にないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="78611-110">型がパブリックスコープ内にあることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="78611-111">型がパブリックの可視性で入れ子になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="78611-112">型がプライベート可視性で入れ子になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="78611-113">型がファミリの可視性で入れ子になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="78611-114">型がアセンブリの可視性で入れ子になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="78611-115">型がファミリおよびアセンブリの可視性で入れ子になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="78611-116">型が、ファミリまたはアセンブリの参照可能範囲に入れ子になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="78611-117">型のレイアウト情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="78611-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="78611-118">この型のフィールドが自動的にレイアウトされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="78611-119">この型のフィールドを順番に配置することを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="78611-120">フィールドレイアウトが明示的に指定されていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="78611-121">型に関するセマンティック情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="78611-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="78611-122">型がクラスであることを示します。</span><span class="sxs-lookup"><span data-stu-id="78611-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="78611-123">型がインターフェイスであることを示します。</span><span class="sxs-lookup"><span data-stu-id="78611-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="78611-124">型が抽象的であることを示します。</span><span class="sxs-lookup"><span data-stu-id="78611-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="78611-125">型を拡張できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="78611-126">クラス名が特別であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-126">Specifies that the class name is special.</span></span> <span data-ttu-id="78611-127">その名前は、方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="78611-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="78611-128">型がインポートされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="78611-129">型がシリアル化可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="78611-130">この型が Windows ランタイム型であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-130">Specifies that this type is a Windows Runtime type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="78611-131">文字列をエンコードおよび書式設定する方法に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="78611-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="78611-132">この型が LPTSTR を ANSI と解釈することを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="78611-133">この型が LPTSTR を Unicode として解釈することを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="78611-134">この型が LPTSTR を自動的に解釈することを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="78611-135">によって指定された標準以外のエンコーディングを型が持つことを指定し `CustomFormatMask` ます。</span><span class="sxs-lookup"><span data-stu-id="78611-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="78611-136">ネイティブ相互運用機能の非標準のエンコード情報を取得するには、このマスクを使用します。</span><span class="sxs-lookup"><span data-stu-id="78611-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="78611-137">これら2つのビットの値の意味は、指定されていません。</span><span class="sxs-lookup"><span data-stu-id="78611-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="78611-138">静的フィールドに最初にアクセスしようとする前に型を初期化する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="78611-139">型がエクスポートされ、型フォワーダーが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="78611-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="78611-140">このフラグと以下のフラグは、共通言語ランタイムによって内部的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="78611-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="78611-141">共通言語ランタイムが名前のエンコーディングを確認する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="78611-142">型にセキュリティが関連付けられていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="78611-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78611-143">必要条件</span><span class="sxs-lookup"><span data-stu-id="78611-143">Requirements</span></span>  
 <span data-ttu-id="78611-144">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78611-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78611-145">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="78611-145">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="78611-146">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78611-146">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78611-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="78611-147">See also</span></span>

- [<span data-ttu-id="78611-148">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="78611-148">Metadata Enumerations</span></span>](metadata-enumerations.md)
