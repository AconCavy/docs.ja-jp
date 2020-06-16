---
title: フレームワーク デザインのガイドライン
description: API の一貫性と使いやすさを確保するために、.NET を拡張して操作するライブラリを設計するためのフレームワークデザインガイドラインを参照してください。
titleSuffix: ''
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 17998adb1d18579f6763a80a82944e742e284e4e
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769068"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="45406-103">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="45406-103">Framework Design Guidelines</span></span>
<span data-ttu-id="45406-104">このセクションでは、.NET Framework を拡張および操作するライブラリを設計するためのガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="45406-104">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="45406-105">この目標は、開発に使用されるプログラミング言語に依存しない統合プログラミングモデルを提供することで、ライブラリデザイナーが API の一貫性と使いやすさを保証できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="45406-105">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="45406-106">.NET Framework を拡張するクラスおよびコンポーネントを開発する場合は、これらのデザインガイドラインに従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="45406-106">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="45406-107">一貫性のないライブラリ設計は、開発者の生産性に悪影響を及ぼし、導入を推奨しません。</span><span class="sxs-lookup"><span data-stu-id="45406-107">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="45406-108">ガイドラインは、「」、「」、および「」という用語で構成される単純な推奨事項としてまとめられてい `Do` `Consider` `Avoid` `Do not` ます。</span><span class="sxs-lookup"><span data-stu-id="45406-108">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="45406-109">これらのガイドラインは、クラスライブラリデザイナーがさまざまなソリューション間のトレードオフを理解できるようにすることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="45406-109">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="45406-110">優れたライブラリ設計では、これらの設計ガイドラインに違反することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="45406-110">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="45406-111">このようなケースはまれであり、明確で説得力のある理由を決定することが重要です。</span><span class="sxs-lookup"><span data-stu-id="45406-111">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="45406-112">これらのガイドラインは、抜粋です*Framework の設計ガイドラインから、再利用可能な .Net ライブラリである2番目のエディション*(Krzysztof Cwalina と Brad abrams) の規則、表現、パターンについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="45406-112">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45406-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="45406-113">In This Section</span></span>  
 [<span data-ttu-id="45406-114">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="45406-114">Naming Guidelines</span></span>](naming-guidelines.md)  
 <span data-ttu-id="45406-115">クラスライブラリのアセンブリ、名前空間、型、およびメンバーの名前付けに関するガイドラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="45406-115">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="45406-116">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="45406-116">Type Design Guidelines</span></span>](type.md)  
 <span data-ttu-id="45406-117">静的クラス、抽象クラス、インターフェイス、列挙体、構造体、およびその他の型を使用するためのガイドラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="45406-117">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="45406-118">メンバーデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="45406-118">Member Design Guidelines</span></span>](member.md)  
 <span data-ttu-id="45406-119">プロパティ、メソッド、コンストラクター、フィールド、イベント、演算子、およびパラメーターのデザインと使用に関するガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="45406-119">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="45406-120">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="45406-120">Designing for Extensibility</span></span>](designing-for-extensibility.md)  
 <span data-ttu-id="45406-121">サブクラス化、イベント、仮想メンバー、コールバックなどの拡張機能について説明し、フレームワークの要件に最も適したメカニズムを選択する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="45406-121">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="45406-122">例外のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="45406-122">Design Guidelines for Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="45406-123">例外をデザイン、スロー、キャッチするためのデザインガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="45406-123">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="45406-124">使用に関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="45406-124">Usage Guidelines</span></span>](usage-guidelines.md)  
 <span data-ttu-id="45406-125">配列、属性、コレクションなどの共通型の使用、シリアル化のサポート、および等値演算子のオーバーロードに関するガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="45406-125">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="45406-126">一般的なデザインパターン</span><span class="sxs-lookup"><span data-stu-id="45406-126">Common Design Patterns</span></span>](common-design-patterns.md)  
 <span data-ttu-id="45406-127">依存関係プロパティの選択と実装に関するガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="45406-127">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="45406-128">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="45406-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="45406-129">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="45406-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45406-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="45406-130">See also</span></span>

- [<span data-ttu-id="45406-131">概要</span><span class="sxs-lookup"><span data-stu-id="45406-131">Overview</span></span>](../../framework/get-started/overview.md)
- [<span data-ttu-id="45406-132">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="45406-132">Development Guide</span></span>](../../framework/development-guide.md)
