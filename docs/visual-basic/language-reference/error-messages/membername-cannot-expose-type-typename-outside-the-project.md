---
title: "'<membername>' は、型 '<typename>' を <containertype> '<containertypename>' 経由でプロジェクトの外側に公開できません。"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 729a9f385d94412469d318cb804d216827eeb0fd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397286"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="4a01b-102">'\<membername>' は、型 '\<typename>' を \<containertype> '\<containertypename>' 経由でプロジェクトの外側に公開できません。</span><span class="sxs-lookup"><span data-stu-id="4a01b-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>
<span data-ttu-id="4a01b-103">変数、プロシージャ パラメーター、または関数の戻り値がそのコンテナーの外側に公開されていますが、コンテナーの外側に公開できない型として宣言されています。</span><span class="sxs-lookup"><span data-stu-id="4a01b-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="4a01b-104">次のスケルトン コードは、このエラーが生成される状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="4a01b-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="4a01b-105">`Protected`、`Friend`、`Protected Friend`、または `Private` として宣言されている型は、その宣言コンテキストの外部でアクセスが制限されることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="4a01b-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="4a01b-106">アクセス制限が緩い変数のデータ型として使用すると、この目的が損なわれます。</span><span class="sxs-lookup"><span data-stu-id="4a01b-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="4a01b-107">上記のスケルトン コードでは、`exposedVar` は `Public` であり、アクセス権を持たないコードに `privateClass` を公開します。</span><span class="sxs-lookup"><span data-stu-id="4a01b-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="4a01b-108">**エラー ID:** BC30909</span><span class="sxs-lookup"><span data-stu-id="4a01b-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4a01b-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4a01b-109">To correct this error</span></span>  
  
- <span data-ttu-id="4a01b-110">変数、プロシージャ パラメーター、または関数の戻り値のアクセス レベルを、少なくともそのデータ型のアクセス レベルと同じ制限になるように変更します。</span><span class="sxs-lookup"><span data-stu-id="4a01b-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a01b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a01b-111">See also</span></span>

- [<span data-ttu-id="4a01b-112">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="4a01b-112">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
