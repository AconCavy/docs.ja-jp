---
title: ICorRuntimeHost インターフェイス
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
ms.openlocfilehash: 4b8018bb84dea08987d91f351b1ab0d9f3b48c56
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503901"
---
# <a name="icorruntimehost-interface"></a><span data-ttu-id="7bb32-102">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7bb32-102">ICorRuntimeHost Interface</span></span>
<span data-ttu-id="7bb32-103">ホストが共通言語ランタイム (CLR) を明示的に開始および停止し、アプリケーションドメインの作成と構成、既定のドメインへのアクセス、およびプロセスで実行されているすべてのドメインの列挙を行うことができるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7bb32-103">Provides methods that enable the host to start and stop the common language runtime (CLR) explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>  
  
 <span data-ttu-id="7bb32-104">.NET Framework バージョン2.0 では、このインターフェイスは[ICLRRuntimeHost](iclrruntimehost-interface.md)によって置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="7bb32-104">In the .NET Framework version 2.0, this interface is superceded by [ICLRRuntimeHost](iclrruntimehost-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7bb32-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-105">Methods</span></span>  
  
|<span data-ttu-id="7bb32-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-106">Method</span></span>|<span data-ttu-id="7bb32-107">説明</span><span class="sxs-lookup"><span data-stu-id="7bb32-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7bb32-108">CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-108">CloseEnum Method</span></span>](icorruntimehost-closeenum-method.md)|<span data-ttu-id="7bb32-109">ドメイン列挙子をドメインリストの先頭にリセットします。</span><span class="sxs-lookup"><span data-stu-id="7bb32-109">Resets a domain enumerator back to the beginning of the domain list.</span></span>|  
|[<span data-ttu-id="7bb32-110">CreateDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-110">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)|<span data-ttu-id="7bb32-111">アプリケーションドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="7bb32-111">Creates an application domain.</span></span> <span data-ttu-id="7bb32-112">呼び出し元は、型のインターフェイスポインターを <xref:System._AppDomain> 型のインスタンスに受信し <xref:System.AppDomain?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="7bb32-112">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>|  
|[<span data-ttu-id="7bb32-113">CreateDomainEx メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-113">CreateDomainEx Method</span></span>](icorruntimehost-createdomainex-method.md)|<span data-ttu-id="7bb32-114">アプリケーションドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="7bb32-114">Creates an application domain.</span></span> <span data-ttu-id="7bb32-115">このメソッドを使用すると、呼び出し元は IAppDomainSetup インスタンスを渡して、返されたインスタンスの追加の機能を構成でき <xref:System._AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="7bb32-115">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>|  
|[<span data-ttu-id="7bb32-116">CreateDomainSetup メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-116">CreateDomainSetup Method</span></span>](icorruntimehost-createdomainsetup-method.md)|<span data-ttu-id="7bb32-117">インスタンスへの型のインターフェイスポインターを取得し `IAppDomainSetup` <xref:System.AppDomainSetup> ます。</span><span class="sxs-lookup"><span data-stu-id="7bb32-117">Gets an interface pointer of type `IAppDomainSetup` to an <xref:System.AppDomainSetup> instance.</span></span> <span data-ttu-id="7bb32-118">`IAppDomainSetup`アプリケーションドメインを作成する前に構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7bb32-118">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>|  
|[<span data-ttu-id="7bb32-119">CreateEvidence メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-119">CreateEvidence Method</span></span>](icorruntimehost-createevidence-method.md)|<span data-ttu-id="7bb32-120">型のインターフェイスポインターを取得します <xref:System.Security.Principal.IIdentity> 。これにより、ホストは、 [createdomain](icorruntimehost-createdomain-method.md)または[createdomainex](icorruntimehost-createdomainex-method.md)に渡すセキュリティ証拠を作成できます。</span><span class="sxs-lookup"><span data-stu-id="7bb32-120">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity>, which allows the host to create security evidence to pass to [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md).</span></span>|  
|[<span data-ttu-id="7bb32-121">CreateLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-121">CreateLogicalThreadState Method</span></span>](icorruntimehost-createlogicalthreadstate-method.md)|<span data-ttu-id="7bb32-122">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7bb32-122">Do not use.</span></span>|  
|[<span data-ttu-id="7bb32-123">CurrentDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-123">CurrentDomain Method</span></span>](icorruntimehost-currentdomain-method.md)|<span data-ttu-id="7bb32-124"><xref:System._AppDomain>現在のスレッドに読み込まれているドメインを表す型のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="7bb32-124">Gets an interface pointer of type <xref:System._AppDomain> that represents the domain loaded on the current thread.</span></span>|  
|[<span data-ttu-id="7bb32-125">DeleteLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-125">DeleteLogicalThreadState Method</span></span>](icorruntimehost-deletelogicalthreadstate-method.md)|<span data-ttu-id="7bb32-126">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7bb32-126">Do not use.</span></span>|  
|[<span data-ttu-id="7bb32-127">EnumDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-127">EnumDomains Method</span></span>](icorruntimehost-enumdomains-method.md)|<span data-ttu-id="7bb32-128">現在のプロセス内のドメインの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="7bb32-128">Gets an enumerator for the domains in the current process.</span></span>|  
|[<span data-ttu-id="7bb32-129">GetConfiguration メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-129">GetConfiguration Method</span></span>](icorruntimehost-getconfiguration-method.md)|<span data-ttu-id="7bb32-130">ホストが CLR のコールバック構成を指定できるようにするオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="7bb32-130">Gets an object that allows the host to specify the callback configuration of the CLR.</span></span>|  
|[<span data-ttu-id="7bb32-131">GetDefaultDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-131">GetDefaultDomain Method</span></span>](icorruntimehost-getdefaultdomain-method.md)|<span data-ttu-id="7bb32-132"><xref:System._AppDomain>現在のプロセスの既定のドメインを表す型のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="7bb32-132">Gets an interface pointer of type <xref:System._AppDomain> that represents the default domain for the current process.</span></span>|  
|[<span data-ttu-id="7bb32-133">LocksHeldByLogicalThread メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-133">LocksHeldByLogicalThread Method</span></span>](icorruntimehost-locksheldbylogicalthread-method.md)|<span data-ttu-id="7bb32-134">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7bb32-134">Do not use.</span></span>|  
|[<span data-ttu-id="7bb32-135">MapFile メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-135">MapFile Method</span></span>](icorruntimehost-mapfile-method.md)|<span data-ttu-id="7bb32-136">指定されたファイルをメモリにマップします。</span><span class="sxs-lookup"><span data-stu-id="7bb32-136">Maps the specified file into memory.</span></span> <span data-ttu-id="7bb32-137">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="7bb32-137">This method is obsolete.</span></span>|  
|[<span data-ttu-id="7bb32-138">NextDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-138">NextDomain Method</span></span>](icorruntimehost-nextdomain-method.md)|<span data-ttu-id="7bb32-139">列挙体の次のドメインへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="7bb32-139">Gets an interface pointer to the next domain in the enumeration.</span></span>|  
|[<span data-ttu-id="7bb32-140">Start メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-140">Start Method</span></span>](icorruntimehost-start-method.md)|<span data-ttu-id="7bb32-141">CLR を開始します。</span><span class="sxs-lookup"><span data-stu-id="7bb32-141">Starts the CLR.</span></span>|  
|[<span data-ttu-id="7bb32-142">Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-142">Stop Method</span></span>](icorruntimehost-stop-method.md)|<span data-ttu-id="7bb32-143">現在のプロセスのランタイムでコードの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="7bb32-143">Stops the execution of code in the runtime for the current process.</span></span>|  
|[<span data-ttu-id="7bb32-144">SwitchInLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-144">SwitchInLogicalThreadState Method</span></span>](icorruntimehost-switchinlogicalthreadstate-method.md)|<span data-ttu-id="7bb32-145">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7bb32-145">Do not use.</span></span>|  
|[<span data-ttu-id="7bb32-146">SwitchOutLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-146">SwitchOutLogicalThreadState Method</span></span>](icorruntimehost-switchoutlogicalthreadstate-method.md)|<span data-ttu-id="7bb32-147">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7bb32-147">Do not use.</span></span>|  
|[<span data-ttu-id="7bb32-148">UnloadDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb32-148">UnloadDomain Method</span></span>](icorruntimehost-unloaddomain-method.md)|<span data-ttu-id="7bb32-149">現在のプロセスから、指定されたアプリケーションドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="7bb32-149">Unloads the specified application domain from the current process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7bb32-150">要件</span><span class="sxs-lookup"><span data-stu-id="7bb32-150">Requirements</span></span>  
 <span data-ttu-id="7bb32-151">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bb32-151">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb32-152">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7bb32-152">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7bb32-153">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7bb32-153">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bb32-154">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="7bb32-154">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb32-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="7bb32-155">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="7bb32-156">ホスティング</span><span class="sxs-lookup"><span data-stu-id="7bb32-156">Hosting</span></span>](index.md)
- [<span data-ttu-id="7bb32-157">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7bb32-157">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- <span data-ttu-id="7bb32-158">[ランタイム ホスト](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7bb32-158">[Runtime Hosts](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
- [<span data-ttu-id="7bb32-159">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7bb32-159">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="7bb32-160">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="7bb32-160">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
