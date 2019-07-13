---
title: SQL Workflow Instance Store
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 7cdd852795283660b8077e14686ad7ce4af76673
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626205"
---
# <a name="sql-workflow-instance-store"></a>SQL Workflow Instance Store
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] には SQL Workflow Instance Store が含まれます。これを使用すると、ワークフロー インスタンスに関する状態情報を SQL Server 2005 または SQL Server 2008 のデータベースに永続化できます。 この機能は主に <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> クラスの形式で実装されます。このクラスは永続化フレームワークの <xref:System.Runtime.DurableInstancing.InstanceStore> 抽象クラスから派生します。 SQL Workflow Instance Store 機能によって SQL 永続性プロバイダーを構成します。このプロバイダーは、ホストが永続化コマンドをストアに送信するときに使用する永続化 API の具象実装です。  
  
 SQL Workflow Instance Store は、セルフホストされているワークフローや、<xref:System.Activities.WorkflowApplication> または <xref:System.ServiceModel.WorkflowServiceHost> を使用するワークフロー サービスだけでなく、<xref:System.ServiceModel.WorkflowServiceHost> を使用して WAS でホストされるサービスをサポートします。 セルフホストされているサービスの SQL Workflow Instance Store 機能をプログラムで構成するには、この機能が公開しているオブジェクト モデルを使用します。 プログラムでオブジェクト モデルや XML 構成ファイルを使用することにより、<xref:System.ServiceModel.WorkflowServiceHost> でホストされるサービスについてこの機能を構成できます。  
  
 SQL Workflow Instance Store 機能 (**SqlWorkflowInstanceStore**クラス) を実装しません<xref:System.ServiceModel.Persistence.PersistenceProviderFactory>永続性ワークフロー以外の WCF サービスの永続性のサポートを提供しないためです。 また、<xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> を実装していないため、3.x ワークフローの永続化は提供しません。 この機能は、WF 4.0 以降のワークフローとワークフロー サービスについてのみ永続化をサポートします。 また、SQL Server 2005 と SQL Server 2008 以外のデータベースはサポートしません。  
  
 このセクションのトピックでは、SQL Workflow Instance Store のプロパティと機能、およびストアの構成方法の詳細を説明します。  
  
 Windows Server App Fabric には、インスタンス ストアを簡単に構成および使用できる独自のインスタンス ストアとツールが用意されています。 詳細については、次を参照してください。 [Windows Server App Fabric のインスタンス ストア](https://go.microsoft.com/fwlink/?LinkId=201201)します。 App Fabric SQL Server 永続性データベース参照の詳細については[App Fabric SQL Server 永続性データベース](https://go.microsoft.com/fwlink/?LinkId=201202)  
  
## <a name="in-this-section"></a>このセクションの内容  
  
- [SQL Workflow Instance Store のプロパティ](properties-of-sql-workflow-instance-store.md)  
  
- [方法: SQL 永続性ワークフローとワークフロー サービスを有効にします。](how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
- [インスタンスのアクティブ化処理](instance-activation.md)  
  
- [クエリのサポート](support-for-queries.md)  
  
- [ストア拡張](store-extensibility.md)  
  
- [セキュリティ](security.md)  
  
- [SQL Server 永続性データベース](sql-server-persistence-database.md)  
  
## <a name="see-also"></a>関連項目

- [永続化のサンプル](https://go.microsoft.com/fwlink/?LinkID=177735)
