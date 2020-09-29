---
title: LINQ to SQL におけるセキュリティ
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: 6260f0c565a25764c8fabd2770d4f06a987aa9bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173394"
---
# <a name="security-in-linq-to-sql"></a><span data-ttu-id="5601a-102">LINQ to SQL におけるセキュリティ</span><span class="sxs-lookup"><span data-stu-id="5601a-102">Security in LINQ to SQL</span></span>

<span data-ttu-id="5601a-103">データベースに接続するときは、常にセキュリティのリスクがあります。</span><span class="sxs-lookup"><span data-stu-id="5601a-103">Security risks are always present when you connect to a database.</span></span> <span data-ttu-id="5601a-104">LINQ to SQL には SQL Server のデータを操作する新しい方法が含まれていますが、セキュリティ メカニズムは追加されていません。</span><span class="sxs-lookup"><span data-stu-id="5601a-104">Although LINQ to SQL may include some new ways to work with data in SQL Server, it does not provide any additional security mechanisms.</span></span>  
  
## <a name="access-control-and-authentication"></a><span data-ttu-id="5601a-105">アクセス制御と認証</span><span class="sxs-lookup"><span data-stu-id="5601a-105">Access Control and Authentication</span></span>  

 <span data-ttu-id="5601a-106">LINQ to SQL には独自のユーザー モデルや認証メカニズムがありません。</span><span class="sxs-lookup"><span data-stu-id="5601a-106">LINQ to SQL does not have its own user model or authentication mechanisms.</span></span> <span data-ttu-id="5601a-107">オブジェクト モデルにマッピングされるデータベース、データベースのテーブル、ビュー、ストアド プロシージャなどへのアクセス制御には SQL Server のセキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="5601a-107">Use SQL Server Security to control access to the database, database tables, views, and stored procedures that are mapped to your object model.</span></span> <span data-ttu-id="5601a-108">ユーザーには必要最小限のアクセス権を与え、ユーザー認証には強力なパスワードを要求してください。</span><span class="sxs-lookup"><span data-stu-id="5601a-108">Grant the minimally required access to users and require strong passwords for user authentication.</span></span>  
  
## <a name="mapping-and-schema-information"></a><span data-ttu-id="5601a-109">マッピングとスキーマ情報</span><span class="sxs-lookup"><span data-stu-id="5601a-109">Mapping and Schema Information</span></span>  

 <span data-ttu-id="5601a-110">オブジェクト モデルまたは外部マッピング ファイルにある、SQL-CLR 型マッピングとデータベース スキーマ情報は、ファイル システムでこれらのファイルに対してアクセス権を持つ全ユーザーに公開されます。</span><span class="sxs-lookup"><span data-stu-id="5601a-110">SQL-CLR type mapping and database schema information in your object model or external mapping file is available for all with access to those files in the file system.</span></span> <span data-ttu-id="5601a-111">オブジェクト モデルまたは外部マッピング ファイルにアクセスできるすべてのユーザーがスキーマ情報を使用できることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="5601a-111">Assume that schema information will be available to all who can access the object model or external mapping file.</span></span> <span data-ttu-id="5601a-112">より広範囲にスキーマ情報をアクセス可能にするには、ファイル セキュリティ メカニズムを使用して、ソース ファイルとマッピング ファイルをセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="5601a-112">To prevent more widespread access to schema information, use file security mechanisms to secure source files and mapping files.</span></span>  
  
## <a name="connection-strings"></a><span data-ttu-id="5601a-113">接続文字列</span><span class="sxs-lookup"><span data-stu-id="5601a-113">Connection Strings</span></span>  

 <span data-ttu-id="5601a-114">接続文字列にパスワードを使用することは、できるだけ避けてください。</span><span class="sxs-lookup"><span data-stu-id="5601a-114">Using passwords in connection strings should be avoided whenever possible.</span></span> <span data-ttu-id="5601a-115">接続文字列自体がセキュリティのリスクであるうえに、接続文字列はオブジェクト リレーショナル デザイナーまたは SQLMetal コマンド ライン ツールの使用時にオブジェクト モデルや外部マッピング ファイルにクリア テキストで追加できます。</span><span class="sxs-lookup"><span data-stu-id="5601a-115">Not only is a connection string a security risk in its own right, but the connection string may also be added in clear text to the object model or external mapping file when using the Object Relational Designer or SQLMetal command-line tool.</span></span> <span data-ttu-id="5601a-116">ファイル システムでオブジェクト モデルまたは外部マッピング ファイルに対してアクセス権があれば、どのユーザーでも接続パスワードを見ることができます (パスワードが接続文字列に含まれている場合)。</span><span class="sxs-lookup"><span data-stu-id="5601a-116">Anyone with access to the object model or external mapping file via the file system could see the connection password (if it is included in the connection string).</span></span>  
  
 <span data-ttu-id="5601a-117">このようなリスクを最小限に抑えるには、統合セキュリティを使用して SQL Server との信頼関係接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="5601a-117">To minimize such risks, use integrated security to make a trusted connection with SQL Server.</span></span> <span data-ttu-id="5601a-118">この方法を使用すると、接続文字列にパスワードを含める必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="5601a-118">By using this approach, you do not have to store a password in the connection string.</span></span> <span data-ttu-id="5601a-119">詳細については、「[SQL Server のセキュリティ](../sql-server-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5601a-119">For more information, see [SQL Server Security](../sql-server-security.md).</span></span>  
  
 <span data-ttu-id="5601a-120">統合セキュリティがない場合は、接続文字列にクリア テキストのパスワードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="5601a-120">In the absence of integrated security, a clear-text password will be needed in the connection string.</span></span> <span data-ttu-id="5601a-121">以下は、接続文字列のセキュリティ保護に最も有効な手段です。</span><span class="sxs-lookup"><span data-stu-id="5601a-121">The best way to help secure your connection string, in increasing order of risk, is as follows:</span></span>  
  
- <span data-ttu-id="5601a-122">統合セキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="5601a-122">Use integrated security.</span></span>  
  
- <span data-ttu-id="5601a-123">接続文字列をパスワードで保護し、接続文字列の配布を最小限にします。</span><span class="sxs-lookup"><span data-stu-id="5601a-123">Secure connection strings with passwords and minimize passing around connection strings.</span></span>  
  
- <span data-ttu-id="5601a-124">接続文字列の代わりに、表示時間に制限のある <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="5601a-124">Use a <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> class instead of a connection string since it limits the duration of exposure.</span></span> <span data-ttu-id="5601a-125">LINQ to SQL の <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> クラスは <xref:System.Data.SqlClient.SqlConnection> を使用してインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="5601a-125">The LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> class can be instantiated using a <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
- <span data-ttu-id="5601a-126">すべての接続文字列の期限と接触点を最小限にします。</span><span class="sxs-lookup"><span data-stu-id="5601a-126">Minimize lifetimes and touch points for all connection strings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5601a-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="5601a-127">See also</span></span>

- [<span data-ttu-id="5601a-128">背景情報</span><span class="sxs-lookup"><span data-stu-id="5601a-128">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="5601a-129">よく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="5601a-129">Frequently Asked Questions</span></span>](frequently-asked-questions.md)
