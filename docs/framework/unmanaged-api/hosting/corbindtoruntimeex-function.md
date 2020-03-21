---
title: CorBindToRuntimeEx 関数
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
ms.openlocfilehash: 3520af5f55f43183920dce7fbd24b70359c023a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176501"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="272f7-102">CorBindToRuntimeEx 関数</span><span class="sxs-lookup"><span data-stu-id="272f7-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="272f7-103">アンマネージ ホストが共通言語ランタイム (CLR: Common Language Runtime) をプロセスに読み込むことを有効にします。</span><span class="sxs-lookup"><span data-stu-id="272f7-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="272f7-104">[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)と`CorBindToRuntimeEx`関数は同じ操作を実行します`CorBindToRuntimeEx`が、この関数では、フラグを設定して CLR の動作を指定できます。</span><span class="sxs-lookup"><span data-stu-id="272f7-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="272f7-105">この関数は、.NET Framework 4 では廃止されました。</span><span class="sxs-lookup"><span data-stu-id="272f7-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="272f7-106">この関数は、次の操作をホストに許可するパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="272f7-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="272f7-107">読み込むランタイムのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="272f7-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="272f7-108">サーバー ビルドまたはワークステーション ビルドのどちらを読み込むのかを指定します。</span><span class="sxs-lookup"><span data-stu-id="272f7-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="272f7-109">同時実行ガベージ コレクションを実行するか、または非同時実行ガベージ コレクションを実行するかを制御します。</span><span class="sxs-lookup"><span data-stu-id="272f7-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="272f7-110">同時実行ガベージ コレクションは、Intel Itanium アーキテクチャ (以前の IA-64) を実装する 64 ビット システム上で WOW64 x86 エミュレーターを実行しているアプリケーションではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="272f7-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="272f7-111">64 ビット Windows システムで WOW64 を使用する方法の詳細については[、「32 ビット アプリケーションの実行](/windows/desktop/WinProg64/running-32-bit-applications)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="272f7-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="272f7-112">アセンブリをドメイン中立として読み込むかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="272f7-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="272f7-113">CLR のインスタンスを開始する前に構成するための追加オプションを設定するために使用できる[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)へのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="272f7-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="272f7-114">構文</span><span class="sxs-lookup"><span data-stu-id="272f7-114">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,
    [in]  LPCWSTR      pwszBuildFlavor,
    [in]  DWORD        startupFlags,
    [in]  REFCLSID     rclsid,
    [in]  REFIID       riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="272f7-115">パラメーター</span><span class="sxs-lookup"><span data-stu-id="272f7-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="272f7-116">[入力] 読み込む CLR のバージョンを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="272f7-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="272f7-117">.NET Framework のバージョン番号は、ピリオドで区切られた 4 つの部分で構成*されます*。</span><span class="sxs-lookup"><span data-stu-id="272f7-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="272f7-118">`pwszVersion` として渡される文字列は、文字 "v" で始まり、バージョン番号の最初の 3 つの部分がその後に続く必要があります (たとえば "v1.0.1529")。</span><span class="sxs-lookup"><span data-stu-id="272f7-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="272f7-119">いくつかのバージョンの CLR は、以前のバージョンの CLR との互換性を指定するポリシー ステートメントと共にインストールされています。</span><span class="sxs-lookup"><span data-stu-id="272f7-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="272f7-120">既定では、スタートアップ shim により、ポリシー ステートメントに対して `pwszVersion` が評価され、要求されたバージョンと互換性がある最新バージョンのランタイムが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="272f7-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="272f7-121">ホストは shim に対し、次に示すように `pwszVersion` パラメーターで値 `STARTUP_LOADER_SAFEMODE` を渡すことにより、ポリシー評価を省略し、`startupFlags` で指定されたバージョンとまったく同じバージョンを読み込ませることができます。</span><span class="sxs-lookup"><span data-stu-id="272f7-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="272f7-122">呼び出し元が `pwszVersion` に null を指定した場合、`CorBindToRuntimeEx` はバージョン番号が .NET Framework 4 ランタイム未満のインストール済みランタイム セットを識別し、そのランタイム セットから最新バージョンのランタイムを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="272f7-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="272f7-123">.NET Framework 4 以降は読み込まれず、それ以前のバージョンがインストールされていない場合は失敗します。</span><span class="sxs-lookup"><span data-stu-id="272f7-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="272f7-124">null を渡すと、ホストはどのバージョンのランタイムを読み込むかを制御できなくなることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="272f7-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="272f7-125">状況によってはこのような方法が適切なこともありますが、読み込むバージョンを特定させておくことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="272f7-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="272f7-126">[入力] CLR のサーバー ビルドまたはワークステーション ビルドのどちらを読み込むかを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="272f7-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="272f7-127">有効な値は `svr` と `wks` です。</span><span class="sxs-lookup"><span data-stu-id="272f7-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="272f7-128">ワークステーション ビルドはシングルプロセッサ コンピューターでクライアント アプリケーションを実行するために最適化され、サーバー ビルドはガベージ コレクションでマルチ プロセッサを利用するために最適化されています。</span><span class="sxs-lookup"><span data-stu-id="272f7-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="272f7-129">null`pwszBuildFlavor`に設定されている場合、ワークステーションビルドがロードされます。</span><span class="sxs-lookup"><span data-stu-id="272f7-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="272f7-130">シングルプロセッサ マシンで実行している場合、ワークステーション ビルドは常に`pwszBuildFlavor``svr`読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="272f7-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="272f7-131">ただし、同時`pwszBuildFlavor`実行ガベージ`svr`コレクションが指定されている場合 (`startupFlags`パラメーターの説明を参照)、サーバー ビルドが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="272f7-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="272f7-132">[in][STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列挙体の値の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="272f7-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="272f7-133">これらのフラグは、同時実行ガベージ コレクション、ドメインに中立なコード、および `pwszVersion` パラメーターの動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="272f7-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="272f7-134">どのフラグも設定されていない場合は、既定はシングル ドメインになります。</span><span class="sxs-lookup"><span data-stu-id="272f7-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="272f7-135">有効な値は、</span><span class="sxs-lookup"><span data-stu-id="272f7-135">The following values are valid:</span></span>  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 <span data-ttu-id="272f7-136">これらのフラグの詳細については[、「STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列挙体」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="272f7-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="272f7-137">[in]`CLSID`インターフェイス[を実装](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)するコクラスの[。](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)</span><span class="sxs-lookup"><span data-stu-id="272f7-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="272f7-138">サポートされている値は CLSID_CorRuntimeHost と CLSID_CLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="272f7-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="272f7-139">[入力] 要求された `IID` のインターフェイスの `rclsid`。</span><span class="sxs-lookup"><span data-stu-id="272f7-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="272f7-140">サポートされている値は IID_ICorRuntimeHost と IID_ICLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="272f7-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="272f7-141">[出力] 返された `riid` へのインターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="272f7-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="272f7-142">解説</span><span class="sxs-lookup"><span data-stu-id="272f7-142">Remarks</span></span>  
 <span data-ttu-id="272f7-143">`pwszVersion` で指定したランタイムのバージョンが存在しない場合は、`CorBindToRuntimeEx` は CLR_E_SHIM_RUNTIMELOAD の HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="272f7-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="272f7-144">Windows ID の実行コンテキストとフロー</span><span class="sxs-lookup"><span data-stu-id="272f7-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="272f7-145">CLR のバージョン 1 では、<xref:System.Security.Principal.WindowsIdentity> オブジェクトは、新しいスレッド、スレッド プール、タイマー コールバックなどの非同期ポイント間をフローしません。</span><span class="sxs-lookup"><span data-stu-id="272f7-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="272f7-146">CLR のバージョン 2.0 では、<xref:System.Threading.ExecutionContext> オブジェクトは現在実行しているスレッドに関する情報をラップして非同期ポイント間をフローしますが、アプリケーション ドメインの境界を越えることはありません。</span><span class="sxs-lookup"><span data-stu-id="272f7-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="272f7-147">同様に、<xref:System.Security.Principal.WindowsIdentity> オブジェクトもすべての非同期ポイント間をフローします。</span><span class="sxs-lookup"><span data-stu-id="272f7-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="272f7-148">したがって、現在スレッドに偽装がある場合は、その偽装もフローします。</span><span class="sxs-lookup"><span data-stu-id="272f7-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="272f7-149">2 つの方法のいずれかでフローを変更できます。</span><span class="sxs-lookup"><span data-stu-id="272f7-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="272f7-150"><xref:System.Threading.ExecutionContext> 設定を変更し、スレッド単位ではフローしないようにします (<xref:System.Threading.ExecutionContext.SuppressFlow%2A>、<xref:System.Security.SecurityContext.SuppressFlow%2A>、および <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> の各メソッドを参照)。</span><span class="sxs-lookup"><span data-stu-id="272f7-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="272f7-151">処理の既定のモードを、現在のスレッドの <xref:System.Security.Principal.WindowsIdentity> 設定がどの状態でも <xref:System.Threading.ExecutionContext> オブジェクトは非同期ポイント間をフローしない、バージョン 1 互換モードに変更します。</span><span class="sxs-lookup"><span data-stu-id="272f7-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="272f7-152">既定のモードを変更する方法は、CLR を読み込むときにマネージド実行可能ファイルを使用するか、アンマネージド ホスト インターフェイスを使用するかに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="272f7-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="272f7-153">マネージ実行可能ファイルの場合は[\<、legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)要素の`enabled`属性を に`true`設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="272f7-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="272f7-154">アンマネージ ホスト インターフェイスを使用する場合は、`STARTUP_LEGACY_IMPERSONATION` 関数を呼び出すときの `startupFlags` パラメーターに `CorBindToRuntimeEx` フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="272f7-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="272f7-155">バージョン 1 互換モードは、その処理全体および処理のすべてのアプリケーション ドメインに適用されます。</span><span class="sxs-lookup"><span data-stu-id="272f7-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="272f7-156">必要条件</span><span class="sxs-lookup"><span data-stu-id="272f7-156">Requirements</span></span>  
 <span data-ttu-id="272f7-157">**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="272f7-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="272f7-158">**ヘッダー:** msCorEE.h</span><span class="sxs-lookup"><span data-stu-id="272f7-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="272f7-159">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="272f7-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="272f7-160">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="272f7-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="272f7-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="272f7-161">See also</span></span>

- [<span data-ttu-id="272f7-162">CorBindToCurrentRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="272f7-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="272f7-163">CorBindToRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="272f7-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="272f7-164">CorBindToRuntimeByCfg 関数</span><span class="sxs-lookup"><span data-stu-id="272f7-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="272f7-165">CorBindToRuntimeHost 関数</span><span class="sxs-lookup"><span data-stu-id="272f7-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="272f7-166">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="272f7-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="272f7-167">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="272f7-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
