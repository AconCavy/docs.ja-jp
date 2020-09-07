---
ms.openlocfilehash: 4416a7c09f2d163961fe2fe3d6dfaa8bd5e66f93
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497838"
---
### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a><span data-ttu-id="16680-101">データ定義言語 (DDL: Data Definition Language) API の動作の変更</span><span class="sxs-lookup"><span data-stu-id="16680-101">Change in behavior in Data Definition Language (DDL) APIs</span></span>

#### <a name="details"></a><span data-ttu-id="16680-102">説明</span><span class="sxs-lookup"><span data-stu-id="16680-102">Details</span></span>

<span data-ttu-id="16680-103">AttachDBFilename が指定されたときの DDL API の動作が、次のように変更されました。</span><span class="sxs-lookup"><span data-stu-id="16680-103">The behavior of DDL APIs when AttachDBFilename is specified has changed as follows:</span></span><ul><li><span data-ttu-id="16680-104">接続文字列で初期カタログ値を指定する必要がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="16680-104">Connection strings need not specify an Initial Catalog value.</span></span> <span data-ttu-id="16680-105">以前は、AttachDBFilename と初期カタログの両方が必要でした。</span><span class="sxs-lookup"><span data-stu-id="16680-105">Previously, both AttachDBFilename and Initial Catalog were required.</span></span></li><li><span data-ttu-id="16680-106">AttachDBFilename と初期カタログの両方が指定され、指定された MDF ファイルが存在した場合、<xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> メソッドは <code>true</code> を返します。</span><span class="sxs-lookup"><span data-stu-id="16680-106">If both AttachDBFilename and Initial Catalog are specified and the given MDF file exists, the <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> method returns <code>true</code>.</span></span> <span data-ttu-id="16680-107">以前は、<code>false</code>が返されていました。</span><span class="sxs-lookup"><span data-stu-id="16680-107">Previously, it returned <code>false</code>.</span></span></li><li><span data-ttu-id="16680-108">AttachDBFilename と初期カタログの両方が指定され、指定された MDF ファイルが存在した場合、<xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> メソッドを呼び出すと、ファイルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="16680-108">If both AttachDBFilename and Initial Catalog are specified and the given MDF file exists, calling the <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> method deletes the files.</span></span></li><li><span data-ttu-id="16680-109">接続文字列で存在しない MDF の AttachDBFilename 値および存在しない初期カタログが指定されたときに <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> が呼び出されると、メソッドでは <xref:System.InvalidOperationException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="16680-109">If <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> is called when the connection string specifies an AttachDBFilename value with an MDF that doesn't exist and an Initial Catalog that doesn't exist, the method throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="16680-110">以前は、<xref:System.Data.SqlClient.SqlException> の例外がスローされていました。</span><span class="sxs-lookup"><span data-stu-id="16680-110">Previously, it threw a <xref:System.Data.SqlClient.SqlException> exception.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="16680-111">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="16680-111">Suggestion</span></span>

<span data-ttu-id="16680-112">これらの変更により、DDL API を使用するアプリケーションおよびツールの構築が簡単になりました。</span><span class="sxs-lookup"><span data-stu-id="16680-112">These changes make it easier to build tools and applications that use the DDL APIs.</span></span> <span data-ttu-id="16680-113">これらの変更は、次のシナリオでアプリケーションの互換性に影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16680-113">These changes can affect application compatibility in the following scenarios:</span></span><ul><li><span data-ttu-id="16680-114"><code>DROP DATABASE</code> で <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> が返されたときに、<xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> を呼び出す代わりに直接 <code>true</code> コマンドを実行するコードをユーザーが作成した場合。</span><span class="sxs-lookup"><span data-stu-id="16680-114">The user writes code that executes a <code>DROP DATABASE</code> command directly instead of calling <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> if <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> returns <code>true</code>.</span></span> <span data-ttu-id="16680-115">データベースがアタッチされておらず、MDF ファイルが存在する場合、これによって既存のコードが破損します。</span><span class="sxs-lookup"><span data-stu-id="16680-115">This breaks existing code If the database is not attached but the MDF file exists.</span></span></li><li><span data-ttu-id="16680-116">初期カタログと MDF ファイルが存在しない場合に、<xref:System.InvalidOperationException> ではなく <xref:System.Data.SqlClient.SqlException> をスローするように、<xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> メソッドを要求するコードをユーザーが作成した場合。</span><span class="sxs-lookup"><span data-stu-id="16680-116">The user writes code that expects the <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> method to throw a <xref:System.Data.SqlClient.SqlException> rather than an <xref:System.InvalidOperationException> when the Initial Catalog and MDF file don't exist.</span></span></li></ul>

| <span data-ttu-id="16680-117">名前</span><span class="sxs-lookup"><span data-stu-id="16680-117">Name</span></span>    | <span data-ttu-id="16680-118">[値]</span><span class="sxs-lookup"><span data-stu-id="16680-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="16680-119">スコープ</span><span class="sxs-lookup"><span data-stu-id="16680-119">Scope</span></span>   |<span data-ttu-id="16680-120">マイナー</span><span class="sxs-lookup"><span data-stu-id="16680-120">Minor</span></span>|
|<span data-ttu-id="16680-121">バージョン</span><span class="sxs-lookup"><span data-stu-id="16680-121">Version</span></span>|<span data-ttu-id="16680-122">4.5</span><span class="sxs-lookup"><span data-stu-id="16680-122">4.5</span></span>|
|<span data-ttu-id="16680-123">種類</span><span class="sxs-lookup"><span data-stu-id="16680-123">Type</span></span>|<span data-ttu-id="16680-124">ランタイム</span><span class="sxs-lookup"><span data-stu-id="16680-124">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="16680-125">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="16680-125">Affected APIs</span></span>

<span data-ttu-id="16680-126">API 分析では検出できません。</span><span class="sxs-lookup"><span data-stu-id="16680-126">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
