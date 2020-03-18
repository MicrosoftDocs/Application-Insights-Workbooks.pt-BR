# <a name="picking-a-set-of-resources-to-analyze-in-workbooks"></a><span data-ttu-id="db9c7-101">Escolhendo um conjunto de recursos para analisar em pastas de trabalho</span><span class="sxs-lookup"><span data-stu-id="db9c7-101">Picking a set of resources to analyze in workbooks</span></span>

<span data-ttu-id="db9c7-102">O modelo de `Resource Picker` é iniciado com a assinatura, o grupo de recursos e os parâmetros de recurso para configurar o contexto de entrada da pasta de trabalho.</span><span class="sxs-lookup"><span data-stu-id="db9c7-102">The `Resource Picker` template gets you started with subscription, resource group and resource parameters to set up the input context of your workbook.</span></span> <span data-ttu-id="db9c7-103">Os parâmetros padrão são definidos para escolher máquinas virtuais, mas é possível configurá-lo para escolher qualquer tipo de recurso.</span><span class="sxs-lookup"><span data-stu-id="db9c7-103">The default parameters are set to pick virtual machines, but you can configure it to pick any type of resource.</span></span> <span data-ttu-id="db9c7-104">O modelo também tem um controle de consulta de ARG que mostra como usar os parâmetros em suas análises.</span><span class="sxs-lookup"><span data-stu-id="db9c7-104">The template also has a ARG query control that shows you how to use the parameters in your analyses.</span></span>

![Imagem](Full.png)

## <a name="setting-up-the-resource-type-to-pick"></a><span data-ttu-id="db9c7-106">Configurando o tipo de recurso a ser escolhido</span><span class="sxs-lookup"><span data-stu-id="db9c7-106">Setting up the resource type to pick</span></span>

1. <span data-ttu-id="db9c7-107">Clique em `Edit` na barra de ferramentas da pasta de trabalho.</span><span class="sxs-lookup"><span data-stu-id="db9c7-107">Hit `Edit` on the workbook toolbar.</span></span>
2. <span data-ttu-id="db9c7-108">Agora, você poderá ver uma lista suspensa `Resource type` antes de `Subscriptions`:</span><span class="sxs-lookup"><span data-stu-id="db9c7-108">You will now be able to see a drop down `Resource type` before `Subscriptions`:</span></span>

    ![Imagem](Parameter.png)
3. <span data-ttu-id="db9c7-110">Expanda a lista suspensa e selecione os tipos de recursos que você deseja separar.</span><span class="sxs-lookup"><span data-stu-id="db9c7-110">Expand the drop down and select the resource types you want picked.</span></span> <span data-ttu-id="db9c7-111">Isso atualizará a lista suspensa de assinatura, o grupo de recursos e os recursos para corresponder à sua seleção.</span><span class="sxs-lookup"><span data-stu-id="db9c7-111">This will update the subscription, resource group and resources drop down to match your selection.</span></span>
4. <span data-ttu-id="db9c7-112">Clique no botão `Edit` na parte inferior direita do controle de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="db9c7-112">Click the `Edit` button at the bottom right of the parameter control.</span></span>
5. <span data-ttu-id="db9c7-113">Na grade de parâmetros, para a linha `Resources`, altere a coluna `Display name` de _Máquinas virtuais_ para o nome amigável do tipo de recurso selecionado (por exemplo, _Contas de Armazenamento_)</span><span class="sxs-lookup"><span data-stu-id="db9c7-113">In the parameters grid, for the row `Resources`, change the `Display name` column from _Virtual machines_ to friendly name of your selected resource type (e.g. _Storage Accounts_)</span></span>
6. <span data-ttu-id="db9c7-114">Clique em `Done Editing` na barra de ferramentas das pastas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="db9c7-114">Click `Done Editing` in the workbooks toolbar.</span></span>

## <a name="selecting-more-or-less-than-10-resources-by-default"></a><span data-ttu-id="db9c7-115">Selecionando mais ou menos de 10 recursos por padrão</span><span class="sxs-lookup"><span data-stu-id="db9c7-115">Selecting more or less than 10 resources by default</span></span>

1. <span data-ttu-id="db9c7-116">Clique em `Edit` na barra de ferramentas da pasta de trabalho.</span><span class="sxs-lookup"><span data-stu-id="db9c7-116">Hit `Edit` on the workbook toolbar.</span></span>
2. <span data-ttu-id="db9c7-117">Clique no botão `Edit` na parte inferior direita do controle de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="db9c7-117">Click the `Edit` button at the bottom right of the parameter control.</span></span>
3. <span data-ttu-id="db9c7-118">Na grade de parâmetros, selecione a linha para `Resources`</span><span class="sxs-lookup"><span data-stu-id="db9c7-118">In the parameters grid, select the row for `Resources`</span></span>
4. <span data-ttu-id="db9c7-119">Clique na barra de ferramentas de controle de ícone `Edit` (ou no lápis).</span><span class="sxs-lookup"><span data-stu-id="db9c7-119">Click on the `Edit` (or pencil) icon control toolbar.</span></span>
5. <span data-ttu-id="db9c7-120">No painel de `Edit Parameter` que aparece, role para baixo até o editor de `Azure Resource Graph Query`.</span><span class="sxs-lookup"><span data-stu-id="db9c7-120">In the `Edit Parameter` pane that pops up, scroll down to the `Azure Resource Graph Query` editor.</span></span> <span data-ttu-id="db9c7-121">Ele deve ter uma consulta parecida com esta:</span><span class="sxs-lookup"><span data-stu-id="db9c7-121">It should have a query that looks like this:</span></span>
    ```sql
    Resources
    | where type in~({ResourceTypes})
    | extend resourceGroupId = strcat('/subscriptions/', subscriptionId, '/resourceGroups/', resourceGroup)
    | where resourceGroupId in~({ResourceGroups}) or '*' in~({ResourceGroups})
    | order by name asc
    | extend Rank = row_number()
    | project value = id, label = name, selected = Rank <= 10, group = resourceGroup
    ```
    <span data-ttu-id="db9c7-122">O código para a seleção de recursos está na última linha da consulta: `selected = Rank <= 10`.</span><span class="sxs-lookup"><span data-stu-id="db9c7-122">The code for resource selection is in the last line of the query: `selected = Rank <= 10`.</span></span> 

6. <span data-ttu-id="db9c7-123">Altere o valor de 10 para um diferente a fim de alterar a seleção padrão</span><span class="sxs-lookup"><span data-stu-id="db9c7-123">Change the value from 10 to a different one to change the default selection</span></span>