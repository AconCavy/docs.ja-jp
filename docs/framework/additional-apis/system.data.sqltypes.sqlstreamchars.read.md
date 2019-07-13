---
title: SqlStreamChars.Read (Char、Int32, Int32) メソッド (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: df715f622f874b3c9297c421eab9f4c7504e696b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634318"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a>SqlStreamChars.Read (Char、Int32, Int32) メソッド

派生クラスでオーバーライドされると、入力ストリームから次の文字セットを読み取ります。 このメソッドを含むアセンブリには、SQLAccess.dll で友人関係があります。 SQL Server で使用するものでは。 その他のデータベースには、そのデータベースによって提供されるホスティング メカニズムを使用します。

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>パラメーター

`buffer`\
読み取る文字の配列。

`offset`\
原点からのオフセット。

`count`\
現在のストリームから読み取る文字の数。

## <a name="returns"></a>戻り値

<xref:System.Int32>\
バッファーに読み取られた合計文字数。

## <a name="remarks"></a>Remarks

> [!WARNING]
> `SqlStreamChars.Read`メソッドはプライベートであり、コード内で直接使用するものではありません。
>
> Microsoft はいかなる運用アプリケーションでこのフィールドの使用をサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.Data (system.data.dll 内)

**.NET framework のバージョン:** 2.0 以降で使用可能です。
