---
title: EnumerateCLRs 関数
ms.date: 03/30/2017
api_name:
- EnumerateCLRs
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type:
- apiref
ms.openlocfilehash: 1f33fb98712939d1e687798547b784819f164d63
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860725"
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="435a6-102">EnumerateCLRs 関数</span><span class="sxs-lookup"><span data-stu-id="435a6-102">EnumerateCLRs Function</span></span>
<span data-ttu-id="435a6-103">プロセスで CLR を列挙するメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="435a6-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="435a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="435a6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="435a6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="435a6-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="435a6-106">[in] 読み込まれている CLR を列挙するプロセスのプロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="435a6-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="435a6-107">[out] CLR スタートアップの継続に使用されるイベント ハンドルを含む配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="435a6-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="435a6-108">配列内の各ハンドルが有効であることは保証されません。</span><span class="sxs-lookup"><span data-stu-id="435a6-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="435a6-109">ハンドルは、`ppStringArrayOut` の同じインデックスにある対応するランタイムの継続スタートアップ イベントとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="435a6-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="435a6-110">[out] プロセスに読み込まれている CLR の完全パスを指定する文字列の配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="435a6-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="435a6-111">[out] 同じサイズの `ppHandleArrayOut` および `pdwArrayLengthOut` の長さを含む DWORD へのポインター。</span><span class="sxs-lookup"><span data-stu-id="435a6-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="435a6-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="435a6-112">Return Value</span></span>  
 <span data-ttu-id="435a6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="435a6-113">S_OK</span></span>  
 <span data-ttu-id="435a6-114">プロセス内の CLR 数が正常に判別され、対応するハンドルとパスの配列が正しく入力されました。</span><span class="sxs-lookup"><span data-stu-id="435a6-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="435a6-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="435a6-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="435a6-116">`ppHandleArrayOut` または `ppStringArrayOut` のいずれかが null であるか、または `pdwArrayLengthOut` が null です。</span><span class="sxs-lookup"><span data-stu-id="435a6-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="435a6-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="435a6-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="435a6-118">ハンドルおよびパス配列に十分なメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="435a6-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="435a6-119">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="435a6-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="435a6-120">読み込まれている CLR を列挙できません。</span><span class="sxs-lookup"><span data-stu-id="435a6-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="435a6-121">解説</span><span class="sxs-lookup"><span data-stu-id="435a6-121">Remarks</span></span>  
 <span data-ttu-id="435a6-122">この関数は、`debuggeePID` で指定された対象プロセスについて、プロセスに読み込まれている CLR のパスの配列 (`ppStringArrayOut`)、同じインデックスにある CLR の継続スタートアップ イベントを含むイベント ハンドルの配列 (`ppHandleArrayOut`)、および読み込まれている CLR の数を示す配列のサイズ (`pdwArrayLengthOut`) を返します。</span><span class="sxs-lookup"><span data-stu-id="435a6-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="435a6-123">Windows オペレーティング システムでは、`debuggeePID` がプロセス識別子に対応づけられます。</span><span class="sxs-lookup"><span data-stu-id="435a6-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="435a6-124">`ppHandleArrayOut` および `ppStringArrayOut` のメモリはこの関数によって割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="435a6-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="435a6-125">割り当てられたメモリを解放するには、 [CloseCLREnumeration 関数](closeclrenumeration-function.md)を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="435a6-125">To free the memory allocated, you must call [CloseCLREnumeration Function](closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="435a6-126">両方の配列パラメーターを null に設定してこの関数を呼び出すことで、対象プロセス内の CLR の数を取得できます。</span><span class="sxs-lookup"><span data-stu-id="435a6-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="435a6-127">この数から、呼び出し元は、作成されるバッファーのサイズを推論できます (`(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`)。</span><span class="sxs-lookup"><span data-stu-id="435a6-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="435a6-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="435a6-128">Requirements</span></span>  
 <span data-ttu-id="435a6-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="435a6-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="435a6-130">**ヘッダー:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="435a6-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="435a6-131">**ライブラリ:** dbgshim .dll</span><span class="sxs-lookup"><span data-stu-id="435a6-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="435a6-132">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="435a6-132">**.NET Framework Versions:** 3.5 SP1</span></span>
