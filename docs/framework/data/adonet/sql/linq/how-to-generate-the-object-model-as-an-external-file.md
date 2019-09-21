---
title: '方法: オブジェクト モデルを外部ファイルとして生成する'
ms.date: 03/30/2017
ms.assetid: 2496fa06-3df4-4ecb-86c4-70a49ea08565
ms.openlocfilehash: 3fd84d878ab07411bba41a13ff3eef91b2425e8a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793592"
---
# <a name="how-to-generate-the-object-model-as-an-external-file"></a>方法: オブジェクト モデルを外部ファイルとして生成する
属性ベースのマッピングに代わる方法として、SQLMetal コマンド ライン ツールを使用することにより、外部 XML ファイルとしてオブジェクト モデルを生成できます。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。 外部 XML マッピング ファイルを使用すると、コードの煩雑さが軽減されます。 さらに、アプリケーションのバイナリを再コンパイルしなくても、外部ファイルを変更するだけで動作を変えることができます。 詳細については、「[外部マッピング](external-mapping.md)」を参照してください。  
  
> [!NOTE]
> オブジェクトリレーショナルデザイナーは、外部マッピングファイルの生成をサポートしていません。  
  
## <a name="example"></a>例  
 次のコマンドは、Northwind サンプル データベースから外部マッピング ファイルを生成します。  
  
```  
sqlmetal /server:myserver /database:northwind /map:externalfile.xml  
```  
  
## <a name="example"></a>例  
 以下は、Northwind サンプル データベース内の Customers テーブルのマッピングを示す、外部マッピング ファイルの一部分です。 この抜粋は、 **/map**オプションを指定して SQLMetal を実行することによって生成されました。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Database xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" Name="northwnd">  
  <Table Name="Customers">  
    <Type Name=".Customer">  
      <Column Name="CustomerID" Member="CustomerID" Storage="_CustomerID" DbType="NChar(5) NOT NULL" CanBeNull="False" IsPrimaryKey="True" />  
      <Column Name="CompanyName" Member="CompanyName" Storage="_CompanyName" DbType="NVarChar(40) NOT NULL" CanBeNull="False" />  
      <Column Name="ContactName" Member="ContactName" Storage="_ContactName" DbType="NVarChar(30)" />  
      <Column Name="ContactTitle" Member="ContactTitle" Storage="_ContactTitle" DbType="NVarChar(30)" />  
      <Column Name="Address" Member="Address" Storage="_Address" DbType="NVarChar(60)" />  
      <Column Name="City" Member="City" Storage="_City" DbType="NVarChar(15)" />  
      <Column Name="Region" Member="Region" Storage="_Region" DbType="NVarChar(15)" />  
      <Column Name="PostalCode" Member="PostalCode" Storage="_PostalCode" DbType="NVarChar(10)" />  
      <Column Name="Country" Member="Country" Storage="_Country" DbType="NVarChar(15)" />  
      <Column Name="Phone" Member="Phone" Storage="_Phone" DbType="NVarChar(24)" />  
      <Column Name="Fax" Member="Fax" Storage="_Fax" DbType="NVarChar(24)" />  
      <Association Name="FK_CustomerCustomerDemo_Customers" Member="CustomerCustomerDemos" Storage="_CustomerCustomerDemos" ThisKey="CustomerID" OtherTable="CustomerCustomerDemo" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
      <Association Name="FK_Orders_Customers" Member="Orders" Storage="_Orders" ThisKey="CustomerID" OtherTable="Orders" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
    </Type>  
  </Table>  
</Database>  
```  
  
## <a name="see-also"></a>関連項目

- [オブジェクト モデルの作成](creating-the-object-model.md)
- [外部マップ](external-mapping.md)
- [方法: Visual Basic または C# でオブジェクト モデルを生成する](how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
