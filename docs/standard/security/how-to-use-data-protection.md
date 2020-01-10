---
title: '方法 : データ保護を使用する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: 0efd677f11189b28b8efc184c04b30a047ab942b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706033"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="abf06-102">方法 : データ保護を使用する</span><span class="sxs-lookup"><span data-stu-id="abf06-102">How to: Use Data Protection</span></span>
<span data-ttu-id="abf06-103">.NET Framework では、データ保護 API (DPAPI) へのアクセスを提供しています。DPAPI を使用すると、現在のユーザー アカウントまたはコンピューターからの情報を使用してデータを暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="abf06-103">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="abf06-104">DPAPI を使用すると、暗号化キーを明示的に生成および格納するという困難な問題を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="abf06-104">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="abf06-105"><xref:System.Security.Cryptography.ProtectedMemory> クラスを使用すると、メモリ内のバイト配列を暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="abf06-105">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="abf06-106">この機能は、Microsoft Windows XP 以降のオペレーティング システムで使用できます。</span><span class="sxs-lookup"><span data-stu-id="abf06-106">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="abf06-107">現在のプロセスによって暗号化されるメモリは、現在のプロセスのみ、すべてのプロセス、または同じユーザーのコンテキストによって復号化されることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="abf06-107">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="abf06-108"><xref:System.Security.Cryptography.ProtectedMemory> オプションの詳しい説明については、「<xref:System.Security.Cryptography.MemoryProtectionScope> 列挙型」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abf06-108">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="abf06-109">バイト配列のコピーを暗号化するには、<xref:System.Security.Cryptography.ProtectedData> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="abf06-109">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="abf06-110">この機能は、Microsoft Windows 2000 以降のオペレーティング システムで使用できます。</span><span class="sxs-lookup"><span data-stu-id="abf06-110">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="abf06-111">現在のユーザー アカウントによって暗号化されたデータは、同じユーザー アカウントによってのみ復号化できることを指定できます。あるいは、現在のユーザー アカウントによって暗号化されたデータは、コンピューター上の任意のアカウントによって復号化できることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="abf06-111">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="abf06-112"><xref:System.Security.Cryptography.ProtectedData> オプションの詳しい説明については、「<xref:System.Security.Cryptography.DataProtectionScope> 列挙型」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abf06-112">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="abf06-113">データの保護を使用してメモリ内のデータを暗号化するには</span><span class="sxs-lookup"><span data-stu-id="abf06-113">To encrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="abf06-114">暗号化するバイト配列、エントロピ、およびメモリ保護スコープを渡す際に、静的な <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="abf06-114">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="abf06-115">データ保護を使用してメモリ内のデータを復号化するには</span><span class="sxs-lookup"><span data-stu-id="abf06-115">To decrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="abf06-116">復号化するバイト配列およびメモリ保護スコープを渡す際に、静的な <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="abf06-116">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="abf06-117">データ保護を使用してファイルやストリームのデータを暗号化するには</span><span class="sxs-lookup"><span data-stu-id="abf06-117">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="abf06-118">ランダム エントロピを作成します。</span><span class="sxs-lookup"><span data-stu-id="abf06-118">Create random entropy.</span></span>  
  
2. <span data-ttu-id="abf06-119">暗号化するバイト配列、エントロピ、およびデータ保護スコープを渡す際に、静的な <xref:System.Security.Cryptography.ProtectedData.Protect%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="abf06-119">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="abf06-120">ファイルまたはストリームに暗号化されたデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="abf06-120">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="abf06-121">データ保護を使用してファイルやストリームからデータを復号化するには</span><span class="sxs-lookup"><span data-stu-id="abf06-121">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="abf06-122">ファイルまたはストリームから暗号化されたデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="abf06-122">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="abf06-123">復号化するバイト配列およびデータ保護スコープを渡す際に、静的な <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="abf06-123">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abf06-124">使用例</span><span class="sxs-lookup"><span data-stu-id="abf06-124">Example</span></span>  
 <span data-ttu-id="abf06-125">次のコード例は、暗号化と復号化の 2 つの形式を示しています。</span><span class="sxs-lookup"><span data-stu-id="abf06-125">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="abf06-126">最初に、コード例では、メモリ内のバイト配列を暗号化してから復号化します。</span><span class="sxs-lookup"><span data-stu-id="abf06-126">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="abf06-127">次に、コード例では、バイト配列のコピーを暗号化し、ファイルに保存して、そのファイルからデータを読み込み、その後データを復号化しています。</span><span class="sxs-lookup"><span data-stu-id="abf06-127">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="abf06-128">例では、元のデータ、暗号化されたデータ、および復号化されたデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="abf06-128">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="abf06-129">コードのコンパイル方法</span><span class="sxs-lookup"><span data-stu-id="abf06-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="abf06-130">`System.Security.dll` への参照を含めます。</span><span class="sxs-lookup"><span data-stu-id="abf06-130">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="abf06-131"><xref:System>、<xref:System.IO>、<xref:System.Security.Cryptography>、および <xref:System.Text> 名前空間を含めます。</span><span class="sxs-lookup"><span data-stu-id="abf06-131">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abf06-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="abf06-132">See also</span></span>

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
