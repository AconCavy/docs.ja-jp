---
title: シンボル ストア診断インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: 044ed5e08a85442c5a73c123cf51529d2fd3f1fc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442177"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="b20e8-102">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="b20e8-103">このトピックでは、コンパイラがデバッガーで使用するシンボル情報を生成できるようにするアンマネージインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b20e8-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b20e8-104">In This Section</span></span>  
 [<span data-ttu-id="b20e8-105">IBindingDisplay インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-105">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)  
 <span data-ttu-id="b20e8-106">実行中のアプリケーションに関する現在のバインド情報を表示するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="b20e8-107">IDebugAutoAttach インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-107">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)  
 <span data-ttu-id="b20e8-108">サーバーによって呼び出されるデバッガーの自動アタッチのインターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="b20e8-109">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-109">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)  
 <span data-ttu-id="b20e8-110">接続通知ソースを登録および登録解除するためのメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="b20e8-111">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-111">INotifySink2 Interface</span></span>](inotifysink2-interface.md)  
 <span data-ttu-id="b20e8-112">シンク通知のメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="b20e8-113">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)  
 <span data-ttu-id="b20e8-114">通知フィルターを設定するためのメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="b20e8-115">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="b20e8-116">エディットコンティニュ機能に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="b20e8-117">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-117">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="b20e8-118">このインターフェイスは、 [ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス](isymunmanagedasyncmethodpropertieswriter-interface.md)への読み取り補数です。</span><span class="sxs-lookup"><span data-stu-id="b20e8-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="b20e8-119">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="b20e8-120">メソッドシンボルごとにオプションの非同期メソッド情報を定義できます。</span><span class="sxs-lookup"><span data-stu-id="b20e8-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="b20e8-121">は、開いているメソッド (つまり、 [Openmethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)と[closemethod メソッド](isymunmanagedwriter-closemethod-method.md)の呼び出しの間) でを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b20e8-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="b20e8-122">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-122">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)  
 <span data-ttu-id="b20e8-123">アンマネージコードのシンボルバインダーを表します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="b20e8-124">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-124">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="b20e8-125">アンマネージコードのシンボルバインダーを表し、インターフェイスを拡張し `ISymUnmanagedBinder` ます。</span><span class="sxs-lookup"><span data-stu-id="b20e8-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="b20e8-126">ISymUnmanagedBinder3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-126">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="b20e8-127">アンマネージコードのシンボルバインダーを表し、インターフェイスを拡張し `ISymUnmanagedBinder` ます。</span><span class="sxs-lookup"><span data-stu-id="b20e8-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="b20e8-128">ISymUnmanagedConstant インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-128">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)  
 <span data-ttu-id="b20e8-129">アンマネージ定数へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="b20e8-130">ISymUnmanagedDispose インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-130">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)  
 <span data-ttu-id="b20e8-131">アンマネージリソースを破棄します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="b20e8-132">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-132">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)  
 <span data-ttu-id="b20e8-133">シンボル ストアによって参照されるドキュメントを表します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="b20e8-134">ISymUnmanagedDocumentWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-134">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="b20e8-135">シンボル ストアで参照されるドキュメントに書き込むためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="b20e8-136">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-136">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="b20e8-137">エディットコンティニュ機能のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="b20e8-138">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-138">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)  
 <span data-ttu-id="b20e8-139">シンボルストア内のメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="b20e8-140">ISymUnmanagedNamespace インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-140">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)  
 <span data-ttu-id="b20e8-141">名前空間を表します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="b20e8-142">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-142">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)  
 <span data-ttu-id="b20e8-143">シンボルストア内のドキュメント、メソッド、および変数へのアクセスを提供するシンボルリーダーを表します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="b20e8-144">ISymUnmanagedReader2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-144">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)  
 <span data-ttu-id="b20e8-145">メソッドトークンと編集およびコピーバージョン番号を指定して、シンボルリーダーメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="b20e8-146">ISymUnmanagedReaderSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="b20e8-147">シンボル検索情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="b20e8-148">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-148">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)  
 <span data-ttu-id="b20e8-149">メソッド内の構文のスコープを表します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="b20e8-150">ISymUnmanagedScope2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-150">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)  
 <span data-ttu-id="b20e8-151">メソッド内の構文のスコープを表し、 `ISymUnmanagedScope` スコープ内で定義された定数に関する情報を取得するメソッドを使用してインターフェイスを拡張します。「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b20e8-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="b20e8-152">ISymUnmanagedSourceServerModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-152">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="b20e8-153">モジュールのソースサーバーデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="b20e8-154">ISymUnmanagedSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="b20e8-155">検索パスに関する情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="b20e8-156">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-156">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)  
 <span data-ttu-id="b20e8-157">パラメーター、ローカル変数、フィールドなどの変数を表します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="b20e8-158">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-158">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)  
 <span data-ttu-id="b20e8-159">シンボルライターを表し、ドキュメント、シーケンスポイント、構文スコープ、および変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="b20e8-160">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-160">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="b20e8-161">シンボルライターを表し、ドキュメント、シーケンスポイント、構文スコープ、および変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="b20e8-162">インターフェイスを拡張 `ISymUnmanagedWriter` します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="b20e8-163">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-163">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="b20e8-164">シンボルライターを表し、ドキュメント、シーケンスポイント、構文スコープ、および変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="b20e8-165">インターフェイスを拡張 `ISymUnmanagedWriter` します。</span><span class="sxs-lookup"><span data-stu-id="b20e8-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="b20e8-166">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-166">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="b20e8-167">ISymUnmanagedWriter4 インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="b20e8-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="b20e8-168">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20e8-168">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="b20e8-169">ISymUnmanagedWriter5 インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="b20e8-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b20e8-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="b20e8-170">Related Sections</span></span>  
 [<span data-ttu-id="b20e8-171">シンボル ストア診断列挙型</span><span class="sxs-lookup"><span data-stu-id="b20e8-171">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="b20e8-172">シンボル ストア診断構造体</span><span class="sxs-lookup"><span data-stu-id="b20e8-172">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="b20e8-173">デバッグ</span><span class="sxs-lookup"><span data-stu-id="b20e8-173">Debugging</span></span>](../debugging/index.md)
