---
title: モデリングとマッピング
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 5592ce5301216c8c3e74231480997d9e44d71a7d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197756"
---
# <a name="modeling-and-mapping"></a>モデリングとマッピング

Entity Framework では、概念モデル、ストレージ モデル、およびこの 2 つのモデル間のマッピングをアプリケーションに最適な方法で定義できます。 Visual Studio の Entity Data Model ツールを使用すると、データベースまたはグラフィカルなモデルから [.edmx ファイル](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))を作成し、データベースまたはモデルが変更されたときにそのファイルを更新できます。  
  
 Entity Framework 4.1 以降では、Code First の開発を使用してモデルをプログラムで作成することもできます。 Code First の開発に対しては、2 つの異なるシナリオがあります。 どちらの場合でも、開発者は .NET Framework のクラス定義をコーディングしてモデルを定義し、データ注釈または Fluent API を使用してオプションで追加のマッピングまたは構成を指定します。  
  
 詳しくは、「[モデルの作成](/ef/ef6/modeling/)」をご覧ください。  
  
 .NET Framework に含まれている EDM ジェネレーターを使用することもできます。 EdmGen.exe は、既存のデータ ソースから .csdl ファイル、.ssdl ファイル、および .msl ファイルを生成します。 モデルとマッピングの内容を手動で作成することもできます。 詳しくは、「[EDM ジェネレーター (EdmGen.exe)](edm-generator-edmgen-exe.md)」をご覧ください。
