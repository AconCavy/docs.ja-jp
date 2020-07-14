---
title: リンク確認要求
description: Just-in-time (JIT) コンパイル時にセキュリティチェックを実行し、コードの直前の呼び出し元アセンブリだけを調べるリンク確認要求について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
ms.openlocfilehash: cd89c4ef27abb92fba567a1f3b490cb9d78fdddd
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282060"
---
# <a name="link-demands"></a><span data-ttu-id="35c32-103">リンク確認要求</span><span class="sxs-lookup"><span data-stu-id="35c32-103">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="35c32-104">リンク確認要求では、Just-In-Time コンパイル時にセキュリティ チェックが実行され、コードの直前の呼び出し元アセンブリだけがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="35c32-104">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="35c32-105">リンクは、コードを関数ポインターの参照やメソッドの呼び出しなどの型の参照にバインドするときに発生します。</span><span class="sxs-lookup"><span data-stu-id="35c32-105">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="35c32-106">呼び出し元のアセンブリが、コードにリンクするための十分な権限を持たない場合は、リンクは許可されず、コードが読み込まれて実行されると、ランタイム例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35c32-106">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="35c32-107">リンク確認要求は、コードから継承するクラスでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="35c32-107">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="35c32-108">この種類の要求では、完全なスタック ウォークが実行されないことと、コードがおびき寄せによる攻撃を受ける可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="35c32-108">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="35c32-109">たとえば、アセンブリ A のメソッドがリンク確認要求によって保護されている場合、アセンブリ B の直接の呼び出し元は、アセンブリ B のアクセス許可に基づいて評価されます。 ただし、アセンブリ B のメソッドを使用してアセンブリ A のメソッドを間接的に呼び出す場合、リンク確認要求は、アセンブリ C のメソッドを評価しません。リンク確認要求で指定されるのは、直接呼び出し元のアセンブリ内の直接の呼び出し元がコードにリンクするために必要なアクセス許可のみです。</span><span class="sxs-lookup"><span data-stu-id="35c32-109">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="35c32-110">すべての呼び出し元がコードを実行するために必要なアクセス許可は指定しません。</span><span class="sxs-lookup"><span data-stu-id="35c32-110">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="35c32-111"><xref:System.Security.CodeAccessPermission.Assert%2A>、<xref:System.Security.CodeAccessPermission.Deny%2A>、および <xref:System.Security.CodeAccessPermission.PermitOnly%2A> の各スタック ウォーク修飾子は、リンク確認要求の評価に影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="35c32-111">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="35c32-112">リンク確認要求は、スタック ウォークを実行しないため、スタック ウォーク修飾子はリンク確認要求に影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="35c32-112">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="35c32-113">リンク確認要求によって保護されているメソッドが[リフレクション](../reflection-and-codedom/reflection.md)によってアクセスされる場合、リンク確認要求は、リフレクションによってアクセスされるコードの直前の呼び出し元をチェックします。</span><span class="sxs-lookup"><span data-stu-id="35c32-113">If a method protected by a link demand is accessed through [Reflection](../reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="35c32-114">これは、メソッドの探索と、リフレクションを使用して行うメソッド呼び出しの両方に該当します。</span><span class="sxs-lookup"><span data-stu-id="35c32-114">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="35c32-115">たとえば、コードがリフレクションを使用して、 <xref:System.Reflection.MethodInfo> リンク確認要求で保護されているメソッドを表すオブジェクトを返し、その**MethodInfo**オブジェクトを、オブジェクトを使用して元のメソッドを呼び出す他のコードに渡すとします。</span><span class="sxs-lookup"><span data-stu-id="35c32-115">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="35c32-116">この場合、リンク確認要求のチェックは2回行われます。1回は**MethodInfo**オブジェクトを返すコードで、もう1つは、それを呼び出すコードの場合です。</span><span class="sxs-lookup"><span data-stu-id="35c32-116">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35c32-117">静的クラスのコンストラクターで実行されるリンク確認要求では、静的コンストラクターは保護されません。これは、静的コンストラクターがアプリケーションのコードの実行パスの外側で、システムによって呼び出されるためです。</span><span class="sxs-lookup"><span data-stu-id="35c32-117">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="35c32-118">その結果、リンク確認要求がクラス全体に適用される場合、静的コンストラクターへのアクセスは保護できませんが、クラスの残りの部分は保護されます。</span><span class="sxs-lookup"><span data-stu-id="35c32-118">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="35c32-119">次のコード フラグメントでは、`ReadData` メソッドにリンクするコードはすべて `CustomPermission` のアクセス許可を持つ必要があることを宣言によって指定しています。</span><span class="sxs-lookup"><span data-stu-id="35c32-119">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="35c32-120">このアクセス許可は架空のカスタム許可であり、.NET Framework には実在しません。</span><span class="sxs-lookup"><span data-stu-id="35c32-120">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="35c32-121">要求は、に**SecurityAction**フラグを渡すことによって行われ `CustomPermissionAttribute` ます。</span><span class="sxs-lookup"><span data-stu-id="35c32-121">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="35c32-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="35c32-122">See also</span></span>

- [<span data-ttu-id="35c32-123">属性</span><span class="sxs-lookup"><span data-stu-id="35c32-123">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="35c32-124">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="35c32-124">Code Access Security</span></span>](code-access-security.md)
