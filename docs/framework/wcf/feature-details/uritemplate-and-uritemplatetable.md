---
title: UriTemplate と UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: da34753867db17fd8ea1bd36bc705b3518d6d650
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976009"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="87f11-102">UriTemplate と UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="87f11-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="87f11-103">Web 開発者は、サービスの応答先となる URI の形状とレイアウトを記述できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="87f11-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="87f11-104">Windows Communication Foundation (WCF) では、開発者が自分の Uri を制御できるように、2つの新しいクラスが追加されました。</span><span class="sxs-lookup"><span data-stu-id="87f11-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="87f11-105"><xref:System.UriTemplate> と <xref:System.UriTemplateTable> は、WCF の URI ベースのディスパッチエンジンの基礎となります。</span><span class="sxs-lookup"><span data-stu-id="87f11-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="87f11-106">これらのクラスは、独自に使用することもできます。これにより、開発者は、WCF サービスを実装することなく、テンプレートと URI マッピング機構を利用できます。</span><span class="sxs-lookup"><span data-stu-id="87f11-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="87f11-107">テンプレート</span><span class="sxs-lookup"><span data-stu-id="87f11-107">Templates</span></span>  
 <span data-ttu-id="87f11-108">テンプレートとは、一連の相対 URI を記述する方法です。</span><span class="sxs-lookup"><span data-stu-id="87f11-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="87f11-109">次の表の URI テンプレートのセットは、各種気象情報を取得するシステムがどのように定義されているかを示しています。</span><span class="sxs-lookup"><span data-stu-id="87f11-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="87f11-110">データ</span><span class="sxs-lookup"><span data-stu-id="87f11-110">Data</span></span>|<span data-ttu-id="87f11-111">テンプレート</span><span class="sxs-lookup"><span data-stu-id="87f11-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="87f11-112">国の天気予報</span><span class="sxs-lookup"><span data-stu-id="87f11-112">National Forecast</span></span>|<span data-ttu-id="87f11-113">weather/national</span><span class="sxs-lookup"><span data-stu-id="87f11-113">weather/national</span></span>|  
