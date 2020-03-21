---
title: IDENTITY_ATTRIBUTE_BLOB 構造体
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IDENTITY_ATTRIBUTE_BLOB
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE_BLOB
helpviewer_keywords:
- IDENTITY_ATTRIBUTE_BLOB structure [.NET Framework fusion]
ms.assetid: af14ae5f-d226-47dd-ba90-8fc6e6605d4d
topic_type:
- apiref
ms.openlocfilehash: 8f838d5c812842e2a637065b25182b6a12609231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176553"
---
# <a name="identity_attribute_blob-structure"></a><span data-ttu-id="cad1a-102">IDENTITY_ATTRIBUTE_BLOB 構造体</span><span class="sxs-lookup"><span data-stu-id="cad1a-102">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>
<span data-ttu-id="cad1a-103">アセンブリ内の 1 つの属性に関する情報を格納`DWORD`し、3 つの s で構成されます。</span><span class="sxs-lookup"><span data-stu-id="cad1a-103">Contains information about a single attribute in an assembly, and consists of three `DWORD`s.</span></span> <span data-ttu-id="cad1a-104">各`DWORD`インターフェイスは`CurrentIntoBuffer`[、IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md)インターフェイスのメソッドによって生成される文字バッファーへのオフセットです。</span><span class="sxs-lookup"><span data-stu-id="cad1a-104">Each `DWORD` is an offset into a character buffer produced by the `CurrentIntoBuffer` method of the [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) interface</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cad1a-105">構文</span><span class="sxs-lookup"><span data-stu-id="cad1a-105">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE_BLOB {  
    DWORD  ofsNamespace;  
    DWORD  ofsName;  
    DWORD  ofsValue;  
}   IDENTITY_ATTRIBUTE_BLOB;  
```  
  
## <a name="members"></a><span data-ttu-id="cad1a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="cad1a-106">Members</span></span>  
  
|<span data-ttu-id="cad1a-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="cad1a-107">Member</span></span>|<span data-ttu-id="cad1a-108">説明</span><span class="sxs-lookup"><span data-stu-id="cad1a-108">Description</span></span>|  
|------------|-----------------|  
|`ofsNamespace`|<span data-ttu-id="cad1a-109">文字バッファーへの最初のオフセット。</span><span class="sxs-lookup"><span data-stu-id="cad1a-109">The first offset into the character buffer.</span></span> <span data-ttu-id="cad1a-110">このオフセットの後には、属性の名前空間ではなく、一連の NULL 文字が続きます。</span><span class="sxs-lookup"><span data-stu-id="cad1a-110">This offset is not followed by the attribute's namespace, but by a series of null characters.</span></span> <span data-ttu-id="cad1a-111">したがって、使用されません。</span><span class="sxs-lookup"><span data-stu-id="cad1a-111">Therefore, it is not used.</span></span>|  
|`ofsName`|<span data-ttu-id="cad1a-112">文字バッファーへの 2 番目のオフセット。</span><span class="sxs-lookup"><span data-stu-id="cad1a-112">The second offset into the character buffer.</span></span> <span data-ttu-id="cad1a-113">この場所は、属性の名前の先頭を示します。</span><span class="sxs-lookup"><span data-stu-id="cad1a-113">This location marks the start of the attribute's name.</span></span>|  
|`ofsValue`|<span data-ttu-id="cad1a-114">文字バッファーへの 3 番目のオフセット。</span><span class="sxs-lookup"><span data-stu-id="cad1a-114">The third offset into the character buffer.</span></span> <span data-ttu-id="cad1a-115">この位置は、属性の値の開始位置を示します。</span><span class="sxs-lookup"><span data-stu-id="cad1a-115">This location marks the start of the attribute's value.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="cad1a-116">サンプル</span><span class="sxs-lookup"><span data-stu-id="cad1a-116">Sample</span></span>  
 <span data-ttu-id="cad1a-117">次の例は、いくつかの`IDENTITY_ATTRIBUTE_BLOB`基本的な手順を示しています。</span><span class="sxs-lookup"><span data-stu-id="cad1a-117">The following example illustrates several basic steps, which eventually result in a populated `IDENTITY_ATTRIBUTE_BLOB` structure:</span></span>  
  
1. <span data-ttu-id="cad1a-118">アセンブリの[IReferenceId](ireferenceidentity-interface.md)を取得します。</span><span class="sxs-lookup"><span data-stu-id="cad1a-118">Obtain an [IReferenceIdentity](ireferenceidentity-interface.md) for the assembly.</span></span>  
  
2. <span data-ttu-id="cad1a-119">メソッドを`IReferenceIdentity::EnumAttributes`呼び出し[、IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md)を取得します。</span><span class="sxs-lookup"><span data-stu-id="cad1a-119">Call the `IReferenceIdentity::EnumAttributes` method, and obtain an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md).</span></span>  
  
3. <span data-ttu-id="cad1a-120">文字バッファーを作成し、構造体としてキャストします`IDENTITY_ATTRIBUTE_BLOB`。</span><span class="sxs-lookup"><span data-stu-id="cad1a-120">Create a character buffer, and cast it as an `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
4. <span data-ttu-id="cad1a-121">インターフェイスの`CurrentIntoBuffer`メソッドを`IEnumIDENTITY_ATTRIBUTE`呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cad1a-121">Call the `CurrentIntoBuffer` method of the `IEnumIDENTITY_ATTRIBUTE` interface.</span></span> <span data-ttu-id="cad1a-122">このメソッドは、属性`Namespace` `Name`、、`Value`および を文字バッファーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="cad1a-122">This method copies the attributes `Namespace`, `Name`, and `Value` into the character buffer.</span></span> <span data-ttu-id="cad1a-123">これらの文字列への 3 つのオフセットは、`IDENTITY_ATTRIBUTE_BLOB`構造体で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cad1a-123">The three offsets to those strings will become available in the `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
```cpp  
// EnumAssemblyAttributes.cpp : main project file.  
  
