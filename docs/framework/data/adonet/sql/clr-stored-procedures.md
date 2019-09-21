---
title: CLR ストアド プロシージャ
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: d2fde4fdcd5ab63906256d814256578b9baa9ecd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782500"
---
# <a name="clr-stored-procedures"></a>CLR ストアド プロシージャ
ストアド プロシージャはスカラー式では使用できないルーチンです。 ストアド プロシージャは、表形式の結果とメッセージをクライアントに返したり、データ定義言語 (DDL) ステートメントおよびデータ操作言語 (DML) ステートメントを呼び出したり、出力パラメーターを返したりすることができます。  
  
> [!NOTE]
> Microsoft Visual Basic では、出力パラメーターのサポートが Microsoft Visual C# と異なります。 次に示すように、パラメーターを参照によって\<渡し、Out () > 属性を適用して出力パラメーターを表す必要があります。  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
詳細については、使用している SQL Server バージョンの[SQL Server ドキュメント](/sql)のバージョンを参照してください。
  
 **SQL Server のドキュメント**

1. [CLR ストアド プロシージャ](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>関連項目

- [マネージコードでの SQL Server 2005 オブジェクトの作成](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [ADO.NET の概要](../ado-net-overview.md)
