---
title: コード アクセス セキュリティ ポリシーの互換性と移行
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
ms.openlocfilehash: 949739b3336a9182eef583cc405e60e09d7ec09d
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217160"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="e79ca-102">コード アクセス セキュリティ ポリシーの互換性と移行</span><span class="sxs-lookup"><span data-stu-id="e79ca-102">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="e79ca-103">コードアクセスセキュリティ (CAS) のポリシー部分は、.NET Framework 4 では廃止されました。</span><span class="sxs-lookup"><span data-stu-id="e79ca-103">The policy portion of code access security (CAS) has been made obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="e79ca-104">その結果、互換性のために残されているポリシーの型とメンバーを明示的または[暗黙的](#implicit_use)に (他の型とメンバーを介して)[明示的](#explicit_use)に呼び出す場合は、コンパイルの警告とランタイム例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e79ca-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="e79ca-105">以下のいずれかの方法で警告やエラーを回避できます。</span><span class="sxs-lookup"><span data-stu-id="e79ca-105">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="e79ca-106">互換性のために残されている呼び出しの .NET Framework 4 の置換に[移行](#migration)しています。</span><span class="sxs-lookup"><span data-stu-id="e79ca-106">[Migrating](#migration) to the .NET Framework 4 replacements for the obsolete calls.</span></span>

   <span data-ttu-id="e79ca-107">\- - または -</span><span class="sxs-lookup"><span data-stu-id="e79ca-107">\- or -</span></span>

