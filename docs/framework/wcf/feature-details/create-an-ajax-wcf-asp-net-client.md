---
title: Visual Studio で AJAX 対応 WCF サービスと ASP.NET クライアントを作成する
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 0bfe55c68f68bfef7b7ec2034413b53d41b0c785
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609357"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="0480c-102">方法 : AJAX 対応 WCF サービスとこのサービスにアクセスする ASP.NET クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="0480c-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="0480c-103">このトピックでは、Visual Studio を使用して、AJAX 対応の Windows Communication Foundation (WCF) サービスと、サービスにアクセスする ASP.NET クライアントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0480c-103">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="0480c-104">ASP.NET Web アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="0480c-104">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="0480c-105">Visual Studio を開きます。</span><span class="sxs-lookup"><span data-stu-id="0480c-105">Open Visual Studio.</span></span>

1. <span data-ttu-id="0480c-106">[**ファイル**] メニューの [**新しい**  >  **プロジェクト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0480c-106">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="0480c-107">[**新しいプロジェクト**] ダイアログで、[**インストールされている**  >  **Visual C#**  >  **web** ] カテゴリを展開し、[ **ASP.NET Web Application (.NET Framework)**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0480c-107">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="0480c-108">プロジェクトに **SandwichServices** という名前を指定し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0480c-108">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="0480c-109">**[新しい ASP.NET Web アプリケーション]** ダイアログで、 **[空]** を選択し、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0480c-109">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![ASP.NET Visual Studio の [web アプリの種類] ダイアログボックス](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="0480c-111">Web フォームを追加する</span><span class="sxs-lookup"><span data-stu-id="0480c-111">Add a web form</span></span>

1. <span data-ttu-id="0480c-112">**ソリューションエクスプローラー**で SandwichServices プロジェクトを右クリックし、[ **Add**  >  **新しい項目**の追加] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0480c-112">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="0480c-113">[**新しい項目の追加**] ダイアログで、[**インストールされている**  >  **Visual C#**]  >  **web**カテゴリを展開し、[ **web フォーム**] テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="0480c-113">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="0480c-114">既定の名前 (**WebForm1**) をそのまま使用し、[ **追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0480c-114">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="0480c-115">**ソース**ビューで*WebForm1*が開きます。</span><span class="sxs-lookup"><span data-stu-id="0480c-115">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="0480c-116">タグ内に次のマークアップを追加し **\<body>** ます。</span><span class="sxs-lookup"><span data-stu-id="0480c-116">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="0480c-117">AJAX 対応 WCF サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="0480c-117">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="0480c-118">**ソリューションエクスプローラー**で SandwichServices プロジェクトを右クリックし、[ **Add**  >  **新しい項目**の追加] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0480c-118">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="0480c-119">[**新しい項目の追加**] ダイアログで、[**インストールされている**  >  **Visual C#**]  >  **Web**カテゴリを展開し、[ **WCF サービス (AJAX 対応)** ] テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="0480c-119">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![Visual Studio での WCF サービス (AJAX 対応) 項目テンプレート](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="0480c-121">サービスにサービスの **名前を指定** し、[ **追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0480c-121">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="0480c-122">*CostService.svc.cs* がエディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="0480c-122">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="0480c-123">サービスに操作を実装します。</span><span class="sxs-lookup"><span data-stu-id="0480c-123">Implement the operation in the service.</span></span> <span data-ttu-id="0480c-124">サンドイッチの数量のコストを計算するには、次のメソッドを cost Service クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="0480c-124">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="0480c-125">サービスにアクセスするようにクライアントを構成する</span><span class="sxs-lookup"><span data-stu-id="0480c-125">Configure the client to access the service</span></span>

1. <span data-ttu-id="0480c-126">*WebForm1*ファイルを開き、[**デザイン**] ビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="0480c-126">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="0480c-127">[ **表示** ] メニューの [ **ツールボックス**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0480c-127">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="0480c-128">[ **AJAX Extensions** ] ノードを展開し、 **ScriptManager** をフォームにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="0480c-128">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="0480c-129">**ソース**ビューに戻り、次のコードをタグの間に追加して、 **\<ScriptManager>** WCF サービスへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="0480c-129">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. <span data-ttu-id="0480c-130">JavaScript 関数のコードを追加 `Calculate()` します。</span><span class="sxs-lookup"><span data-stu-id="0480c-130">Add the code for the JavaScript function `Calculate()`.</span></span> <span data-ttu-id="0480c-131">次のコードを web フォームの **head** セクションに配置します。</span><span class="sxs-lookup"><span data-stu-id="0480c-131">Place the following code in the **head** section of the web form:</span></span>

    ```html
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
    ```

   <span data-ttu-id="0480c-132">このコードは、3つのサンドイッチの価格を計算するために、コストサービスのメソッドを呼び出し、 **additionResult**というスパンに結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="0480c-132">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="0480c-133">プログラムの実行</span><span class="sxs-lookup"><span data-stu-id="0480c-133">Run the program</span></span>

<span data-ttu-id="0480c-134">*WebForm1*にフォーカスがあることを確認し、[**開始**] ボタンをクリックして web クライアントを起動します。</span><span class="sxs-lookup"><span data-stu-id="0480c-134">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="0480c-135">ボタンには緑色の三角形が表示され、 **IIS Express (Microsoft Edge)** のようなものが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0480c-135">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="0480c-136">または、 <kbd>F5</kbd>キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0480c-136">Or, you can press <kbd>F5</kbd>.</span></span> <span data-ttu-id="0480c-137">[ **Price-3 サンドイッチ** ] ボタンをクリックして、予想される出力 "3.75" を生成します。</span><span class="sxs-lookup"><span data-stu-id="0480c-137">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example"></a><span data-ttu-id="0480c-138">例</span><span class="sxs-lookup"><span data-stu-id="0480c-138">Example</span></span>

<span data-ttu-id="0480c-139">*CostService.svc.cs*ファイルの完全なコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0480c-139">The following is the full code in the *CostService.svc.cs* file:</span></span>

```csharp
using System.ServiceModel;
using System.ServiceModel.Activation;

namespace SandwichServices
{
    [ServiceContract(Namespace = "")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class CostService
    {
        [OperationContract]
        public double CostOfSandwiches(int quantity)
        {
            return 1.25 * quantity;
        }
    }
}
```

<span data-ttu-id="0480c-140">次に、 *WebForm1* ページの完全な内容を示します。</span><span class="sxs-lookup"><span data-stu-id="0480c-140">The following is the full contents of the *WebForm1.aspx* page:</span></span>

```aspx-csharp
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SandwichServices.WebForm1" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
</head>
<body>
    <form id="form1" runat="server">
        <div>
        </div>
        <asp:ScriptManager ID="ScriptManager1" runat="server">
            <Services>
                <asp:ServiceReference Path="~/CostService.svc" />
            </Services>
        </asp:ScriptManager>

        <input type="button" value="Price of 3 sandwiches" onclick="Calculate()" />
        <br />
        <span id="additionResult"></span>
    </form>
</body>
</html>
```
