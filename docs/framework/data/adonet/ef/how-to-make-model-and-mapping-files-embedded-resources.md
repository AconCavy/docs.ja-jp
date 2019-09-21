---
title: '方法: モデル ファイルとマッピング ファイルを組み込みリソースにする'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 371f8f0317295ee39d543b5637afb93102036b62
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854597"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>方法: モデル ファイルとマッピング ファイルを組み込みリソースにする
Entity Framework を使用すると、モデルファイルとマッピングファイルをアプリケーションの埋め込みリソースとして配置できます。 モデル ファイルとマッピング ファイルが組み込まれたアセンブリは、エンティティ接続と同じアプリケーション ドメインに読み込む必要があります。 詳細については、「[Connection Strings (接続文字列)](connection-strings.md)」をご覧ください。 既定では、Entity Data Model ツールによってモデルファイルとマッピングファイルが埋め込まれます。 モデルファイルとマッピングファイルを手動で定義する場合は、次の手順を使用して、ファイルが埋め込みリソースとして Entity Framework アプリケーションと共に配置されるようにします。  
  
> [!NOTE]
> 組み込みリソースを保持するには、モデル ファイルとマッピング ファイルを変更するたびに、この手順を繰り返す必要があります。  
  
### <a name="to-embed-model-and-mapping-files"></a>モデル ファイルとマッピング ファイルを組み込むには  
  
1. **ソリューションエクスプローラー**で、概念 (.csdl) ファイルを選択します。  
  
2. **[プロパティ]** ペインで、 **[ビルドアクション]** を **[埋め込みリソース]** に設定します。  
  
3. ストレージ (.ssdl) ファイルとマッピング (.msl) ファイルに対して手順 1. と手順 2. を繰り返します。  
  
4. **ソリューションエクスプローラー**で、app.config ファイルをダブルクリックし、次のいずれかの`Metadata`形式に基づい`connectionString`て属性のパラメーターを変更します。  
  
    - `Metadata=` `res://<assemblyFullName>/<resourceName>;`  
  
    - `Metadata=` `res://*/<resourceName>;`  
  
    - `Metadata=res://*;`  
  
     詳細については、「[Connection Strings (接続文字列)](connection-strings.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次の接続文字列は、 [AdventureWorks Sales model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)の埋め込みモデルファイルとマッピングファイルを参照します。 この接続文字列は、プロジェクトの App.config ファイルに格納されています。  

## <a name="see-also"></a>関連項目

- [モデリングとマッピング](modeling-and-mapping.md)
- [方法: 接続文字列を定義する](how-to-define-the-connection-string.md)
- [方法: EntityConnection 接続文字列を作成する](how-to-build-an-entityconnection-connection-string.md)
- [ADO.NET Entity Data Model ツール](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