|<span data-ttu-id="87f11-114">州の天気予報</span><span class="sxs-lookup"><span data-stu-id="87f11-114">State Forecast</span></span>|<span data-ttu-id="87f11-115">weather/{state}</span><span class="sxs-lookup"><span data-stu-id="87f11-115">weather/{state}</span></span>|  
|<span data-ttu-id="87f11-116">都市の天気予報</span><span class="sxs-lookup"><span data-stu-id="87f11-116">City Forecast</span></span>|<span data-ttu-id="87f11-117">weather/{state}/{city}</span><span class="sxs-lookup"><span data-stu-id="87f11-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="87f11-118">アクティビティの天気予報</span><span class="sxs-lookup"><span data-stu-id="87f11-118">Activity Forecast</span></span>|<span data-ttu-id="87f11-119">weather/{state}/{city}/{activity}</span><span class="sxs-lookup"><span data-stu-id="87f11-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="87f11-120">この表は、構造が似ている一連の URI を示しています。</span><span class="sxs-lookup"><span data-stu-id="87f11-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="87f11-121">各エントリが URI テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="87f11-121">Each entry is a URI template.</span></span> <span data-ttu-id="87f11-122">中かっこで囲まれたセグメントは変数を表します。</span><span class="sxs-lookup"><span data-stu-id="87f11-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="87f11-123">中かっこで囲まれていないセグメントはリテラル文字を表します。</span><span class="sxs-lookup"><span data-stu-id="87f11-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="87f11-124">WCF テンプレートクラスを使用すると、開発者は受信 URI ("/weather/wa/seattle/cycling" など) を取得し、それを説明するテンプレートに一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="87f11-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="87f11-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="87f11-125">UriTemplate</span></span>  
 <span data-ttu-id="87f11-126"><xref:System.UriTemplate> は、URI テンプレートをカプセル化するクラスです。</span><span class="sxs-lookup"><span data-stu-id="87f11-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="87f11-127">コンストラクターは、テンプレートを定義する文字列パラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="87f11-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="87f11-128">この文字列には、次のセクションで説明する形式のテンプレートが含まれます。</span><span class="sxs-lookup"><span data-stu-id="87f11-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="87f11-129"><xref:System.UriTemplate> クラスには、受信 URI をテンプレートと照合するメソッド、テンプレートから URI を生成するメソッド、テンプレートで使用されている変数名のコレクションを取得するメソッド、2 つのテンプレートが等しいかどうかを判断するメソッド、およびテンプレートの文字列を返すメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="87f11-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="87f11-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> は、ベース アドレスと候補となる URI を取得し、その URI をテンプレートと照合します。</span><span class="sxs-lookup"><span data-stu-id="87f11-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="87f11-131">URI とテンプレートが一致した場合は、<xref:System.UriTemplateMatch> インスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="87f11-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="87f11-132"><xref:System.UriTemplateMatch> オブジェクトには、ベース URI、候補となる URI、クエリ パラメーターの名前/値コレクション、相対パス セグメントの配列、一致した変数の名前/値コレクション、照合を実行する際に使用する <xref:System.UriTemplate> インスタンス、候補となる URI の一致していない部分を含む文字列 (テンプレートにワイルドカードが含まれているときに使用)、およびテンプレートに関連付けられたオブジェクトが格納されます。</span><span class="sxs-lookup"><span data-stu-id="87f11-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87f11-133"><xref:System.UriTemplate> クラスは、候補となる URI をテンプレートと照合するときにスキームとポート番号を無視します。</span><span class="sxs-lookup"><span data-stu-id="87f11-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="87f11-134">テンプレートから URI を生成できるメソッドとして、<xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> と <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> の 2 つのメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="87f11-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="87f11-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> は、ベース アドレスおよびパラメーターの名前/値コレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="87f11-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="87f11-136">テンプレートのバインド時に、これらのパラメーターが変数に代入されます。</span><span class="sxs-lookup"><span data-stu-id="87f11-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="87f11-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> は、名前と値のペアを取得し、これらのペアを左から右の順に代入します。</span><span class="sxs-lookup"><span data-stu-id="87f11-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="87f11-138"><xref:System.UriTemplate.ToString> は、テンプレート文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="87f11-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="87f11-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A> プロパティには、テンプレート文字列のパス セグメント内で使用される変数の名前のコレクションが格納されます。</span><span class="sxs-lookup"><span data-stu-id="87f11-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="87f11-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> は <xref:System.UriTemplate> をパラメーターとして受け取り、2 つのテンプレートが等しいかどうかを示すブール値を返します。</span><span class="sxs-lookup"><span data-stu-id="87f11-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="87f11-141">詳細については、このトピックで後述する「テンプレートの等価性」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87f11-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="87f11-142"><xref:System.UriTemplate> は、HTTP URI 文法に準じるすべての URI スキームで使用できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="87f11-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="87f11-143">サポートされている URI スキームの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="87f11-143">The following are examples of supported URI schemes.</span></span>  
  
- <span data-ttu-id="87f11-144">http://</span><span class="sxs-lookup"><span data-stu-id="87f11-144">http://</span></span>  
  
- <span data-ttu-id="87f11-145">https://</span><span class="sxs-lookup"><span data-stu-id="87f11-145">https://</span></span>  
  
- <span data-ttu-id="87f11-146">net.tcp://</span><span class="sxs-lookup"><span data-stu-id="87f11-146">net.tcp://</span></span>  
  
- <span data-ttu-id="87f11-147">net.pipe://</span><span class="sxs-lookup"><span data-stu-id="87f11-147">net.pipe://</span></span>  
  
