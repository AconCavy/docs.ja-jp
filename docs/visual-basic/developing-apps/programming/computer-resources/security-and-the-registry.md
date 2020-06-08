---
title: セキュリティとレジストリ
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 2eba9d177769b22de3f931bc7af4905a80e316b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359969"
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="38e8b-102">セキュリティとレジストリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38e8b-102">Security and the Registry (Visual Basic)</span></span>

<span data-ttu-id="38e8b-103">ここでは、レジストリにデータを格納するときのセキュリティへの影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="38e8b-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="38e8b-104">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="38e8b-104">Permissions</span></span>  

 <span data-ttu-id="38e8b-105">レジストリ キーがアクセス制御リスト (ACL) によって保護されていても、パスワードなど他人に知られたくないデータをプレーン テキストでレジストリに格納するのは危険です。</span><span class="sxs-lookup"><span data-stu-id="38e8b-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="38e8b-106">レジストリを操作すると、システム リソースや保護情報への不適切なアクセスが許可され、セキュリティが損なわれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="38e8b-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="38e8b-107">これらのプロパティを使うには、<xref:System.Security.Permissions.RegistryPermissionAccess> 列挙型の読み書きアクセス許可が必要です。これは、レジストリ変数へのアクセスを制御します。</span><span class="sxs-lookup"><span data-stu-id="38e8b-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="38e8b-108">完全な信頼で実行されるコード (既定のセキュリティ ポリシーでは、これはユーザーのローカル ハード ディスクにインストールされているコードです) は、レジストリにアクセスするために必要なアクセス許可を持っています。</span><span class="sxs-lookup"><span data-stu-id="38e8b-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="38e8b-109">詳細については、<xref:System.Security.Permissions.RegistryPermission> クラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="38e8b-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="38e8b-110">レジストリ変数は、<xref:System.Security.Permissions.RegistryPermission> を持たないコードがアクセスできるメモリの場所には格納しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="38e8b-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="38e8b-111">同様に、アクセス許可を付与するときは、ジョブの実行に必要な最低限の特権を付与します。</span><span class="sxs-lookup"><span data-stu-id="38e8b-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="38e8b-112">レジストリ アクセス許可のアクセス値は <xref:System.Security.Permissions.RegistryPermissionAccess> 列挙型により定義されます。</span><span class="sxs-lookup"><span data-stu-id="38e8b-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="38e8b-113">次の表はそのメンバーの詳細です。</span><span class="sxs-lookup"><span data-stu-id="38e8b-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="38e8b-114">値</span><span class="sxs-lookup"><span data-stu-id="38e8b-114">Value</span></span>|<span data-ttu-id="38e8b-115">レジストリ変数へのアクセス</span><span class="sxs-lookup"><span data-stu-id="38e8b-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="38e8b-116">作成、読み取り、書き込み</span><span class="sxs-lookup"><span data-stu-id="38e8b-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="38e8b-117">作成</span><span class="sxs-lookup"><span data-stu-id="38e8b-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="38e8b-118">アクセス権なし</span><span class="sxs-lookup"><span data-stu-id="38e8b-118">No access</span></span>|  
|`Read`|<span data-ttu-id="38e8b-119">Read</span><span class="sxs-lookup"><span data-stu-id="38e8b-119">Read</span></span>|  
|`Write`|<span data-ttu-id="38e8b-120">Write</span><span class="sxs-lookup"><span data-stu-id="38e8b-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="38e8b-121">レジストリ キーの値のチェック</span><span class="sxs-lookup"><span data-stu-id="38e8b-121">Checking Values in Registry Keys</span></span>  

 <span data-ttu-id="38e8b-122">レジストリの値を作成するときは、その値が既存の値である場合の処理を決めておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="38e8b-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="38e8b-123">悪意のあるユーザーによって作成された別のプロセスが既に値を作成し、アクセス権を持っている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="38e8b-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="38e8b-124">レジストリ値にデータを設定すると、そのデータを他のプロセスから利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="38e8b-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="38e8b-125">これを回避するには、`GetValue` メソッドを使います。</span><span class="sxs-lookup"><span data-stu-id="38e8b-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="38e8b-126">このメソッドは、キーがまだ存在しない場合、`Nothing` を返します。</span><span class="sxs-lookup"><span data-stu-id="38e8b-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="38e8b-127">Web アプリケーションからレジストリを読み取るとき、現在のユーザーの ID は Web アプリケーションに実装されている認証と偽装によって決まります。</span><span class="sxs-lookup"><span data-stu-id="38e8b-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e8b-128">参照</span><span class="sxs-lookup"><span data-stu-id="38e8b-128">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="38e8b-129">レジストリからの読み取りとレジストリへの書き込み</span><span class="sxs-lookup"><span data-stu-id="38e8b-129">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
