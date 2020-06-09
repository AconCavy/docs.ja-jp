---
title: .NET Framework の暗号モデル
description: .NET での通常の暗号化アルゴリズムの実装を確認します。 オブジェクトの継承、ストリームのデザイン、& 構成の拡張可能な暗号化モデルについて説明します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: 11af4c15c8b291df898a3c2416faa15875eab70b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596320"
---
# <a name="net-framework-cryptography-model"></a><span data-ttu-id="40933-104">.NET Framework の暗号モデル</span><span class="sxs-lookup"><span data-stu-id="40933-104">.NET Framework Cryptography Model</span></span>

<span data-ttu-id="40933-105">.NET Framework は、多くの標準的な暗号化アルゴリズムの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="40933-105">The .NET Framework provides implementations of many standard cryptographic algorithms.</span></span> <span data-ttu-id="40933-106">これらのアルゴリズムは簡単に使用でき、またできるだけ安全な既定のプロパティを提供しています。</span><span class="sxs-lookup"><span data-stu-id="40933-106">These algorithms are easy to use and have the safest possible default properties.</span></span> <span data-ttu-id="40933-107">さらに、オブジェクトの継承、ストリームの設計、および構成の .NET Framework の暗号モデルは非常に拡張性に優れています。</span><span class="sxs-lookup"><span data-stu-id="40933-107">In addition, the .NET Framework cryptography model of object inheritance, stream design, and configuration is extremely extensible.</span></span>

## <a name="object-inheritance"></a><span data-ttu-id="40933-108">オブジェクトの継承</span><span class="sxs-lookup"><span data-stu-id="40933-108">Object Inheritance</span></span>

<span data-ttu-id="40933-109">.NET Framework のセキュリティ システムは、拡張可能な派生クラス継承のパターンを実装しています。</span><span class="sxs-lookup"><span data-stu-id="40933-109">The .NET Framework security system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="40933-110">階層は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="40933-110">The hierarchy is as follows:</span></span>

- <span data-ttu-id="40933-111"><xref:System.Security.Cryptography.SymmetricAlgorithm>、<xref:System.Security.Cryptography.AsymmetricAlgorithm> または <xref:System.Security.Cryptography.HashAlgorithm> などのアルゴリズム型クラス。</span><span class="sxs-lookup"><span data-stu-id="40933-111">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm> or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="40933-112">このレベルは抽象レベルです。</span><span class="sxs-lookup"><span data-stu-id="40933-112">This level is abstract.</span></span>

- <span data-ttu-id="40933-113"><xref:System.Security.Cryptography.Aes>、<xref:System.Security.Cryptography.RC2>、または <xref:System.Security.Cryptography.ECDiffieHellman> など、アルゴリズム型クラスから継承されるアルゴリズム クラス。</span><span class="sxs-lookup"><span data-stu-id="40933-113">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="40933-114">このレベルは抽象レベルです。</span><span class="sxs-lookup"><span data-stu-id="40933-114">This level is abstract.</span></span>

- <span data-ttu-id="40933-115"><xref:System.Security.Cryptography.AesManaged>、<xref:System.Security.Cryptography.RC2CryptoServiceProvider>、または <xref:System.Security.Cryptography.ECDiffieHellmanCng> など、アルゴリズム クラスから継承されるアルゴリズム クラスの実装。</span><span class="sxs-lookup"><span data-stu-id="40933-115">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="40933-116">このレベルは完全に実装されます。</span><span class="sxs-lookup"><span data-stu-id="40933-116">This level is fully implemented.</span></span>

<span data-ttu-id="40933-117">派生クラスのこのパターンを使用すると、新しいアルゴリズムの追加、または既存アルゴリズムの新規実装の追加を簡単に行えます。</span><span class="sxs-lookup"><span data-stu-id="40933-117">Using this pattern of derived classes, it is easy to add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="40933-118">たとえば、新しい公開キー アルゴリズムを作成するには、<xref:System.Security.Cryptography.AsymmetricAlgorithm> クラスから継承します。</span><span class="sxs-lookup"><span data-stu-id="40933-118">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="40933-119">特定のアルゴリズムの実装を新しく作成するには、そのアルゴリズムの非抽象派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="40933-119">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>

## <a name="how-algorithms-are-implemented-in-the-net-framework"></a><span data-ttu-id="40933-120">.NET Framework でアルゴリズムを実装する方法</span><span class="sxs-lookup"><span data-stu-id="40933-120">How Algorithms Are Implemented in the .NET Framework</span></span>

<span data-ttu-id="40933-121">アルゴリズムに使用できるさまざまな実装例として、対称アルゴリズムを検討します。</span><span class="sxs-lookup"><span data-stu-id="40933-121">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="40933-122">すべての対称アルゴリズムのベースは <xref:System.Security.Cryptography.SymmetricAlgorithm> であり、次のアルゴリズムによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="40933-122">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by the following algorithms:</span></span>

