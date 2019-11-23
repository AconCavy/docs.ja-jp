---
title: COM+ サービス モデル構成ツール (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 13368dfa7ca9d7981ac146b87e83f77077eaf537
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320734"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="71188-102">COM+ サービス モデル構成ツール (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="71188-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="71188-103">COM+ サービス モデル構成コマンド ライン ツール (ComSvcConfig.exe) を使用すると、COM+ インターフェイスを Web サービスとして公開するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="71188-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71188-104">構文</span><span class="sxs-lookup"><span data-stu-id="71188-104">Syntax</span></span>  
  
```console  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="71188-105">コメント</span><span class="sxs-lookup"><span data-stu-id="71188-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71188-106">ComSvcConfig.exe を使用するには、ローカル コンピューターの管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="71188-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="71188-107">ツールは次の場所にあります。</span><span class="sxs-lookup"><span data-stu-id="71188-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="71188-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="71188-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
 <span data-ttu-id="71188-109">Comsvcconfig.exe の詳細については、「[方法: COM + サービスモデル構成ツールを使用](./feature-details/how-to-use-the-com-service-model-configuration-tool.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71188-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="71188-110">次の表は、ComSvcConfig.exe で使用できるモードを示します。</span><span class="sxs-lookup"><span data-stu-id="71188-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="71188-111">オプション</span><span class="sxs-lookup"><span data-stu-id="71188-111">Option</span></span>|<span data-ttu-id="71188-112">説明</span><span class="sxs-lookup"><span data-stu-id="71188-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="71188-113">サービス モデル統合に COM+ インターフェイスの構成をインストールします。</span><span class="sxs-lookup"><span data-stu-id="71188-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="71188-114">短縮形 : `/i`。</span><span class="sxs-lookup"><span data-stu-id="71188-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="71188-115">サービス モデル統合から COM+ インターフェイスの構成をアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="71188-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="71188-116">短縮形 : `/u`。</span><span class="sxs-lookup"><span data-stu-id="71188-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="71188-117">サービス モデル統合に構成されるインターフェイスを持つ COM+ アプリケーションとコンポーネントの情報を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="71188-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="71188-118">短縮形 : `/l`。</span><span class="sxs-lookup"><span data-stu-id="71188-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="71188-119">次の表は、ComSvcConfig.exe で使用できるフラグを示します。</span><span class="sxs-lookup"><span data-stu-id="71188-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="71188-120">オプション</span><span class="sxs-lookup"><span data-stu-id="71188-120">Option</span></span>|<span data-ttu-id="71188-121">説明</span><span class="sxs-lookup"><span data-stu-id="71188-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="71188-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="71188-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="71188-123">構成する COM+ アプリケーションを指定します。</span><span class="sxs-lookup"><span data-stu-id="71188-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="71188-124">短縮形 : `/a`。</span><span class="sxs-lookup"><span data-stu-id="71188-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="71188-125">`/contract:` \<*ClassID* &#124; *ProgID* &#124; \*、*interfaceid* &#124; *InterfaceName* &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="71188-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="71188-126">サービスのコントラクトとして構成される COM+ コンポーネントとインターフェイスを指定します。</span><span class="sxs-lookup"><span data-stu-id="71188-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="71188-127">短縮形 : `/c`。</span><span class="sxs-lookup"><span data-stu-id="71188-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="71188-128">コンポーネントとインターフェイスの名前を指定するときにはワイルドカード文字 (\*) を使用できますが、意図していないインターフェイスを公開する可能性があるため、使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="71188-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="71188-129">`/hosting:` \<*complus* &#124; *\>*</span><span class="sxs-lookup"><span data-stu-id="71188-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="71188-130">COM+ ホスト モードと Web ホスト モードのどちらを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="71188-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="71188-131">短縮形 : `/h`。</span><span class="sxs-lookup"><span data-stu-id="71188-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="71188-132">COM+ ホスト モードを使用するには、COM + アプリケーションの明示的なアクティブ化が必要です。</span><span class="sxs-lookup"><span data-stu-id="71188-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="71188-133">Web ホスト モードを使用すると、COM+ アプリケーションを必要なときに自動的にアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="71188-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="71188-134">COM+ アプリケーションがライブラリ アプリケーションの場合は、インターネット インフォメーション サービス (IIS) のプロセスで実行します。</span><span class="sxs-lookup"><span data-stu-id="71188-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="71188-135">COM+ アプリケーションがサーバー アプリケーションの場合は、Dllhost.exe のプロセスで実行します。</span><span class="sxs-lookup"><span data-stu-id="71188-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="71188-136">`/webSite:` \<*WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="71188-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="71188-137">Web ホスト モードを使用する場合は、ホストする Web サイトを指定します (`/hosting` フラグを参照)。</span><span class="sxs-lookup"><span data-stu-id="71188-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="71188-138">短縮形 : `/w`。</span><span class="sxs-lookup"><span data-stu-id="71188-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="71188-139">Web サイトを指定しない場合は、既定の Web サイトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="71188-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="71188-140">`/webDirectory:` \<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="71188-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="71188-141">Web ホストを使用する場合は、ホストする仮想ディレクトリを指定します (`/hosting` フラグを参照)。</span><span class="sxs-lookup"><span data-stu-id="71188-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="71188-142">短縮形 : `/d`。</span><span class="sxs-lookup"><span data-stu-id="71188-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="71188-143">サービスからコントラクト定義を取得するクライアントをサポートするには、既定のサービス構成に Metadata Exchange (MEX) サービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="71188-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="71188-144">短縮形 : `/x`。</span><span class="sxs-lookup"><span data-stu-id="71188-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="71188-145">アプリケーション、コンポーネント、およびインターフェイス情報を ID として表示します。</span><span class="sxs-lookup"><span data-stu-id="71188-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="71188-146">短縮形 : `/k`。</span><span class="sxs-lookup"><span data-stu-id="71188-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="71188-147">ComSvcConfig.exe がロゴを表示しないようにします。</span><span class="sxs-lookup"><span data-stu-id="71188-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="71188-148">短縮形 : `/n`。</span><span class="sxs-lookup"><span data-stu-id="71188-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="71188-149">発生するエラーに加えて、すべての警告または情報テキストを出力します。</span><span class="sxs-lookup"><span data-stu-id="71188-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="71188-150">短縮形 : `/v`。</span><span class="sxs-lookup"><span data-stu-id="71188-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="71188-151">使用方法を示すメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="71188-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="71188-152">短縮形 : `/?`。</span><span class="sxs-lookup"><span data-stu-id="71188-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="71188-153">指定されたインターフェイスが、公開できる 1 つ以上のメソッド署名を含む場合にサービス構成を生成します。</span><span class="sxs-lookup"><span data-stu-id="71188-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="71188-154">サービスの初期化時に、互換性のあるメソッドはサービス コントラクトで操作として表示され、互換性のないメソッドはサービス コントラクトから除外されます。</span><span class="sxs-lookup"><span data-stu-id="71188-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="71188-155">このフラグが指定されていない場合は、指定されたインターフェイスが互換性のないメソッドを 1 つ以上含むとツールはサービス構成を生成しません。</span><span class="sxs-lookup"><span data-stu-id="71188-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="71188-156">使用例</span><span class="sxs-lookup"><span data-stu-id="71188-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="71188-157">説明</span><span class="sxs-lookup"><span data-stu-id="71188-157">Description</span></span>  
 <span data-ttu-id="71188-158">次の例は、COM+ ホスト モードを使用する Web サービスとして公開されるインターフェイスのセットに (OnlineStore COM+ アプリケーションの) `IFinances` コンポーネントの `ItemOrders.IFinancial` インターフェイスを追加します。</span><span class="sxs-lookup"><span data-stu-id="71188-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="71188-159">発生するエラーに加えて、すべての警告が出力されます。</span><span class="sxs-lookup"><span data-stu-id="71188-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="71188-160">コード</span><span class="sxs-lookup"><span data-stu-id="71188-160">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="71188-161">説明</span><span class="sxs-lookup"><span data-stu-id="71188-161">Description</span></span>  
 <span data-ttu-id="71188-162">次の例は、Web ホスト モードを使用する Web サービスとして公開されるインターフェイスのセットに (OnlineWarehouse COM+ アプリケーションの) `IStockLevels` コンポーネントの `ItemInventory.Warehouse` インターフェイスを追加します。</span><span class="sxs-lookup"><span data-stu-id="71188-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="71188-163">Web サービスは、IIS の OnlineWarehouse 仮想ディレクトリで Web ホストされます。</span><span class="sxs-lookup"><span data-stu-id="71188-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="71188-164">コード</span><span class="sxs-lookup"><span data-stu-id="71188-164">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="71188-165">説明</span><span class="sxs-lookup"><span data-stu-id="71188-165">Description</span></span>  
 <span data-ttu-id="71188-166">次の例は、Web サービスとして公開されるインターフェイスのセットから (OnlineStore COM+ アプリケーションの) `IFinances` コンポーネントの `ItemOrders.Financial` インターフェイスを削除します。</span><span class="sxs-lookup"><span data-stu-id="71188-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="71188-167">コード</span><span class="sxs-lookup"><span data-stu-id="71188-167">Code</span></span>  
  
```console  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="71188-168">説明</span><span class="sxs-lookup"><span data-stu-id="71188-168">Description</span></span>  
 <span data-ttu-id="71188-169">次の例は、ローカル マシン上の OnlineStore COM+ アプリケーションの現在公開されている COM+ ホスト インターフェイスを、対応するアドレスやバインディングの詳細と共に一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="71188-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="71188-170">コード</span><span class="sxs-lookup"><span data-stu-id="71188-170">Code</span></span>  
  
```console  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="71188-171">参照</span><span class="sxs-lookup"><span data-stu-id="71188-171">See also</span></span>

- [<span data-ttu-id="71188-172">方法 : COM+ サービス モデル構成ツールを使用する</span><span class="sxs-lookup"><span data-stu-id="71188-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](./feature-details/how-to-use-the-com-service-model-configuration-tool.md)
