---
title: ICLRDomainManager::SetAppDomainManagerType メソッド
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
ms.openlocfilehash: 89b3f9f248a445cc0568236d6a1df14269de4187
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615697"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="0101e-102">ICLRDomainManager::SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="0101e-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="0101e-103"><xref:System.AppDomainManager?displayProperty=nameWithType>既定のアプリケーションドメインを初期化するために使用されるアプリケーションドメインマネージャーのクラスから派生した型を指定します。</span><span class="sxs-lookup"><span data-stu-id="0101e-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0101e-104">構文</span><span class="sxs-lookup"><span data-stu-id="0101e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0101e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0101e-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="0101e-106">からアプリケーションドメインマネージャーの種類を含むアセンブリの表示名です。たとえば、"使用しているバージョン = 1.0.0.0, Culture = ニュートラル, PublicKeyToken = 6856bccf150f00b3" のようになります。</span><span class="sxs-lookup"><span data-stu-id="0101e-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="0101e-107">から名前空間を含む、アプリケーションドメインマネージャーの型名。</span><span class="sxs-lookup"><span data-stu-id="0101e-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="0101e-108">からアプリケーションドメインマネージャーに関する情報を提供する[EInitializeNewDomainFlags](einitializenewdomainflags-enumeration.md)列挙値の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="0101e-108">[in] A combination of [EInitializeNewDomainFlags](einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0101e-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="0101e-109">Return Value</span></span>  
 <span data-ttu-id="0101e-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="0101e-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0101e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0101e-111">HRESULT</span></span>|<span data-ttu-id="0101e-112">説明</span><span class="sxs-lookup"><span data-stu-id="0101e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0101e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0101e-113">S_OK</span></span>|<span data-ttu-id="0101e-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="0101e-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="0101e-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0101e-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0101e-116">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="0101e-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0101e-117">解説</span><span class="sxs-lookup"><span data-stu-id="0101e-117">Remarks</span></span>  
 <span data-ttu-id="0101e-118">現時点では、に対して定義されている値 `dwInitializeDomainFlags` はのみです `eInitializeNewDomainFlags_NoSecurityChanges` 。これは、アプリケーションドメインマネージャーがメソッドの実行中にセキュリティ設定を変更しないことを共通言語ランタイム (CLR) に通知し <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="0101e-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0101e-119">これにより、CLR は条件付き (APTCA) 属性を持つアセンブリの読み込みを最適化でき <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="0101e-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="0101e-120">これにより、このアセンブリセットの推移的なクロージャが大きい場合に、起動時間が大幅に向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0101e-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0101e-121">ホストがアプリケーションドメインマネージャーに対してを指定した場合 `eInitializeNewDomainFlags_NoSecurityChanges` 、 <xref:System.InvalidOperationException> アプリケーションドメインのセキュリティを変更しようとすると、がスローされます。</span><span class="sxs-lookup"><span data-stu-id="0101e-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="0101e-122">[ICLRControl:: SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)メソッドを呼び出すことは、を `ICLRDomainManager::SetAppDomainManagerType` 使用してを呼び出すことと同じです `eInitializeNewDomainFlags_None` 。</span><span class="sxs-lookup"><span data-stu-id="0101e-122">Calling the [ICLRControl::SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0101e-123">要件</span><span class="sxs-lookup"><span data-stu-id="0101e-123">Requirements</span></span>  
 <span data-ttu-id="0101e-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0101e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0101e-125">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="0101e-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0101e-126">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0101e-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0101e-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0101e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0101e-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="0101e-128">See also</span></span>

- [<span data-ttu-id="0101e-129">ホスティング</span><span class="sxs-lookup"><span data-stu-id="0101e-129">Hosting</span></span>](index.md)
- [<span data-ttu-id="0101e-130">ICLRDomainManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0101e-130">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)
- [<span data-ttu-id="0101e-131">EInitializeNewDomainFlags 列挙体</span><span class="sxs-lookup"><span data-stu-id="0101e-131">EInitializeNewDomainFlags Enumeration</span></span>](einitializenewdomainflags-enumeration.md)
