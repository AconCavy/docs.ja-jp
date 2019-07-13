---
title: ユーザ補助ガイドラインをサポートする Windows フォーム コントロールのプロパティ
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: b3f10fe472e449d39385facdbc716cba9b3f7382
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640496"
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>ユーザ補助ガイドラインをサポートする Windows フォーム コントロールのプロパティ
Windows フォームの標準的なツールボックス コントロールでは、キーボード フォーカスを公開することや、画面要素の公開など、アクセシビリティのガイドラインの多くをサポートします。  
  
## <a name="planning-ahead-for-accessibility"></a>アクセシビリティの計画を立てる  
 コントロールのプロパティは、次の表に示すように、その他のユーザー補助のガイドラインをサポートするために使用できます。 さらに、メニューを使用して、プログラムの機能にアクセスできるようにする必要があります。  
  
|コントロールのプロパティ|ユーザー補助機能に関する考慮事項|  
|----------------------|--------------------------------------|  
|AccessibleDescription|説明は、スクリーン リーダーなどのユーザー補助機能に報告されます。 ユーザー補助機能は専用のプログラムおよびデバイスで、障碍を持つユーザーがコンピューターをより効果的に使用するよう助けます。|  
|AccessibleName|この名前は、ユーザー補助機能が報告されます。|  
|AccessibleRole|ユーザー インターフェイスの要素の使用方法をについて説明します。|  
|TabIndex|フォームで実用的な移動パスを作成します。 コントロールがタブ オーダー内直後に、関連するラベルのテキスト ボックスなどの組み込みのラベルがない場合に重要です。|  
|テキスト|アクセス キーを作成するのにには、"&"の文字を使用します。 アクセス キーの使用は、文書化されているキーボード アクセス機能を提供することの一部です。|  
|フォント サイズ|フォント サイズが調整可能でない場合は、10 ポイント以上に設定する必要があります。 フォームのフォント サイズを設定すると、後からフォームに追加されるすべてのコントロールが同じサイズになります。|  
|前景色|このプロパティが、既定値に設定されている場合、ユーザーの色の設定は、フォームで使用します。|  
|背景色|このプロパティが、既定値に設定されている場合、ユーザーの色の設定は、フォームで使用します。|  
|BackgroundImage|このプロパティは、テキストを読みやすくする場合は空白のままにします。|  
  
## <a name="see-also"></a>関連項目

- [チュートリアル: ユーザー補助対応の Windows ベースのアプリケーションを作成します。](walkthrough-creating-an-accessible-windows-based-application.md)
