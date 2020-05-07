---
title: ICLRDebuggingLibraryProvider::ProvideLibrary メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
ms.openlocfilehash: 7bbb49dc6ee9b1d29dd61ccdcfdacb62740133ed
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860263"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="449d9-102">ICLRDebuggingLibraryProvider::ProvideLibrary メソッド</span><span class="sxs-lookup"><span data-stu-id="449d9-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>

<span data-ttu-id="449d9-103">共通言語ランタイム (CLR) のバージョン固有のデバッグライブラリをオンデマンドで検索して読み込むことができるようにする、ライブラリプロバイダーのコールバックインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="449d9-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>

## <a name="syntax"></a><span data-ttu-id="449d9-104">構文</span><span class="sxs-lookup"><span data-stu-id="449d9-104">Syntax</span></span>

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a><span data-ttu-id="449d9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="449d9-105">Parameters</span></span>

`pwszFilename` \
<span data-ttu-id="449d9-106">から要求されているモジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="449d9-106">[in] The name of the module being requested.</span></span>

`dwTimestamp` \
<span data-ttu-id="449d9-107">からPE ファイルの COFF ファイルヘッダーに格納されている日付と時刻のタイムスタンプ。</span><span class="sxs-lookup"><span data-stu-id="449d9-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>

`pLibraryProvider` \
<span data-ttu-id="449d9-108">からPE `SizeOfImage`ファイルの COFF オプションファイルヘッダーに格納されているフィールド。</span><span class="sxs-lookup"><span data-stu-id="449d9-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>

`hModule` \
<span data-ttu-id="449d9-109">入出力要求されたモジュールへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="449d9-109">[out] The handle to the requested module.</span></span>

## <a name="return-value"></a><span data-ttu-id="449d9-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="449d9-110">Return Value</span></span>

<span data-ttu-id="449d9-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="449d9-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="449d9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="449d9-112">HRESULT</span></span>|<span data-ttu-id="449d9-113">説明</span><span class="sxs-lookup"><span data-stu-id="449d9-113">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="449d9-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="449d9-114">S_OK</span></span>|<span data-ttu-id="449d9-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="449d9-115">The method completed successfully.</span></span>|

## <a name="exceptions"></a><span data-ttu-id="449d9-116">例外</span><span class="sxs-lookup"><span data-stu-id="449d9-116">Exceptions</span></span>

## <a name="remarks"></a><span data-ttu-id="449d9-117">解説</span><span class="sxs-lookup"><span data-stu-id="449d9-117">Remarks</span></span>

<span data-ttu-id="449d9-118">`ProvideLibrary`デバッガーが、mscordbi.dll や mscordacwks などの特定の CLR ファイルをデバッグするために必要なモジュールを提供できるようにします。</span><span class="sxs-lookup"><span data-stu-id="449d9-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="449d9-119">モジュールハンドルは、 [ICLRDebugging:: CanUnloadNow](iclrdebugging-canunloadnow-method.md)メソッドの呼び出しによって解放される可能性があることが示されるまで有効なままにしておく必要があります。その時点で、呼び出し元がハンドルを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="449d9-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>

<span data-ttu-id="449d9-120">デバッガーは、使用可能な任意の方法を使用して、デバッグモジュールを見つけたり調達したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="449d9-120">The debugger may use any available means to locate or procure the debugging module.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="449d9-121">この機能により、API 呼び出し元は、実行可能ファイルや悪意のあるコードを含むモジュールを提供できます。</span><span class="sxs-lookup"><span data-stu-id="449d9-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="449d9-122">セキュリティ上の理由から、呼び出し元はを`ProvideLibrary`使用して、それ自体を実行しないコードを配布することはできません。</span><span class="sxs-lookup"><span data-stu-id="449d9-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>
>
> <span data-ttu-id="449d9-123">Mscordbi.dll や mscordacwks など、既にリリースされているライブラリで深刻なセキュリティの問題が検出された場合、shim には、ファイルの不適切なバージョンを認識するように修正プログラムを適用できます。</span><span class="sxs-lookup"><span data-stu-id="449d9-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="449d9-124">その後、shim は、修正されたバージョンのファイルに対する要求を発行し、要求に応答して指定されている場合は無効なバージョンを拒否します。</span><span class="sxs-lookup"><span data-stu-id="449d9-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="449d9-125">これは、ユーザーが shim の新しいバージョンに修正プログラムを適用している場合にのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="449d9-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="449d9-126">修正プログラム脆弱性のバージョンは脆弱なままです。</span><span class="sxs-lookup"><span data-stu-id="449d9-126">Unpatched versions will remain vulnerable.</span></span>

## <a name="requirements"></a><span data-ttu-id="449d9-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="449d9-127">Requirements</span></span>

<span data-ttu-id="449d9-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="449d9-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="449d9-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="449d9-129">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="449d9-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="449d9-130">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="449d9-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="449d9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="449d9-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="449d9-132">See also</span></span>

- [<span data-ttu-id="449d9-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="449d9-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="449d9-134">デバッグ</span><span class="sxs-lookup"><span data-stu-id="449d9-134">Debugging</span></span>](index.md)