- <span data-ttu-id="87f11-148">sb://</span><span class="sxs-lookup"><span data-stu-id="87f11-148">sb://</span></span>  
  
 <span data-ttu-id="87f11-149">file:// や urn:// などのスキームは、HTTP URI 文法に準じていません。このため、URI テンプレートで使用すると予期せぬ結果が発生します。</span><span class="sxs-lookup"><span data-stu-id="87f11-149">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="87f11-150">テンプレート文字列の構文</span><span class="sxs-lookup"><span data-stu-id="87f11-150">Template String Syntax</span></span>  
 <span data-ttu-id="87f11-151">テンプレートには、パス、クエリ (省略可能)、およびフラグメント (省略可能) の 3 つの部分があります。</span><span class="sxs-lookup"><span data-stu-id="87f11-151">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="87f11-152">テンプレートの一例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="87f11-152">For an example, see the following template:</span></span>  
  
`"/weather/{state}/{city}?forecast={length)#frag1`  
  
 <span data-ttu-id="87f11-153">パスは "/weather/{state}/{city}"、クエリは "?forecast={length}、フラグメントは "#frag1" でそれぞれ構成されています。</span><span class="sxs-lookup"><span data-stu-id="87f11-153">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="87f11-154">パス式では、先頭と末尾のスラッシュは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="87f11-154">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="87f11-155">クエリ式とフラグメント式は、いずれも式全体を省略できます。</span><span class="sxs-lookup"><span data-stu-id="87f11-155">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="87f11-156">パスは、'/' で区切られた一連のセグメントで構成されます。各セグメントには、リテラル値、変数名 ({中かっこ} で記述)、またはワイルドカード ('\*' として記述) を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="87f11-156">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="87f11-157">上記のテンプレートでは、"/weather/" セグメントがリテラル値で、"{state}" と "{city}" が変数です。</span><span class="sxs-lookup"><span data-stu-id="87f11-157">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="87f11-158">変数の名前は中かっこの内容から取得され、後で具象値に置き換えて*終了 URI*を作成できます。</span><span class="sxs-lookup"><span data-stu-id="87f11-158">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="87f11-159">ワイルドカードは省略可能ですが、URI の末尾でのみ使用できます。この場合、"残りのパス" と論理的に一致します。</span><span class="sxs-lookup"><span data-stu-id="87f11-159">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="87f11-160">クエリ式が存在する場合は、' & ' で区切られた一連の順序付けられていない名前と値のペアを指定します。</span><span class="sxs-lookup"><span data-stu-id="87f11-160">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="87f11-161">クエリ式の要素には、リテラル ペア (x=2) または変数ペア (x={var}) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="87f11-161">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="87f11-162">変数を指定できるのはクエリ式の右辺のみです。</span><span class="sxs-lookup"><span data-stu-id="87f11-162">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="87f11-163">({someName} = {someValue}) は指定できません。</span><span class="sxs-lookup"><span data-stu-id="87f11-163">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="87f11-164">対になっていない値 (?x) は使用できません。</span><span class="sxs-lookup"><span data-stu-id="87f11-164">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="87f11-165">空のクエリ式と、1 つの '?' だけで構成されたクエリ式は同じものです (いずれも "任意のクエリ" を意味します)。</span><span class="sxs-lookup"><span data-stu-id="87f11-165">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="87f11-166">フラグメント式はリテラル値で構成できます。変数は使用できません。</span><span class="sxs-lookup"><span data-stu-id="87f11-166">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="87f11-167">テンプレート文字列内のすべてのテンプレート変数名は、一意であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="87f11-167">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="87f11-168">テンプレート変数名では、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="87f11-168">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="87f11-169">有効なテンプレート文字列の例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="87f11-169">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="87f11-170">""</span><span class="sxs-lookup"><span data-stu-id="87f11-170">""</span></span>  
  
- <span data-ttu-id="87f11-171">"/shoe"</span><span class="sxs-lookup"><span data-stu-id="87f11-171">"/shoe"</span></span>  
  