* <xref:System.Security.Cryptography.Aes>
* <xref:System.Security.Cryptography.DES>
* <xref:System.Security.Cryptography.RC2>
* <xref:System.Security.Cryptography.Rijndael>
* <xref:System.Security.Cryptography.TripleDES>

<span data-ttu-id="40933-123"><xref:System.Security.Cryptography.Aes> は、<xref:System.Security.Cryptography.AesCryptoServiceProvider> と <xref:System.Security.Cryptography.AesManaged> の 2 つのクラスによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="40933-123"><xref:System.Security.Cryptography.Aes> is inherited by two classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> and <xref:System.Security.Cryptography.AesManaged>.</span></span> <span data-ttu-id="40933-124"><xref:System.Security.Cryptography.AesCryptoServiceProvider> クラスは Aes の Windows 暗号化 API (CAPI) 実装のラッパーですが、<xref:System.Security.Cryptography.AesManaged> クラスは全体がマネージド コードで書かれています。</span><span class="sxs-lookup"><span data-stu-id="40933-124">The <xref:System.Security.Cryptography.AesCryptoServiceProvider> class is a wrapper around the Windows Cryptography API (CAPI) implementation of Aes, whereas the <xref:System.Security.Cryptography.AesManaged> class is written entirely in managed code.</span></span> <span data-ttu-id="40933-125">さらに、マネージド実装と CAPI 実装に加え、3 つ目の実装、Cryptography Next Generation (CNG) もあります。</span><span class="sxs-lookup"><span data-stu-id="40933-125">There is also a third type of implementation, Cryptography Next Generation (CNG), in addition to the managed and CAPI implementations.</span></span> <span data-ttu-id="40933-126">CNG アルゴリズムの例が <xref:System.Security.Cryptography.ECDiffieHellmanCng> です。</span><span class="sxs-lookup"><span data-stu-id="40933-126">An example of a CNG algorithm is <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="40933-127">CNG アルゴリズムは、Windows Vista 以降のバージョンで利用可能です。</span><span class="sxs-lookup"><span data-stu-id="40933-127">CNG algorithms are available on Windows Vista and later.</span></span>

<span data-ttu-id="40933-128">ご自身にとって最適な実装を選択できます。</span><span class="sxs-lookup"><span data-stu-id="40933-128">You can choose which implementation is best for you.</span></span> <span data-ttu-id="40933-129">マネージ実装は、.NET Framework をサポートするすべてのプラットフォームで使用できます。</span><span class="sxs-lookup"><span data-stu-id="40933-129">The managed implementations are available on all platforms that support .NET Framework.</span></span> <span data-ttu-id="40933-130">CAPI 実装は、以前のオペレーティングシステムで使用でき、開発されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="40933-130">The CAPI implementations are available on older operating systems and are no longer being developed.</span></span> <span data-ttu-id="40933-131">CNG は、新しい開発が行われる最新の実装です。</span><span class="sxs-lookup"><span data-stu-id="40933-131">CNG is the latest implementation where new development will take place.</span></span> <span data-ttu-id="40933-132">ただし、マネージド実装は連邦情報処理規格 (FIPS: Federal Information Processing Standard) に認定されておらず、ラッパー クラスよりも低速である場合があります。</span><span class="sxs-lookup"><span data-stu-id="40933-132">However, the managed implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the wrapper classes.</span></span>

## <a name="stream-design"></a><span data-ttu-id="40933-133">ストリーム デザイン</span><span class="sxs-lookup"><span data-stu-id="40933-133">Stream Design</span></span>

<span data-ttu-id="40933-134">共通言語ランタイムは、対称アルゴリズムおよびハッシュ アルゴリズムを実装するためのストリーム指向デザインを使用しています。</span><span class="sxs-lookup"><span data-stu-id="40933-134">The common language runtime uses a stream-oriented design for implementing symmetric algorithms and hash algorithms.</span></span> <span data-ttu-id="40933-135">この設計の中心となるは、<xref:System.IO.Stream> クラスから派生する <xref:System.Security.Cryptography.CryptoStream> クラスです。</span><span class="sxs-lookup"><span data-stu-id="40933-135">The core of this design is the <xref:System.Security.Cryptography.CryptoStream> class, which derives from the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="40933-136">ストリーム ベースの暗号化オブジェクトは、単一の標準インターフェイス (`CryptoStream`) をサポートし、オブジェクトのデータ転送部分を処理します。</span><span class="sxs-lookup"><span data-stu-id="40933-136">Stream-based cryptographic objects support a single standard interface (`CryptoStream`) for handling the data transfer portion of the object.</span></span> <span data-ttu-id="40933-137">すべてのオブジェクトは標準のインターフェイス上に構築されるため、複数のオブジェクト (ハッシュ オブジェクトに続く暗号化オブジェクトなど) を連結したり、データ用の中間ストレージなしでデータ上で複数の操作を実行したりできます。</span><span class="sxs-lookup"><span data-stu-id="40933-137">Because all the objects are built on a standard interface, you can chain together multiple objects (such as a hash object followed by an encryption object), and you can perform multiple operations on the data without needing any intermediate storage for it.</span></span> <span data-ttu-id="40933-138">また、ストリーミング モデルを使用して、より小さなオブジェクトからオブジェクトを構築することもできます。</span><span class="sxs-lookup"><span data-stu-id="40933-138">The streaming model also enables you to build objects from smaller objects.</span></span> <span data-ttu-id="40933-139">たとえば、複合暗号化とハッシュ アルゴリズムは 1 つのストリーム オブジェクトと見ることができますが、このオブジェクトは一連の複数のストリーム オブジェクトから作成されているかもしれません。</span><span class="sxs-lookup"><span data-stu-id="40933-139">For example, a combined encryption and hash algorithm can be viewed as a single stream object, although this object might be built from a set of stream objects.</span></span>

