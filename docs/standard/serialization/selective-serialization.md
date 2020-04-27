---
title: 選択的シリアル化
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: cc5d7964d5f3268f08721593fefc07e3eff853ca
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159599"
---
# <a name="selective-serialization"></a><span data-ttu-id="96afe-102">選択的シリアル化</span><span class="sxs-lookup"><span data-stu-id="96afe-102">Selective serialization</span></span>
<span data-ttu-id="96afe-103">クラスには、シリアル化できないフィールドが含まれていることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="96afe-103">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="96afe-104">たとえば、クラスのメンバー変数の 1 つにスレッド ID が格納されているとします。</span><span class="sxs-lookup"><span data-stu-id="96afe-104">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="96afe-105">クラスを逆シリアル化すると、クラスのシリアル化時に格納された ID を持つスレッドが実行されなくなることがあります。したがって、この値をシリアル化しても意味はありません。</span><span class="sxs-lookup"><span data-stu-id="96afe-105">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="96afe-106">以下のように、メンバー変数に [NonSerialized](xref:System.NonSerializedAttribute) 属性を使用してマークすることで、メンバー変数がシリアル化されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="96afe-106">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="96afe-107">機密データを含むオブジェクトは、可能であれば、シリアル化できないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="96afe-107">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="96afe-108">オブジェクトをシリアル化する必要がある場合は、機密データを格納する特定のフィールドに `NonSerialized` 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="96afe-108">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="96afe-109">これらのフィールドをシリアル化の対象から除外しない場合は、フィールドに格納されているデータがシリアル化のアクセス許可を持つ任意のコードに公開されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="96afe-109">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="96afe-110">安全なシリアル化コードの記述の詳細については、「[セキュリティとシリアル化](../../../docs/framework/misc/security-and-serialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96afe-110">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="96afe-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="96afe-111">See also</span></span>

- [<span data-ttu-id="96afe-112">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="96afe-112">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="96afe-113">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="96afe-113">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="96afe-114">セキュリティとシリアル化</span><span class="sxs-lookup"><span data-stu-id="96afe-114">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
