---
title: 識別子 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d58a5edd-7b5c-48e1-b5d7-a326ff426aa4
ms.openlocfilehash: 7e9b12ca351b021fab62988969cb98310cb55cc2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203697"
---
# <a name="identifiers-entity-sql"></a><span data-ttu-id="50a52-102">識別子 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="50a52-102">Identifiers (Entity SQL)</span></span>

<span data-ttu-id="50a52-103">識別子はクエリ式の別名、変数参照、オブジェクトのプロパティ、関数などを表すために [!INCLUDE[esql](../../../../../../includes/esql-md.md)] で使用されます。</span><span class="sxs-lookup"><span data-stu-id="50a52-103">Identifiers are used in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to represent query expression aliases, variable references, properties of objects, functions, and so on.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="50a52-104">の識別子には、単純な識別子と引用符で囲まれた識別子の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="50a52-104">provides two kinds of identifiers: simple identifiers and quoted identifiers.</span></span>  
  
## <a name="simple-identifiers"></a><span data-ttu-id="50a52-105">単純な識別子</span><span class="sxs-lookup"><span data-stu-id="50a52-105">Simple Identifiers</span></span>  

 <span data-ttu-id="50a52-106">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の単純な識別子は、英数字とアンダースコア文字のシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="50a52-106">A simple identifier in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is a sequence of alphanumeric and underscore characters.</span></span> <span data-ttu-id="50a52-107">識別子の最初の文字は英文字 (a ～ z または A ～ Z) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="50a52-107">The first character of the identifier must be an alphabetical character (a-z or A-Z).</span></span>  
  
## <a name="quoted-identifiers"></a><span data-ttu-id="50a52-108">引用符で囲まれた識別子</span><span class="sxs-lookup"><span data-stu-id="50a52-108">Quoted Identifiers</span></span>  

 <span data-ttu-id="50a52-109">引用符で囲まれた識別子とは、角かっこ ([]) で囲まれた文字のシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="50a52-109">A quoted identifier is any sequence of characters enclosed in square brackets ([]).</span></span> <span data-ttu-id="50a52-110">引用符で囲まれた識別子を使用すると、単純な識別子内では無効になる文字を使用して識別子を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="50a52-110">Quoted identifiers let you specify identifiers with characters that are not valid in identifiers.</span></span> <span data-ttu-id="50a52-111">角かっこ内のすべての文字 (すべての空白文字を含む) が識別子の一部になります。</span><span class="sxs-lookup"><span data-stu-id="50a52-111">All characters between the square brackets become part of the identifier, including all white space.</span></span>  
  
 <span data-ttu-id="50a52-112">ただし、次の文字を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="50a52-112">A quoted identifier cannot include the following characters:</span></span>  
  
- <span data-ttu-id="50a52-113">改行</span><span class="sxs-lookup"><span data-stu-id="50a52-113">Newline.</span></span>  
  
- <span data-ttu-id="50a52-114">キャリッジ リターン</span><span class="sxs-lookup"><span data-stu-id="50a52-114">Carriage returns.</span></span>  
  
- <span data-ttu-id="50a52-115">タブ</span><span class="sxs-lookup"><span data-stu-id="50a52-115">Tabs.</span></span>  
  
- <span data-ttu-id="50a52-116">バックスペース</span><span class="sxs-lookup"><span data-stu-id="50a52-116">Backspace.</span></span>  
  
