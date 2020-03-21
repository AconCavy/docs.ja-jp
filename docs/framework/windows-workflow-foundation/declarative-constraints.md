---
title: 宣言の制約
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: 321021e3d73daecae07268f33807c992414a7b4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182959"
---
# <a name="declarative-constraints"></a><span data-ttu-id="3781d-102">宣言の制約</span><span class="sxs-lookup"><span data-stu-id="3781d-102">Declarative Constraints</span></span>
<span data-ttu-id="3781d-103">宣言の制約には、アクティビティ、およびそのアクティビティと他のアクティビティとの関係に関する検証の強力なメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3781d-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="3781d-104">アクティビティに関する制約はプロセスの作成中に構成されますが、ワークフロー ホストによって追加の制約を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3781d-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="3781d-105">ここでは、宣言の制約を使用してアクティビティを検証する方法の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="3781d-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="3781d-106">宣言の制約の使用</span><span class="sxs-lookup"><span data-stu-id="3781d-106">Using Declarative Constraints</span></span>  
 <span data-ttu-id="3781d-107">制約とは、検証ロジックを含むアクティビティです。</span><span class="sxs-lookup"><span data-stu-id="3781d-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="3781d-108">この制約アクティビティは、コードまたは XAML で作成できます。</span><span class="sxs-lookup"><span data-stu-id="3781d-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="3781d-109">制約アクティビティを作成したら、アクティビティの作成者はアクティビティの <xref:System.Activities.Activity.Constraints%2A> プロパティにこの制約を追加して検証を実行します。またはこの制約を使用して、<xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> インスタンスの <xref:System.Activities.Validation.ValidationSettings> プロパティを使った追加の検証を実行します。</span><span class="sxs-lookup"><span data-stu-id="3781d-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="3781d-110">検証ロジックは、アクティビティのメタデータの検証など、単純な検証で構成されますが、親アクティビティ、子アクティビティ、および兄弟アクティビティに対する現在のアクティビティの関係を考慮した検証を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="3781d-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="3781d-111">制約は、<xref:System.Activities.Validation.Constraint%601> アクティビティを使用して作成されます。また、検証のエラーと警告の作成を補助し、ワークフロー内の関連するアクティビティに関する情報を提供する追加の検証アクティビティがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="3781d-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="3781d-112">AssertValidation と AddValidationError</span><span class="sxs-lookup"><span data-stu-id="3781d-112">AssertValidation and AddValidationError</span></span>  
 <span data-ttu-id="3781d-113"><xref:System.Activities.Validation.AssertValidation> アクティビティは、その <xref:System.Activities.Validation.AssertValidation.Assertion%2A> プロパティから参照される式を評価します。また、式が `false` に評価されると、検証のエラーまたは警告が <xref:System.Activities.Validation.ValidationResults> に追加されます。</span><span class="sxs-lookup"><span data-stu-id="3781d-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="3781d-114"><xref:System.Activities.Validation.AssertValidation.Message%2A> プロパティは検証エラーを示し、<xref:System.Activities.Validation.AssertValidation.IsWarning%2A> は検証の失敗がエラーか警告かを指定します。</span><span class="sxs-lookup"><span data-stu-id="3781d-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="3781d-115"><xref:System.Activities.Validation.AssertValidation.IsWarning%2A> の既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="3781d-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="3781d-116">次の例では、検証対象のアクティビティの <xref:System.Activities.Activity.DisplayName%2A> が 2 文字以下の場合、検証の警告を返す制約を宣言します。</span><span class="sxs-lookup"><span data-stu-id="3781d-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="3781d-117"><xref:System.Activities.Validation.Constraint%601> に使用されるジェネリック型パラメーターには、この制約によって検証されるアクティビティの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="3781d-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="3781d-118">この制約では、ジェネリック型として <xref:System.Activities.Activity> を使用します。この制約はすべての種類のアクティビティに使用できます。</span><span class="sxs-lookup"><span data-stu-id="3781d-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