- <span data-ttu-id="87f11-172">"/shoe/\*"</span><span class="sxs-lookup"><span data-stu-id="87f11-172">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="87f11-173">"{shoe}/boat"</span><span class="sxs-lookup"><span data-stu-id="87f11-173">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="87f11-174">"{靴}/{boat}/bed/{quilt}"</span><span class="sxs-lookup"><span data-stu-id="87f11-174">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="87f11-175">"靴/{ボート}"</span><span class="sxs-lookup"><span data-stu-id="87f11-175">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="87f11-176">"靴/{ボート}/\*"</span><span class="sxs-lookup"><span data-stu-id="87f11-176">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="87f11-177">"靴/ボート? x = 2"</span><span class="sxs-lookup"><span data-stu-id="87f11-177">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="87f11-178">"靴/{ボート}? x = {ベッド}"</span><span class="sxs-lookup"><span data-stu-id="87f11-178">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="87f11-179">"靴/{ボート}? x = {ベッド} & y = バンド"</span><span class="sxs-lookup"><span data-stu-id="87f11-179">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="87f11-180">"? x = {靴}"</span><span class="sxs-lookup"><span data-stu-id="87f11-180">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="87f11-181">"靴? x = 3 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="87f11-181">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="87f11-182">無効なテンプレート文字列の例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="87f11-182">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="87f11-183">"{靴}/{SHOE}/x = 2" –変数名が重複しています。</span><span class="sxs-lookup"><span data-stu-id="87f11-183">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="87f11-184">"{靴}/boat/? ベッド = {靴}" –変数名が重複しています。</span><span class="sxs-lookup"><span data-stu-id="87f11-184">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="87f11-185">"? x = 2 & x = 3" –クエリ文字列内の名前と値のペアは、リテラルであっても一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="87f11-185">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="87f11-186">"? x = 2 &" –クエリ文字列の形式が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="87f11-186">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="87f11-187">"? 2 & x = {靴}" –クエリ文字列は、名前と値のペアである必要があります。</span><span class="sxs-lookup"><span data-stu-id="87f11-187">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="87f11-188">"? y = 2 & & X = 3" –クエリ文字列は名前と値のペアである必要があります。名前の先頭を ' & ' にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="87f11-188">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="87f11-189">複合パス セグメント</span><span class="sxs-lookup"><span data-stu-id="87f11-189">Compound Path Segments</span></span>  
 <span data-ttu-id="87f11-190">複合パス セグメントでは、単一の URI パス セグメントに複数の変数およびリテラルと組み合わせた変数を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="87f11-190">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="87f11-191">有効な複合パス セグメントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="87f11-191">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="87f11-192">/filename.{ext}/</span><span class="sxs-lookup"><span data-stu-id="87f11-192">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="87f11-193">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="87f11-193">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="87f11-194">/{filename}.{ext}/</span><span class="sxs-lookup"><span data-stu-id="87f11-194">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="87f11-195">/{a}.{b}someLiteral{c}({d})/</span><span class="sxs-lookup"><span data-stu-id="87f11-195">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="87f11-196">無効なパス セグメントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="87f11-196">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="87f11-197">/{}-変数には名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="87f11-197">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="87f11-198">/{shoe}{boat} – 変数はリテラルによって分割されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="87f11-198">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="87f11-199">照合と複合パス セグメント</span><span class="sxs-lookup"><span data-stu-id="87f11-199">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="87f11-200">複合パス セグメントを使用すると、1 つのパス セグメント内に複数の変数を含む UriTemplate を定義できます。</span><span class="sxs-lookup"><span data-stu-id="87f11-200">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="87f11-201">たとえば、次のテンプレート文字列の場合は "Addresses/{state}" となります。{city} "2 つの変数 (都道府県と市) が同じセグメント内で定義されています。</span><span class="sxs-lookup"><span data-stu-id="87f11-201">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="87f11-202">このテンプレートは、`http://example.com/Washington.Redmond` などの URL と一致しますが、`http://example.com/Washington.Redmond.Microsoft`のような URL にも一致します。</span><span class="sxs-lookup"><span data-stu-id="87f11-202">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="87f11-203">後者の場合、州変数には "ワシントン" が含まれ、city 変数には "Redmond. Microsoft" が含まれます。</span><span class="sxs-lookup"><span data-stu-id="87f11-203">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="87f11-204">この場合、任意のテキスト ('/' 以外) が {city} 変数と一致することになります。</span><span class="sxs-lookup"><span data-stu-id="87f11-204">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="87f11-205">"Extra" テキストと一致しないテンプレートが必要な場合は、"Addresses/{state}/{city}" のように、別のテンプレートセグメントに変数を配置します。</span><span class="sxs-lookup"><span data-stu-id="87f11-205">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="87f11-206">名前付きワイルドカード セグメント</span><span class="sxs-lookup"><span data-stu-id="87f11-206">Named Wildcard Segments</span></span>  
 <span data-ttu-id="87f11-207">名前付きワイルドカードセグメントは、ワイルドカード文字 '\*' で始まる変数名を持つ任意のパス変数セグメントです。</span><span class="sxs-lookup"><span data-stu-id="87f11-207">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="87f11-208">次のテンプレート文字列には、"shoe" という名前付きワイルドカード セグメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="87f11-208">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
