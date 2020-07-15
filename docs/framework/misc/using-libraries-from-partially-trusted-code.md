---
title: 部分信頼コードからのライブラリの使用
description: 部分的に信頼されているコードからライブラリを使用する方法について説明します。 AllowPartiallyTrustedCallersAttribute 属性を使用して、共有マネージライブラリを呼び出します。
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
ms.openlocfilehash: d2e015e381a3778bbab9977af20897ce9f1955c1
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309223"
---
# <a name="using-libraries-from-partially-trusted-code"></a><span data-ttu-id="8b69d-104">部分信頼コードからのライブラリの使用</span><span class="sxs-lookup"><span data-stu-id="8b69d-104">Using Libraries from Partially Trusted Code</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> <span data-ttu-id="8b69d-105">このトピックでは、厳密な名前付きアセンブリの動作について説明し、[レベル 1](security-transparent-code-level-1.md)のアセンブリにのみ適用します。</span><span class="sxs-lookup"><span data-stu-id="8b69d-105">This topic addresses the behavior of strong-named assemblies and applies only to [Level 1](security-transparent-code-level-1.md) assemblies.</span></span> <span data-ttu-id="8b69d-106">[セキュリティ透過的なコード、](security-transparent-code-level-2.md) .NET Framework 4 以降のレベル2のアセンブリは、厳密な名前の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="8b69d-106">[Security-Transparent Code, Level 2](security-transparent-code-level-2.md) assemblies in the .NET Framework 4 or later are not affected by strong names.</span></span> <span data-ttu-id="8b69d-107">セキュリティシステムへの変更の詳細については、「[セキュリティの変更](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b69d-107">For more information about changes to the security system, see [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="8b69d-108">ホストまたはサンドボックスから不完全な信頼を受けているアプリケーションは、ライブラリの作成者が <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性を使用して具体的に許可しない限り、共有マネージド ライブラリを呼び出せません。</span><span class="sxs-lookup"><span data-stu-id="8b69d-108">Applications that receive less than full trust from their host or sandbox are not allowed to call shared managed libraries unless the library writer specifically allows them to through the use of the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="8b69d-109">そのため、アプリケーションの作成者は、ライブラリによっては部分的に信頼されたコンテキストから使用できないことを認識する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b69d-109">Therefore, application writers must be aware that some libraries will not be available to them from a partially trusted context.</span></span> <span data-ttu-id="8b69d-110">既定では、部分信頼[サンドボックス](how-to-run-partially-trusted-code-in-a-sandbox.md)で実行され、完全に信頼されたアセンブリの一覧にないすべてのコードは、部分的に信頼されています。</span><span class="sxs-lookup"><span data-stu-id="8b69d-110">By default, all code that executes in a partial-trust [sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md) and is not in the list of full-trust assemblies is partially trusted.</span></span> <span data-ttu-id="8b69d-111">部分的に信頼されたコンテキストからコードを実行する、または部分的に信頼されたコードによってコードが呼び出されることはないと考えられる場合は、このセクションの情報を考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8b69d-111">If you do not expect your code to be executed from a partially trusted context or to be called by partially trusted code, you do not have to be concerned about the information in this section.</span></span> <span data-ttu-id="8b69d-112">ただし、部分的に信頼されたコードと対話する必要があるコード、または部分的に信頼されたコンテキストから操作するコードを記述する場合は、次の要因を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b69d-112">However, if you write code that must interact with partially trusted code or operate from a partially trusted context, you should consider the following factors:</span></span>  
  
- <span data-ttu-id="8b69d-113">ライブラリは、複数のアプリケーションで共有するために、厳密な名前で署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b69d-113">Libraries must be signed with a strong name in order to be shared by multiple applications.</span></span> <span data-ttu-id="8b69d-114">厳密な名前を使用すると、コードをグローバル アセンブリ キャッシュに配置したり、サンドボックス化する <xref:System.AppDomain> の完全信頼一覧に追加したりできます。また、コンシューマーは、実際にあなたが発信する特定のモバイル コードを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="8b69d-114">Strong names allow your code to be placed in the global assembly cache or added to the full-trust list of a sandboxing <xref:System.AppDomain>, and allow consumers to verify that a particular piece of mobile code actually originates from you.</span></span>  
  
- <span data-ttu-id="8b69d-115">既定では、厳密な名前の[レベル 1](security-transparent-code-level-1.md)の共有ライブラリは、完全な信頼に対して暗黙的な[LinkDemand](link-demands.md)を実行します。ライブラリの作成者は何もする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8b69d-115">By default, strong-named [Level 1](security-transparent-code-level-1.md) shared libraries perform an implicit [LinkDemand](link-demands.md) for full trust automatically, without the library writer having to do anything.</span></span>  
  
