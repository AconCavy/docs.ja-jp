---
title: セキュリティとユーザー入力
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: 0d34b06b44241feb7d6e3c8f76447b861563cfdc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705861"
---
# <a name="security-and-user-input"></a><span data-ttu-id="ce10b-102">セキュリティとユーザー入力</span><span class="sxs-lookup"><span data-stu-id="ce10b-102">Security and User Input</span></span>

<span data-ttu-id="ce10b-103">ユーザー データにはあらゆる種類の入力 (Web 要求または URL からのデータや、Microsoft Windows Forms アプリケーションのコントロールへの入力など) がありますが、これはコードに悪影響を及ぼすことがあります。このようなデータはパラメーターとして直接使用され、他のコードを呼び出す場合が多いためです。</span><span class="sxs-lookup"><span data-stu-id="ce10b-103">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="ce10b-104">この状況は、悪意のあるコードが不明なパラメーターを使用してコードを呼び出すことと似ており、同じ予防策をとる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce10b-104">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="ce10b-105">実際には、ユーザー入力の安全性を保つ方が困難です。潜在的に信頼されていないデータの存在をトレースするスタック フレームがないためです。</span><span class="sxs-lookup"><span data-stu-id="ce10b-105">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="ce10b-106">これらは最も微小で見つけにくいセキュリティ バグです。セキュリティとは無関係に見えるコードに存在すことができ、他のコードに悪いデータを送り出すゲートウェイだからです。</span><span class="sxs-lookup"><span data-stu-id="ce10b-106">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="ce10b-107">このようなバグを探し出すには、あらゆる種類の入力データを追跡し、可能性のある値の範囲を想像し、そのデータを扱うコードがすべてのケースを処理できるかどうかを検討します。</span><span class="sxs-lookup"><span data-stu-id="ce10b-107">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="ce10b-108">これらのバグは、範囲チェックを使用して、コードで処理できない入力を拒否することで修正できます。</span><span class="sxs-lookup"><span data-stu-id="ce10b-108">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="ce10b-109">ユーザー データに関連する重要な注意事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ce10b-109">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="ce10b-110">サーバー応答内のすべてのユーザー データは、クライアント上でサーバーのサイトのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="ce10b-110">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="ce10b-111">ご使用の Web サーバーがユーザー データを受け取り、返す Web ページにそのデータを挿入する場合、たとえば、そのデータが **\<script>** タグを組み込んで、サーバーからのように実行する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ce10b-111">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="ce10b-112">クライアントはすべての URL を要求できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ce10b-112">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="ce10b-113">巧妙なパスまたは無効なパスに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ce10b-113">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="ce10b-114">..\、極端に長いパス。</span><span class="sxs-lookup"><span data-stu-id="ce10b-114">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="ce10b-115">ワイルドカード文字 (\*) の使用。</span><span class="sxs-lookup"><span data-stu-id="ce10b-115">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="ce10b-116">トークンの展開 (%token%)。</span><span class="sxs-lookup"><span data-stu-id="ce10b-116">Token expansion (%token%).</span></span>

  - <span data-ttu-id="ce10b-117">特別な意味を持つ変わった形式のパス。</span><span class="sxs-lookup"><span data-stu-id="ce10b-117">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="ce10b-118">代替ファイル システム ストリーム名、`filename::$DATA` など。</span><span class="sxs-lookup"><span data-stu-id="ce10b-118">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="ce10b-119">ファイル名の短縮バージョン、`longfilename`に対して `longfi~1` など。</span><span class="sxs-lookup"><span data-stu-id="ce10b-119">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="ce10b-120">Eval(userdata) は何でも実行できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ce10b-120">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="ce10b-121">ユーザー データを含む名前の遅延バインディングを警戒してください。</span><span class="sxs-lookup"><span data-stu-id="ce10b-121">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="ce10b-122">Web データを扱う場合は、許容されるさまざまな形式のエスケープを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ce10b-122">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="ce10b-123">16 進数エスケープ (%nn)。</span><span class="sxs-lookup"><span data-stu-id="ce10b-123">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="ce10b-124">Unicode エスケープ (%nnn)。</span><span class="sxs-lookup"><span data-stu-id="ce10b-124">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="ce10b-125">オーバーロング UTF-8 エスケープ (%nn%nn)。</span><span class="sxs-lookup"><span data-stu-id="ce10b-125">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="ce10b-126">ダブル エスケープ (%nn が %mmnn になります。%mm は '%' のエスケープです)。</span><span class="sxs-lookup"><span data-stu-id="ce10b-126">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="ce10b-127">標準形式が複数あるユーザー名に注意してください。</span><span class="sxs-lookup"><span data-stu-id="ce10b-127">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="ce10b-128">たとえば、よく使用するのは MYDOMAIN\\*username* 形式または *username*@mydomain.example.com 形式です。</span><span class="sxs-lookup"><span data-stu-id="ce10b-128">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce10b-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce10b-129">See also</span></span>

- [<span data-ttu-id="ce10b-130">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="ce10b-130">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
