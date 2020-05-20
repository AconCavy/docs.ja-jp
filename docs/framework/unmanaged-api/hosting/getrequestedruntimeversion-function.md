---
title: GetRequestedRuntimeVersion 関数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: b7a38d28b55842e9358bd9c7019b84c529526613
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617166"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="7d840-102">GetRequestedRuntimeVersion 関数</span><span class="sxs-lookup"><span data-stu-id="7d840-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="7d840-103">指定したアプリケーションによって要求された共通言語ランタイム (CLR) のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="7d840-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="7d840-104">そのバージョンがインストールされていない場合は、要求されるバージョンより前にインストールされた最も新しいバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="7d840-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="7d840-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="7d840-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d840-106">構文</span><span class="sxs-lookup"><span data-stu-id="7d840-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d840-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7d840-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="7d840-108">からアプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="7d840-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="7d840-109">入出力正常に完了したときのバージョン番号の文字列を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="7d840-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7d840-110">からバージョンバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="7d840-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="7d840-111">入出力バージョン番号文字列の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7d840-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d840-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="7d840-112">Return Value</span></span>  
 <span data-ttu-id="7d840-113">このメソッドは、次の値に加えて、Winerror.h で定義されている標準のコンポーネントオブジェクトモデル (COM) エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="7d840-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="7d840-114">リターン コード</span><span class="sxs-lookup"><span data-stu-id="7d840-114">Return code</span></span>|<span data-ttu-id="7d840-115">説明</span><span class="sxs-lookup"><span data-stu-id="7d840-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7d840-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d840-116">S_OK</span></span>|<span data-ttu-id="7d840-117">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="7d840-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="7d840-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="7d840-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="7d840-119">バージョンバッファーが、バージョン文字列を格納するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="7d840-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="7d840-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7d840-120">E_POINTER</span></span>|<span data-ttu-id="7d840-121">`pdwLength` が null です。</span><span class="sxs-lookup"><span data-stu-id="7d840-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d840-122">要件</span><span class="sxs-lookup"><span data-stu-id="7d840-122">Requirements</span></span>  
 <span data-ttu-id="7d840-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d840-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d840-124">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7d840-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d840-125">**ライブラリ:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7d840-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d840-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d840-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d840-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d840-127">See also</span></span>

- [<span data-ttu-id="7d840-128">GetRequestedRuntimeInfo 関数</span><span class="sxs-lookup"><span data-stu-id="7d840-128">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="7d840-129">GetVersionFromProcess 関数</span><span class="sxs-lookup"><span data-stu-id="7d840-129">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="7d840-130">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="7d840-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