```csharp  
public static Constraint ActivityDisplayNameIsNotSetWarning()  
{  
    DelegateInArgument<Activity> element = new DelegateInArgument<Activity>();  
  
    return new Constraint<Activity>  
    {  
        Body = new ActivityAction<Activity, ValidationContext>  
        {  
            Argument1 = element,  
            Handler = new AssertValidation  
            {  
                IsWarning = true,  
                Assertion = new InArgument<bool>(env => (element.Get(env).DisplayName.Length > 2)),  
                Message = new InArgument<string>("It is a best practice to have a DisplayName of more than 2 characters."),  
            }  
        }  
    };  
}  
```  
  
 <span data-ttu-id="3781d-119">あるアクティビティに対してこの制約を指定するには、次のコード例のように、アクティビティの <xref:System.Activities.Activity.Constraints%2A> に追加します。</span><span class="sxs-lookup"><span data-stu-id="3781d-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
```csharp  
public sealed class SampleActivity : CodeActivity  
{  
    public SampleActivity()  
    {  
        base.Constraints.Add(ActivityDisplayNameIsNotSetWarning());  
    }  
  
    // Activity implementation omitted.  
}  
```  
  
 <span data-ttu-id="3781d-120">また、ホストは <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> を使用してワークフローでアクティビティの制約を指定することもできます。この方法については、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="3781d-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="3781d-121"><xref:System.Activities.Validation.AddValidationError> アクティビティは、式を評価せずに、検証のエラーまたは警告を生成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3781d-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="3781d-122">このプロパティは <xref:System.Activities.Validation.AssertValidation> に似ており、<xref:System.Activities.Statements.If> アクティビティなど、制約のフロー コントロール アクティビティと併用できます。</span><span class="sxs-lookup"><span data-stu-id="3781d-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="3781d-123">ワークフロー関係のアクティビティ</span><span class="sxs-lookup"><span data-stu-id="3781d-123">Workflow Relationship Activities</span></span>

<span data-ttu-id="3781d-124">複数の検証アクティビティが使用できます。これにより検証されるアクティビティに関連してワークフロー内の他のアクティビティに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="3781d-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="3781d-125"><xref:System.Activities.Validation.GetParentChain> は現在のアクティビティとルート アクティビティ間のすべてのアクティビティを含むアクティビティのコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="3781d-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="3781d-126"><xref:System.Activities.Validation.GetChildSubtree> は再帰パターンで子アクティビティを含むアクティビティのコレクションを提供し、<xref:System.Activities.Validation.GetWorkflowTree> はワークフロー中のすべてのアクティビティを取得します。</span><span class="sxs-lookup"><span data-stu-id="3781d-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
<span data-ttu-id="3781d-127">次の例では、 `CreateState` アクティビティを定義します。</span><span class="sxs-lookup"><span data-stu-id="3781d-127">In the following example, a `CreateState` activity is defined.</span></span> <span data-ttu-id="3781d-128">`CreateState` アクティビティは `CreateCountry` アクティビティ内に含まれる必要があり、`GetParent` メソッドはこの要件を強制する制約を返します。</span><span class="sxs-lookup"><span data-stu-id="3781d-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="3781d-129">`GetParent` は <xref:System.Activities.Validation.GetParentChain> アクティビティを <xref:System.Activities.Statements.ForEach%601> アクティビティと組み合わせて使用し、`CreateState` のアクティビティの親アクティビティを確認し、要件を満たしているかどうか判断します。</span><span class="sxs-lookup"><span data-stu-id="3781d-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
```csharp  
public sealed class CreateState : CodeActivity  
{  
    public CreateState()  
    {  
        base.Constraints.Add(CheckParent());  
        this.Cities = new List<Activity>();
    }  
  
    public List<Activity> Cities { get; set; }  
  
    public string Name { get; set; }
  
    static Constraint CheckParent()  
    {  
        DelegateInArgument<CreateState> element = new DelegateInArgument<CreateState>();  
        DelegateInArgument<ValidationContext> context = new DelegateInArgument<ValidationContext>();
        Variable<bool> result = new Variable<bool>();  
        DelegateInArgument<Activity> parent = new DelegateInArgument<Activity>();  
  
        return new Constraint<CreateState>  
        {
            Body = new ActivityAction<CreateState,ValidationContext>  
            {
                Argument1 = element,  
                Argument2 = context,  
                Handler = new Sequence  
                {  
                    Variables =  
                    {  
                        result
                    },  
                    Activities =  
                    {  
                        new ForEach<Activity>  
                        {
                            Values = new GetParentChain  
                            {  
                                ValidationContext = context
                            },  
                            Body = new ActivityAction<Activity>  
                            {
                                Argument = parent,
                                Handler = new If()  
                                {
                                    Condition = new InArgument<bool>((env) => object.Equals(parent.Get(env).GetType(),typeof(CreateCountry))),
                                    Then = new Assign<bool>  
                                    {  
                                        Value = true,  
                                        To = result  
                                    }  
                                }  
                            }
                        },  
                        new AssertValidation  
                        {  
                            Assertion = new InArgument<bool>(result),  
                            Message = new InArgument<string> ("CreateState has to be inside a CreateCountry activity"),
                        }  
                    }  
                }  
            }  
        };  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // not needed for the sample  
    }  
}  
```
  
