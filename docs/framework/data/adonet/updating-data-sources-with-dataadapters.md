---
title: DataAdapter によるデータ ソースの更新
description: DataAdapter の Update メソッドが、DataSet からの変更を ADO.NET アプリケーションのデータ ソースに反映させて解決する方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: e2348a3a89aa1c28856bfc21aaa25f2c8327aac7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286185"
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="36a72-103">DataAdapter によるデータ ソースの更新</span><span class="sxs-lookup"><span data-stu-id="36a72-103">Updating Data Sources with DataAdapters</span></span>

<span data-ttu-id="36a72-104">`Update` の <xref:System.Data.Common.DataAdapter> メソッドを呼び出して、変更を <xref:System.Data.DataSet> からデータ ソースに反映します。</span><span class="sxs-lookup"><span data-stu-id="36a72-104">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="36a72-105">`Update` メソッドは、`Fill` メソッドと同様に、引数として `DataSet` のインスタンスおよびオプションの <xref:System.Data.DataTable> オブジェクトまたは `DataTable` 名を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="36a72-105">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="36a72-106">`DataSet` のインスタンスは、行われた変更点を格納する `DataSet` です。`DataTable` は、変更点の取得元のテーブルです。</span><span class="sxs-lookup"><span data-stu-id="36a72-106">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="36a72-107">`DataTable` を指定しなかった場合、`DataTable` 内の最初の `DataSet` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="36a72-107">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>

<span data-ttu-id="36a72-108">`Update` メソッドを呼び出すと、`DataAdapter` は、既に加えられた変更を解析し、適切なコマンド (INSERT、UPDATE、または DELETE) を実行します。</span><span class="sxs-lookup"><span data-stu-id="36a72-108">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="36a72-109">`DataAdapter` は <xref:System.Data.DataRow> へ加えられた変更を検出すると、<xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>、<xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>、または <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> を使用してその変更を処理します。</span><span class="sxs-lookup"><span data-stu-id="36a72-109">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="36a72-110">その結果、デザイン時にコマンド構文を指定し、可能な場合はストアド プロシージャを使用することにより、ADO.NET アプリケーションのパフォーマンスを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="36a72-110">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="36a72-111">コマンドは `Update` を呼び出す前に明示的に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36a72-111">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="36a72-112">`Update` を呼び出し、その更新に関連する適切なコマンドが存在しない場合 (たとえば、削除済みの行に関連する `DeleteCommand` が存在しない場合) は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="36a72-112">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>

> [!NOTE]
> <span data-ttu-id="36a72-113">SQL Server のストアド プロシージャで、`DataAdapter` を使用してデータを編集または削除する場合、ストアド プロシージャの定義に SET NOCOUNT ON は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="36a72-113">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="36a72-114">処理された行数がゼロとして返され、`DataAdapter` によってコンカレンシーの競合として解釈されてしまいます。</span><span class="sxs-lookup"><span data-stu-id="36a72-114">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="36a72-115">この場合、<xref:System.Data.DBConcurrencyException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="36a72-115">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>

