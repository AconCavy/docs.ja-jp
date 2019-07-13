---
title: レコード式のコピーと更新
description: "'コピーと更新式を' 既存のレコードまたは匿名のレコード、更新プログラムをコピーするフィールドを指定して、更新されたレコードまたは匿名のレコードを返します記述する方法について説明します。"
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: d16f5ca337047ab2eecc8828b21d8a423bf39a1f
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041731"
---
# <a name="copy-and-update-record-expressions"></a>レコード式のコピーと更新

A*コピーして更新するレコード式*を既存のレコードをコピーし、指定のフィールドを更新し、更新されたレコードを返す式を指定します。

## <a name="syntax"></a>構文

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Remarks

レコードと匿名は可能な更新プログラムを既存のレコードがないように、既定では、変更できません。 更新したレコードを作成するには、レコードのすべてのフィールドには、もう一度指定する必要があります。 このタスクを簡略化する、*コピーして、式を更新*ことができます。 この式は、既存のレコードには、式から指定したフィールドと、式で指定された存在しないフィールドを使用して、同じ型の新しいデフォルトを作成します。

これは、フィールドの値の一部を変更する可能性があります、既存のレコードをコピーする必要があるときに役立ちます。

新しく作成されたレコード インスタンスがかかります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

使用することがそのレコードのフィールドでのみ更新する場合は、*コピーして更新するレコード式*次のように。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>関連項目

- [レコード](records.md)
- [匿名のレコード](anonymous-records.md)
- [F# 言語リファレンス](index.md)
