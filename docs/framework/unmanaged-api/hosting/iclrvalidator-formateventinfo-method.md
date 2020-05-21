---
title: ICLRValidator::FormatEventInfo メソッド
ms.date: 03/30/2017
api_name:
- ICLRValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type:
- apiref
ms.openlocfilehash: 164a8c15a501af44aabb95852400621f05bbe873
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762800"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="61b37-102">ICLRValidator::FormatEventInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="61b37-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="61b37-103">指定された検証エラーに関する詳細メッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="61b37-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61b37-104">構文</span><span class="sxs-lookup"><span data-stu-id="61b37-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61b37-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="61b37-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="61b37-106">から検証エラーハンドラーに渡された HRESULT 値。</span><span class="sxs-lookup"><span data-stu-id="61b37-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="61b37-107">から`VEContext`検証エラーに関するコンテキスト情報を格納しているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="61b37-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="61b37-108">[入力、出力]わかりやすいエラーメッセージ。</span><span class="sxs-lookup"><span data-stu-id="61b37-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="61b37-109">からエラーメッセージの最大長。</span><span class="sxs-lookup"><span data-stu-id="61b37-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="61b37-110">からメッセージで使用される追加パラメーターのセーフ配列。</span><span class="sxs-lookup"><span data-stu-id="61b37-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61b37-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="61b37-111">Return Value</span></span>  
  
|<span data-ttu-id="61b37-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61b37-112">HRESULT</span></span>|<span data-ttu-id="61b37-113">説明</span><span class="sxs-lookup"><span data-stu-id="61b37-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61b37-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="61b37-114">S_OK</span></span>|<span data-ttu-id="61b37-115">`FormatEventInfo`正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="61b37-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="61b37-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="61b37-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="61b37-117">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="61b37-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="61b37-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="61b37-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="61b37-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="61b37-119">The call timed out.</span></span>|  
|<span data-ttu-id="61b37-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="61b37-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="61b37-121">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="61b37-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="61b37-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="61b37-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="61b37-123">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="61b37-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="61b37-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="61b37-124">E_FAIL</span></span>|<span data-ttu-id="61b37-125">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="61b37-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="61b37-126">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="61b37-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="61b37-127">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="61b37-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61b37-128">要件</span><span class="sxs-lookup"><span data-stu-id="61b37-128">Requirements</span></span>  
 <span data-ttu-id="61b37-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61b37-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61b37-130">**ヘッダー:** IValidator、IValidator</span><span class="sxs-lookup"><span data-stu-id="61b37-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="61b37-131">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="61b37-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61b37-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61b37-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61b37-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="61b37-133">See also</span></span>

- [<span data-ttu-id="61b37-134">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="61b37-134">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="61b37-135">ICLRValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="61b37-135">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
