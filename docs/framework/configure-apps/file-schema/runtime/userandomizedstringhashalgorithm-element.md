---
title: <UseRandomizedStringHashAlgorithm> 要素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
ms.openlocfilehash: cc9708b8cca6520932fbf0e1975a05cad5fad485
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115043"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="d80f5-102">\<UseRandomizedStringHashAlgorithm > 要素</span><span class="sxs-lookup"><span data-stu-id="d80f5-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="d80f5-103">共通言語ランタイムがアプリケーション ドメインごとに文字列のハッシュ コードを計算するかどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="d80f5-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
<span data-ttu-id="d80f5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d80f5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d80f5-105">&nbsp;&nbsp;[ **\<runtime>** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="d80f5-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="d80f5-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<UseRandomizedStringHashAlgorithm >**</span><span class="sxs-lookup"><span data-stu-id="d80f5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d80f5-107">構文</span><span class="sxs-lookup"><span data-stu-id="d80f5-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d80f5-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d80f5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d80f5-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d80f5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d80f5-110">属性</span><span class="sxs-lookup"><span data-stu-id="d80f5-110">Attributes</span></span>  
  
|<span data-ttu-id="d80f5-111">属性</span><span class="sxs-lookup"><span data-stu-id="d80f5-111">Attribute</span></span>|<span data-ttu-id="d80f5-112">説明</span><span class="sxs-lookup"><span data-stu-id="d80f5-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d80f5-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="d80f5-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d80f5-114">アプリケーション ドメインごとに文字列のハッシュ コードを計算するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d80f5-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d80f5-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="d80f5-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d80f5-116">[値]</span><span class="sxs-lookup"><span data-stu-id="d80f5-116">Value</span></span>|<span data-ttu-id="d80f5-117">説明</span><span class="sxs-lookup"><span data-stu-id="d80f5-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="d80f5-118">共通言語ランタイムは、アプリケーション ドメインごとに文字列のハッシュ コードを計算しません。1 つのアルゴリズムを使用して文字列のハッシュ コードを計算します。</span><span class="sxs-lookup"><span data-stu-id="d80f5-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="d80f5-119">既定値です。</span><span class="sxs-lookup"><span data-stu-id="d80f5-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="d80f5-120">共通言語ランタイムは、アプリケーション ドメインごとに文字列のハッシュ コードを計算します。</span><span class="sxs-lookup"><span data-stu-id="d80f5-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="d80f5-121">異なるアプリケーション ドメインや異なるプロセスで同一の文字列のハッシュ コードは異なります。</span><span class="sxs-lookup"><span data-stu-id="d80f5-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d80f5-122">子要素</span><span class="sxs-lookup"><span data-stu-id="d80f5-122">Child Elements</span></span>  
 <span data-ttu-id="d80f5-123">なし。</span><span class="sxs-lookup"><span data-stu-id="d80f5-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d80f5-124">親要素</span><span class="sxs-lookup"><span data-stu-id="d80f5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d80f5-125">要素</span><span class="sxs-lookup"><span data-stu-id="d80f5-125">Element</span></span>|<span data-ttu-id="d80f5-126">説明</span><span class="sxs-lookup"><span data-stu-id="d80f5-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d80f5-127">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="d80f5-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d80f5-128">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="d80f5-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d80f5-129">コメント</span><span class="sxs-lookup"><span data-stu-id="d80f5-129">Remarks</span></span>  
 <span data-ttu-id="d80f5-130">既定では、<xref:System.StringComparer> のクラスと <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> のメソッドは、アプリケーション ドメイン間で一貫したハッシュ コードを生成する単一のハッシュ アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="d80f5-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="d80f5-131">これは、`enabled` 要素の `<UseRandomizedStringHashAlgorithm>` 属性を `0` に設定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="d80f5-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="d80f5-132">これは、.NET Framework 4 で使用されるハッシュアルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="d80f5-132">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="d80f5-133"><xref:System.StringComparer> クラスと <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> メソッドは、別のハッシュ アルゴリズムを使用してアプリケーション ドメインごとのハッシュ コードを計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="d80f5-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="d80f5-134">その結果、同じ文字列のハッシュ コードが、アプリケーション ドメイン間で異なります。</span><span class="sxs-lookup"><span data-stu-id="d80f5-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="d80f5-135">これはオプトイン機能であり、この機能を利用するには、`enabled` 要素の `<UseRandomizedStringHashAlgorithm>` 属性を `1` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d80f5-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="d80f5-136">ハッシュ テーブルの文字列検索は、通常 O(1) 操作です。</span><span class="sxs-lookup"><span data-stu-id="d80f5-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="d80f5-137">ただし、多数の競合が発生した場合、参照は O (n<sup>2</sup>) 操作になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d80f5-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="d80f5-138">特にハッシュ コードを計算するキーがユーザーによる入力データに基づいている場合、`<UseRandomizedStringHashAlgorithm>` 構成要素を使用して、アプリケーション ドメインごとにランダムなハッシュ アルゴリズムを生成でき、潜在的な競合の数を制限できます。</span><span class="sxs-lookup"><span data-stu-id="d80f5-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d80f5-139">例</span><span class="sxs-lookup"><span data-stu-id="d80f5-139">Example</span></span>  
 <span data-ttu-id="d80f5-140">次の例では、値が「This is a string.」であるプライベート文字列定数 `DisplayString` を含む `s` クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="d80f5-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="d80f5-141">また、メソッドを実行しているアプリケーション ドメインの名前と共に文字列値とハッシュ コードを表示する `ShowStringHashCode` メソッドも含まれています。</span><span class="sxs-lookup"><span data-stu-id="d80f5-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="d80f5-142">構成ファイルを指定せずにこの例を実行すると、次のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d80f5-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="d80f5-143">文字列のハッシュ コードが 2 つアプリケーション ドメインで同じであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d80f5-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="d80f5-144">ただし、例のディレクトリに次の構成ファイルを追加して例を実行すると、同じ文字列のハッシュ コードがアプリケーション ドメインによって異なります。</span><span class="sxs-lookup"><span data-stu-id="d80f5-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="d80f5-145">構成ファイルが存在する場合、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d80f5-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="d80f5-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="d80f5-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
