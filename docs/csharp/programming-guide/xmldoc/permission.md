---
title: <permission> - C# プログラミング ガイド
description: XML タグについて説明 <permission> します。 このタグを使用すると、メンバーのアクセスをドキュメント化できます。一方、PermissionSet クラスを使用すると、メンバーへのアクセスを指定できます。
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 38c87505b8b2973875e474ffd296dc02b7fb9de6
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381724"
---
# <a name="permission-c-programming-guide"></a>\<permission> (C# プログラミング ガイド)

## <a name="syntax"></a>構文

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>パラメーター

- cref = "`member`"

  現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。 コンパイラは、指定されたコード要素が存在し、出力の XML で `member` が正規要素名に変換されることを確認します。 *member* は、二重引用符 (" ") で囲む必要があります。

  ジェネリック型への cref 参照を作成する方法については、[cref 属性](./cref-attribute.md)に関するページを参照してください。

- `description`

  メンバーへのアクセスの説明です。

## <a name="remarks"></a>Remarks

`<permission>` タグを使用すると、メンバーのアクセスをドキュメント化できます。 <xref:System.Security.PermissionSet> クラスを使用すると、メンバーへのアクセスを指定できます。

コンパイル時に [-doc](../../language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。

## <a name="example"></a>例

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ドキュメント コメント用の推奨タグ](./recommended-tags-for-documentation-comments.md)
