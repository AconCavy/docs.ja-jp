---
title: '軽減策: アプリ ドメイン全体でのオブジェクトの逆シリアル化'
ms.date: 03/30/2017
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
ms.openlocfilehash: e2d90a77cab699646bd31eaa162d1bd1744fd51b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457927"
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a><span data-ttu-id="07de7-102">軽減策: アプリ ドメイン全体でのオブジェクトの逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="07de7-102">Mitigation: Deserialization of Objects Across App Domains</span></span>
<span data-ttu-id="07de7-103">場合によっては、アプリが異なるアプリケーション ベースを持つ複数のアプリ ドメインを使用すると、アプリ ドメイン間で論理呼び出しコンテキストのオブジェクトを逆シリアル化しようとして、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="07de7-103">In some cases, when an app uses two or more app domains with different application bases, the attempt to deserialize objects in the logical call context across app domains throws an exception.</span></span>  
  
## <a name="diagnosing-the-issue"></a><span data-ttu-id="07de7-104">問題の診断</span><span class="sxs-lookup"><span data-stu-id="07de7-104">Diagnosing the issue</span></span>  
 <span data-ttu-id="07de7-105">問題は、次の条件の順序で発生します。</span><span class="sxs-lookup"><span data-stu-id="07de7-105">The issue arises under the following sequence of conditions:</span></span>  
  
1. <span data-ttu-id="07de7-106">アプリケーションが異なるアプリケーション ベースを持つ複数のアプリ ドメインを使用します。</span><span class="sxs-lookup"><span data-stu-id="07de7-106">An app uses two or more app domains with different application bases.</span></span>  
  
2. <span data-ttu-id="07de7-107">一部の型は、<xref:System.Runtime.Remoting.Messaging.LogicalCallContext> や <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> などのメソッドを呼び出して <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType> に明示的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="07de7-107">Some types are explicitly added to the <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> by calling a method such as <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> or <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="07de7-108">これらの型は、シリアル化可能としてマークされず、グローバル アセンブリ キャッシュに格納されません。</span><span class="sxs-lookup"><span data-stu-id="07de7-108">These types are not marked as serializable and are not stored in the global assembly cache.</span></span>  
  
3. <span data-ttu-id="07de7-109">後で、既定以外のアプリ ドメインで実行されているコードは、構成ファイルから値を読み取るか、XML を使用してオブジェクトを逆シリアル化しようとします。</span><span class="sxs-lookup"><span data-stu-id="07de7-109">Later, code running in the non-default app domain tries to read a value from a configuration file or use XML to deserialize an object.</span></span>  
  
4. <span data-ttu-id="07de7-110">構成ファイルから読み取るか、オブジェクトを逆シリアル化するために、<xref:System.Xml.XmlReader> オブジェクトは構成システムにアクセスしようとします。</span><span class="sxs-lookup"><span data-stu-id="07de7-110">In order to read from a configuration file or deserialize the object, an <xref:System.Xml.XmlReader> object tries to access the configuration system.</span></span>  
  
5. <span data-ttu-id="07de7-111">構成システムがまだ初期化されていないときは、初期化を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07de7-111">If the configuration system has not already been initialized, it must complete its initialization.</span></span> <span data-ttu-id="07de7-112">これは特に、ランタイムが次のように構成システムの固定のパスを作成する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="07de7-112">This means, among other things, that the runtime has to create a stable path for a configuration system, which it does as follows:</span></span>  
  
    1. <span data-ttu-id="07de7-113">これは既定以外のアプリ ドメインの証拠を検索します。</span><span class="sxs-lookup"><span data-stu-id="07de7-113">It looks for evidence for the non-default app domain.</span></span>  
  
    2. <span data-ttu-id="07de7-114">既定のアプリ ドメインに基づいて既定以外のアプリ ドメインの証拠を計算しようとします。</span><span class="sxs-lookup"><span data-stu-id="07de7-114">It tries to calculate the evidence for the non-default app domain based on the default app domain.</span></span>  
  
    3. <span data-ttu-id="07de7-115">既定のアプリ ドメインの証拠を取得するための呼び出しは、既定以外のアプリ ドメインから既定のアプリ ドメインへのアプリ ドメイン間の呼び出しをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="07de7-115">The call to get evidence for the default app domain triggers a cross-app domain call from the non-default app domain to the default app domain.</span></span>  
  
    4. <span data-ttu-id="07de7-116">.NET Framework のアプリ ドメイン間コントラクトの一部として、論理呼び出しコンテキストの内容も、アプリ ドメインの境界を越えてマーシャリングされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="07de7-116">As part of the cross-app domain contract in the .NET Framework, the contents of the logical call context also have to be marshaled across app domain boundaries.</span></span>  
  
6. <span data-ttu-id="07de7-117">論理呼び出しコンテキストに含まれる型が既定のアプリ ドメインで解決できないため、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="07de7-117">Because the types that are in the logical call context cannot be resolved in the default app domain, an exception is thrown.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="07de7-118">対応策</span><span class="sxs-lookup"><span data-stu-id="07de7-118">Mitigation</span></span>  
 <span data-ttu-id="07de7-119">この問題を回避するには、次を実行します</span><span class="sxs-lookup"><span data-stu-id="07de7-119">To work around this issue, do the following</span></span>  
  
1. <span data-ttu-id="07de7-120">例外がスローされたときにコール スタックで `get_Evidence` の呼び出しを検索します。</span><span class="sxs-lookup"><span data-stu-id="07de7-120">Look for the call to `get_Evidence` in the call stack when the exception is thrown.</span></span> <span data-ttu-id="07de7-121">この例外は、<xref:System.IO.FileNotFoundException> や <xref:System.Runtime.Serialization.SerializationException> などの例外の大きなサブセットであることもあります。</span><span class="sxs-lookup"><span data-stu-id="07de7-121">The exception can be any of a large subset of exceptions, including <xref:System.IO.FileNotFoundException> and <xref:System.Runtime.Serialization.SerializationException>.</span></span>  
  
2. <span data-ttu-id="07de7-122">オブジェクトが論理呼び出しコンテキストに追加されないアプリ内の場所を特定して、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="07de7-122">Identify the place in the app where no objects are added to the logical call context and add the following code:</span></span>  
  
    ```csharp
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```
  
## <a name="see-also"></a><span data-ttu-id="07de7-123">参照</span><span class="sxs-lookup"><span data-stu-id="07de7-123">See also</span></span>

- [<span data-ttu-id="07de7-124">アプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="07de7-124">Application compatibility</span></span>](application-compatibility.md)
