---
title: ファイル エンコーディング
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: f906b2f2d747a7950c70a24549bbf5423e5b87b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401746"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="31353-102">ファイル エンコーディング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31353-102">File Encodings (Visual Basic)</span></span>

<span data-ttu-id="31353-103">ファイル エンコーディングは、文字エンコーディングとも呼ばれ、テキストを処理するときの文字の表現方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="31353-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="31353-104">言語で処理できる (または処理できない) 文字という観点から、あるエンコードが他のエンコーディングよりも望ましいということがありますが、一般的には Unicode が好まれます。</span><span class="sxs-lookup"><span data-stu-id="31353-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>

<span data-ttu-id="31353-105">ファイルに対する読み取りと書き込みでは、ファイル エンコーディングが適切に一致しないと、例外が発生したり、不正な結果となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="31353-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>

## <a name="types-of-encodings"></a><span data-ttu-id="31353-106">エンコーディングの種類</span><span class="sxs-lookup"><span data-stu-id="31353-106">Types of Encodings</span></span>

<span data-ttu-id="31353-107">ファイルを扱うときには、Unicode は最適なエンコーディングです。</span><span class="sxs-lookup"><span data-stu-id="31353-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="31353-108">Unicode は、世界共通の文字エンコーディング規則で、技術的な記号や出版で使用される特殊文字などを含む、現在のコンピューティングで使用されるすべての文字を、16 ビットのコード値で表します。</span><span class="sxs-lookup"><span data-stu-id="31353-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>

<span data-ttu-id="31353-109">これまでの文字エンコーディング規則は、Windows ANSI 文字セットなどの従来からある文字セットで構成されており、8 ビットのコード値や 8 ビット値の組み合わせを使用して、特定の言語や地域で使用する文字を表していました。</span><span class="sxs-lookup"><span data-stu-id="31353-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>

## <a name="encoding-class"></a><span data-ttu-id="31353-110">Encoding クラス</span><span class="sxs-lookup"><span data-stu-id="31353-110">Encoding Class</span></span>

<span data-ttu-id="31353-111"><xref:System.Text.Encoding> クラスは文字エンコーディングを表します。</span><span class="sxs-lookup"><span data-stu-id="31353-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="31353-112">次の表は、利用可能なエンコーディングの型の一覧とそれぞれの説明です。</span><span class="sxs-lookup"><span data-stu-id="31353-112">This table lists the type of encodings available and describes each.</span></span>

|<span data-ttu-id="31353-113">name</span><span class="sxs-lookup"><span data-stu-id="31353-113">Name</span></span>|<span data-ttu-id="31353-114">[説明]</span><span class="sxs-lookup"><span data-stu-id="31353-114">Description</span></span>|
|---|---|
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="31353-115">Unicode 文字の ASCII 文字エンコードを表します。</span><span class="sxs-lookup"><span data-stu-id="31353-115">Represents an ASCII character encoding of Unicode characters.</span></span>|
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="31353-116">Unicode 文字の UTF-16 エンコーディングを表します。</span><span class="sxs-lookup"><span data-stu-id="31353-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="31353-117">Unicode 文字の UTF-32 エンコーディングを表します。</span><span class="sxs-lookup"><span data-stu-id="31353-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="31353-118">Unicode 文字の UTF-7 エンコードを表します。</span><span class="sxs-lookup"><span data-stu-id="31353-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="31353-119">Unicode 文字の UTF-8 エンコードを表します。</span><span class="sxs-lookup"><span data-stu-id="31353-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|

## <a name="see-also"></a><span data-ttu-id="31353-120">参照</span><span class="sxs-lookup"><span data-stu-id="31353-120">See also</span></span>

- [<span data-ttu-id="31353-121">ファイルの読み取り</span><span class="sxs-lookup"><span data-stu-id="31353-121">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="31353-122">ファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="31353-122">Writing to Files</span></span>](writing-to-files.md)