- <span data-ttu-id="50a52-117">追加の角かっこ (識別子の境界を表す角かっこの中の角かっこ)</span><span class="sxs-lookup"><span data-stu-id="50a52-117">Additional square brackets (that is, square brackets within the square brackets that delineate the identifier).</span></span>  
  
 <span data-ttu-id="50a52-118">Unicode 文字を含めることはできます。</span><span class="sxs-lookup"><span data-stu-id="50a52-118">A quoted-identifier can include Unicode characters.</span></span>  
  
 <span data-ttu-id="50a52-119">引用符で囲まれた識別子を使用することにより、次の例のように、識別子では無効な文字を含むプロパティ名を作成できます。</span><span class="sxs-lookup"><span data-stu-id="50a52-119">Quoted identifiers enable you to create property name characters that are not valid in identifiers, as illustrated in the following example:</span></span>  
  
 `SELECT c.ContactName AS [Contact Name] FROM customers AS c`  
  
 <span data-ttu-id="50a52-120">また、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の予約済みキーワードを識別子として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="50a52-120">You can also use quoted identifiers to specify an identifier that is a reserved keyword of [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="50a52-121">たとえば、`Email` 型に "From" という名前のプロパティがある場合、次のように角かっこを使用することで、予約済みキーワードの FROM と区別できます。</span><span class="sxs-lookup"><span data-stu-id="50a52-121">For example, if the type `Email` has a property named "From", you can disambiguate it from the reserved keyword FROM by using square brackets, as follows:</span></span>  
  
 `SELECT e.[From] FROM emails AS e`  
  
 <span data-ttu-id="50a52-122">ドット (.) 演算子の右側に引用符で囲まれた識別子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="50a52-122">You can use a quoted identifier on the right side of a dot (.) operator.</span></span>  
  
 `SELECT t FROM ts as t WHERE t.[property] == 2`  
  
 <span data-ttu-id="50a52-123">識別子に角かっこを使用するには、角かっこをもう 1 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="50a52-123">To use the square bracket in an identifier, add an extra square bracket.</span></span> <span data-ttu-id="50a52-124">次の例では、"`abc]`" が識別子です。</span><span class="sxs-lookup"><span data-stu-id="50a52-124">In the following example "`abc]`" is the identifier:</span></span>  
  
 `SELECT t from ts as t WHERE t.[abc]]] == 2`  
  
 <span data-ttu-id="50a52-125">引用符で囲まれた識別子の比較セマンティクスについては、「[入力文字セット](input-character-set-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="50a52-125">For quoted identifier comparison semantics, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="aliasing-rules"></a><span data-ttu-id="50a52-126">別名の規則</span><span class="sxs-lookup"><span data-stu-id="50a52-126">Aliasing Rules</span></span>  

 <span data-ttu-id="50a52-127">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のクエリでは、次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] コンストラクトなど、必要な場合は常に別名を指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="50a52-127">We recommend specifying aliases in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries whenever needed, including the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs:</span></span>  
  
- <span data-ttu-id="50a52-128">行コンストラクターのフィールド</span><span class="sxs-lookup"><span data-stu-id="50a52-128">Fields of a row constructor.</span></span>  
  
- <span data-ttu-id="50a52-129">クエリ式の FROM 句の項目</span><span class="sxs-lookup"><span data-stu-id="50a52-129">Items in the FROM clause of a query expression.</span></span>  
  
- <span data-ttu-id="50a52-130">クエリ式の SELECT 句の項目</span><span class="sxs-lookup"><span data-stu-id="50a52-130">Items in the SELECT clause of a query expression.</span></span>  
  
- <span data-ttu-id="50a52-131">クエリ式の GROUP BY 句の項目</span><span class="sxs-lookup"><span data-stu-id="50a52-131">Items in the GROUP BY clause of a query expression.</span></span>  
  
### <a name="valid-aliases"></a><span data-ttu-id="50a52-132">有効な別名</span><span class="sxs-lookup"><span data-stu-id="50a52-132">Valid Aliases</span></span>  

 <span data-ttu-id="50a52-133">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] での有効な別名は、単純な識別子および引用符で囲まれた識別子です。</span><span class="sxs-lookup"><span data-stu-id="50a52-133">Valid aliases in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are any simple identifier or quoted identifier.</span></span>  
  
### <a name="alias-generation"></a><span data-ttu-id="50a52-134">別名の生成</span><span class="sxs-lookup"><span data-stu-id="50a52-134">Alias Generation</span></span>  

 <span data-ttu-id="50a52-135">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のクエリ式で別名が指定されていない場合、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では次の単純な規則に基づいて別名が生成されます。</span><span class="sxs-lookup"><span data-stu-id="50a52-135">If no alias is specified in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the following simple rules:</span></span>  
  