#include "stdafx.h"  
  
#include "fusion.h"  
#include "windows.h"  
#include "stdio.h"  
#include "mscoree.h"  
#include "isolation.h"  
  
typedef HRESULT (__stdcall *PFNGETREF)(LPCWSTR pwzFile, REFIID riid, IUnknown **ppUnk);  
typedef HRESULT (__stdcall *PFNGETAUTH)(IIdentityAuthority **ppIIdentityAuthority);  
  
PFNGETREF                   g_pfnGetAssemblyIdentityFromFile = NULL;  
PFNGETAUTH                  g_pfnGetIdentityAuthority = NULL;  
IUnknown                    *g_pUnk = NULL;  
  
bool Init()  
{  
    HRESULT     hr = S_OK;  
    DWORD       dwSize = 0;  
    bool        bRC = false;  
  
    hr = CorBindToRuntimeEx(NULL, L"wks", 0, CLSID_CorRuntimeHost,  
                           IID_ICorRuntimeHost, (void **)&g_pUnk);  
    if(FAILED(hr)) {  
        printf("Error: Failed to initialize CLR runtime! hr = 0x%0x\n",  
                hr);  
        goto Exit;  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetAssemblyIdentityFromFile",  
                         (VOID **)&g_pfnGetAssemblyIdentityFromFile);  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetIdentityAuthority",  
                                (VOID **)&g_pfnGetIdentityAuthority);  
    }  
  
    if (!g_pfnGetAssemblyIdentityFromFile ||
        !g_pfnGetIdentityAuthority)  
    {  
        printf("Error: Cannot get required APIs from fusion.dll!\n");  
        goto Exit;  
    }  
  
    bRC = true;  
  
Exit:  
    return bRC;  
}  
  
void Shutdown()  
{  
    if(g_pUnk) {  
        g_pUnk->Release();  
        g_pUnk = NULL;  
    }  
}  
  
