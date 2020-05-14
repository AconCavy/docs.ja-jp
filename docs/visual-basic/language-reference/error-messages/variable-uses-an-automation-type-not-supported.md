---
title: サポートされていない Automation の型が変数で使用されています
ms.date: 07/20/2015
f1_keywords:
- vbrID458
ms.assetid: bde4f4da-493b-452c-b6e4-1d370edba4cd
ms.openlocfilehash: 944c0c63cd0d7ae7f9ff770fd123231464af1eaf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344828"
---
# <a name="variable-uses-an-automation-type-not-supported-in-visual-basic"></a><span data-ttu-id="62bc4-102">Visual Basic でサポートされていないオートメーションが変数で使用されています。</span><span class="sxs-lookup"><span data-stu-id="62bc4-102">Variable uses an Automation type not supported in Visual Basic</span></span>

<span data-ttu-id="62bc4-103">Visual Basic でサポートされていないデータ型を持つタイプ ライブラリまたはオブジェクト ライブラリに定義された変数を使用しようとしました。</span><span class="sxs-lookup"><span data-stu-id="62bc4-103">You tried to use a variable defined in a type library or object library that has a data type not supported by Visual Basic.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="62bc4-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="62bc4-104">To correct this error</span></span>

- <span data-ttu-id="62bc4-105">Visual Basic によって認識される型の変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="62bc4-105">Use a variable of a type recognized by Visual Basic.</span></span>

     <span data-ttu-id="62bc4-106">\- または -</span><span class="sxs-lookup"><span data-stu-id="62bc4-106">-or-</span></span>

- <span data-ttu-id="62bc4-107">`FileGet` または `FileGetObject` の使用中にこのエラーが発生した場合は、使用しようとしているファイルが `FilePut` または `FilePutObject` と共に書き込まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="62bc4-107">If you encounter this error while using `FileGet` or `FileGetObject`, make sure the file you are trying to use was written to with `FilePut` or `FilePutObject`.</span></span>

## <a name="see-also"></a><span data-ttu-id="62bc4-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="62bc4-108">See also</span></span>

- [<span data-ttu-id="62bc4-109">データの種類</span><span class="sxs-lookup"><span data-stu-id="62bc4-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
