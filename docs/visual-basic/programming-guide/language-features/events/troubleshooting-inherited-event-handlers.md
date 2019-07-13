---
title: Visual Basic での継承されたイベント ハンドラーのトラブルシューティング
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: f2ddef64ca02ca7c96c6c906f5ee79e3cf99dece
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64604060"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Visual Basic での継承されたイベント ハンドラーのトラブルシューティング
このトピックでは、継承されたコンポーネントのイベント ハンドラーで発生する一般的な問題を一覧表示します。  
  
## <a name="procedures"></a>手順  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>イベント ハンドラーのコードは呼び出しごとに 2 回実行します  
  
- 継承されたイベント ハンドラーが含めることはできません、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句。 基本クラスのメソッドは既に、イベントに関連付けられたが発生します。 削除、`Handles`句継承されたメソッドから。  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- 継承されたメソッドがあるない場合、`Handles`キーワード、コードに追加が含まれていないことを確認します[AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)または他のメソッドを同じイベントを処理します。  
  
## <a name="see-also"></a>関連項目

- [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
