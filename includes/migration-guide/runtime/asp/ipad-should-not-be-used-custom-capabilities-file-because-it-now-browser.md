---
ms.openlocfilehash: 84f570cbbd97be79426e117d4c97ec182a397fd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379560"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>iPad はブラウザー機能になったため、カスタム機能ファイルでは使用できない

|   |   |
|---|---|
|説明|.NET Framework 4.5 以降では、iPad は既定の ASP.NET ブラウザー機能ファイルの識別子であるため、カスタム機能ファイルでは使用できません|
|提案される解決策|iPad 固有の機能が必要な場合は、ユーザー エージェントのマッチングで新しい &quot;IPad&quot; ID を生成するのではなく、定義済みのゲートウェイ refID &quot;IPad&quot; で機能を設定して、iPad の動作を変更する必要があります。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
