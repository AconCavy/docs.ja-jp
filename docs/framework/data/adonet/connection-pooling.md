---
title: 接続プール
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: c431011cf57fd9ef79c2f0a099ab1080116c571f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786714"
---
# <a name="connection-pooling"></a><span data-ttu-id="45512-102">接続プール</span><span class="sxs-lookup"><span data-stu-id="45512-102">Connection Pooling</span></span>
<span data-ttu-id="45512-103">データ ソースへの接続は時間のかかる処理です。</span><span class="sxs-lookup"><span data-stu-id="45512-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="45512-104">接続を開くコストを最小限にするため、ADO.NET では、"*接続プール*" と呼ばれる最適化の手法が使われています。接続プールを使うことで、接続を開いて閉じるという処理の繰り返しによって生じるコストを、最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="45512-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="45512-105">接続プールは、.NET Framework データ プロバイダーに応じて異なる処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="45512-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45512-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="45512-106">In This Section</span></span>  
 [<span data-ttu-id="45512-107">SQL Server の接続プール (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="45512-107">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="45512-108">接続プールの概要および SQL Server における接続プールの動作を説明します。</span><span class="sxs-lookup"><span data-stu-id="45512-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="45512-109">OLE DB、ODBC、および Oracle 接続プール</span><span class="sxs-lookup"><span data-stu-id="45512-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="45512-110">.NET Framework Data Provider for OLE DB、.NET Framework Data Provider for ODBC、および .NET Framework Data Provider for Oracle の接続プールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="45512-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45512-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="45512-111">See also</span></span>

- [<span data-ttu-id="45512-112">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="45512-112">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="45512-113">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="45512-113">ADO.NET Overview</span></span>](ado-net-overview.md)
