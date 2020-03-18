---
title: '方法: IPv6 のサポートを有効にするようにコンピューター構成ファイルを変更する'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 73408afe9fcb35daa898c08b087a3411a6cb342b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180801"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="b57bd-102">方法: IPv6 のサポートを有効にするようにコンピューター構成ファイルを変更する</span><span class="sxs-lookup"><span data-stu-id="b57bd-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="b57bd-103">次のコード例では、IPv6 のサポートを有効にするようにコンピューター構成ファイルの *machine.config* を変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b57bd-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="b57bd-104">*machine.config* ファイルは、Windows がインストールされたディレクトリの *%Windir%\Microsoft.NET\Framework* フォルダーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b57bd-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="b57bd-105">コンピューターにインストールされた .NET Framework のバージョンごとに、 *%Windir%\Microsoft.NET\Framework* の下のフォルダーに別々の *machine.config* ファイルがあります (たとえば、*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*)。</span><span class="sxs-lookup"><span data-stu-id="b57bd-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="b57bd-106">これらの設定は、コンピューター構成ファイルよりも優先されるアプリケーション構成ファイルでも行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b57bd-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="b57bd-107">.NET Framework バージョン 1.1 以前では、**ipv6 enabled** 構成スイッチの値で <xref:System.Net.Dns?displayProperty=nameWithType> クラスのメンバーが IPv6 アドレスを返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b57bd-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="b57bd-108">.NET Framework バージョン 2.0 以降では、Windows が IPv6 をサポートしている場合、<xref:System.Net.Dns?displayProperty=nameWithType> クラスのすべてのメンバー (<xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> メソッドなど) が 1 つの制限付きで IPv6 アドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="b57bd-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="b57bd-109"><xref:System.Net.Dns?displayProperty=nameWithType> クラスの古いメンバー (<xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> メソッドなど) は、構成ファイル内の値を読み取り、認識します。</span><span class="sxs-lookup"><span data-stu-id="b57bd-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b57bd-110">.NET Framework バージョン 2.0 以降では、IPv6 は既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="b57bd-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="b57bd-111">.NET Framework バージョン 1.1 以前では、IPv6 は既定で無効になります。</span><span class="sxs-lookup"><span data-stu-id="b57bd-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b57bd-112">例</span><span class="sxs-lookup"><span data-stu-id="b57bd-112">Example</span></span>  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>
    ……………  
    </settings>  
    ………………  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b57bd-113">参照</span><span class="sxs-lookup"><span data-stu-id="b57bd-113">See also</span></span>

- [<span data-ttu-id="b57bd-114">IPv6 アドレス指定</span><span class="sxs-lookup"><span data-stu-id="b57bd-114">IPv6 Addressing</span></span>](ipv6-addressing.md)
- [<span data-ttu-id="b57bd-115">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="b57bd-115">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="b57bd-116">\<ipv6> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="b57bd-116">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
