---
title: ハッシュ コードによるデータの整合性の保証
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
ms.openlocfilehash: 98bdce59ccbbb3b1d00ea5521169214c2bd7a10b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706202"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="e4306-102">ハッシュ コードによるデータの整合性の保証</span><span class="sxs-lookup"><span data-stu-id="e4306-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="e4306-103">ハッシュ値は、データを一意に識別する固定長の数値です。</span><span class="sxs-lookup"><span data-stu-id="e4306-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="e4306-104">ハッシュ値は、大量のデータを非常に小さな数値として表現するため、デジタル署名と一緒に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e4306-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="e4306-105">大きな値で署名するよりも、ハッシュ値を使用すれば効率的に署名できます。</span><span class="sxs-lookup"><span data-stu-id="e4306-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="e4306-106">ハッシュ値は、安全でないチャネルを介して送信されたデータの整合性を検証するためにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e4306-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="e4306-107">受信したデータのハッシュ値を送信したデータのハッシュ値と比較すると、データが変更されたかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="e4306-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="e4306-108">このトピックでは、<xref:System.Security.Cryptography?displayProperty=nameWithType> 名前空間のクラスを使用してハッシュ コードの生成と検証を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4306-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="e4306-109">ハッシュの生成</span><span class="sxs-lookup"><span data-stu-id="e4306-109">Generating a Hash</span></span>  
 <span data-ttu-id="e4306-110">マネージド ハッシュ クラスでは、バイト配列またはマネージド ストリーム オブジェクトのいずれかをハッシュできます。</span><span class="sxs-lookup"><span data-stu-id="e4306-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="e4306-111">SHA1 ハッシュ アルゴリズムを使用して文字列のハッシュ値を作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e4306-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="e4306-112">この例では、<xref:System.Text.UnicodeEncoding> クラスを使用して文字列をバイト配列に変換し、<xref:System.Security.Cryptography.SHA1Managed> クラスを使用してバイト配列をハッシュします。</span><span class="sxs-lookup"><span data-stu-id="e4306-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="e4306-113">ハッシュ値はコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4306-113">The hash value is then displayed to the console.</span></span>  

 <span data-ttu-id="e4306-114">SHA1 の衝突の問題のため、SHA256 以上をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e4306-114">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="e4306-115">上記のコードは、次の文字列をコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="e4306-115">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="e4306-116">ハッシュの検証</span><span class="sxs-lookup"><span data-stu-id="e4306-116">Verifying a Hash</span></span>  
 <span data-ttu-id="e4306-117">データをハッシュ値と比較すると、整合性を判断できます。</span><span class="sxs-lookup"><span data-stu-id="e4306-117">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="e4306-118">通常、データは特定のタイミングでハッシュされ、ハッシュ値はなんらかの方法で保護されます。</span><span class="sxs-lookup"><span data-stu-id="e4306-118">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="e4306-119">後でデータをもう一度ハッシュし、保護されている値と比較できます。</span><span class="sxs-lookup"><span data-stu-id="e4306-119">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="e4306-120">ハッシュ値が一致する場合、データは変更されていません。</span><span class="sxs-lookup"><span data-stu-id="e4306-120">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="e4306-121">値が一致しない場合は、データが破損しています。</span><span class="sxs-lookup"><span data-stu-id="e4306-121">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="e4306-122">このシステムを機能させるには、保護されたハッシュを暗号化するか、信頼されていないあらゆる対象に対して内密を保つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4306-122">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="e4306-123">文字列の前のハッシュ値を新しいハッシュ値と比較する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e4306-123">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="e4306-124">この例では、ループ処理でハッシュ値の各バイトをすべて比較します。</span><span class="sxs-lookup"><span data-stu-id="e4306-124">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="e4306-125">2 つのハッシュ値が一致する場合は、上記のコードによってコンソールに次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4306-125">If the two hash values match, this code displays the following to the console:</span></span>  
  
```console  
The hash codes match.  
```  
  
 <span data-ttu-id="e4306-126">一致しない場合は、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="e4306-126">If they do not match, the code displays the following:</span></span>  
  
```console  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4306-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4306-127">See also</span></span>

- [<span data-ttu-id="e4306-128">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="e4306-128">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
