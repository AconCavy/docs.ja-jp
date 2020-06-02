---
title: パラメーターに名前を付ける
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 0d5c5cd144fbae88439ee981fbdb6e30ff487005
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290163"
---
# <a name="naming-parameters"></a><span data-ttu-id="c6725-102">パラメーターに名前を付ける</span><span class="sxs-lookup"><span data-stu-id="c6725-102">Naming Parameters</span></span>
<span data-ttu-id="c6725-103">読みやすくするために、パラメーター名のガイドラインに従うことが重要です。これは、ビジュアルデザインツールが Intellisense とクラス参照機能を提供する場合に、ドキュメントとデザイナーにパラメーターが表示されるためです。</span><span class="sxs-lookup"><span data-stu-id="c6725-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="c6725-104">パラメーター名にキャメルを使用する✔️ます。</span><span class="sxs-lookup"><span data-stu-id="c6725-104">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="c6725-105">✔️、説明的なパラメーター名を使用します。</span><span class="sxs-lookup"><span data-stu-id="c6725-105">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="c6725-106">パラメーターの型ではなく、パラメーターの意味に基づいて名前を使用することを✔️してください。</span><span class="sxs-lookup"><span data-stu-id="c6725-106">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="c6725-107">演算子のオーバーロードパラメーターの名前付け</span><span class="sxs-lookup"><span data-stu-id="c6725-107">Naming Operator Overload Parameters</span></span>
 <span data-ttu-id="c6725-108">`left` `right` パラメーターに意味がない場合は、二項演算子のオーバーロードパラメーター名に and を使用✔️ます。</span><span class="sxs-lookup"><span data-stu-id="c6725-108">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="c6725-109">`value`パラメーターに意味がない場合は、単項演算子のオーバーロードパラメーター名には✔️を使用します。</span><span class="sxs-lookup"><span data-stu-id="c6725-109">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="c6725-110">✔️演算子を使用すると、有意な値が追加されます。</span><span class="sxs-lookup"><span data-stu-id="c6725-110">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="c6725-111">❌演算子のオーバーロードパラメーター名には、省略形または数値インデックスを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c6725-111">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="c6725-112">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="c6725-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c6725-113">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="c6725-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c6725-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6725-114">See also</span></span>

- [<span data-ttu-id="c6725-115">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c6725-115">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="c6725-116">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c6725-116">Naming Guidelines</span></span>](naming-guidelines.md)