`"literal/{*shoe}"`  
  
 <span data-ttu-id="87f11-209">ワイルドカード セグメントは、次の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="87f11-209">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="87f11-210">1 つのテンプレート文字列に含められる名前付きワイルドカード セグメントは 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="87f11-210">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="87f11-211">名前付きワイルドカード セグメントは、パス内の右端のセグメントにある必要があります。</span><span class="sxs-lookup"><span data-stu-id="87f11-211">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="87f11-212">名前付きワイルドカード セグメントは、匿名ワイルドカード セグメントのあるテンプレート文字列には使用できません。</span><span class="sxs-lookup"><span data-stu-id="87f11-212">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="87f11-213">名前付きワイルドカード セグメントの名前は一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="87f11-213">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="87f11-214">名前付きワイルドカード セグメントには既定値を指定できません。</span><span class="sxs-lookup"><span data-stu-id="87f11-214">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="87f11-215">名前付きワイルドカードセグメントの末尾を "/" にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="87f11-215">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="87f11-216">既定変数値</span><span class="sxs-lookup"><span data-stu-id="87f11-216">Default Variable Values</span></span>  
 <span data-ttu-id="87f11-217">既定変数値を使用すると、テンプレート内で変数に既定値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="87f11-217">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="87f11-218">既定変数は、変数を宣言する中かっこを使用して指定することも、UriTemplate コンストラクターに渡されるコレクションとして指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="87f11-218">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="87f11-219">次のテンプレートに、既定値のある変数を使用して <xref:System.UriTemplate> を指定する 2 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="87f11-219">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="87f11-220">このテンプレートでは、既定値が `a` で `1` という名前の変数と、既定値が `b` で `5` という名前の変数が宣言されています。</span><span class="sxs-lookup"><span data-stu-id="87f11-220">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87f11-221">パス セグメント変数のみが、既定値を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="87f11-221">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="87f11-222">クエリ文字列変数、複合セグメント変数、および名前付きワイルドカード変数には、既定値を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="87f11-222">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="87f11-223">候補 URI との照合時に、既定値のある変数がどのように処理されるかを次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="87f11-223">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");

UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);
Uri candidate = new Uri("http://localhost:8000/OR");

UriTemplateMatch m1 = t.Match(baseAddress, candidate);

Console.WriteLine($"Template: {t}");
Console.WriteLine($"Candidate URI: {candidate}");

