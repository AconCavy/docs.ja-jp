---
title: <typeparam> - C# プログラミング ガイド
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793364"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="f99be-102">\<typeparam> (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f99be-102">\<typeparam> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="f99be-103">構文</span><span class="sxs-lookup"><span data-stu-id="f99be-103">Syntax</span></span>

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a><span data-ttu-id="f99be-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f99be-104">Parameters</span></span>

- `name`

  <span data-ttu-id="f99be-105">型パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="f99be-105">The name of the type parameter.</span></span> <span data-ttu-id="f99be-106">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="f99be-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="f99be-107">型パラメーターの説明。</span><span class="sxs-lookup"><span data-stu-id="f99be-107">A description for the type parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="f99be-108">解説</span><span class="sxs-lookup"><span data-stu-id="f99be-108">Remarks</span></span>

<span data-ttu-id="f99be-109">`<typeparam>` タグは、型パラメーターを説明するためにジェネリック型またはメソッドの宣言のコメントで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99be-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="f99be-110">ジェネリック型またはメソッドの型パラメーターごとにタグを追加します。</span><span class="sxs-lookup"><span data-stu-id="f99be-110">Add a tag for each type parameter of the generic type or method.</span></span>

<span data-ttu-id="f99be-111">詳細については、「[ジェネリック](../generics/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f99be-111">For more information, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="f99be-112">`<typeparam>` タグのテキストは、IntelliSense、[オブジェクト ブラウザー ウィンドウ](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser)、コード コメント Web レポートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f99be-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>

<span data-ttu-id="f99be-113">コンパイル時に [-doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="f99be-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="f99be-114">例</span><span class="sxs-lookup"><span data-stu-id="f99be-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="f99be-115">参照</span><span class="sxs-lookup"><span data-stu-id="f99be-115">See also</span></span>

- [<span data-ttu-id="f99be-116">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="f99be-116">C# reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="f99be-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f99be-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="f99be-118">ドキュメント コメント用の推奨タグ</span><span class="sxs-lookup"><span data-stu-id="f99be-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