<span data-ttu-id="36a72-116">Command パラメーターを使用して、`DataSet` 内の各変更行に対する SQL ステートメントまたはストアド プロシージャに入力値と出力値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="36a72-116">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="36a72-117">詳しくは、「[DataAdapter パラメーター](dataadapter-parameters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="36a72-117">For more information, see [DataAdapter Parameters](dataadapter-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="36a72-118"><xref:System.Data.DataTable> の行を Delete することと、行を Remove することの違いを理解することが大切です。</span><span class="sxs-lookup"><span data-stu-id="36a72-118">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="36a72-119">`Remove` メソッドまたは `RemoveAt` メソッドを呼び出した場合、行は直ちに削除されます。</span><span class="sxs-lookup"><span data-stu-id="36a72-119">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="36a72-120">その後、`DataTable` または `DataSet` を `DataAdapter` に渡し、`Update` を呼び出しても、バックエンド データ ソースの対応する行には影響しません。</span><span class="sxs-lookup"><span data-stu-id="36a72-120">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="36a72-121">`Delete` メソッドを使用した場合、行はそのまま `DataTable` 内に維持され、削除対象としてマークされます。</span><span class="sxs-lookup"><span data-stu-id="36a72-121">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="36a72-122">その後、`DataTable` または `DataSet` を `DataAdapter` に渡し、`Update` を呼び出すと、バックエンド データ ソースから対応する行が削除されます。</span><span class="sxs-lookup"><span data-stu-id="36a72-122">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>

<span data-ttu-id="36a72-123">`DataTable` を単一データベース テーブルに割り当てたり、単一データベースから生成する場合は、<xref:System.Data.Common.DbCommandBuilder> オブジェクトを利用して自動的に `DeleteCommand` の `InsertCommand` オブジェクト、`UpdateCommand` オブジェクト、および `DataAdapter` オブジェクトを生成できます。</span><span class="sxs-lookup"><span data-stu-id="36a72-123">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="36a72-124">詳細については、「[CommandBuilder でのコマンドの生成](generating-commands-with-commandbuilders.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36a72-124">For more information, see [Generating Commands with CommandBuilders](generating-commands-with-commandbuilders.md).</span></span>

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="36a72-125">UpdatedRowSource を使用した値の DataSet への割り当て</span><span class="sxs-lookup"><span data-stu-id="36a72-125">Using UpdatedRowSource to Map Values to a DataSet</span></span>

<span data-ttu-id="36a72-126">`DataTable` オブジェクトの `DataAdapter` プロパティを使用すると、<xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> の Update メソッドを呼び出した後、データ ソースから返された値を <xref:System.Data.Common.DbCommand> に割り当てる方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="36a72-126">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="36a72-127">`UpdatedRowSource` プロパティを <xref:System.Data.UpdateRowSource> 列挙型の値の 1 つに設定することで、`DataAdapter` コマンドが返した出力パラメーターを無視するか、`DataSet` 内の変更行に適用するかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="36a72-127">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="36a72-128">最初に返された行 (存在する場合) を、`DataTable` 内の変更行に適用するかどうかを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="36a72-128">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>

<span data-ttu-id="36a72-129">`UpdateRowSource` 列挙型のさまざまの値と、それらの値が `DataAdapter` で使用されるコマンドの動作にどのように影響するかを次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="36a72-129">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>

|<span data-ttu-id="36a72-130">UpdatedRowSource 列挙型</span><span class="sxs-lookup"><span data-stu-id="36a72-130">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="36a72-131">説明</span><span class="sxs-lookup"><span data-stu-id="36a72-131">Description</span></span>|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="36a72-132">出力パラメーターと返された結果セットの最初の行を `DataSet` 内の変更行に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="36a72-132">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="36a72-133">返された結果セットの最初の行のデータだけを `DataSet` 内の変更行に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="36a72-133">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="36a72-134">出力パラメーターまたは返された結果セットの行が無視されます。</span><span class="sxs-lookup"><span data-stu-id="36a72-134">Any output parameters or rows of a returned result set are ignored.</span></span>|
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="36a72-135">出力パラメーターだけを `DataSet` 内の変更行に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="36a72-135">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|

<span data-ttu-id="36a72-136">`Update` メソッドは変更点を元のデータ ソースに反映させますが、`DataSet` に最後にデータを格納した後、他のクライアントがデータ ソースのデータを変更した可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="36a72-136">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="36a72-137">`DataSet` を現在のデータで更新するには、`DataAdapter` および `Fill` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="36a72-137">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="36a72-138">新しい行がテーブルに追加され、更新された情報が既存の行に取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="36a72-138">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="36a72-139">`Fill` メソッドは、`DataSet` の行と `SelectCommand` によって返された行の主キーの値を調べて、新しい行が追加されたか、または既存の行が更新されたかを判断します。</span><span class="sxs-lookup"><span data-stu-id="36a72-139">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="36a72-140">`Fill` メソッドは、`DataSet` によって返された結果の行に一致する主キーの値を持つ `SelectCommand` の行を見つけた場合、`SelectCommand` によって返された行の情報で既存の行を更新して、既存の行の <xref:System.Data.DataRow.RowState%2A> を `Unchanged` に設定します。</span><span class="sxs-lookup"><span data-stu-id="36a72-140">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="36a72-141">`SelectCommand` によって返された行の主キーの値が、`DataSet` のどの行の主キーの値にも一致しない場合、`Fill` メソッドは、`RowState` が `Unchanged` の新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="36a72-141">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>

> [!NOTE]
> <span data-ttu-id="36a72-142">`SelectCommand` が OUTER JOIN の結果を返す場合、`DataAdapter` は、生成される `PrimaryKey` に `DataTable` 値を設定しません。</span><span class="sxs-lookup"><span data-stu-id="36a72-142">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="36a72-143">自分で `PrimaryKey` を定義して、重複行が正しく反映されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="36a72-143">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="36a72-144">詳しくは、「[主キーの定義](./dataset-datatable-dataview/defining-primary-keys.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="36a72-144">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>

<span data-ttu-id="36a72-145">`Update` メソッド呼び出すときに発生する可能性がある例外を処理するには、行更新エラーが発生したときに `RowUpdated` イベントを使用して応答するか (「[DataAdapter のイベント処理](handling-dataadapter-events.md)」を参照)、または `Update` メソッドを呼び出す前に `DataAdapter.ContinueUpdateOnError` を `true` に設定し、更新が完了した時点で特定の行の `RowError` プロパティに格納されているエラー情報に応答します (「[行エラー情報](./dataset-datatable-dataview/row-error-information.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="36a72-145">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](./dataset-datatable-dataview/row-error-information.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="36a72-146">`DataSet`、`DataTable`、または `DataRow` に対して `AcceptChanges` を呼び出すと、`DataRow` に対するすべての `Original` の値が、`DataRow` に対する `Current` の値で上書きされます。</span><span class="sxs-lookup"><span data-stu-id="36a72-146">Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="36a72-147">行を一意に識別するフィールド値が変更された場合は、`AcceptChanges` 呼び出しの後に `Original` 値がデータ ソースの値と一致しなくなります。</span><span class="sxs-lookup"><span data-stu-id="36a72-147">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="36a72-148">`AcceptChanges` は、`DataAdapter` の Update メソッドを呼び出す間に、各行について自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="36a72-148">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="36a72-149">Update メソッドの呼び出し中に元の値を維持するには、まず `AcceptChangesDuringUpdate` の `DataAdapter` プロパティを false に設定するか、`RowUpdated` イベントのイベント ハンドラーを作成し、その <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> を <xref:System.Data.UpdateStatus.SkipCurrentRow> に設定します。</span><span class="sxs-lookup"><span data-stu-id="36a72-149">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="36a72-150">詳しくは、「[DataSet の内容のマージ](./dataset-datatable-dataview/merging-dataset-contents.md)」および「[DataAdapter のイベント処理](handling-dataadapter-events.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="36a72-150">For more information, see [Merging DataSet Contents](./dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="36a72-151">例</span><span class="sxs-lookup"><span data-stu-id="36a72-151">Example</span></span>

<span data-ttu-id="36a72-152">次の例では、`DataAdapter` の `UpdateCommand` を明示的に設定し、その `Update` メソッドを呼び出すことにより、変更済みの行に対して更新を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="36a72-152">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="36a72-153">UPDATE ステートメントの WHERE 句に指定したパラメーターが `Original` の `SourceColumn` 値を使用するように設定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="36a72-153">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="36a72-154">`Current` 値が既に変更されている可能性、そしてデータ ソースの値と一致していない可能性があるため、この設定は重要です。</span><span class="sxs-lookup"><span data-stu-id="36a72-154">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="36a72-155">`Original` 値は、データ ソースから `DataTable` にデータを取得するために使用された値です。</span><span class="sxs-lookup"><span data-stu-id="36a72-155">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a><span data-ttu-id="36a72-156">AutoIncrement 列</span><span class="sxs-lookup"><span data-stu-id="36a72-156">AutoIncrement Columns</span></span>

<span data-ttu-id="36a72-157">データ ソースから取得したテーブルに自動インクリメント列がある場合、自動インクリメント値をストアド プロシージャの出力パラメーターとして取得してそれをテーブルの列に割り当てるか、ストアド プロシージャまたは SQL ステートメントによって返された結果セットの最初の行の自動インクリメント値を取得するか、または `DataSet` の `RowUpdated` イベントを使用して追加の SELECT コマンドを実行することによって、`DataAdapter` の列に値を格納できます。</span><span class="sxs-lookup"><span data-stu-id="36a72-157">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="36a72-158">詳細と例については、「[ID 値および Autonumber 値の取得](retrieving-identity-or-autonumber-values.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="36a72-158">For more information and an example, see [Retrieving Identity or Autonumber Values](retrieving-identity-or-autonumber-values.md).</span></span>

## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="36a72-159">挿入、更新、削除の順序</span><span class="sxs-lookup"><span data-stu-id="36a72-159">Ordering of Inserts, Updates, and Deletes</span></span>

<span data-ttu-id="36a72-160">通常の条件下では、`DataSet` を使用して行う変更の順序をデータ ソースに送信することが重要です。</span><span class="sxs-lookup"><span data-stu-id="36a72-160">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="36a72-161">たとえば、既存の行の主キーの値を更新し、その新しい主キーの値を外部キーとして新しい行を追加する場合、更新は挿入の前に処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36a72-161">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>

<span data-ttu-id="36a72-162">`Select` の `DataTable` メソッドを使用すると、特定の `DataRow` を持つ行だけを参照する `RowState` 配列を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="36a72-162">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="36a72-163">その後で、返された `DataRow` 配列を `Update` の `DataAdapter` メソッドに渡して変更行を処理できます。</span><span class="sxs-lookup"><span data-stu-id="36a72-163">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="36a72-164">更新する行のサブセットを指定することで、挿入、更新、および削除の処理順序を制御できます。</span><span class="sxs-lookup"><span data-stu-id="36a72-164">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>

## <a name="example"></a><span data-ttu-id="36a72-165">例</span><span class="sxs-lookup"><span data-stu-id="36a72-165">Example</span></span>

<span data-ttu-id="36a72-166">たとえば次のコードでは、テーブルの削除行を最初に処理し、次に更新行、最後に挿入行を処理します。</span><span class="sxs-lookup"><span data-stu-id="36a72-166">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>

```vb
Dim table As DataTable = dataSet.Tables("Customers")

' First process deletes.
dataSet.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Deleted))

' Next process updates.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.ModifiedCurrent))

' Finally, process inserts.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Added))
```

```csharp
DataTable table = dataSet.Tables["Customers"];

// First process deletes.
adapter.Update(table.Select(null, null, DataViewRowState.Deleted));

// Next process updates.
adapter.Update(table.Select(null, null,
  DataViewRowState.ModifiedCurrent));

// Finally, process inserts.
adapter.Update(table.Select(null, null, DataViewRowState.Added));
```

## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="36a72-167">DataAdapter を使用したデータの取得と更新</span><span class="sxs-lookup"><span data-stu-id="36a72-167">Use a DataAdapter to Retrieve and Update Data</span></span>

<span data-ttu-id="36a72-168">DataAdapter を使用すると、データを取得および更新できます。</span><span class="sxs-lookup"><span data-stu-id="36a72-168">You can use a DataAdapter to retrieve and update the data.</span></span>

- <span data-ttu-id="36a72-169">このサンプルでは、DataAdapter.AcceptChangesDuringFill を使用してデータベース内のデータを複製します。</span><span class="sxs-lookup"><span data-stu-id="36a72-169">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="36a72-170">このプロパティが false として設定されている場合、AcceptChanges はテーブルにデータを格納するときに呼び出されず、新しく追加された行が挿入された行として処理されます。</span><span class="sxs-lookup"><span data-stu-id="36a72-170">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="36a72-171">そのため、このサンプルでは、これらの行を使用して、データベースに新しい行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="36a72-171">So, the sample uses these rows to insert the new rows into the database.</span></span>

- <span data-ttu-id="36a72-172">このサンプルでは、DataAdapter.TableMappings を使用して、ソース テーブルと DataTable 間のマッピングを定義します。</span><span class="sxs-lookup"><span data-stu-id="36a72-172">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>

- <span data-ttu-id="36a72-173">このサンプルでは、DataAdapter.FillLoadOption を使用して、アダプターが DbDataReader から DataTable にデータを設定する方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="36a72-173">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="36a72-174">DataTable を作成するときに、プロパティを LoadOption.Upsert または LoadOption.PreserveChanges として設定した場合のみ、データベースのデータを現在のバージョンまたは元のバージョンに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="36a72-174">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>

- <span data-ttu-id="36a72-175">このサンプルでは、DbDataAdapter.UpdateBatchSize を使用してバッチ操作を実行することにより、テーブルを更新します。</span><span class="sxs-lookup"><span data-stu-id="36a72-175">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>

<span data-ttu-id="36a72-176">サンプルをコンパイルして実行する前に、サンプル データベースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36a72-176">Before you compile and run the sample, you need to create the sample database:</span></span>

```sql
USE [master]
GO

CREATE DATABASE [MySchool]

GO

USE [MySchool]
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,
[Year] [smallint] NOT NULL,
[Title] [nvarchar](100) NOT NULL,
[Credits] [int] NOT NULL,
[DepartmentID] [int] NOT NULL,
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED
(
[CourseID] ASC,
[Year] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,
[Name] [nvarchar](50) NOT NULL,
[Budget] [money] NOT NULL,
[StartDate] [datetime] NOT NULL,
[Administrator] [int] NULL,
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED
(
[DepartmentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)

SET IDENTITY_INSERT [dbo].[Department] ON

INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)
SET IDENTITY_INSERT [dbo].[Department] OFF

ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])
REFERENCES [dbo].[Department] ([DepartmentID])
GO
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]
GO
```

<span data-ttu-id="36a72-177">このコード サンプルを含む C# プロジェクトと Visual Basic プロジェクトは、[開発者コード サンプル](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D)のページにあります。</span><span class="sxs-lookup"><span data-stu-id="36a72-177">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.SqlClient;
using System.Linq;
using CSDataAdapterOperations.Properties;

namespace CSDataAdapterOperations.Properties {
   internal sealed partial class Settings : global::System.Configuration.ApplicationSettingsBase {

      private static Settings defaultInstance = ((Settings)(global::System.Configuration.ApplicationSettingsBase.Synchronized(new Settings())));

      public static Settings Default {
         get {
            return defaultInstance;
         }
      }

      [global::System.Configuration.ApplicationScopedSettingAttribute()]
      [global::System.Configuration.DefaultSettingValueAttribute("Data Source=(local);Initial Catalog=MySchool;Integrated Security=True")]
      public string MySchoolConnectionString {
         get {
            return ((string)(this["MySchoolConnectionString"]));
         }
      }
   }
}

class Program {
   static void Main(string[] args) {
      Settings settings = new Settings();

      // Copy the data from the database.  Get the table Department and Course from the database.
      String selectString = @"SELECT [DepartmentID],[Name],[Budget],[StartDate],[Administrator]
                                     FROM [MySchool].[dbo].[Department];

                                   SELECT [CourseID],@Year as [Year],Max([Title]) as [Title],
                                   Max([Credits]) as [Credits],Max([DepartmentID]) as [DepartmentID]
                                   FROM [MySchool].[dbo].[Course]
                                   Group by [CourseID]";

      DataSet mySchool = new DataSet();

      SqlCommand selectCommand = new SqlCommand(selectString);
      SqlParameter parameter = selectCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2);
      parameter.Value = new Random(DateTime.Now.Millisecond).Next(9999);

      // Use DataTableMapping to map the source tables and the destination tables.
      DataTableMapping[] tableMappings = {new DataTableMapping("Table", "Department"), new DataTableMapping("Table1", "Course")};
      CopyData(mySchool, settings.MySchoolConnectionString, selectCommand, tableMappings);

      Console.WriteLine("The following tables are from the database.");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      // Roll back the changes
      DataTable department = mySchool.Tables["Department"];
      DataTable course = mySchool.Tables["Course"];

      department.Rows[0]["Name"] = "New" + department.Rows[0][1];
      course.Rows[0]["Title"] = "New" + course.Rows[0]["Title"];
      course.Rows[0]["Credits"] = 10;

      Console.WriteLine("After we changed the tables:");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      department.RejectChanges();
      Console.WriteLine("After use the RejectChanges method in Department table to roll back the changes:");
      ShowDataTable(department);

      DataColumn[] primaryColumns = { course.Columns["CourseID"] };
      DataColumn[] resetColumns = { course.Columns["Title"] };
      ResetCourse(course, settings.MySchoolConnectionString, primaryColumns, resetColumns);
      Console.WriteLine("After use the ResetCourse method in Course table to roll back the changes:");
      ShowDataTable(course);

      // Batch update the table.
      String insertString = @"Insert into [MySchool].[dbo].[Course]([CourseID],[Year],[Title],
                                   [Credits],[DepartmentID])
             values (@CourseID,@Year,@Title,@Credits,@DepartmentID)";
      SqlCommand insertCommand = new SqlCommand(insertString);
      insertCommand.Parameters.Add("@CourseID", SqlDbType.NVarChar, 10, "CourseID");
      insertCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2, "Year");
      insertCommand.Parameters.Add("@Title", SqlDbType.NVarChar, 100, "Title");
      insertCommand.Parameters.Add("@Credits", SqlDbType.Int, 4, "Credits");
      insertCommand.Parameters.Add("@DepartmentID", SqlDbType.Int, 4, "DepartmentID");

      const Int32 batchSize = 10;
      BatchInsertUpdate(course, settings.MySchoolConnectionString, insertCommand, batchSize);
   }

   private static void CopyData(DataSet dataSet, String connectionString, SqlCommand selectCommand, DataTableMapping[] tableMappings) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {adapter.TableMappings.AddRange(tableMappings);
            // If set the AcceptChangesDuringFill as the false, AcceptChanges will not be called on a
            // DataRow after it is added to the DataTable during any of the Fill operations.
            adapter.AcceptChangesDuringFill = false;

            adapter.Fill(dataSet);
         }
      }
   }

   // Roll back only one column or several columns data of the Course table by call ResetDataTable method.
   private static void ResetCourse(DataTable table, String connectionString,
       DataColumn[] primaryColumns, DataColumn[] resetColumns) {
      table.PrimaryKey = primaryColumns;

      // Build the query string
      String primaryCols = String.Join(",", primaryColumns.Select(col => col.ColumnName));
      String resetCols = String.Join(",", resetColumns.Select(col => $"Max({col.ColumnName}) as {col.ColumnName}"));

      String selectString = $"Select {primaryCols},{resetCols} from Course Group by {primaryCols}");

      SqlCommand selectCommand = new SqlCommand(selectString);

      ResetDataTable(table, connectionString, selectCommand);
   }

   // RejectChanges will roll back all changes made to the table since it was loaded, or the last time AcceptChanges
   // was called. When you copy from the database, you can lose all the data after calling RejectChanges
   // The ResetDataTable method rolls back one or more columns of data.
   private static void ResetDataTable(DataTable table, String connectionString,
       SqlCommand selectCommand) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {
            // The incoming values for this row will be written to the current version of each
            // column. The original version of each column's data will not be changed.
            adapter.FillLoadOption = LoadOption.Upsert;

            adapter.Fill(table);
         }
      }
   }

   private static void BatchInsertUpdate(DataTable table, String connectionString,
       SqlCommand insertCommand, Int32 batchSize) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         insertCommand.Connection = connection;
         // When setting UpdateBatchSize to a value other than 1, all the commands
         // associated with the SqlDataAdapter have to have their UpdatedRowSource
         // property set to None or OutputParameters. An exception is thrown otherwise.
         insertCommand.UpdatedRowSource = UpdateRowSource.None;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter()) {
            adapter.InsertCommand = insertCommand;
            // Gets or sets the number of rows that are processed in each round-trip to the server.
            // Setting it to 1 disables batch updates, as rows are sent one at a time.
            adapter.UpdateBatchSize = batchSize;

            adapter.Update(table);

            Console.WriteLine("Successfully to update the table.");
         }
      }
   }

   private static void ShowDataTable(DataTable table) {
      foreach (DataColumn col in table.Columns) {
         Console.Write("{0,-14}", col.ColumnName);
      }
      Console.WriteLine("{0,-14}", "RowState");

      foreach (DataRow row in table.Rows) {
         foreach (DataColumn col in table.Columns) {
            if (col.DataType.Equals(typeof(DateTime)))
               Console.Write("{0,-14:d}", row[col]);
            else if (col.DataType.Equals(typeof(Decimal)))
               Console.Write("{0,-14:C}", row[col]);
            else
               Console.Write("{0,-14}", row[col]);
         }
         Console.WriteLine("{0,-14}", row.RowState);
      }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="36a72-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="36a72-178">See also</span></span>

- [<span data-ttu-id="36a72-179">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="36a72-179">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="36a72-180">行の状態とバージョン</span><span class="sxs-lookup"><span data-stu-id="36a72-180">Row States and Row Versions</span></span>](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [<span data-ttu-id="36a72-181">AcceptChange と RejectChange</span><span class="sxs-lookup"><span data-stu-id="36a72-181">AcceptChanges and RejectChanges</span></span>](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [<span data-ttu-id="36a72-182">DataSet の内容のマージ</span><span class="sxs-lookup"><span data-stu-id="36a72-182">Merging DataSet Contents</span></span>](./dataset-datatable-dataview/merging-dataset-contents.md)
- [<span data-ttu-id="36a72-183">ID 値および Autonumber 値の取得</span><span class="sxs-lookup"><span data-stu-id="36a72-183">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)
- [<span data-ttu-id="36a72-184">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="36a72-184">ADO.NET Overview</span></span>](ado-net-overview.md)