void Usage()  
{  
    printf("EnumAssemblyAttributes: A tool to enumerate the identity
            attributes of a given assembly.\n\n");  
    printf("Usage: EnumAssemblyAttributes AssemblyFilePath\n");  
    printf("\n");  
}  
  
int _cdecl wmain(int argc, LPCWSTR argv[])  
{  
    int     iResult = 1;  
    IUnknown                    *pUnk  = NULL;  
    IReferenceIdentity          *pRef  = NULL;  
    HRESULT                     hr     = S_OK;
    IEnumIDENTITY_ATTRIBUTE     *pEnum = NULL;  
    BYTE                        abData[1024];  
    DWORD                       cbAvailable;  
    DWORD                       cbUsed;  
    IDENTITY_ATTRIBUTE_BLOB     *pBlob;  
  
    if(argc != 2) {  
        Usage();  
        goto Exit;  
    }  
  
    if(!Init()) {  
        printf("Failure initializing EnumIdAttr.\n");  
        goto Exit;  
    }  
  
    hr = g_pfnGetAssemblyIdentityFromFile(argv[1],
                            __uuidof(IReferenceIdentity), &pUnk);  
  
    if (FAILED(hr)) {  
        printf("GetAssemblyIdentityFromFile failed with hr = 0x%x",
                hr);  
        goto Exit;  
    }  
  
    hr = pUnk->QueryInterface(__uuidof(IReferenceIdentity),
                              (void**)&pRef);  
    if (FAILED(hr)) {  
        goto Exit;  
    }  
  
    hr = pRef->EnumAttributes(&pEnum);  
    if (FAILED(hr)) {  
        printf("IReferenceIdentity::EnumAttributes failed with hr =
                0x%x", hr);  
        goto Exit;  
    }  
  
    pBlob = (IDENTITY_ATTRIBUTE_BLOB *)(abData);  
    while (1) {  
        cbAvailable = sizeof(abData);  
        hr = pEnum->CurrentIntoBuffer(cbAvailable, abData, &cbUsed);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer failed
                    with hr = 0x%x", hr);  
            goto Exit;  
        }  
  
        if (! cbUsed) {  
            break;  
        }  
  
        LPWSTR pwzNameSpace = (LPWSTR)(abData + pBlob->ofsNamespace);  
        LPWSTR pwzName      = (LPWSTR)(abData + pBlob->ofsName);  
        LPWSTR pwzValue     = (LPWSTR)(abData + pBlob->ofsValue);  
        printf("%ws: %ws = %ws\n", pwzNameSpace, pwzName, pwzValue);  
  
        hr = pEnum->Skip(1);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::Skip failed with hr =
                    0x%x", hr);  
            goto Exit;  
        }  
    }  
  
    iResult = 0;  
  
Exit:  
  
    Shutdown();  
  
    if (pUnk) {  
        pUnk->Release();  
    }  
  
    if (pRef) {  
        pRef->Release();  
    }  
  
    if (pEnum) {  
        pEnum->Release();  
    }  
  
    return iResult;  
}  
```  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="cad1a-124">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="cad1a-124">To run the sample</span></span>  
 <span data-ttu-id="cad1a-125">C:\\>列挙アセンブリ属性.exe C:\WINDOWS\NET\フレームワーク\v2.0.50727\システム.dll</span><span class="sxs-lookup"><span data-stu-id="cad1a-125">C:\\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span></span>  
  
### <a name="sample-output"></a><span data-ttu-id="cad1a-126">サンプル出力</span><span class="sxs-lookup"><span data-stu-id="cad1a-126">Sample output</span></span>  
 <span data-ttu-id="cad1a-127">カルチャ = ニュートラル</span><span class="sxs-lookup"><span data-stu-id="cad1a-127">Culture = neutral</span></span>  
  
 <span data-ttu-id="cad1a-128">名前 = システム</span><span class="sxs-lookup"><span data-stu-id="cad1a-128">name = System</span></span>  
  
 <span data-ttu-id="cad1a-129">プロセッサアーキテクチャ = MSIL</span><span class="sxs-lookup"><span data-stu-id="cad1a-129">processorArchitecture = MSIL</span></span>  
  
 <span data-ttu-id="cad1a-130">公開キートークン = b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="cad1a-130">PublicKeyToken = b77a5c561934e089</span></span>  
  
 <span data-ttu-id="cad1a-131">バージョン = 2.0.0.0</span><span class="sxs-lookup"><span data-stu-id="cad1a-131">Version = 2.0.0.0</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cad1a-132">必要条件</span><span class="sxs-lookup"><span data-stu-id="cad1a-132">Requirements</span></span>  
 <span data-ttu-id="cad1a-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cad1a-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cad1a-134">**ヘッダー:** アイソレーション.h</span><span class="sxs-lookup"><span data-stu-id="cad1a-134">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="cad1a-135">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cad1a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cad1a-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="cad1a-136">See also</span></span>

- [<span data-ttu-id="cad1a-137">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cad1a-137">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
- [<span data-ttu-id="cad1a-138">IEnumIDENTITY_ATTRIBUTE インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cad1a-138">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
- [<span data-ttu-id="cad1a-139">IDENTITY_ATTRIBUTE 構造体</span><span class="sxs-lookup"><span data-stu-id="cad1a-139">IDENTITY_ATTRIBUTE Structure</span></span>](identity-attribute-structure.md)
- [<span data-ttu-id="cad1a-140">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="cad1a-140">Fusion Structures</span></span>](fusion-structures.md)
