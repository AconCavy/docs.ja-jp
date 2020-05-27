---
ms.openlocfilehash: 32030698c12de87daef5e1d8851a0f55ec36d688
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721092"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="e4dd2-101">Pkcs8PrivateKeyInfo コンストラクターでの引数の検証の改善</span><span class="sxs-lookup"><span data-stu-id="e4dd2-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="e4dd2-102">.NET Core 3.0 Preview 9 以降では、`Pkcs8PrivateKeyInfo` コンストラクターが `algorithmParameters` パラメーターを単一の BER でエンコードされた値として検証します。</span><span class="sxs-lookup"><span data-stu-id="e4dd2-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e4dd2-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="e4dd2-103">Change description</span></span>

<span data-ttu-id="e4dd2-104">.NET Core 3.0 Preview 9 以前では、[`Pkcs8PrivateKeyInfo` コンストラクター](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))では、`algorithmParameters` 引数が検証されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="e4dd2-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="e4dd2-105">この引数が不正な値を表した場合、コンストラクターは成功していましたが、引数が許容されないものであった場合 (`preEncodedValue`)、<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>、<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>、<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>、または <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> メソッドのいずれかの呼び出しに対し、<xref:System.ArgumentException> または <xref:System.Security.Cryptography.CryptographicException> のいずれかがスローされていました。</span><span class="sxs-lookup"><span data-stu-id="e4dd2-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="e4dd2-106">Preview 9 より前の .NET Core 3.0 で実行した場合、<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> メソッドが呼び出された場合のみ、次のコードで例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e4dd2-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="e4dd2-107">この引数は、.NET Core 3.0 Preview 9 からはコンストラクター内で検証され、値が不正な場合、メソッドにより <xref:System.Security.Cryptography.CryptographicException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e4dd2-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="e4dd2-108">この変更により、例外はデータ エラーのソースに近づきます。</span><span class="sxs-lookup"><span data-stu-id="e4dd2-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="e4dd2-109">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e4dd2-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="e4dd2-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="e4dd2-110">Version introduced</span></span>

<span data-ttu-id="e4dd2-111">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="e4dd2-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e4dd2-112">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="e4dd2-112">Recommended action</span></span>

<span data-ttu-id="e4dd2-113">例外の処理が必要な場合、有効な `algorithmParameters` 値のみを指定するようにします。そのようにしなければ、`Pkcs8PrivateKeyInfo` コンストラクターへのその呼び出しは <xref:System.ArgumentException> と <xref:System.Security.Cryptography.CryptographicException> の両方に対してテストされます。</span><span class="sxs-lookup"><span data-stu-id="e4dd2-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

#### <a name="category"></a><span data-ttu-id="e4dd2-114">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="e4dd2-114">Category</span></span>

<span data-ttu-id="e4dd2-115">暗号</span><span class="sxs-lookup"><span data-stu-id="e4dd2-115">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e4dd2-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="e4dd2-116">Affected APIs</span></span>

- <span data-ttu-id="e4dd2-117">[Pkcs8PrivateKeyInfo コンストラクター](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="e4dd2-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
