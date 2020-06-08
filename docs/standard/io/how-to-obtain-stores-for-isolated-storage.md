---
title: '方法 : 分離ストレージでストアを取得する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
ms.openlocfilehash: a08563b67239c679e3bc88876781508fd78bea75
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291839"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a><span data-ttu-id="b0de5-102">方法 : 分離ストレージでストアを取得する</span><span class="sxs-lookup"><span data-stu-id="b0de5-102">How to: Obtain Stores for Isolated Storage</span></span>
<span data-ttu-id="b0de5-103">分離ストアでは、データ コンパートメント内の仮想ファイル システムを公開します。</span><span class="sxs-lookup"><span data-stu-id="b0de5-103">An isolated store exposes a virtual file system within a data compartment.</span></span> <span data-ttu-id="b0de5-104"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> クラスでは、分離ストアと対話するためのいくつかのメソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b0de5-104">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies a number of methods for interacting with an isolated store.</span></span> <span data-ttu-id="b0de5-105">ストアを作成して取得するために、<xref:System.IO.IsolatedStorage.IsolatedStorageFile> では次の 3 つの静的メソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b0de5-105">To create and retrieve stores, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> provides three static methods:</span></span>  
  
- <span data-ttu-id="b0de5-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> は、ユーザーおよびアセンブリ別に分離されるストレージを返します。</span><span class="sxs-lookup"><span data-stu-id="b0de5-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> returns storage that is isolated by user and assembly.</span></span>  
  
- <span data-ttu-id="b0de5-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> は、ドメインおよびアセンブリ別に分離されるストレージを返します。</span><span class="sxs-lookup"><span data-stu-id="b0de5-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> returns storage that is isolated by domain and assembly.</span></span>  
  
     <span data-ttu-id="b0de5-108">両方のメソッドで、呼び出し元のコードに属するストアが取得されます。</span><span class="sxs-lookup"><span data-stu-id="b0de5-108">Both methods retrieve a store that belongs to the code from which they are called.</span></span>  
  
