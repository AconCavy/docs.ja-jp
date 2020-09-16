---
title: '方法: カスタム永続参加要素を作成する'
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: d1d59f139b666790920eaabe032878dca1617b62
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557046"
---
# <a name="how-to-create-a-custom-persistence-participant"></a><span data-ttu-id="42561-102">方法: カスタム永続参加要素を作成する</span><span class="sxs-lookup"><span data-stu-id="42561-102">How to: Create a Custom Persistence Participant</span></span>
<span data-ttu-id="42561-103">次の手順では、永続参加要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="42561-103">The following procedure has steps to create a persistence participant.</span></span> <span data-ttu-id="42561-104">永続参加要素の実装例については、永続化のサンプルと[ストアの機能拡張](store-extensibility.md)[に](/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100))関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="42561-104">See the [Participating in Persistence](/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100)) sample and [Store Extensibility](store-extensibility.md) topic for sample implementations of persistence participants.</span></span>  
  
1. <span data-ttu-id="42561-105"><xref:System.Activities.Persistence.PersistenceParticipant> または <xref:System.Activities.Persistence.PersistenceIOParticipant> クラスから派生するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="42561-105">Create a class deriving from the <xref:System.Activities.Persistence.PersistenceParticipant> or the <xref:System.Activities.Persistence.PersistenceIOParticipant> class.</span></span> <span data-ttu-id="42561-106">PersistenceIOParticipant クラスは、i/o 操作に参加できるだけでなく、PersistenceParticipant クラスと同じ機能拡張ポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="42561-106">The PersistenceIOParticipant class offers the same extensibility points as the PersistenceParticipant class in addition to being able to participate in I/O operations.</span></span> <span data-ttu-id="42561-107">次のうち、必要な手順を行います。</span><span class="sxs-lookup"><span data-stu-id="42561-107">Follow one or more of the following steps.</span></span>  
  