## <a name="additional-constraints"></a><span data-ttu-id="3781d-130">追加の制約</span><span class="sxs-lookup"><span data-stu-id="3781d-130">Additional Constraints</span></span>  
 <span data-ttu-id="3781d-131">ワークフロー ホスト作成者は、ワークフロー内のアクティビティに追加の検証の制約を指定できます。この場合、制約を作成し、それを <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> インスタンスの <xref:System.Activities.Validation.ValidationSettings> ディクショナリに追加します。</span><span class="sxs-lookup"><span data-stu-id="3781d-131">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="3781d-132"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> の各アイテムには、制約の適用対象であるアクティビティの種類と、その種類のアクティビティに対する追加の制約一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3781d-132">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="3781d-133">ワークフローで検証が呼び出されると、派生クラスを含め、指定した種類の各アクティビティは制約を評価します。</span><span class="sxs-lookup"><span data-stu-id="3781d-133">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="3781d-134">この例では、前のセクションの `ActivityDisplayNameIsNotSetWarning` 制約は、ワークフロー内のすべてのアクティビティに適用されます。</span><span class="sxs-lookup"><span data-stu-id="3781d-134">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
```csharp  
Activity wf = new Sequence  
{  
    // Workflow Details Omitted.  
};  
  
ValidationSettings settings = new ValidationSettings()  
{  
  
    AdditionalConstraints =  
    {  
        {typeof(Activity), new List<Constraint> {ActivityDisplayNameIsNotSetWarning()}},
    }  
};  
  
// Validate the workflow.  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
// Evaluate the results.  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error in " + error.Source.DisplayName + ": " + error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning in " + warning.Source.DisplayName + ": " + warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="3781d-135"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> の <xref:System.Activities.Validation.ValidationSettings> プロパティが `true` の場合、<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> を呼び出すことで検証が開始されると、指定した追加の制約のみが評価されます。</span><span class="sxs-lookup"><span data-stu-id="3781d-135">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="3781d-136">これは、特定の検証の構成についてワークフローを調べる場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3781d-136">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="3781d-137">ただし、ワークフローを呼び出すときに、ワークフロー内で構成されている検証ロジックが評価され、ワークフローが正常に開始するようにこれに合格する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3781d-137">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> <span data-ttu-id="3781d-138">検証の呼び出しの詳細については、「[アクティビティ検証の呼び出し](invoking-activity-validation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3781d-138">For more information about invoking validation, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>