- <span data-ttu-id="8b69d-116">呼び出し元に完全な信頼がないにもかかわらず、このようなライブラリを呼び出そうとする場合、ランタイムは <xref:System.Security.SecurityException> をスローします。これにより、呼び出し元はライブラリにリンクできなくなります。</span><span class="sxs-lookup"><span data-stu-id="8b69d-116">If a caller does not have full trust but still tries to call such a library, the runtime throws a <xref:System.Security.SecurityException> and the caller is not allowed to link to the library.</span></span>  
  
- <span data-ttu-id="8b69d-117">自動**LinkDemand**を無効にし、例外がスローされないようにするには、 **AllowPartiallyTrustedCallersAttribute**属性を共有ライブラリのアセンブリスコープに配置します。</span><span class="sxs-lookup"><span data-stu-id="8b69d-117">In order to disable the automatic **LinkDemand** and prevent the exception from being thrown, you can place the **AllowPartiallyTrustedCallersAttribute** attribute on the assembly scope of a shared library.</span></span> <span data-ttu-id="8b69d-118">この属性により、部分的に信頼されたマネージド コードからライブラリを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8b69d-118">This attribute allows your libraries to be called from partially trusted managed code.</span></span>  
  
- <span data-ttu-id="8b69d-119">それでも、この属性を持つライブラリへのアクセスが許可されている部分的に信頼されたコードは、<xref:System.AppDomain> が定義する追加の制約を受けます。</span><span class="sxs-lookup"><span data-stu-id="8b69d-119">Partially trusted code that is granted access to a library with this attribute is still subject to further restrictions defined by the <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="8b69d-120">部分的に信頼されたコードが**AllowPartiallyTrustedCallersAttribute**属性を持たないライブラリを呼び出す場合、プログラムによる方法はありません。</span><span class="sxs-lookup"><span data-stu-id="8b69d-120">There is no programmatic way for partially trusted code to call a library that does not have the **AllowPartiallyTrustedCallersAttribute** attribute.</span></span>  
  
 <span data-ttu-id="8b69d-121">特定のアプリケーションに対してプライベートなライブラリは、厳密な名前または**AllowPartiallyTrustedCallersAttribute**属性を必要とせず、アプリケーション外部の悪意のあるコードから参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="8b69d-121">Libraries that are private to a specific application do not require a strong name or the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be referenced by potentially malicious code outside the application.</span></span> <span data-ttu-id="8b69d-122">このようなコードは、部分的に信頼されたモバイル コードの意図的または意図的でない誤使用から保護されています。開発者は追加で何かをする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8b69d-122">Such code is protected against intentional or unintentional misuse by partially trusted mobile code without the developer having to do anything extra.</span></span>  
  
 <span data-ttu-id="8b69d-123">次の種類のコードについて、部分的に信頼されたコードによる使用を明示的に有効にすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="8b69d-123">You should consider explicitly enabling use by partially trusted code for the following types of code:</span></span>  
  
- <span data-ttu-id="8b69d-124">セキュリティの脆弱性を入念にテストしたコードと、「[安全なコーディングのガイドライン](../../standard/security/secure-coding-guidelines.md)」で説明されているガイドラインに準拠していること。</span><span class="sxs-lookup"><span data-stu-id="8b69d-124">Code that has been diligently tested for security vulnerabilities and is in compliance with the guidelines described in [Secure Coding Guidelines](../../standard/security/secure-coding-guidelines.md).</span></span>  
  
- <span data-ttu-id="8b69d-125">部分的に信頼されたシナリオ用に特に記述された厳密な名前のコード ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="8b69d-125">Strong-named code libraries that are specifically written for partially trusted scenarios.</span></span>  
  
- <span data-ttu-id="8b69d-126">インターネットからダウンロードしたコードによって呼び出される、厳密な名前で署名された (部分的に信頼された、または完全に信頼された) すべてのコンポーネント。 </span><span class="sxs-lookup"><span data-stu-id="8b69d-126">Any components (whether partially or fully trusted) signed with a strong name that will be called by code that is downloaded from the Internet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b69d-127">.NET Framework クラスライブラリ内の一部のクラスには**AllowPartiallyTrustedCallersAttribute**属性がないため、部分的に信頼されたコードから呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="8b69d-127">Some classes in the .NET Framework class library do not have the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be called by partially trusted code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b69d-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b69d-128">See also</span></span>

- [<span data-ttu-id="8b69d-129">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8b69d-129">Code Access Security</span></span>](code-access-security.md)