// Display contents of BoundVariables
Console.WriteLine("BoundVariables:");
foreach (string key in m1.BoundVariables.AllKeys)
{
    Console.WriteLine($"\t{key}={m1.BoundVariables[key]}");
}
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/
// Candidate URI: http://localhost:8000/OR
// BoundVariables:
//         STATE=OR
//         CITY=Redmond
```  
  
> [!NOTE]
> <span data-ttu-id="87f11-224">`http://localhost:8000///` などの URI が、前のコードに記載されているテンプレートと一致しません。ただし、`http://localhost:8000/` などの URI は同じです。</span><span class="sxs-lookup"><span data-stu-id="87f11-224">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="87f11-225">テンプレートを使用して URI を作成する場合に、既定値のある変数がどのように処理されるかを次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="87f11-225">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
<span data-ttu-id="87f11-226">変数の既定値として `null` が指定されている場合、さらに追加の制約があります。</span><span class="sxs-lookup"><span data-stu-id="87f11-226">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="87f11-227">テンプレート文字列の右端のセグメントに変数を含んでいるか、その変数の右側にあるすべてのセグメントが `null` を既定値としている変数のみに既定値として `null` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="87f11-227">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="87f11-228">既定値に `null` が指定されている有効なテンプレート文字列を次に示します。</span><span class="sxs-lookup"><span data-stu-id="87f11-228">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="87f11-229">既定値が `null`の無効なテンプレート文字列を次に示します。</span><span class="sxs-lookup"><span data-stu-id="87f11-229">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="87f11-230">既定値と照合</span><span class="sxs-lookup"><span data-stu-id="87f11-230">Default Values and Matching</span></span>  
 <span data-ttu-id="87f11-231">候補 URI と既定値が指定されているテンプレートとの照合時に、候補 URI に値が指定されていない場合には、<xref:System.UriTemplateMatch.BoundVariables%2A> コレクションに既定値が配置されます。</span><span class="sxs-lookup"><span data-stu-id="87f11-231">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="87f11-232">テンプレートの等価性</span><span class="sxs-lookup"><span data-stu-id="87f11-232">Template Equivalence</span></span>  
 <span data-ttu-id="87f11-233">すべてのテンプレートのリテラルが一致し、同じセグメントに変数がある場合、2つのテンプレートは*構造的に同等*であると言われます。</span><span class="sxs-lookup"><span data-stu-id="87f11-233">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="87f11-234">たとえば、次のテンプレートは構造的に等しいテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="87f11-234">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="87f11-235">/a/{var1}/b b/{var2}? x = 1 & y = 2</span><span class="sxs-lookup"><span data-stu-id="87f11-235">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="87f11-236">a/{x}/b% 20b/{var1}? y = 2 & x = 1</span><span class="sxs-lookup"><span data-stu-id="87f11-236">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="87f11-237">a/{y}/B% 20B/{z}/? y = 2 & x = 1</span><span class="sxs-lookup"><span data-stu-id="87f11-237">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="87f11-238">次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="87f11-238">A few things to notice:</span></span>  
  
