---
title: この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 8e2caa158c3874d216671979430a03b11bf60066
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095682"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="06957-102">この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした</span><span class="sxs-lookup"><span data-stu-id="06957-102">This single-instance application could not connect to the original instance</span></span>

<span data-ttu-id="06957-103">この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした。</span><span class="sxs-lookup"><span data-stu-id="06957-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="06957-104">この問題の考えられる原因の一部は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="06957-104">Some of the possible causes for this problem are as follows:</span></span>  
  
- <span data-ttu-id="06957-105">元のインスタンスが応答を停止した。</span><span class="sxs-lookup"><span data-stu-id="06957-105">The original instance stopped responding.</span></span>  
  
- <span data-ttu-id="06957-106">カーネル オブジェクトを作成するためのアクセス許可がアプリケーションにない。</span><span class="sxs-lookup"><span data-stu-id="06957-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="06957-107">カーネルオブジェクトの詳細については、「 [mutex](../../standard/threading/mutexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06957-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="06957-108">カーネル オブジェクトの基本名は、アセンブリの GUID、メジャー バージョン番号、およびマイナー バージョン番号を連結したものです。</span><span class="sxs-lookup"><span data-stu-id="06957-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="06957-109">たとえば、基本名が `3639f15d-9547-43da-8145-60da347829915.1`になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="06957-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="06957-110">アプリケーションを開発しているときに、このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="06957-110">To correct this error when developing the application</span></span>  
  
1. <span data-ttu-id="06957-111">アプリケーションが応答していない状態にならないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="06957-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2. <span data-ttu-id="06957-112">カーネル オブジェクトを作成するための十分なアクセス許可がアプリケーションにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="06957-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3. <span data-ttu-id="06957-113">アプリケーションの元のインスタンスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="06957-113">Restart the original instance of the application.</span></span>  
  
4. <span data-ttu-id="06957-114">コンピューターを再起動して、元のインスタンス アプリケーションへの接続に必要なリソースを使用している可能性のあるプロセスをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="06957-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5. <span data-ttu-id="06957-115">エラーが発生した状況を記録して、Microsoft 製品サポート サービスに電話でご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="06957-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06957-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="06957-116">See also</span></span>

- [<span data-ttu-id="06957-117">デバッガーの基本事項</span><span class="sxs-lookup"><span data-stu-id="06957-117">Debugger Basics</span></span>](/visualstudio/debugger/debugger-feature-tour)
