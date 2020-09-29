---
title: プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 17c31301e28c757954e72ba103254f038905671f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874360"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました

プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました。 そのため、XML IntelliSense は使用できません。  
  
 プロジェクトに含まれている XML スキーマ定義 (XSD) スキーマにエラーがあります。 このエラーは、プロジェクト用の既存の XSD スキーマ セットと競合する XSD スキーマ (.xsd) ファイルを追加したときに発生します。  
  
 **エラー ID:** BC36810  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- **[エラー一覧]** ウィンドウで警告をダブルクリックします。 Visual Basic により、警告の原因となった XSD ファイル内の場所に移動します。 XSD スキーマのエラーを修正します。  
  
- 必要な XSD スキーマ (.xsd) ファイルがすべてプロジェクトに含まれていることを確認します。 **ソリューション エクスプローラー**で .xsd ファイルを表示するには、 **[プロジェクト]** メニューの **[すべてのファイルを表示]** をクリックする必要がある場合があります。 .xsd ファイルを右クリックし、 **[プロジェクトに含める]** をクリックしてプロジェクトにファイルを含めます。  
  
- XML to Schema ウィザードを使用している場合は、同じソースからスキーマを複数回推論すると、このエラーが発生することがあります。 この場合、プロジェクトから既存の XSD スキーマ ファイルを削除し、新しい XML to Schema 項目テンプレートを追加してから、プロジェクトに適用できるすべての XML ソースを XML to Schema ウィザードに提供できます。  
  
- XSD スキーマでエラーが識別されない場合は、XML コンパイラに詳細なエラー メッセージを提供するのに十分な情報がない可能性があります。 プロジェクトに含まれている .xsd ファイルの XML 名前空間が、Visual Studio の XML スキーマ セットで識別された xml 名前空間と一致することを確認すると、より詳細なエラー情報を取得できる場合があります。  
  
## <a name="see-also"></a>関連項目

- [[エラー一覧] ウィンドウ](/visualstudio/ide/reference/error-list-window)
- [XML](../../programming-guide/language-features/xml/index.md)
