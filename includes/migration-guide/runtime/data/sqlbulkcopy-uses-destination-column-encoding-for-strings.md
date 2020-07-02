---
ms.openlocfilehash: 1329a86db4227f75dfba7c50bbbdc2fc23099528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620280"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a><span data-ttu-id="b4faf-101">SqlBulkCopy で文字列に挿入先の列エンコードが使用される</span><span class="sxs-lookup"><span data-stu-id="b4faf-101">SqlBulkCopy uses destination column encoding for strings</span></span>

#### <a name="details"></a><span data-ttu-id="b4faf-102">説明</span><span class="sxs-lookup"><span data-stu-id="b4faf-102">Details</span></span>

<span data-ttu-id="b4faf-103">データを列に挿入する場合、<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> は <code>VARCHAR</code> と <code>CHAR</code> の型の既定エンコードではなく、挿入先の列のエンコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="b4faf-103">When inserting data into a column, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> uses the encoding of the destination column rather than the default encoding for <code>VARCHAR</code> and <code>CHAR</code> types.</span></span> <span data-ttu-id="b4faf-104">この変更により、挿入先の列が既定のエンコードを使用しない場合に、既定のエンコードを使用することによって発生するデータ破損の可能性がなくなります。</span><span class="sxs-lookup"><span data-stu-id="b4faf-104">This change eliminates the possibility of data corruption caused by using the default encoding when the destination column does not use the default encoding.</span></span> <span data-ttu-id="b4faf-105">まれに、エンコードに変更を加えることによって、挿入先の列に収まりきらない大きいデータが生成された場合に、既存のアプリケーションで SqlException の例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="b4faf-105">In rare cases, an existing application may throw a SqlException exception if the change in encoding produces data that is too big to fit into the destination column.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b4faf-106">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="b4faf-106">Suggestion</span></span>

<span data-ttu-id="b4faf-107"><xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> では、エンコードが異なるため、データは破損しなくなると予想します。</span><span class="sxs-lookup"><span data-stu-id="b4faf-107">Expect that <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> will no longer corrupt data due to encoding differences.</span></span> <span data-ttu-id="b4faf-108">挿入先の列のサイズ制限に近づいている文字列がコピーされている場合、データの事前エンコード (コピーして挿入先の行にデータが収まることを確認するため) や <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> のキャッチが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="b4faf-108">If strings near the destination column's size limit are being copied, it may be necessary to either pre-encode data (to be copied to check that the data will fit in the destination column) or catch <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="b4faf-109">名前</span><span class="sxs-lookup"><span data-stu-id="b4faf-109">Name</span></span>    | <span data-ttu-id="b4faf-110">[値]</span><span class="sxs-lookup"><span data-stu-id="b4faf-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b4faf-111">スコープ</span><span class="sxs-lookup"><span data-stu-id="b4faf-111">Scope</span></span>   |<span data-ttu-id="b4faf-112">エッジ</span><span class="sxs-lookup"><span data-stu-id="b4faf-112">Edge</span></span>|
|<span data-ttu-id="b4faf-113">バージョン</span><span class="sxs-lookup"><span data-stu-id="b4faf-113">Version</span></span>|<span data-ttu-id="b4faf-114">4.5</span><span class="sxs-lookup"><span data-stu-id="b4faf-114">4.5</span></span>|
|<span data-ttu-id="b4faf-115">種類</span><span class="sxs-lookup"><span data-stu-id="b4faf-115">Type</span></span>|<span data-ttu-id="b4faf-116">ランタイム</span><span class="sxs-lookup"><span data-stu-id="b4faf-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b4faf-117">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="b4faf-117">Affected APIs</span></span>

-<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)></li></ul>|