- <span data-ttu-id="e79ca-108">[\<NetFx40_LegacySecurityPolicy > configuration 要素](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)を使用して、従来の CAS ポリシーの動作を選択します。</span><span class="sxs-lookup"><span data-stu-id="e79ca-108">Using the [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="e79ca-109">このトピックには、次のセクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e79ca-109">This topic contains the following sections:</span></span>

- [<span data-ttu-id="e79ca-110">明示的な使用</span><span class="sxs-lookup"><span data-stu-id="e79ca-110">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="e79ca-111">暗黙の使用</span><span class="sxs-lookup"><span data-stu-id="e79ca-111">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="e79ca-112">エラーと警告</span><span class="sxs-lookup"><span data-stu-id="e79ca-112">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="e79ca-113">移行: 互換性のために残されている呼び出しの置換</span><span class="sxs-lookup"><span data-stu-id="e79ca-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="e79ca-114">互換性: CAS ポリシーレガシオプションの使用</span><span class="sxs-lookup"><span data-stu-id="e79ca-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="e79ca-115">明示的な使用</span><span class="sxs-lookup"><span data-stu-id="e79ca-115">Explicit Use</span></span>

<span data-ttu-id="e79ca-116">直接セキュリティ ポリシーを操作するメンバー、または CAS ポリシーをサンドボックス化することが必要なメンバーは廃止され、既定ではエラーを発生するようになりました。</span><span class="sxs-lookup"><span data-stu-id="e79ca-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="e79ca-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e79ca-117">Examples of these are:</span></span>

- <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>

<a name="implicit_use"></a>

## <a name="implicit-use"></a><span data-ttu-id="e79ca-118">暗黙的な使用</span><span class="sxs-lookup"><span data-stu-id="e79ca-118">Implicit Use</span></span>

<span data-ttu-id="e79ca-119">アセンブリの読み込みオーバーロードの中にはエラーを生成するものがあります。CAS ポリシーを暗黙的に使用することが原因です。</span><span class="sxs-lookup"><span data-stu-id="e79ca-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="e79ca-120">これらのオーバーロードはCAS ポリシーを解決するために <xref:System.Security.Policy.Evidence> パラメーターを取り、アセンブリにアクセス許可セットを提供します。</span><span class="sxs-lookup"><span data-stu-id="e79ca-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="e79ca-121">次に例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="e79ca-121">Here are some examples.</span></span> <span data-ttu-id="e79ca-122">パラメーターとして <xref:System.Security.Policy.Evidence> を取るオーバーロードが廃止されました。</span><span class="sxs-lookup"><span data-stu-id="e79ca-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

- <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

<a name="errors_and_warnings"></a>

## <a name="errors-and-warnings"></a><span data-ttu-id="e79ca-123">エラーおよび警告</span><span class="sxs-lookup"><span data-stu-id="e79ca-123">Errors and Warnings</span></span>

<span data-ttu-id="e79ca-124">廃止された種類とメンバーが使用されると、以下のエラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="e79ca-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="e79ca-125"><xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 型自体は廃止されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e79ca-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="e79ca-126">コンパイル時の警告:</span><span class="sxs-lookup"><span data-stu-id="e79ca-126">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="e79ca-127">実行時の例外:</span><span class="sxs-lookup"><span data-stu-id="e79ca-127">Run-time exception:</span></span>

<span data-ttu-id="e79ca-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="e79ca-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="e79ca-129">移行: 廃止された呼び出しの代替方法</span><span class="sxs-lookup"><span data-stu-id="e79ca-129">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="e79ca-130">アセンブリの信頼レベルの判別</span><span class="sxs-lookup"><span data-stu-id="e79ca-130">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="e79ca-131">CAS ポリシーは多くの場合、アセンブリ、アプリケーション ドメインのアクセス許可セット、または信頼レベルを判断するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e79ca-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="e79ca-132">.NET Framework 4 では、セキュリティポリシーを解決する必要がない次の便利なプロパティが公開されています。</span><span class="sxs-lookup"><span data-stu-id="e79ca-132">The .NET Framework 4 exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="e79ca-133">アプリケーション ドメインのサンドボックス化</span><span class="sxs-lookup"><span data-stu-id="e79ca-133">Application Domain Sandboxing</span></span>

<span data-ttu-id="e79ca-134">通常 <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> メソッドは、アプリケーション ドメイン内のアセンブリをサンド ボックス化するために使用します。</span><span class="sxs-lookup"><span data-stu-id="e79ca-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="e79ca-135">.NET Framework 4 は、この目的で <xref:System.Security.Policy.PolicyLevel> を使用する必要がないメンバーを公開します。</span><span class="sxs-lookup"><span data-stu-id="e79ca-135">The .NET Framework 4 exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="e79ca-136">詳細については、「[方法: サンドボックスで部分信頼コードを実行する](how-to-run-partially-trusted-code-in-a-sandbox.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e79ca-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="e79ca-137">部分的に信頼できるコードに対する安全なまたは適切なアクセス許可セットの決定</span><span class="sxs-lookup"><span data-stu-id="e79ca-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="e79ca-138">多くの場合ホストでは、ホストされているコードをサンドボックス化するための適切なアクセス許可を判別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e79ca-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="e79ca-139">.NET Framework 4 より前は、CAS ポリシーは、<xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> 方法でこれを行う方法を提供していました。</span><span class="sxs-lookup"><span data-stu-id="e79ca-139">Before the .NET Framework 4, CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e79ca-140">代替として、.NET Framework 4 には、指定された証拠の安全な標準のアクセス許可セットを返す <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> メソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e79ca-140">As a replacement, .NET Framework 4 provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="e79ca-141">サンドボックス化以外のシナリオ: アセンブリ読み込みのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="e79ca-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="e79ca-142">アセンブリ読み込みオーバーロードを使用する目的は、アセンブリのサンドボックス化の代わりに、アセンブリ読み込みオーバーロードでないと使用できないパラメーターを指定することです。</span><span class="sxs-lookup"><span data-stu-id="e79ca-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="e79ca-143">.NET Framework 4 以降では、パラメーターとして <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> オブジェクトを必要としないアセンブリ読み込みオーバーロード (<xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>など) を使用して、このシナリオを有効にします。</span><span class="sxs-lookup"><span data-stu-id="e79ca-143">Starting with the .NET Framework 4, assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="e79ca-144">アセンブリをサンドボックス化する場合には、<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> オーバー ロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="e79ca-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="e79ca-145">互換性: CAS ポリシーのレガシー オプションを使用する</span><span class="sxs-lookup"><span data-stu-id="e79ca-145">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="e79ca-146">[\<NetFx40_LegacySecurityPolicy > configuration 要素](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)を使用して、プロセスまたはライブラリが従来の CAS ポリシーを使用するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="e79ca-146">The [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="e79ca-147">この要素を有効にすると、ポリシーと証拠のオーバーロードは、framework の以前のバージョンの場合と同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="e79ca-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="e79ca-148">CAS ポリシーの動作は特定のランタイム バージョンに固有なので、そのランタイム バージョンの CAS ポリシーを変更しても、別のバージョンの CAS ポリシーには影響しません。</span><span class="sxs-lookup"><span data-stu-id="e79ca-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e79ca-149">参照</span><span class="sxs-lookup"><span data-stu-id="e79ca-149">See also</span></span>

- [<span data-ttu-id="e79ca-150">方法 : サンドボックスで部分信頼コードを実行する</span><span class="sxs-lookup"><span data-stu-id="e79ca-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="e79ca-151">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="e79ca-151">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
