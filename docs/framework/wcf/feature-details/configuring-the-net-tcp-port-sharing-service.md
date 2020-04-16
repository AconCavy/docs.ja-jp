---
title: Net.TCP ポート共有サービスを構成する
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: fea2e734099c4c623dcde2a37f4c164cf9ce61ac
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464193"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="59774-102">Net.TCP ポート共有サービスを構成する</span><span class="sxs-lookup"><span data-stu-id="59774-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="59774-103">Net.TCP トランスポートを使用する自己ホスト型サービスは、`ListenBacklog` や `MaxPendingAccepts` など、いくつかの高度な設定を制御できます。これらは、ネットワーク通信で使用される、ベースである TCP ソケットの動作をコンロトールします。</span><span class="sxs-lookup"><span data-stu-id="59774-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="59774-104">ただし、各ソケットに対するこれらの設定は、トランスポート バインディングでポート共有が無効化されている場合 (既定では有効) に、バインディング レベルでのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="59774-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="59774-105">net.tcp バインディングは、(トランスポート バインド要素で `portSharingEnabled =true` を設定することで) ポート共有が有効化されている場合、外部プロセス (Net.TCP ポート共有サービスをホストする SMSvcHost.exe) に対し、自身の代わりに TCP ソケットを管理することを暗黙的に許可しています。</span><span class="sxs-lookup"><span data-stu-id="59774-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="59774-106">たとえば、TCP を使用している場合は次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="59774-106">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="59774-107">この方法で設定すると、サービスのトランスポート バインド要素に指定したソケット設定は無視され、SMSvcHost.exe で指定されたソケット設定が採用されます。</span><span class="sxs-lookup"><span data-stu-id="59774-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="59774-108">SMSvcHost.exe を構成するには、SmSvcHost.exe.config という XML 構成ファイルを作成し、SMSvcHost.exe 実行可能ファイルと同じ物理ディレクトリ (たとえば、C:\Windows\Microsoft.NET\Framework\v4.5) に配置します。</span><span class="sxs-lookup"><span data-stu-id="59774-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="59774-109">次の例では、すべての構成可能値の既定値を明示的に指定した SMSvcHost.exe.config のサンプルを示します。</span><span class="sxs-lookup"><span data-stu-id="59774-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!-- 16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!-- 30 seconds -->  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->  
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->  
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
    </system.serviceModel.activation>
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="59774-110">SMSvcHost.exe.config を変更する場合</span><span class="sxs-lookup"><span data-stu-id="59774-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="59774-111">一般的に、SMSvcHost.exe.config ファイルの内容を変更する際には、このファイルに指定するすべての構成設定は、Net.TCP ポート共有サービスを使用するコンピューターのすべてのサービスに影響するため、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="59774-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="59774-112">これには、Windows プロセス アクティブ化サービス (WAS) の TCP アクティブ化機能を使用する Windows Vista 上のアプリケーションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="59774-112">This includes applications on Windows Vista that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="59774-113">ただし、Net.TCP ポート共有サービスの既定の構成を変更する必要のある状況もあります。</span><span class="sxs-lookup"><span data-stu-id="59774-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="59774-114">たとえば、`maxPendingAccepts` の既定値は 4 \* プロセッサ数です。</span><span class="sxs-lookup"><span data-stu-id="59774-114">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="59774-115">ポート共有を使用する多数のサービスをホストするサーバーでは、この値を大きくして、最大のスループットを実現することができます。</span><span class="sxs-lookup"><span data-stu-id="59774-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="59774-116">`maxPendingConnections` の既定値は 100 です。</span><span class="sxs-lookup"><span data-stu-id="59774-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="59774-117">サービスを呼び出すクライアントが同時に複数存在し、サービスがクライアント接続を切断する場合も、この値を大きくすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="59774-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="59774-118">SMSvcHost.exe.config には、ポート共有サービスを使用する可能性のあるプロセス ID に関する情報も含まれています。</span><span class="sxs-lookup"><span data-stu-id="59774-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="59774-119">プロセスが、共有 TCP ポートを使用するためにポート共有サービスに接続すると、そのプロセスのプロセス ID が、ポート共有サービスの使用が許可されている ID のリストに照合されます。</span><span class="sxs-lookup"><span data-stu-id="59774-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="59774-120">これらの ID は、SMSvcHost.exe.config\<ファイルの [アカウント> セクションでセキュリティ識別子 (SID) として指定されます。</span><span class="sxs-lookup"><span data-stu-id="59774-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="59774-121">既定では、ポート共有サービスへのアクセス許可は、システム アカウント (LocalService、LocalSystem、NetworkService) や管理者グループのメンバーに与えられます。</span><span class="sxs-lookup"><span data-stu-id="59774-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="59774-122">ポート共有サービスに接続するために別の ID (ユーザー ID など) でプロセスが実行されることを許可しているアプリケーションでは、適切な SID を SMSvcHost.exe.config に明示的に追加する必要があります (これらの変更は SMSvc.exe プロセスが再起動されるまで適用されません)。</span><span class="sxs-lookup"><span data-stu-id="59774-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59774-123">ユーザー アカウント制御 (UAC) が有効になっている Windows Vista システムでは、ローカル ユーザーは、自分のアカウントが Administrators グループのメンバーであっても、昇格されたアクセス許可を必要とします。</span><span class="sxs-lookup"><span data-stu-id="59774-123">On Windows Vista systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="59774-124">これらのユーザーが昇格せずにポート共有サービスを利用できるようにするには、ユーザーの SID (またはユーザーがメンバーであるグループの SID) を SMSvcHost.exe.config の\<allowAccounts> セクションに明示的に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59774-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="59774-125">既定の SMSvcHost.exe.config ファイルは、カスタムの `etwProviderId` を指定することによって、SMSvcHost.exe のトレースの影響がサービス トレースに及ぶのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="59774-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59774-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="59774-126">See also</span></span>

- [<span data-ttu-id="59774-127">\<></span><span class="sxs-lookup"><span data-stu-id="59774-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