2. <span data-ttu-id="42561-108"><xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="42561-108">Implement the <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> method.</span></span> <span data-ttu-id="42561-109">**Collectvalues**メソッドには、2つのディクショナリパラメーターがあります。1つは読み取り/書き込み値を格納するためのもので、もう1つは書き込み専用の値を格納するためのもので、後でクエリで使用します。</span><span class="sxs-lookup"><span data-stu-id="42561-109">The **CollectValues** method has two dictionary parameters, one for storing read/write values and the other one for storing write-only values (used later in queries).</span></span> <span data-ttu-id="42561-110">このメソッドでは、永続参加要素に固有のデータをこれらのディクショナリに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42561-110">In this method, you should populate these dictionaries with data that is specific to a persistence participant.</span></span> <span data-ttu-id="42561-111">各ディクショナリには、値の名前がキーとして格納されているほか、値そのものが <xref:System.Runtime.DurableInstancing.InstanceValue> オブジェクトとして格納されています。</span><span class="sxs-lookup"><span data-stu-id="42561-111">Each dictionary contains the name of the value as the key and the value itself as an <xref:System.Runtime.DurableInstancing.InstanceValue> object.</span></span>  
  
    <span data-ttu-id="42561-112">ReadWriteValues ディクショナリ内の値は、 **Instancevalue** オブジェクトとしてパッケージ化されます。</span><span class="sxs-lookup"><span data-stu-id="42561-112">The values in the readWriteValues dictionary are packaged as **InstanceValue** objects.</span></span> <span data-ttu-id="42561-113">書き込み専用辞書の値は、InstanceValueOptions を使用して **Instancevalue** オブジェクトとしてパッケージ化されます。省略可能で、InstanceValueOption. WriteOnly set です。</span><span class="sxs-lookup"><span data-stu-id="42561-113">The values in the write-only dictionary are packaged as **InstanceValue** objects with InstanceValueOptions.Optional and InstanceValueOption.WriteOnly set.</span></span> <span data-ttu-id="42561-114">すべての永続参加要素の**Collectvalues**実装によって提供される各**instancevalue**には、一意の名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="42561-114">Each **InstanceValue** provided by the **CollectValues** implementations across all persistence participants must have a unique name.</span></span>
  
    ```csharp  
    protected virtual void CollectValues(out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
3. <span data-ttu-id="42561-115"><xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="42561-115">Implement the <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> method.</span></span> <span data-ttu-id="42561-116">**Mapvalues**メソッドは、 **collectvalues**メソッドが受け取るパラメーターに似た2つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="42561-116">The **MapValues** method takes two parameters that are similar to the parameters that the **CollectValues** method receives.</span></span> <span data-ttu-id="42561-117">**Collectvalues**ステージで収集されたすべての値は、これらのディクショナリパラメーターを通じて渡されます。</span><span class="sxs-lookup"><span data-stu-id="42561-117">All the values collected in the **CollectValues** stage are passed through these dictionary parameters.</span></span> <span data-ttu-id="42561-118">**Mapvalues**ステージによって追加された新しい値は、書き込み専用の値に追加されます。</span><span class="sxs-lookup"><span data-stu-id="42561-118">The new values added by the **MapValues** stage are added to the write-only values.</span></span>  <span data-ttu-id="42561-119">書き込み専用のディクショナリが、インスタンスの値に直接関連付けられていない外部ソースにデータを提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="42561-119">The write-only dictionary is used to provide data to an external source not directly associated with the instance values.</span></span> <span data-ttu-id="42561-120">すべての永続参加要素で **Mapvalues** メソッドの実装によって提供される各値には、一意の名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="42561-120">Each value provided by implementations of the **MapValues** method across all persistence participants must have a unique name.</span></span>  
  
    ```csharp  
    protected virtual IDictionary<XName,Object> MapValues(IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
     <span data-ttu-id="42561-121"><xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> メソッドは <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> が提供しない機能を提供し、<xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> が処理しなかった別の永続参加により提供される、別の値への依存関係が許可されます。</span><span class="sxs-lookup"><span data-stu-id="42561-121">The <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> method provides functionality that <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> does not, in that it allows for a dependency on another value provided by another persistence participant that hasn’t been processed by <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> yet.</span></span>  
  
4. <span data-ttu-id="42561-122">**Publishvalues**メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="42561-122">Implement the **PublishValues** method.</span></span> <span data-ttu-id="42561-123">**Publishvalues**メソッドは、永続化ストアから読み込まれたすべての値を含むディクショナリを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="42561-123">The **PublishValues** method receives a dictionary containing all the values loaded from the persistence store.</span></span>  
  
    ```csharp  
    protected virtual void PublishValues(IDictionary<XName,Object> readWriteValues)
    {
    }
    ```  
  
5. <span data-ttu-id="42561-124">参加要素が永続 i/o 参加要素の場合は、 **Beginonsave** メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="42561-124">Implement the **BeginOnSave** method if the participant is a persistence I/O participant.</span></span> <span data-ttu-id="42561-125">このメソッドは保存操作中に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="42561-125">This method is called during a Save operation.</span></span> <span data-ttu-id="42561-126">この方法では、ワークフローインスタンスの永続化 (保存) を行うために i/o 補完を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42561-126">In this method, you should perform I/O adjunct to the persisting (saving) workflow instances.</span></span>  <span data-ttu-id="42561-127">ホストが、対応する永続化コマンドのトランザクションを使用している場合、同じトランザクションが Transaction.Current で確立されます。</span><span class="sxs-lookup"><span data-stu-id="42561-127">If the host is using a transaction for the corresponding persistence command, the same transaction is provided in Transaction.Current.</span></span>  <span data-ttu-id="42561-128">さらに、PersistenceIOParticipant はトランザクションの一貫性の要件を通知することがあります。この場合、ホストはほかに使用されなければ、永続化のトランザクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="42561-128">Additionally, PersistenceIOParticipants may advertise a transactional consistency requirement, in which case the host creates a transaction for the persistence episode if one would not otherwise be used.</span></span>  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnSave(IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```  
  
6. <span data-ttu-id="42561-129">参加要素が永続 i/o 参加要素の場合は、 **Beginonload** メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="42561-129">Implement the **BeginOnLoad** method if the participant is a persistence I/O participant.</span></span> <span data-ttu-id="42561-130">このメソッドは読み込み操作中に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="42561-130">This method is called during a Load operation.</span></span> <span data-ttu-id="42561-131">このメソッドでは、ワークフローインスタンスの読み込みに対して i/o 補完を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42561-131">In this method, you should perform I/O adjunct to the loading of workflow instances.</span></span> <span data-ttu-id="42561-132">ホストが、対応する永続化コマンドのトランザクションを使用している場合、同じトランザクションが Transaction.Current で確立されます。</span><span class="sxs-lookup"><span data-stu-id="42561-132">If the host is using a transaction for the corresponding persistence command, the same transaction is provided in Transaction.Current.</span></span> <span data-ttu-id="42561-133">さらに、永続化 i/o の参加者はトランザクションの一貫性の要件を提供する場合があります。その場合、ホストは永続化のためのトランザクションを作成します (これを使用しない場合)。</span><span class="sxs-lookup"><span data-stu-id="42561-133">Additionally, Persistence I/O participants may advertise a transactional consistency requirement, in which case the host creates a transaction for the persistence episode if one would not otherwise be used.</span></span>  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnLoad(IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```