- <span data-ttu-id="50a52-136">クエリ式 (別名が指定されていないクエリ式) が単純な識別子または引用符で囲まれた識別子の場合は、その識別子が別名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="50a52-136">If the query expression (for which the alias is unspecified) is a simple or quoted identifier, that identifier is used as the alias.</span></span> <span data-ttu-id="50a52-137">たとえば、`ROW(a, [b])` が `ROW(a AS a, [b] AS [b])` になります。</span><span class="sxs-lookup"><span data-stu-id="50a52-137">For example, `ROW(a, [b])` becomes `ROW(a AS a, [b] AS [b])`.</span></span>  
  
- <span data-ttu-id="50a52-138">より複雑なクエリ式でも、最後の構成要素が単純な識別子であれば、その識別子が別名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="50a52-138">If the query expression is a more complex expression, but the last component of that query expression is a simple identifier, then that identifier is used as the alias.</span></span> <span data-ttu-id="50a52-139">たとえば、`ROW(a.a1, b.[b1])` が `ROW(a.a1 AS a1, b.[b1] AS [b1])` になります。</span><span class="sxs-lookup"><span data-stu-id="50a52-139">For example, `ROW(a.a1, b.[b1])` becomes `ROW(a.a1 AS a1, b.[b1] AS [b1])`.</span></span>  
  
 <span data-ttu-id="50a52-140">後に使用する別名に対しては暗黙的な別名を使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="50a52-140">We recommend that you do not use implicit aliasing if you want to use the alias name later.</span></span> <span data-ttu-id="50a52-141">別名 (暗黙的な別名または明示的な別名) が同じスコープで競合していたり繰り返し使用されていたりするとコンパイル エラーが発生しますが、</span><span class="sxs-lookup"><span data-stu-id="50a52-141">Anytime aliases (implicit or explicit) conflict or are repeated in the same scope, there will be a compile error.</span></span> <span data-ttu-id="50a52-142">暗黙的な別名は、同じ名前の明示的または暗黙的な別名があってもそのままコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="50a52-142">An implicit alias will pass compilation even if there is an explicit or implicit alias of the same name.</span></span>  
  
 <span data-ttu-id="50a52-143">暗黙的な別名は、ユーザー入力に基づいて自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="50a52-143">Implicit aliases are autogenerated based on user input.</span></span> <span data-ttu-id="50a52-144">たとえば次のコードでは、両方の列の別名として NAME が生成されるため、競合が発生します。</span><span class="sxs-lookup"><span data-stu-id="50a52-144">For example, the following line of code will generate NAME as an alias for both columns and therefore will conflict.</span></span>  
  
```sql  
SELECT product.NAME, person.NAME  
```  
  
 <span data-ttu-id="50a52-145">明示的な別名を使用している次のコードも同じように失敗しますが、</span><span class="sxs-lookup"><span data-stu-id="50a52-145">The following line of code, which uses explicit aliases, will also fail.</span></span> <span data-ttu-id="50a52-146">こちらの方がコードを見たときにエラーを発見しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="50a52-146">However, the failure will be more apparent by reading the code.</span></span>  
  
```sql  
SELECT 1 AS X, 2 AS X …  
```  
  
