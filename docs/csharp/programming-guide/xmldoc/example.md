---
title: <example> - C# プログラミング ガイド
description: XML タグについて説明 <example> します。 このタグを使用すると、メソッドまたは他のライブラリ メンバーの使用例を指定できます。
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: dd529e8f2a54cf9086d0d8c555dd1adb70b99126
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381529"
---
# <a name="example-c-programming-guide"></a>\<example> (C# プログラミング ガイド)

## <a name="syntax"></a>構文

```xml
<example>description</example>
```

## <a name="parameters"></a>パラメーター

- `description`

  コード例の説明です。

## <a name="remarks"></a>Remarks

`<example>` タグを使用すると、メソッドまたは他のライブラリ メンバーの使用例を指定できます。 一般的に、[\<code>](./code.md) タグが使用されます。

コンパイル時に [-doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。

## <a name="example"></a>例

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメント用の推奨タグ](./recommended-tags-for-documentation-comments.md)