- <span data-ttu-id="87f11-239">テンプレートに先頭のスラッシュが含まれている場合、最初の 1 つだけが無視されます。</span><span class="sxs-lookup"><span data-stu-id="87f11-239">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="87f11-240">テンプレート文字列が構造的に等しいかどうかを比較する場合、変数名とパス セグメントでは大文字小文字は無視されますが、クエリ文字列では区別されます。</span><span class="sxs-lookup"><span data-stu-id="87f11-240">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="87f11-241">クエリ文字列は順序なしです。</span><span class="sxs-lookup"><span data-stu-id="87f11-241">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="87f11-242">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="87f11-242">UriTemplateTable</span></span>  
 <span data-ttu-id="87f11-243"><xref:System.UriTemplateTable> クラスは、開発者が選択したオブジェクトにバインドされた <xref:System.UriTemplate> オブジェクトの結合テーブルを表します。</span><span class="sxs-lookup"><span data-stu-id="87f11-243">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="87f11-244"><xref:System.UriTemplateTable> を呼び出す前に、<xref:System.UriTemplate> に 1 つ以上の <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> を含めておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="87f11-244">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="87f11-245"><xref:System.UriTemplateTable> が呼び出されるまでは、<xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> の内容を変更できます。</span><span class="sxs-lookup"><span data-stu-id="87f11-245">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="87f11-246"><xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> が呼び出されると、検証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="87f11-246">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="87f11-247">実行される検証の種類は、`allowMultiple` に対する <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> パラメーターの値によって異なります。</span><span class="sxs-lookup"><span data-stu-id="87f11-247">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="87f11-248"><xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> を渡して `false` を呼び出した場合、<xref:System.UriTemplateTable> はテーブル内に複数のテンプレートが存在しないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="87f11-248">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="87f11-249">構造的に等しいテンプレートが見つかった場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="87f11-249">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="87f11-250">これは、受信 URI と一致するテンプレートが 1 つだけであることを確認する場合に、<xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> と組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="87f11-250">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="87f11-251"><xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> を渡して `true` を呼び出した場合、<xref:System.UriTemplateTable> は、構造的に等しい複数のテンプレートが <xref:System.UriTemplateTable> に含まれることを許可します。</span><span class="sxs-lookup"><span data-stu-id="87f11-251">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="87f11-252"><xref:System.UriTemplate> に追加された一連の <xref:System.UriTemplateTable> オブジェクトにクエリ文字列が含まれている場合、これらの文字列をあいまいにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="87f11-252">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="87f11-253">許可されるのは同一のクエリ文字列です。</span><span class="sxs-lookup"><span data-stu-id="87f11-253">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87f11-254"><xref:System.UriTemplateTable> では、HTTP 以外のスキームを使用したベース アドレスを使用できますが、候補 URI をテンプレートと照合する場合にスキームおよびポート番号は無視されます。</span><span class="sxs-lookup"><span data-stu-id="87f11-254">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="87f11-255">クエリ文字列のあいまいさ</span><span class="sxs-lookup"><span data-stu-id="87f11-255">Query String Ambiguity</span></span>  
 <span data-ttu-id="87f11-256">複数のテンプレートと一致する URI が存在する場合、等しいパスを共有するテンプレートにあいまいなクエリ文字列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="87f11-256">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="87f11-257">クエリ文字列の次のセットにはあいまいさはありません。</span><span class="sxs-lookup"><span data-stu-id="87f11-257">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="87f11-258">?x=1</span><span class="sxs-lookup"><span data-stu-id="87f11-258">?x=1</span></span>  
  
- <span data-ttu-id="87f11-259">?x=2</span><span class="sxs-lookup"><span data-stu-id="87f11-259">?x=2</span></span>  
  
- <span data-ttu-id="87f11-260">?x=3</span><span class="sxs-lookup"><span data-stu-id="87f11-260">?x=3</span></span>  
  
- <span data-ttu-id="87f11-261">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="87f11-261">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="87f11-262">? x = 2 & z = {var}</span><span class="sxs-lookup"><span data-stu-id="87f11-262">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="87f11-263">?x=3</span><span class="sxs-lookup"><span data-stu-id="87f11-263">?x=3</span></span>  
  
- <span data-ttu-id="87f11-264">?x=1</span><span class="sxs-lookup"><span data-stu-id="87f11-264">?x=1</span></span>  
  
- <span data-ttu-id="87f11-265">?</span><span class="sxs-lookup"><span data-stu-id="87f11-265">?</span></span>  
  
- <span data-ttu-id="87f11-266">?</span><span class="sxs-lookup"><span data-stu-id="87f11-266">?</span></span> <span data-ttu-id="87f11-267">x={var}</span><span class="sxs-lookup"><span data-stu-id="87f11-267">x={var}</span></span>  
  