## <a name="scoping-rules"></a><span data-ttu-id="50a52-147">スコープの規則</span><span class="sxs-lookup"><span data-stu-id="50a52-147">Scoping Rules</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="50a52-148">ではスコープの規則が定義されています。これにより、クエリ言語で特定の変数をいつ参照できるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="50a52-148">defines scoping rules that determine when particular variables are visible in the query language.</span></span> <span data-ttu-id="50a52-149">一部の式やステートメントでは新しい名前が導入されます。</span><span class="sxs-lookup"><span data-stu-id="50a52-149">Some expressions or statements introduce new names.</span></span> <span data-ttu-id="50a52-150">スコープの規則は、そのような名前をどこで使用でき、いつ (どこで) 同じ名前の新しい宣言によって前の名前を参照できなくなるのかが決まります。</span><span class="sxs-lookup"><span data-stu-id="50a52-150">The scoping rules determine where those names can be used, and when or where a new declaration with the same name as another can hide its predecessor.</span></span>  
  
 <span data-ttu-id="50a52-151">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のクエリで名前を定義すると、それらはスコープの中で定義されたことになります。</span><span class="sxs-lookup"><span data-stu-id="50a52-151">When names are defined in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, they are said to be defined within a scope.</span></span> <span data-ttu-id="50a52-152">スコープはクエリの全領域をカバーします。</span><span class="sxs-lookup"><span data-stu-id="50a52-152">A scope covers an entire region of the query.</span></span> <span data-ttu-id="50a52-153">特定のスコープで定義されている名前は、そのスコープのすべての式や名前参照から参照できます。</span><span class="sxs-lookup"><span data-stu-id="50a52-153">All expressions or name references within a certain scope can see names that are defined within that scope.</span></span> <span data-ttu-id="50a52-154">スコープが始まる前や終わった後では、そのスコープで定義されている名前は参照できません。</span><span class="sxs-lookup"><span data-stu-id="50a52-154">Before a scope begins and after it ends, names that are defined within the scope cannot be referenced.</span></span>  
  
 <span data-ttu-id="50a52-155">スコープは入れ子にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="50a52-155">Scopes can be nested.</span></span> <span data-ttu-id="50a52-156">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の一部では、領域全体をカバーする新しいスコープが導入され、これらの領域には、やはりスコープが導入される他の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の式を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="50a52-156">Parts of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] introduce new scopes that cover entire regions, and these regions can contain other [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions that also introduce scopes.</span></span> <span data-ttu-id="50a52-157">スコープが入れ子になっている場合、最も内側のスコープに含まれている参照からは、そのスコープで定義されている名前を参照できるだけでなく、</span><span class="sxs-lookup"><span data-stu-id="50a52-157">When scopes are nested, references can be made to names that are defined in the innermost scope, which contains the reference.</span></span> <span data-ttu-id="50a52-158">それより外側のスコープで定義されている名前も参照できます。</span><span class="sxs-lookup"><span data-stu-id="50a52-158">References can also be made to any names that are defined in any outer scopes.</span></span> <span data-ttu-id="50a52-159">同じスコープ内で定義されている 2 つのスコープは兄弟スコープと見なされます。</span><span class="sxs-lookup"><span data-stu-id="50a52-159">Any two scopes defined within the same scope are considered sibling scopes.</span></span> <span data-ttu-id="50a52-160">兄弟スコープで定義されている名前を参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="50a52-160">References cannot be made to names that are defined within sibling scopes.</span></span>  
  
 <span data-ttu-id="50a52-161">内側のスコープで宣言した名前が外側のスコープで宣言されている名前と一致する場合、内側のスコープ内の参照や、そのスコープの中で宣言したスコープ内の参照は、その新しく宣言した名前のみを参照します。</span><span class="sxs-lookup"><span data-stu-id="50a52-161">If a name declared in an inner scope matches a name declared in an outer scope, references within the inner scope or within scopes declared within that scope refer only to the newly declared name.</span></span> <span data-ttu-id="50a52-162">外側のスコープの名前は参照できません。</span><span class="sxs-lookup"><span data-stu-id="50a52-162">The name in the outer scope is hidden.</span></span>  
  
 <span data-ttu-id="50a52-163">同じスコープの中であっても、まだ定義されていない名前を参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="50a52-163">Even within the same scope, names cannot be referenced before they are defined.</span></span>  
  
 <span data-ttu-id="50a52-164">グローバルな名前は実行環境の一部として存在することができます。</span><span class="sxs-lookup"><span data-stu-id="50a52-164">Global names can exist as part of the execution environment.</span></span> <span data-ttu-id="50a52-165">たとえば、永続的なコレクションや環境変数の名前がこれに含まれます。</span><span class="sxs-lookup"><span data-stu-id="50a52-165">This can include names of persistent collections or environment variables.</span></span> <span data-ttu-id="50a52-166">名前をグローバルにするには、最も外側のスコープで宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50a52-166">For a name to be global, it must be declared in the outermost scope.</span></span>  
  
 <span data-ttu-id="50a52-167">パラメーターはスコープに含まれません。</span><span class="sxs-lookup"><span data-stu-id="50a52-167">Parameters are not in a scope.</span></span> <span data-ttu-id="50a52-168">パラメーターの参照には特別な構文が含まれるため、パラメーターの名前がクエリ内の他の名前と衝突することはありません。</span><span class="sxs-lookup"><span data-stu-id="50a52-168">Because references to parameters include special syntax, names of parameters will never collide with other names in the query.</span></span>  
  
### <a name="query-expressions"></a><span data-ttu-id="50a52-169">クエリ式</span><span class="sxs-lookup"><span data-stu-id="50a52-169">Query Expressions</span></span>  

 <span data-ttu-id="50a52-170">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のクエリ式では、新しいスコープが導入されます。</span><span class="sxs-lookup"><span data-stu-id="50a52-170">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query expression introduces a new scope.</span></span> <span data-ttu-id="50a52-171">FROM 句で定義された名前は、出現順 (左から右の順) に from スコープに導入されます。</span><span class="sxs-lookup"><span data-stu-id="50a52-171">Names that are defined in the FROM clause are introduced into the from scope in order of appearance, left to right.</span></span> <span data-ttu-id="50a52-172">結合リストでは、既にリストで定義されている名前を式で参照できます。</span><span class="sxs-lookup"><span data-stu-id="50a52-172">In the join list, expressions can refer to names that were defined earlier in the list.</span></span> <span data-ttu-id="50a52-173">FROM 句で指定された要素のパブリック プロパティ (フィールドなど) は from スコープに追加されません。</span><span class="sxs-lookup"><span data-stu-id="50a52-173">Public properties (fields and so on) of elements identified in the FROM clause are not added to the from-scope.</span></span> <span data-ttu-id="50a52-174">それらは常に、別名で修飾された名前で参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50a52-174">They must be always referenced by the alias-qualified name.</span></span> <span data-ttu-id="50a52-175">通常は、SELECT 式のすべての部分が from スコープに含まれると見なされます。</span><span class="sxs-lookup"><span data-stu-id="50a52-175">Typically, all parts of the SELECT expression are considered within the from-scope.</span></span>  
  
 <span data-ttu-id="50a52-176">GROUP BY 句でも新しい兄弟スコープが形成されます。</span><span class="sxs-lookup"><span data-stu-id="50a52-176">The GROUP BY clause also introduces a new sibling scope.</span></span> <span data-ttu-id="50a52-177">各グループは、そのグループ内の要素のコレクションを参照するグループ名を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="50a52-177">Each group can have a group name that refers to the collection of elements in the group.</span></span> <span data-ttu-id="50a52-178">各グループ化式も、group スコープに新しい名前を導入します。</span><span class="sxs-lookup"><span data-stu-id="50a52-178">Each grouping expression will also introduce a new name into the group-scope.</span></span> <span data-ttu-id="50a52-179">さらに、入れ子集計 (名前付きグループ) もスコープに追加されます。</span><span class="sxs-lookup"><span data-stu-id="50a52-179">Additionally, the nest aggregate (or the named group) is also added to the scope.</span></span> <span data-ttu-id="50a52-180">グループ化式自体は from スコープに含まれますが、</span><span class="sxs-lookup"><span data-stu-id="50a52-180">The grouping expressions themselves are within the from-scope.</span></span> <span data-ttu-id="50a52-181">選択リスト (投影)、HAVING 句、および ORDER BY 句は、GROUP BY 句が使用されている場合には from スコープではなく group スコープに含まれると見なされます。</span><span class="sxs-lookup"><span data-stu-id="50a52-181">However, when a GROUP BY clause is used, the select-list (projection), HAVING clause, and ORDER BY clause are considered to be within the group-scope, and not the from-scope.</span></span> <span data-ttu-id="50a52-182">集計は、この後で説明するように特別扱いになります。</span><span class="sxs-lookup"><span data-stu-id="50a52-182">Aggregates receive special treatment, as described in the following bulleted list.</span></span>  
  
 <span data-ttu-id="50a52-183">スコープに関する追加の注意事項を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="50a52-183">The following are additional notes about scopes:</span></span>  
  
- <span data-ttu-id="50a52-184">選択リストでは、新しい名前が順番にスコープに導入されます。</span><span class="sxs-lookup"><span data-stu-id="50a52-184">The select-list can introduce new names into the scope, in order.</span></span> <span data-ttu-id="50a52-185">右側の投影式では、左側で投影されている名前を参照できます。</span><span class="sxs-lookup"><span data-stu-id="50a52-185">Projection expressions to the right might refer to names projected on the left.</span></span>  
  
- <span data-ttu-id="50a52-186">ORDER BY 句では、選択リストで指定されている名前 (別名) を参照できます。</span><span class="sxs-lookup"><span data-stu-id="50a52-186">The ORDER BY clause can refer to names (aliases) specified in the select list.</span></span>  
  
- <span data-ttu-id="50a52-187">SELECT 式内の句が評価される順序によって、名前がスコープに導入される順序が決まります。</span><span class="sxs-lookup"><span data-stu-id="50a52-187">The order of evaluation of clauses within the SELECT expression determines the order that names are introduced into the scope.</span></span> <span data-ttu-id="50a52-188">FROM 句が最初に評価され、WHERE 句、GROUP BY 句、HAVING 句、SELECT 句の順に続き、最後に ORDER BY 句が評価されます。</span><span class="sxs-lookup"><span data-stu-id="50a52-188">The FROM clause is evaluated first, followed by the WHERE clause, GROUP BY clause, HAVING clause, SELECT clause, and finally the ORDER BY clause.</span></span>  
  
### <a name="aggregate-handling"></a><span data-ttu-id="50a52-189">集計の処理</span><span class="sxs-lookup"><span data-stu-id="50a52-189">Aggregate Handling</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="50a52-190">では、コレクションベースの集計とグループベースの集計の 2 つの形式の集計がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="50a52-190">supports two forms of aggregates: collection-based aggregates and group-based aggregates.</span></span> <span data-ttu-id="50a52-191">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] ではコレクションベースの集計を使用することをお勧めします。グループベースの集計は、SQL との互換性のためにサポートされています。</span><span class="sxs-lookup"><span data-stu-id="50a52-191">Collection-based aggregates are the preferred construct in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], and group-based aggregates are supported for SQL compatibility.</span></span>  
  
 <span data-ttu-id="50a52-192">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、集計を解決するとき、まずコレクション ベースの集計として処理することが試みられます。</span><span class="sxs-lookup"><span data-stu-id="50a52-192">When resolving an aggregate, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] first tries to treat it as a collection-based aggregate.</span></span> <span data-ttu-id="50a52-193">それが失敗した場合、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、参照へのその集計入力が入れ子集計に変換されて、この新しい式の解決が試みられます。以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="50a52-193">If that fails, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] transforms the aggregate input into a reference to the nest aggregate and tries to resolve this new expression, as illustrated in the following example.</span></span>  
  
 `AVG(t.c) becomes AVG(group..(t.c))`  
  
## <a name="see-also"></a><span data-ttu-id="50a52-194">関連項目</span><span class="sxs-lookup"><span data-stu-id="50a52-194">See also</span></span>

- [<span data-ttu-id="50a52-195">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="50a52-195">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="50a52-196">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="50a52-196">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="50a52-197">入力文字セット</span><span class="sxs-lookup"><span data-stu-id="50a52-197">Input Character Set</span></span>](input-character-set-entity-sql.md)
