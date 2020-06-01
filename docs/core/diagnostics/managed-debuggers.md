---
title: マネージド デバッガー - .NET Core
description: Visual Studio および Visual Studio Code のマネージド デバッガーの概要。
ms.date: 08/05/2019
ms.openlocfilehash: 28cc21980bc78234f7af3b4668e2fa77fbf8ce5b
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2020
ms.locfileid: "84200856"
---
# <a name="net-core-managed-debuggers"></a><span data-ttu-id="9c121-103">.NET Core マネージド デバッガー</span><span class="sxs-lookup"><span data-stu-id="9c121-103">.NET Core managed debuggers</span></span>

<span data-ttu-id="9c121-104">デバッガーを使用すると、プログラムを一時停止したりステップ バイ ステップで実行したりできます。</span><span class="sxs-lookup"><span data-stu-id="9c121-104">Debuggers allow programs to be paused or executed step-by-step.</span></span> <span data-ttu-id="9c121-105">一時停止すると、プロセスの現在の状態を表示できます。</span><span class="sxs-lookup"><span data-stu-id="9c121-105">When paused, the current state of the process can be viewed.</span></span> <span data-ttu-id="9c121-106">主要なセクションをステップ実行することにより、コードとその動作の結果が生成される理由を理解することができます。</span><span class="sxs-lookup"><span data-stu-id="9c121-106">By stepping through key sections, you gain understanding of your code and why it produces the result that it does.</span></span>

<span data-ttu-id="9c121-107">Microsoft では、**Visual Studio** と **Visual Studio Code** のマネージド コード用のデバッガーを提供しています。</span><span class="sxs-lookup"><span data-stu-id="9c121-107">Microsoft provides debuggers for managed code in **Visual Studio** and **Visual Studio Code**.</span></span>

## <a name="visual-studio-managed-debugger"></a><span data-ttu-id="9c121-108">Visual Studio マネージド デバッガー</span><span class="sxs-lookup"><span data-stu-id="9c121-108">Visual Studio managed debugger</span></span>

<span data-ttu-id="9c121-109">**Visual Studio** は、最も包括的なデバッガーを利用できる統合開発環境です。</span><span class="sxs-lookup"><span data-stu-id="9c121-109">**Visual Studio** is an integrated development environment with the most comprehensive debugger available.</span></span> <span data-ttu-id="9c121-110">Visual Studio は、Windows で作業する開発者にとって最適な選択肢です。</span><span class="sxs-lookup"><span data-stu-id="9c121-110">Visual Studio is an excellent choice for developers working on Windows.</span></span>

- [<span data-ttu-id="9c121-111">チュートリアル - Visual Studio を使用した Windows での .NET Core アプリケーションのデバッグ</span><span class="sxs-lookup"><span data-stu-id="9c121-111">Tutorial - Debugging a .NET Core application on Windows with Visual Studio</span></span>](../tutorials/debugging-with-visual-studio.md)

<span data-ttu-id="9c121-112">Visual Studio は Windows アプリケーションですが、Linux および macOS アプリをリモートでデバッグするために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="9c121-112">While Visual Studio is a Windows application, it can still be used to debug Linux and macOS apps remotely.</span></span>

- [<span data-ttu-id="9c121-113">Visual Studio を使用した Linux/OSX での .NET Core アプリケーションのデバッグ</span><span class="sxs-lookup"><span data-stu-id="9c121-113">Debugging a .NET Core application on Linux/OSX with Visual Studio</span></span>](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 <span data-ttu-id="9c121-114">ASP.NET Core アプリのデバッグで必要な手順は若干異なります。</span><span class="sxs-lookup"><span data-stu-id="9c121-114">Debugging ASP.NET Core apps require slightly different instructions.</span></span>

- [<span data-ttu-id="9c121-115">Visual Studio での ASP.NET Core アプリのデバッグ</span><span class="sxs-lookup"><span data-stu-id="9c121-115">Debug ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a><span data-ttu-id="9c121-116">Visual Studio Code のマネージド デバッガー</span><span class="sxs-lookup"><span data-stu-id="9c121-116">Visual Studio Code managed debugger</span></span>

<span data-ttu-id="9c121-117">**Visual Studio Code** は、軽量のクロス プラットフォーム コード エディターです。</span><span class="sxs-lookup"><span data-stu-id="9c121-117">**Visual Studio Code** is a lightweight cross-platform code editor.</span></span> <span data-ttu-id="9c121-118">これは Visual Studio と同じ .NET Core デバッガー実装を使用しますが、簡略化されたユーザー インターフェイスを備えています。</span><span class="sxs-lookup"><span data-stu-id="9c121-118">It uses the same .NET Core debugger implementation as Visual Studio, but with a simplified user interface.</span></span>

- [<span data-ttu-id="9c121-119">チュートリアル - Visual Studio Code を使用した .NET Core アプリケーションのデバッグ</span><span class="sxs-lookup"><span data-stu-id="9c121-119">Tutorial - Debugging a .NET Core application with Visual Studio Code</span></span>](../tutorials/debugging-with-visual-studio-code.md)
- [<span data-ttu-id="9c121-120">Visual Studio Code でのデバッグ</span><span class="sxs-lookup"><span data-stu-id="9c121-120">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)
