---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 10789f9a2940c239ae20c8fd1e9d48bca0e820ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963697"
---
# <a name="contract"></a>コントラクト
コントラクト  
  
## <a name="syntax"></a>構文  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a>メソッド  
 Contract クラスで定義されているメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 Contract クラスには、次のプロパティがあります。  
  
### <a name="appdomainid"></a>AppDomainId  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 コントラクトをホストする appdomain の appdomain ID。  
  
### <a name="behaviors"></a>ビヘイビアー  
 データの種類:動作の配列  
  
 アクセスの種類:読み取り専用  
  
 このコントラクトに関連付けられている動作。  
  
### <a name="name"></a>名前  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 WSDL でのコントラクトの名前。  
  
### <a name="namespace"></a>名前空間  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 WSDL での `portType` 要素の名前空間。  
  
### <a name="operations"></a>操作  
 データの種類:配列の操作  
  
 アクセスの種類:読み取り専用  
  
 このコントラクトの操作。  
  
### <a name="processid"></a>ProcessId  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 コントラクトをホストするプロセスのプロセス ID。  
  
### <a name="ref"></a>ref  
 データの種類:コントラクト  
  
 アクセスの種類:読み取り専用  
  
 コントラクトが双方向コントラクトのときのコールバックの型。  
  
### <a name="sessionmode"></a>SessionMode  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 コントラクトでチャネル セッションを使用するために、このコントラクトに関連付けられたバインディングが必要かどうかを示します。  
  
### <a name="type"></a>型  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 コントラクトの型。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.ContractDescription>