- <span data-ttu-id="b0de5-109">静的メソッド <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> は、スコープ パラメーターの組み合わせを渡すことで指定される分離ストアを返します。</span><span class="sxs-lookup"><span data-stu-id="b0de5-109">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> returns an isolated store that is specified by passing in a combination of scope parameters.</span></span>  
  
 <span data-ttu-id="b0de5-110">次のコードでは、ユーザー、アセンブリ、およびドメイン別に分離されるストアを返します。</span><span class="sxs-lookup"><span data-stu-id="b0de5-110">The following code returns a store that is isolated by user, assembly, and domain.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <span data-ttu-id="b0de5-111"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドを使用して、ストアが移動ユーザー プロファイルと共にローミングするように指定することができます。</span><span class="sxs-lookup"><span data-stu-id="b0de5-111">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method to specify that a store should roam with a roaming user profile.</span></span> <span data-ttu-id="b0de5-112">この設定方法の詳細については、「[分離のタイプ](types-of-isolation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0de5-112">For details on how to set this up, see [Types of Isolation](types-of-isolation.md).</span></span>  
  
 <span data-ttu-id="b0de5-113">異なるアセンブリ内から取得される分離ストアは、既定では異なるストアとなります。</span><span class="sxs-lookup"><span data-stu-id="b0de5-113">Isolated stores obtained from within different assemblies are, by default, different stores.</span></span> <span data-ttu-id="b0de5-114"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドのパラメーターでアセンブリまたはドメインの証拠を渡すことで、異なるアセンブリまたはドメインのストアにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b0de5-114">You can access the store of a different assembly or domain by passing in the assembly or domain evidence in the parameters of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="b0de5-115">この場合、アプリケーション ドメイン ID で分離ストレージにアクセスするアクセス許可が必要になります。</span><span class="sxs-lookup"><span data-stu-id="b0de5-115">This requires permission to access isolated storage by application domain identity.</span></span> <span data-ttu-id="b0de5-116">詳細については、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドのオーバーロードに関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0de5-116">For more information, see the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method overloads.</span></span>  
  
 <span data-ttu-id="b0de5-117"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>、および <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドは <xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="b0de5-117">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> methods return an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object.</span></span> <span data-ttu-id="b0de5-118">状況に最適な分離タイプの判別に役立つ「[分離のタイプ](types-of-isolation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0de5-118">To help you decide which isolation type is most appropriate for your situation, see [Types of Isolation](types-of-isolation.md).</span></span> <span data-ttu-id="b0de5-119">分離ストレージ ファイル オブジェクトがある場合は、分離ストレージ メソッドを使用して、ファイルとディレクトリの読み取り、書き込み、作成、削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b0de5-119">When you have an isolated storage file object, you can use the isolated storage methods to read, write, create, and delete files and directories.</span></span>  
  
 <span data-ttu-id="b0de5-120">ストア自体を取得するのに十分なアクセス権がないコードに <xref:System.IO.IsolatedStorage.IsolatedStorageFile> オブジェクトを渡さないようにするためのメカニズムはありません。</span><span class="sxs-lookup"><span data-stu-id="b0de5-120">There is no mechanism that prevents code from passing an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object to code that does not have sufficient access to get the store itself.</span></span> <span data-ttu-id="b0de5-121">ドメインとアセンブリの ID と分離ストレージのアクセス許可が確認されるのは、通常、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>、または <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドで <xref:System.IO.IsolatedStorage.IsolatedStorage> オブジェクトへの参照が取得される場合のみです。</span><span class="sxs-lookup"><span data-stu-id="b0de5-121">Domain and assembly identities and isolated storage permissions are checked only when a reference to an <xref:System.IO.IsolatedStorage.IsolatedStorage> object is obtained, typically in the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="b0de5-122">したがって、<xref:System.IO.IsolatedStorage.IsolatedStorageFile> への参照を保護するのは、これらの参照を使用するコードの役目です。</span><span class="sxs-lookup"><span data-stu-id="b0de5-122">Protecting references to <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects is, therefore, the responsibility of the code that uses these references.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0de5-123">例</span><span class="sxs-lookup"><span data-stu-id="b0de5-123">Example</span></span>  
 <span data-ttu-id="b0de5-124">次のコードでは、ユーザーとアセンブリ別に分離されるストアを取得するクラスの単純な例を示します。</span><span class="sxs-lookup"><span data-stu-id="b0de5-124">The following code provides a simple example of a class obtaining a store that is isolated by user and assembly.</span></span> <span data-ttu-id="b0de5-125"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> メソッドが渡す引数に <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> を追加することで、ユーザー、ドメイン、およびアセンブリ別に分離されるストアを取得するようにコードを変更できます。</span><span class="sxs-lookup"><span data-stu-id="b0de5-125">The code can be changed to retrieve a store that is isolated by user, domain, and assembly by adding <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> to the arguments that the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method passes.</span></span>  
  
 <span data-ttu-id="b0de5-126">コードを実行したら、コマンド ラインで「**StoreAdm /LIST**」と入力して、ストアが作成されたことを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="b0de5-126">After you run the code, you can confirm that a store was created by typing **StoreAdm /LIST** at the command line.</span></span> <span data-ttu-id="b0de5-127">これにより、[分離ストレージ ツール (Storeadm.exe)](../../framework/tools/storeadm-exe-isolated-storage-tool.md) が実行され、ユーザーの現在の分離ストアがすべてリストされます。</span><span class="sxs-lookup"><span data-stu-id="b0de5-127">This runs the [Isolated Storage tool (Storeadm.exe)](../../framework/tools/storeadm-exe-isolated-storage-tool.md) and lists all the current isolated stores for the user.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b0de5-128">参照</span><span class="sxs-lookup"><span data-stu-id="b0de5-128">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [<span data-ttu-id="b0de5-129">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="b0de5-129">Isolated Storage</span></span>](isolated-storage.md)
- [<span data-ttu-id="b0de5-130">分離のタイプ</span><span class="sxs-lookup"><span data-stu-id="b0de5-130">Types of Isolation</span></span>](types-of-isolation.md)
- [<span data-ttu-id="b0de5-131">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="b0de5-131">Assemblies in .NET</span></span>](../assembly/index.md)
