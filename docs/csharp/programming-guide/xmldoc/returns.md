---
title: <returns> - C# プログラミング ガイド
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 784d9effa589c962b8a2b982fd199f74309fb4dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789711"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="05544-102">\<returns> (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="05544-102">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="05544-103">構文</span><span class="sxs-lookup"><span data-stu-id="05544-103">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="05544-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05544-104">Parameters</span></span>

- `description`

  <span data-ttu-id="05544-105">戻り値の説明。</span><span class="sxs-lookup"><span data-stu-id="05544-105">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="05544-106">解説</span><span class="sxs-lookup"><span data-stu-id="05544-106">Remarks</span></span>

<span data-ttu-id="05544-107">\<returns> タグは、戻り値を説明するためにメソッドの宣言のコメントで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05544-107">The \<returns> tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="05544-108">コンパイル時に [-doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="05544-108">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="05544-109">例</span><span class="sxs-lookup"><span data-stu-id="05544-109">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="05544-110">参照</span><span class="sxs-lookup"><span data-stu-id="05544-110">See also</span></span>

- [<span data-ttu-id="05544-111">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="05544-111">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="05544-112">ドキュメント コメント用の推奨タグ</span><span class="sxs-lookup"><span data-stu-id="05544-112">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
