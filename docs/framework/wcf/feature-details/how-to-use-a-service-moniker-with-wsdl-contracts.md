---
title: '方法: WSDL コントラクトと共にサービス モニカーを使用する'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 7bc628952d4a7198f0b5545014ae931bbf73dab3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2019
ms.locfileid: "70968996"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a>方法: WSDL コントラクトと共にサービス モニカーを使用する
完全に自己完結型である COM Interop クライアントの構築が必要になる場合があります。 呼び出そうとするサービスで MEX エンドポイントが公開されておらず、WCF クライアントの DLL が COM interop に登録されていないこともあります。 このような場合、サービスを記述した WSDL ファイルを作成し、そのファイルを WCF サービス モニカーに渡すことができます。 ここでは、WCF WSDL モニカーを使用して、WCF の入門サンプルを呼び出す方法を説明します。  
  
### <a name="using-the-wsdl-service-moniker"></a>WSDL サービス モニカーの使用  
  
1. 入門サンプル ソリューションを開き、ビルドします。  
  
2. Internet Explorer を開き、に`http://localhost/ServiceModelSamples/Service.svc`移動して、サービスが動作していることを確認します。  
  
3. Service.cs ファイルで、次の属性を CalculatorService クラスに追加します。  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. バインディング名前空間をサービスの App.config に追加します。  

5. アプリケーションが読み取る WSDL ファイルを作成します。 名前空間は手順 3. と 4. で追加されたため、を`http://localhost/ServiceModelSamples/Service.svc?wsdl`参照して、IE を使用してサービスの WSDL 記述全体を照会できます。 次に、そのファイルをサービスの WSDL.xml として Internet Explorer で保存できます。 手順 3. と 4. で名前空間を指定しなかった場合、上記の URL を照会したときに返される WSDL ドキュメントは、完全な WSDL ではありません。 返される WSDL ドキュメントには、他の WSDL ドキュメントをインポートするためのインポート ステートメントが追加されています。 各インポート ステートメントを実行し、サービスから返された WSDL とインポートした WSDL を組み合わせることによって、完全な WSDL ドキュメントを作成する必要があります。  
  
6. Visual Basic 6.0 を開き、新しい標準 .exe ファイルを作成します。 フォームにボタンを追加し、追加したボタンをダブルクリックして次のコードをクリック ハンドラーに追加します。  
  
    ```vb
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    > モニカーの形式が正しくないか、`GetObject` を呼び出せない場合は、"構文が無効です" というメッセージが返されます。  このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。  
  
7. Visual Basic アプリケーションを実行します。 メッセージ ボックスに、Subtract(145, 76.54) を呼び出した結果が表示されます。  
  
## <a name="see-also"></a>関連項目

- [はじめに](../../../../docs/framework/wcf/samples/getting-started-sample.md)
- [COM アプリケーションとの統合の概要](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
