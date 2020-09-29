---
title: NULL 値が許容される構造化型 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: fc2230401ef98c005ab52a845de37482c0dcf698
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202265"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="d12fc-102">NULL 値が許容される構造化型 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d12fc-102">Nullable Structured Types (Entity SQL)</span></span>

<span data-ttu-id="d12fc-103">構造化型の `null` インスタンスは、存在しないインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="d12fc-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="d12fc-104">これは、すべてのプロパティの値が `null` であるインスタンスとは異なります。</span><span class="sxs-lookup"><span data-stu-id="d12fc-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="d12fc-105">このトピックでは、NULL 値が許容される構造化型について説明します。この内容には、NULL 値が許容される型、および構造化 NULL 値が許容される型の `null` インスタンスを生成するコード パターンも含まれます。</span><span class="sxs-lookup"><span data-stu-id="d12fc-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="d12fc-106">NULL 値が許容される構造化型の種類</span><span class="sxs-lookup"><span data-stu-id="d12fc-106">Kinds of Nullable Structured Types</span></span>  

 <span data-ttu-id="d12fc-107">NULL 値が許容される構造化型には、3 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="d12fc-107">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="d12fc-108">行型。</span><span class="sxs-lookup"><span data-stu-id="d12fc-108">Row types.</span></span>  
  
- <span data-ttu-id="d12fc-109">複合型。</span><span class="sxs-lookup"><span data-stu-id="d12fc-109">Complex types.</span></span>  
  
- <span data-ttu-id="d12fc-110">エンティティ型。</span><span class="sxs-lookup"><span data-stu-id="d12fc-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="d12fc-111">構造化型の NULL インスタンスを生成するコード パターン</span><span class="sxs-lookup"><span data-stu-id="d12fc-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  

 <span data-ttu-id="d12fc-112">次のシナリオは、`null` インスタンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="d12fc-112">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="d12fc-113">構造化型としての `null` の構造化</span><span class="sxs-lookup"><span data-stu-id="d12fc-113">Shaping `null` as a structured type:</span></span>  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="d12fc-114">派生型に対する基本データ型のキャスト</span><span class="sxs-lookup"><span data-stu-id="d12fc-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="d12fc-115">false の条件での外部結合</span><span class="sxs-lookup"><span data-stu-id="d12fc-115">Outer join on false condition:</span></span>  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="d12fc-116">--または</span><span class="sxs-lookup"><span data-stu-id="d12fc-116">--or</span></span>  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="d12fc-117">--または</span><span class="sxs-lookup"><span data-stu-id="d12fc-117">--or</span></span>  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="d12fc-118">`null` 参照の逆参照</span><span class="sxs-lookup"><span data-stu-id="d12fc-118">Dereferencing a `null` reference:</span></span>  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="d12fc-119">空のコレクションからの ANYELEMENT の取得</span><span class="sxs-lookup"><span data-stu-id="d12fc-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="d12fc-120">構造化型の `null` インスタンスのチェック</span><span class="sxs-lookup"><span data-stu-id="d12fc-120">Checking for `null` instances of structured types:</span></span>  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d12fc-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d12fc-121">See also</span></span>

- [<span data-ttu-id="d12fc-122">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="d12fc-122">Entity SQL Overview</span></span>](entity-sql-overview.md)
