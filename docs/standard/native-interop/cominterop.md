---
title: .NET での COM 相互運用
description: .NET で COM ライブラリを相互運用する方法について説明します。
ms.date: 07/11/2019
ms.openlocfilehash: 63205ae5c09d6c3929da13788eb781cd975ca814
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627375"
---
# <a name="com-interop-in-net"></a><span data-ttu-id="fea1b-103">.NET での COM 相互運用</span><span class="sxs-lookup"><span data-stu-id="fea1b-103">COM Interop in .NET</span></span>

<span data-ttu-id="fea1b-104">コンポーネント オブジェクト モデル (COM) では、オブジェクトがその機能を他のコンポーネントに公開し、Windows プラットフォームのアプリケーションをホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="fea1b-104">The Component Object Model (COM) lets an object expose its functionality to other components and to host applications on Windows platforms.</span></span> <span data-ttu-id="fea1b-105">ユーザーが既存のコード ベースを使用して相互運用できるように支援するために、.NET Framework は、COM ライブラリとの相互運用に向けて常に強力なサポートを行っています。</span><span class="sxs-lookup"><span data-stu-id="fea1b-105">To help enable users to interoperate with their existing code bases, the .NET Framework has always provided strong support for interoperating with COM libraries.</span></span> <span data-ttu-id="fea1b-106">.NET Core 3.0 では、このサポートの大部分が、Windows の .NET Core に追加されました。</span><span class="sxs-lookup"><span data-stu-id="fea1b-106">In .NET Core 3.0, a large portion of this support has been added to .NET Core on Windows.</span></span> <span data-ttu-id="fea1b-107">このドキュメントでは、共通の COM 相互運用テクノロジのしくみと、既存の COM ライブラリとの相互運用に向けたその利用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fea1b-107">The documentation here will explain how the common COM interop technologies work and how you can utilize them to interoperate with your existing COM libraries.</span></span>

- [<span data-ttu-id="fea1b-108">COM ラッパー</span><span class="sxs-lookup"><span data-stu-id="fea1b-108">COM Wrappers</span></span>](./com-wrappers.md)
- [<span data-ttu-id="fea1b-109">COM 呼び出し可能ラッパー</span><span class="sxs-lookup"><span data-stu-id="fea1b-109">COM Callable Wrappers</span></span>](./com-callable-wrapper.md)
- [<span data-ttu-id="fea1b-110">ランタイム呼び出し可能ラッパー</span><span class="sxs-lookup"><span data-stu-id="fea1b-110">Runtime Callable Wrappers</span></span>](./runtime-callable-wrapper.md)
- [<span data-ttu-id="fea1b-111">COM 相互運用のための .NET 型の要件</span><span class="sxs-lookup"><span data-stu-id="fea1b-111">Qualifying .NET Types for COM Interoperation</span></span>](./qualify-net-types-for-interoperation.md)