- <span data-ttu-id="87f11-268">?</span><span class="sxs-lookup"><span data-stu-id="87f11-268">?</span></span>  
  
- <span data-ttu-id="87f11-269">? m = get & c = rss</span><span class="sxs-lookup"><span data-stu-id="87f11-269">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="87f11-270">? m = put & c = rss</span><span class="sxs-lookup"><span data-stu-id="87f11-270">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="87f11-271">? m = get & c = atom</span><span class="sxs-lookup"><span data-stu-id="87f11-271">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="87f11-272">? m = put & c = atom</span><span class="sxs-lookup"><span data-stu-id="87f11-272">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="87f11-273">クエリ文字列テンプレートの次のセットにはあいまいさがあります。</span><span class="sxs-lookup"><span data-stu-id="87f11-273">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="87f11-274">?x=1</span><span class="sxs-lookup"><span data-stu-id="87f11-274">?x=1</span></span>  
  
- <span data-ttu-id="87f11-275">?x={var}</span><span class="sxs-lookup"><span data-stu-id="87f11-275">?x={var}</span></span>  
  
 <span data-ttu-id="87f11-276">"x=1" - 両方のテンプレートに一致します。</span><span class="sxs-lookup"><span data-stu-id="87f11-276">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="87f11-277">?x=1</span><span class="sxs-lookup"><span data-stu-id="87f11-277">?x=1</span></span>  
  
- <span data-ttu-id="87f11-278">?y=2</span><span class="sxs-lookup"><span data-stu-id="87f11-278">?y=2</span></span>  
  
 <span data-ttu-id="87f11-279">"x = 1 & y = 2" は両方のテンプレートに一致します。</span><span class="sxs-lookup"><span data-stu-id="87f11-279">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="87f11-280">これは、クエリ文字列に、一致するテンプレートよりも多くのクエリ文字列変数が含まれている可能性があるからです。</span><span class="sxs-lookup"><span data-stu-id="87f11-280">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="87f11-281">?x=1</span><span class="sxs-lookup"><span data-stu-id="87f11-281">?x=1</span></span>  
  
- <span data-ttu-id="87f11-282">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="87f11-282">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="87f11-283">"x = 1 & y = 3" は両方のテンプレートに一致します。</span><span class="sxs-lookup"><span data-stu-id="87f11-283">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="87f11-284">? x = 3 & y = 4</span><span class="sxs-lookup"><span data-stu-id="87f11-284">?x=3&y=4</span></span>  
  
- <span data-ttu-id="87f11-285">? x = 3 & z = 5</span><span class="sxs-lookup"><span data-stu-id="87f11-285">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87f11-286">文字 á と Á が URI パスまたは <xref:System.UriTemplate> のパス セグメントのリテラルの一部として出現した場合、これらは異なる文字と見なされます (ただし、a と A は同じ文字と見なされます)。</span><span class="sxs-lookup"><span data-stu-id="87f11-286">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="87f11-287">文字 á と Á が <xref:System.UriTemplate> の {variableName} またはクエリ文字列の一部として出現した場合は、これらは同じ文字と見なされます (a と A も同じ文字と見なされます)。</span><span class="sxs-lookup"><span data-stu-id="87f11-287">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f11-288">関連項目</span><span class="sxs-lookup"><span data-stu-id="87f11-288">See also</span></span>

- [<span data-ttu-id="87f11-289">WCF Web HTTP プログラミング モデルの概要</span><span class="sxs-lookup"><span data-stu-id="87f11-289">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="87f11-290">WCF Web HTTP プログラミング オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="87f11-290">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="87f11-291">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="87f11-291">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [<span data-ttu-id="87f11-292">UriTemplate テーブル</span><span class="sxs-lookup"><span data-stu-id="87f11-292">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="87f11-293">UriTemplate テーブル ディスパッチャー</span><span class="sxs-lookup"><span data-stu-id="87f11-293">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
