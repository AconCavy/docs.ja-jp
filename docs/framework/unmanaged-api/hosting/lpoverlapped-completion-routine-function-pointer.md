---
title: LPOVERLAPPED_COMPLETION_ROUTINE 関数ポインター
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
ms.openlocfilehash: c0bdd9e59f5794dbb0d447dc2cc6cb682bfdf09f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008483"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a><span data-ttu-id="b6226-102">LPOVERLAPPED_COMPLETION_ROUTINE 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="b6226-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="b6226-103">デバイスに対する重複 I/O (非同期 I/O) が完了したときに、ホストに通知する関数を指します。</span><span class="sxs-lookup"><span data-stu-id="b6226-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="b6226-104">この関数ポインターは .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="b6226-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6226-105">構文</span><span class="sxs-lookup"><span data-stu-id="b6226-105">Syntax</span></span>  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6226-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b6226-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="b6226-107">からデバイスが閉じられている場合は、エラーコードである値。それ以外の場合、この値は0です。</span><span class="sxs-lookup"><span data-stu-id="b6226-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="b6226-108">デバイスを閉じると、デバイスに対するすべての保留中の i/o が直ちに完了します。</span><span class="sxs-lookup"><span data-stu-id="b6226-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="b6226-109">からI/o 操作によって転送されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="b6226-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="b6226-110">からI/o 要求を完了するために使用される情報を格納する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b6226-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6226-111">コメント</span><span class="sxs-lookup"><span data-stu-id="b6226-111">Remarks</span></span>  
 <span data-ttu-id="b6226-112">`LPOVERLAPPED_COMPLETION_ROUTINE`ポイントがコールバック関数であり、ホストアプリケーションのライターによって実装されている必要がある関数。</span><span class="sxs-lookup"><span data-stu-id="b6226-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="b6226-113">コールバック関数を使用すると、ホストは、完了した i/o 要求を処理できます。</span><span class="sxs-lookup"><span data-stu-id="b6226-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6226-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="b6226-114">Requirements</span></span>  
 <span data-ttu-id="b6226-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6226-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6226-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b6226-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6226-117">**ライブラリ:** Mscorwks.dll</span><span class="sxs-lookup"><span data-stu-id="b6226-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="b6226-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6226-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6226-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6226-119">See also</span></span>

- [<span data-ttu-id="b6226-120">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="b6226-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
