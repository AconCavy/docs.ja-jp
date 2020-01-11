---
title: ICLRStrongName::StrongNameSignatureGenerationEx メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
ms.openlocfilehash: 34614fe24127787a113bab4975a50f1c8d2d875e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899497"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="6e931-102">ICLRStrongName::StrongNameSignatureGenerationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="6e931-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="6e931-103">指定したフラグに従って、指定したアセンブリの厳密な名前の署名を生成します。</span><span class="sxs-lookup"><span data-stu-id="6e931-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e931-104">構文</span><span class="sxs-lookup"><span data-stu-id="6e931-104">Syntax</span></span>  
  
```cpp
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e931-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e931-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="6e931-106">から厳密な名前の署名が生成されるアセンブリのマニフェストを含むファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="6e931-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="6e931-107">から公開キーと秘密キーのペアを格納するキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="6e931-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="6e931-108">`pbKeyBlob` が null の場合、`wszKeyContainer` は暗号化サービスプロバイダー (CSP) 内の有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e931-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="6e931-109">この場合、コンテナーに格納されているキーペアがファイルの署名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e931-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="6e931-110">`pbKeyBlob` が null でない場合、キーのペアは、バイナリラージオブジェクト (BLOB) に格納されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="6e931-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="6e931-111">から公開/秘密キーのペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6e931-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="6e931-112">このペアは、Win32 `CryptExportKey` 関数によって作成される形式です。</span><span class="sxs-lookup"><span data-stu-id="6e931-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="6e931-113">`pbKeyBlob` が null の場合、`wszKeyContainer` によって指定されたキーコンテナーには、キーのペアが含まれていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="6e931-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="6e931-114">から`pbKeyBlob`のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="6e931-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="6e931-115">入出力共通言語ランタイムが署名を返す場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6e931-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="6e931-116">`ppbSignatureBlob` が null の場合、ランタイムは `wszFilePath`によって指定されたファイルに署名を格納します。</span><span class="sxs-lookup"><span data-stu-id="6e931-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="6e931-117">`ppbSignatureBlob` が null でない場合は、共通言語ランタイムによって、署名を返す領域が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="6e931-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="6e931-118">呼び出し元は、 [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)メソッドを使用してこの領域を解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e931-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="6e931-119">入出力返されたシグネチャのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="6e931-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6e931-120">から次の値の1つまたは複数です。</span><span class="sxs-lookup"><span data-stu-id="6e931-120">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="6e931-121">`SN_SIGN_ALL_FILES` (0x00000001)-リンクされたモジュールのすべてのハッシュを再計算します。</span><span class="sxs-lookup"><span data-stu-id="6e931-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="6e931-122">`SN_TEST_SIGN` (0x00000002)-アセンブリにテスト署名します。</span><span class="sxs-lookup"><span data-stu-id="6e931-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e931-123">戻り値</span><span class="sxs-lookup"><span data-stu-id="6e931-123">Return Value</span></span>  
 <span data-ttu-id="6e931-124">メソッドが正常に完了した場合は `S_OK`。それ以外の場合は、失敗を示す HRESULT 値 (「リストの[一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="6e931-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e931-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="6e931-125">Remarks</span></span>  
 <span data-ttu-id="6e931-126">署名を作成せずに署名のサイズを計算するには、`wszFilePath` に null を指定します。</span><span class="sxs-lookup"><span data-stu-id="6e931-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="6e931-127">署名は、ファイルに直接格納するか、呼び出し元に返すことができます。</span><span class="sxs-lookup"><span data-stu-id="6e931-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="6e931-128">`SN_SIGN_ALL_FILES` が指定されていても、公開キーが含まれていない場合 (`pbKeyBlob` と `wszFilePath` の両方が null の場合)、リンクモジュールのハッシュは再計算されますが、アセンブリは再署名されません。</span><span class="sxs-lookup"><span data-stu-id="6e931-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="6e931-129">`SN_TEST_SIGN` が指定されている場合、共通言語ランタイムヘッダーは、アセンブリが厳密な名前で署名されていることを示すために変更されません。</span><span class="sxs-lookup"><span data-stu-id="6e931-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e931-130">要件</span><span class="sxs-lookup"><span data-stu-id="6e931-130">Requirements</span></span>  
 <span data-ttu-id="6e931-131">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e931-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e931-132">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="6e931-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6e931-133">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6e931-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e931-134">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e931-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e931-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e931-135">See also</span></span>

- [<span data-ttu-id="6e931-136">StrongNameSignatureGeneration メソッド</span><span class="sxs-lookup"><span data-stu-id="6e931-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="6e931-137">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e931-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
