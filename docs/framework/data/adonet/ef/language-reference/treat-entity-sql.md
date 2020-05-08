---
title: TREAT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 06c4200434f443446e8981dcefe2baf43b1af4b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149896"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="11122-102">TREAT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="11122-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="11122-103">特定の基本データ型のオブジェクトを指定の派生型のオブジェクトとして処理します。</span><span class="sxs-lookup"><span data-stu-id="11122-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11122-104">構文</span><span class="sxs-lookup"><span data-stu-id="11122-104">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="11122-105">引数</span><span class="sxs-lookup"><span data-stu-id="11122-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="11122-106">エンティティを返す任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="11122-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11122-107">指定の式の型は、特定のデータ型のサブタイプである必要があります。または、データ型は式の型のサブタイプである必要があります。</span><span class="sxs-lookup"><span data-stu-id="11122-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="11122-108">エンティティ型。</span><span class="sxs-lookup"><span data-stu-id="11122-108">An entity type.</span></span> <span data-ttu-id="11122-109">型は名前空間で修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11122-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11122-110">指定の式は、特定のデータ型のサブタイプである必要があります。または、データ型は式のサブタイプである必要があります。</span><span class="sxs-lookup"><span data-stu-id="11122-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11122-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="11122-111">Return Value</span></span>  
 <span data-ttu-id="11122-112">指定されたデータ型の値。</span><span class="sxs-lookup"><span data-stu-id="11122-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11122-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="11122-113">Remarks</span></span>  
 <span data-ttu-id="11122-114">TREAT は関連クラス間でキャストを実行するために使用します。</span><span class="sxs-lookup"><span data-stu-id="11122-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="11122-115">たとえば、 `Employee` が `Person` から派生し、p が `Person`型である場合、 `TREAT(p AS NamespaceName.Employee)` はジェネリック型の `Person` インスタンスを `Employee`にキャストします。つまり、p を `Employee`として処理できます。</span><span class="sxs-lookup"><span data-stu-id="11122-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="11122-116">TREAT は、次のようにクエリを実行できる継承シナリオで使用されます。</span><span class="sxs-lookup"><span data-stu-id="11122-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 <span data-ttu-id="11122-117">このクエリは、 `Person` エンティティを `Employee` 型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="11122-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="11122-118">p の値が実際には `Employee`型でない場合、この式は `null`値を返します。</span><span class="sxs-lookup"><span data-stu-id="11122-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11122-119">指定する式 `Employee` は、指定するデータ型 `Person` のサブタイプである必要があります。または、データ型は式のサブタイプである必要があります。</span><span class="sxs-lookup"><span data-stu-id="11122-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="11122-120">そうでない場合は、コンパイル時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="11122-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="11122-121">次の表に、いくつかの通常パターンと一般的でないパターンにおける TREAT の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="11122-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="11122-122">すべての例外はクライアント側にスローされてから、プロバイダーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="11122-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="11122-123">パターン</span><span class="sxs-lookup"><span data-stu-id="11122-123">Pattern</span></span>|<span data-ttu-id="11122-124">動作</span><span class="sxs-lookup"><span data-stu-id="11122-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="11122-125">`DbNull`を返します。</span><span class="sxs-lookup"><span data-stu-id="11122-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="11122-126">例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="11122-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="11122-127">例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="11122-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="11122-128">`EntityType` または `null`を返します。</span><span class="sxs-lookup"><span data-stu-id="11122-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="11122-129">例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="11122-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="11122-130">例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="11122-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="11122-131">例</span><span class="sxs-lookup"><span data-stu-id="11122-131">Example</span></span>  
 <span data-ttu-id="11122-132">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、TREAT 演算子を使用して、Course 型のオブジェクトを OnsiteCourse 型のオブジェクトのコレクションに変換します。</span><span class="sxs-lookup"><span data-stu-id="11122-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="11122-133">このクエリは、 [School モデル](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))に基づいています。</span><span class="sxs-lookup"><span data-stu-id="11122-133">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="11122-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="11122-134">See also</span></span>

- [<span data-ttu-id="11122-135">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="11122-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="11122-136">NULL 値が許容される構造化型</span><span class="sxs-lookup"><span data-stu-id="11122-136">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
