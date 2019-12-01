---
ms.openlocfilehash: 4d479636f41095610eaf39f92ad0dad4863ab8b5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568197"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="8b389-101">TypeDescriptionProviderAttribute は別のアセンブリに移動されました</span><span class="sxs-lookup"><span data-stu-id="8b389-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="8b389-102"><xref:System.ComponentModel.TypeDescriptionProviderAttribute> クラスは異動されました。</span><span class="sxs-lookup"><span data-stu-id="8b389-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8b389-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="8b389-103">Change description</span></span>

<span data-ttu-id="8b389-104">.NET Core 2.2 およびそれ以前のバージョンでは、<xref:System.ComponentModel.TypeDescriptionProviderAttribute> クラスは *System.ComponentModel.TypeConverter* アセンブリにあります。</span><span class="sxs-lookup"><span data-stu-id="8b389-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="8b389-105">.NET Core 3.0 以降では、*System.ObjectModel* アセンブリに含まれています。</span><span class="sxs-lookup"><span data-stu-id="8b389-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8b389-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="8b389-106">Version introduced</span></span>

<span data-ttu-id="8b389-107">3.0</span><span class="sxs-lookup"><span data-stu-id="8b389-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8b389-108">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="8b389-108">Recommended action</span></span>

<span data-ttu-id="8b389-109">この変更によって影響を受けるのは、リフレクションを使用し、<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> などのメソッドや、型が特定のアセンブリにあることを想定している <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> のオーバーロードを呼び出すことによって、<xref:System.ComponentModel.TypeDescriptionProviderAttribute> 型を読み込んでいるアプリケーションのみです。</span><span class="sxs-lookup"><span data-stu-id="8b389-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="8b389-110">これに該当する場合は、メソッドの呼び出しで参照されているアセンブリを、型の新しいアセンブリの場所を反映するように更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b389-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="8b389-111">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="8b389-111">Category</span></span>

<span data-ttu-id="8b389-112">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="8b389-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8b389-113">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="8b389-113">Affected APIs</span></span>

- <span data-ttu-id="8b389-114">なし</span><span class="sxs-lookup"><span data-stu-id="8b389-114">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