## <a name="cryptographic-configuration"></a><span data-ttu-id="40933-140">暗号化の構成</span><span class="sxs-lookup"><span data-stu-id="40933-140">Cryptographic Configuration</span></span>

<span data-ttu-id="40933-141">暗号化の構成によって、アルゴリズムの特定の実装のアルゴリズム名への解決が可能になり、.NET Framework の暗号化クラスの機能を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="40933-141">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET Framework cryptography classes.</span></span> <span data-ttu-id="40933-142">アルゴリズムの独自のハードウェアまたはソフトウェア実装を追加して、実装を任意のアルゴリズム名にマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="40933-142">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="40933-143">構成ファイルでアルゴリズムを指定しない場合は、既定の設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="40933-143">If an algorithm is not specified in the configuration file, the default settings are used.</span></span> <span data-ttu-id="40933-144">暗号化の構成の詳細については、「[暗号化クラスの構成](../../framework/configure-apps/configure-cryptography-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40933-144">For more information about cryptographic configuration, see [Configuring Cryptography Classes](../../framework/configure-apps/configure-cryptography-classes.md).</span></span>

## <a name="choosing-an-algorithm"></a><span data-ttu-id="40933-145">アルゴリズムの選択</span><span class="sxs-lookup"><span data-stu-id="40933-145">Choosing an Algorithm</span></span>

<span data-ttu-id="40933-146">データの整合性、データのプライバシー保護、またはキー生成など、さまざまな理由のためにアルゴリズムを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="40933-146">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="40933-147">対称アルゴリズムおよびハッシュ アルゴリズムは、整合性の理由 (変更の防止) またはプライバシー上の理由 (表示の防止) のいずれかのためにデータを保護することを意図しています。</span><span class="sxs-lookup"><span data-stu-id="40933-147">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="40933-148">ハッシュ アルゴリズムは、主にデータの整合性用に使用されます。</span><span class="sxs-lookup"><span data-stu-id="40933-148">Hash algorithms are used primarily for data integrity.</span></span>

<span data-ttu-id="40933-149">アプリケーションで推奨されるアルゴリズムの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="40933-149">Here is a list of recommended algorithms by application:</span></span>

- <span data-ttu-id="40933-150">データのプライバシー : </span><span class="sxs-lookup"><span data-stu-id="40933-150">Data privacy:</span></span>
  - <xref:System.Security.Cryptography.Aes>
- <span data-ttu-id="40933-151">データの整合性 : </span><span class="sxs-lookup"><span data-stu-id="40933-151">Data integrity:</span></span>
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- <span data-ttu-id="40933-152">デジタル署名 : </span><span class="sxs-lookup"><span data-stu-id="40933-152">Digital signature:</span></span>
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="40933-153">キー交換 : </span><span class="sxs-lookup"><span data-stu-id="40933-153">Key exchange:</span></span>
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="40933-154">乱数生成 : </span><span class="sxs-lookup"><span data-stu-id="40933-154">Random number generation:</span></span>
  - <xref:System.Security.Cryptography.RNGCryptoServiceProvider>
- <span data-ttu-id="40933-155">パスワードからのキー生成 :  </span><span class="sxs-lookup"><span data-stu-id="40933-155">Generating a key from a password:</span></span>
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a><span data-ttu-id="40933-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="40933-156">See also</span></span>

- [<span data-ttu-id="40933-157">暗号化サービス</span><span class="sxs-lookup"><span data-stu-id="40933-157">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="40933-158">C での暗号化プロトコル、アルゴリズム、およびソースコードの適用 (Schneier)</span><span class="sxs-lookup"><span data-stu-id="40933-158">Applied Cryptography Protocols, Algorithms, and Source Code in C, by Bruce Schneier</span></span>](https://www.schneier.com/books/applied_cryptography/)
