---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804450"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>MEF カタログは IEnumerable を実装するため、シリアライザーの作成には使用できなくなった

|   |   |
|---|---|
|説明|.NET Framework 4.5 以降では、MEF カタログは IEnumerable を実装するため、シリアライザー (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> オブジェクト) の作成には使用できなくなりました。 MEF カタログをシリアル化しようとすると、例外がスローされます。|
|提案される解決策|シリアライザーの作成に MEF を使用できなくなりました。|
|スコープ|Major|
|バージョン|4.5|
|型|ランタイム|
