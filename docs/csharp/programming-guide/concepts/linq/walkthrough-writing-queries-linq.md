---
title: 'チュートリアル: C# でのクエリの作成 (LINQ)'
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: f2135c6c3649ba2fc87e3b49770439688a58269b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418051"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="c7403-102">チュートリアル: C# でのクエリの作成 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c7403-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="c7403-103">このチュートリアルでは、LINQ クエリ式の記述に使用される C# 言語機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="c7403-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="c7403-104">C# プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="c7403-104">Create a C# Project</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7403-105">以下に示すのは Visual Studio 用の手順です。</span><span class="sxs-lookup"><span data-stu-id="c7403-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="c7403-106">別の開発環境を使用している場合は、System.Core.dll への参照と <xref:System.Linq?displayProperty=nameWithType> 名前空間の `using` ディレクティブを使用したコンソール プロジェクトを作成してください。</span><span class="sxs-lookup"><span data-stu-id="c7403-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="c7403-107">Visual Studio でプロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="c7403-107">To create a project in Visual Studio</span></span>  
  
1. <span data-ttu-id="c7403-108">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="c7403-108">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="c7403-109">メニュー バーで、 **[ファイル]** 、 **[新規作成]** 、 **[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7403-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="c7403-110">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c7403-110">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="c7403-111">**[インストール済み]** 、 **[テンプレート]** 、 **[Visual C#]** の順に展開し、 **[コンソール アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c7403-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4. <span data-ttu-id="c7403-112">**[名前]** テキスト ボックスで、別の名前を入力するか、既定の名前をそのまま使用し、 **[OK]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="c7403-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="c7403-113">**ソリューション エクスプローラー**に新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c7403-113">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="c7403-114">プロジェクトには、System.Core.dll への参照と、<xref:System.Linq?displayProperty=nameWithType> 名前空間の `using` ディレクティブが使用されています。</span><span class="sxs-lookup"><span data-stu-id="c7403-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="c7403-115">メモリ内データ ソースの作成</span><span class="sxs-lookup"><span data-stu-id="c7403-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="c7403-116">クエリのデータ ソースは、`Student` オブジェクトのシンプルなリストです。</span><span class="sxs-lookup"><span data-stu-id="c7403-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="c7403-117">各 `Student` レコードには、名前、姓、およびクラスでのテストの点数を表す整数の配列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c7403-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="c7403-118">このコードをプロジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="c7403-118">Copy this code into your project.</span></span> <span data-ttu-id="c7403-119">これには、次のような特徴があります。</span><span class="sxs-lookup"><span data-stu-id="c7403-119">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="c7403-120">`Student` クラスは自動実装プロパティで構成されています。</span><span class="sxs-lookup"><span data-stu-id="c7403-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
- <span data-ttu-id="c7403-121">リスト内の各生徒は、オブジェクト初期化子で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="c7403-121">Each student in the list is initialized with an object initializer.</span></span>  
  
- <span data-ttu-id="c7403-122">リスト自体は、コレクション初期化子で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="c7403-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="c7403-123">この全体的なデータ構造は、コンストラクターへの明示的な呼び出しや、明示的なメンバー アクセスを行うことなく初期化され、インスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="c7403-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="c7403-124">これらの新機能について詳しくは、「[自動実装プロパティ](../../classes-and-structs/auto-implemented-properties.md)」および「[オブジェクト初期化子とコレクション初期化子](../../classes-and-structs/object-and-collection-initializers.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c7403-124">For more information about these new features, see [Auto-Implemented Properties](../../classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="c7403-125">データ ソースを追加するには</span><span class="sxs-lookup"><span data-stu-id="c7403-125">To add the data source</span></span>  
  
- <span data-ttu-id="c7403-126">`Student` クラスと、初期化された生徒リストを、プロジェクト内の `Program` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="c7403-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="c7403-127">生徒リストに新しい生徒を追加するには</span><span class="sxs-lookup"><span data-stu-id="c7403-127">To add a new Student to the Students list</span></span>  
  
1. <span data-ttu-id="c7403-128">新しい `Student` を `Students` リストに追加し、目的の名前とテスト点数を使用します。</span><span class="sxs-lookup"><span data-stu-id="c7403-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="c7403-129">オブジェクト初期化子の構文をより効果的に学習するために、新しい生徒の情報をすべて入力するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="c7403-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="c7403-130">クエリの作成</span><span class="sxs-lookup"><span data-stu-id="c7403-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="c7403-131">簡単なクエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="c7403-131">To create a simple query</span></span>  
  
- <span data-ttu-id="c7403-132">アプリケーションの `Main` メソッドで、シンプルなクエリを作成します。このクエリでは、実行時に、最初のテストの点数が 90 を超える全生徒のリストを生成するようにします。</span><span class="sxs-lookup"><span data-stu-id="c7403-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="c7403-133">`Student` オブジェクト全体が選択されているため、クエリの型は `IEnumerable<Student>` です。</span><span class="sxs-lookup"><span data-stu-id="c7403-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="c7403-134">コードでは、[var](../../../language-reference/keywords/var.md) キーワードを使用して暗黙的型指定を使用することもできますが、結果を明確に示すために、明示的型指定を使用します。</span><span class="sxs-lookup"><span data-stu-id="c7403-134">Although the code could also use implicit typing by using the [var](../../../language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="c7403-135">(`var` について詳しくは、「[暗黙的に型指定されたローカル変数](../../classes-and-structs/implicitly-typed-local-variables.md)」をご覧ください。)</span><span class="sxs-lookup"><span data-stu-id="c7403-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="c7403-136">なお、クエリの範囲変数 (`student`) は、ソース内の各 `Student` への参照として機能し、各オブジェクトのメンバー アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="c7403-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="c7403-137">クエリの実行</span><span class="sxs-lookup"><span data-stu-id="c7403-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="c7403-138">クエリを実行するには</span><span class="sxs-lookup"><span data-stu-id="c7403-138">To execute the query</span></span>  
  
1. <span data-ttu-id="c7403-139">クエリを実行する `foreach` ループを記述します。</span><span class="sxs-lookup"><span data-stu-id="c7403-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="c7403-140">コードについては、以下の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c7403-140">Note the following about the code:</span></span>  
  
    - <span data-ttu-id="c7403-141">返されたシーケンス内の各要素は、`foreach` ループ内の反復変数を通じてアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="c7403-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    - <span data-ttu-id="c7403-142">この変数の型は `Student` で、クエリ変数の型は互換性があります (`IEnumerable<Student>`)。</span><span class="sxs-lookup"><span data-stu-id="c7403-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2. <span data-ttu-id="c7403-143">このコードを追加したら、アプリケーションをビルドして実行し、 **[コンソール]** ウィンドウで結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="c7403-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="c7403-144">別のフィルター条件を追加するには</span><span class="sxs-lookup"><span data-stu-id="c7403-144">To add another filter condition</span></span>  
  
1. <span data-ttu-id="c7403-145">クエリを改良するために、`where` 句で複数のブール条件を結合することができます。</span><span class="sxs-lookup"><span data-stu-id="c7403-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="c7403-146">次のコードでは、最初の点数が 90 より高く、最後の点数が 80 未満の生徒が返されるようにするための条件を追加しています。</span><span class="sxs-lookup"><span data-stu-id="c7403-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="c7403-147">`where` 句は次のコードのようになります。</span><span class="sxs-lookup"><span data-stu-id="c7403-147">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="c7403-148">詳しくは、「[where 句](../../../language-reference/keywords/where-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c7403-148">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="c7403-149">クエリの変更</span><span class="sxs-lookup"><span data-stu-id="c7403-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="c7403-150">結果を並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="c7403-150">To order the results</span></span>  
  
1. <span data-ttu-id="c7403-151">クエリの結果は、一定の基準で順序付けしたほうが見やすくなります。</span><span class="sxs-lookup"><span data-stu-id="c7403-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="c7403-152">返されたシーケンスは、ソース要素内のアクセス可能なフィールドによって順序付けすることができます。</span><span class="sxs-lookup"><span data-stu-id="c7403-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="c7403-153">たとえば、次の `orderby` 句では、各生徒の名前を基準にして、A から Z へのアルファベット順で結果を並べるようにしています。</span><span class="sxs-lookup"><span data-stu-id="c7403-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="c7403-154">次の `orderby` 句をクエリに追加します (`where` ステートメントの直後、`select` ステートメントの前)。</span><span class="sxs-lookup"><span data-stu-id="c7403-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. <span data-ttu-id="c7403-155">`orderby` 句を変更し、最初のテストの点数を基準にして、結果を逆順 (最高点から最低点) で並べるようにします。</span><span class="sxs-lookup"><span data-stu-id="c7403-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. <span data-ttu-id="c7403-156">`WriteLine` 書式文字列を変更して、点数を表示できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c7403-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="c7403-157">詳しくは、「[orderby 句](../../../language-reference/keywords/orderby-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c7403-157">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="c7403-158">結果をグループ化するには</span><span class="sxs-lookup"><span data-stu-id="c7403-158">To group the results</span></span>  
  
1. <span data-ttu-id="c7403-159">グループ化は、クエリ式の強力な機能です。</span><span class="sxs-lookup"><span data-stu-id="c7403-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="c7403-160">グループ句を使用したクエリでは、グループのシーケンスが生成され、各グループ自体に、`Key` と、そのグループの全メンバーで構成されたシーケンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c7403-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="c7403-161">次の新しいクエリでは、生徒の姓の頭文字をキーに使用して、生徒をグループ化しています。</span><span class="sxs-lookup"><span data-stu-id="c7403-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. <span data-ttu-id="c7403-162">クエリの型が変更されたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c7403-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="c7403-163">`char` 型をキーに持つグループのシーケンスと、`Student` オブジェクトのシーケンスが生成されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c7403-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="c7403-164">クエリの型が変更されたため、次のコードでは `foreach` 実行ループも変更されています。</span><span class="sxs-lookup"><span data-stu-id="c7403-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. <span data-ttu-id="c7403-165">アプリケーションを実行し、 **[コンソール]** ウィンドウで結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="c7403-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="c7403-166">詳しくは、「[group 句](../../../language-reference/keywords/group-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c7403-166">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="c7403-167">変数を暗黙的に型指定するには</span><span class="sxs-lookup"><span data-stu-id="c7403-167">To make the variables implicitly typed</span></span>  
  
1. <span data-ttu-id="c7403-168">`IGroupings` の `IEnumerables` を明示的にコーディングするのは非常に面倒です。</span><span class="sxs-lookup"><span data-stu-id="c7403-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="c7403-169">`var` を使用すれば、同じクエリや `foreach` ループをはるかに効率的に記述できます。</span><span class="sxs-lookup"><span data-stu-id="c7403-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="c7403-170">`var` キーワードは、オブジェクトの型を変更しません。型を推論するようにコンパイラに指示するだけです。</span><span class="sxs-lookup"><span data-stu-id="c7403-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="c7403-171">`studentQuery` の型と反復変数 `group` を `var` に変更し、クエリを再実行します。</span><span class="sxs-lookup"><span data-stu-id="c7403-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="c7403-172">内部の `foreach` ループで、反復変数の型は `Student` のままになっており、クエリは以前と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="c7403-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="c7403-173">反復変数 `s` を `var` に変更し、クエリを再実行します。</span><span class="sxs-lookup"><span data-stu-id="c7403-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="c7403-174">まったく同じ結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="c7403-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="c7403-175">[var](../../../language-reference/keywords/var.md) について詳しくは、「[暗黙的に型指定されたローカル変数](../../classes-and-structs/implicitly-typed-local-variables.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c7403-175">For more information about [var](../../../language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="c7403-176">グループをキー値で順序付けるには</span><span class="sxs-lookup"><span data-stu-id="c7403-176">To order the groups by their key value</span></span>  
  
1. <span data-ttu-id="c7403-177">前のクエリを実行すると、グループはアルファベット順になりません。</span><span class="sxs-lookup"><span data-stu-id="c7403-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="c7403-178">これを変えるには、`group` 句の後に `orderby` 句を記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7403-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="c7403-179">しかし `orderby` 句を使用するには、まず、`group` 句によって作成されたグループへの参照として機能する識別子が必要になります。</span><span class="sxs-lookup"><span data-stu-id="c7403-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="c7403-180">この識別子は、次のように `into` キーワード使用して記述します。</span><span class="sxs-lookup"><span data-stu-id="c7403-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="c7403-181">このクエリを実行すると、グループがアルファベット順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="c7403-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="c7403-182">let を使用して識別子を導入するには</span><span class="sxs-lookup"><span data-stu-id="c7403-182">To introduce an identifier by using let</span></span>  
  
1. <span data-ttu-id="c7403-183">`let` キーワードを使用すると、任意の式の結果の識別子をクエリ式に導入できます。</span><span class="sxs-lookup"><span data-stu-id="c7403-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="c7403-184">この識別子は、次の例のように便利に使用できます。式の結果を格納することで、何度も計算を行う必要がなくなり、パフォーマンスの向上につながります。</span><span class="sxs-lookup"><span data-stu-id="c7403-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="c7403-185">詳しくは、「[let 句](../../../language-reference/keywords/let-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c7403-185">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="c7403-186">クエリ式でメソッド構文を使用するには</span><span class="sxs-lookup"><span data-stu-id="c7403-186">To use method syntax in a query expression</span></span>  
  
1. <span data-ttu-id="c7403-187">「[LINQ でのクエリ構文とメソッド構文](./query-syntax-and-method-syntax-in-linq.md)」で説明したように、一部のクエリ操作は、メソッド構文を使用することでのみ表現できます。</span><span class="sxs-lookup"><span data-stu-id="c7403-187">As described in [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="c7403-188">次のコードは、ソース シーケンス内の各 `Student` の合計点数を計算し、そのクエリの結果に対して `Average()` メソッドを呼び出して、クラスの平均点数を計算します。</span><span class="sxs-lookup"><span data-stu-id="c7403-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="c7403-189">select 句で変換またはプロジェクトを実行するには</span><span class="sxs-lookup"><span data-stu-id="c7403-189">To transform or project in the select clause</span></span>  
  
1. <span data-ttu-id="c7403-190">クエリでは、ソース シーケンス内の要素とは異なる要素のシーケンスを生成することがよくあります。</span><span class="sxs-lookup"><span data-stu-id="c7403-190">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="c7403-191">前のクエリと実行ループを削除またはコメント アウトして、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c7403-191">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="c7403-192">クエリが (`Students` ではなく) 文字列のシーケンスを返すことに注意してください。このことは、`foreach` ループに反映されます。</span><span class="sxs-lookup"><span data-stu-id="c7403-192">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. <span data-ttu-id="c7403-193">このチュートリアルの前のコードでは、クラスの平均点が約 334 と示されました。</span><span class="sxs-lookup"><span data-stu-id="c7403-193">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="c7403-194">合計点がクラス平均よりも高い `Students` のシーケンスを (生徒の `Student ID` と共に) 生成するには、`select` ステートメントで匿名型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c7403-194">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="c7403-195">次の手順</span><span class="sxs-lookup"><span data-stu-id="c7403-195">Next Steps</span></span>  
 <span data-ttu-id="c7403-196">C# でのクエリ操作の基本が理解できたら、興味がある種類の LINQ プロバイダーについて、ドキュメントやサンプルを読んでみましょう。</span><span class="sxs-lookup"><span data-stu-id="c7403-196">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="c7403-197">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c7403-197">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="c7403-198">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="c7403-198">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="c7403-199">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c7403-199">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)  
  
 [<span data-ttu-id="c7403-200">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="c7403-200">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="c7403-201">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7403-201">See also</span></span>

- [<span data-ttu-id="c7403-202">統合言語クエリ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c7403-202">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="c7403-203">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="c7403-203">LINQ Query Expressions</span></span>](../../../linq/index.md)
