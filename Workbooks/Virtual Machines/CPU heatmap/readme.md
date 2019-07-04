# <a name="cpu-heatmap"></a><span data-ttu-id="e85bc-101">mapa de calor da CPU</span><span class="sxs-lookup"><span data-stu-id="e85bc-101">CPU heatmap</span></span>

<span data-ttu-id="e85bc-102">Esta pasta de trabalho é uma boa maneira de visualizar os pontos de acesso no uso da CPU de suas máquinas virtuais.</span><span class="sxs-lookup"><span data-stu-id="e85bc-102">This workbook is a good way to visualize hot spots in the CPU utilization of your virtual machines.</span></span>

![Ilustre o mapa de calor de uma CPU](cpu-heatmap.png)

## <a name="changing-the-cpu-threshold"></a><span data-ttu-id="e85bc-104">Alteração do limite da CPU</span><span class="sxs-lookup"><span data-stu-id="e85bc-104">Changing the CPU threshold</span></span>
<span data-ttu-id="e85bc-105">Por padrão, esta pasta de trabalho destaca as máquinas virtuais com `Percentage CPU` médio maior que 75%.</span><span class="sxs-lookup"><span data-stu-id="e85bc-105">By default, this workbook highlights virtual machines with average `Percentage CPU` greater than 75%.</span></span> <span data-ttu-id="e85bc-106">Se você quiser que esse limite seja maior ou menor, eis as etapas a serem seguidas:</span><span class="sxs-lookup"><span data-stu-id="e85bc-106">If you wish for this threshold to be higher or lower, these are the steps for follow:</span></span>

1. <span data-ttu-id="e85bc-107">Clique no item `Edit` da barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="e85bc-107">Click the `Edit` item in the toolbar.</span></span>
2. <span data-ttu-id="e85bc-108">Clique no botão `↑ Edit`, na parte inferior direita do controle de hive.</span><span class="sxs-lookup"><span data-stu-id="e85bc-108">Click on the `↑ Edit` button to the bottom-right of the hive control.</span></span>
3. <span data-ttu-id="e85bc-109">Na lista `Columns Available After Merge`, role para baixo e selecione o item `[Added column] - Cell Color`.</span><span class="sxs-lookup"><span data-stu-id="e85bc-109">In the `Columns Available After Merge` list, scroll down and select the `[Added column] - Cell Color` item.</span></span>
4. <span data-ttu-id="e85bc-110">Clique no botão `Edit added item` da barra de ferramentas de controles de hive.</span><span class="sxs-lookup"><span data-stu-id="e85bc-110">Click on the `Edit added item` button in the hive controls toolbar.</span></span>
5. <span data-ttu-id="e85bc-111">No painel que se abre, clique em `Edit`, no item que diz `Percentage CPU > 75 Result is E8976A`, para ver um pop-up de configurações</span><span class="sxs-lookup"><span data-stu-id="e85bc-111">In the pane tha opens up, click `Edit` on the item that says `Percentage CPU > 75 Result is E8976A` to see a settings pop up</span></span>
    1. <span data-ttu-id="e85bc-112">Defina o campo `Second operand` com o limite desejado – digamos que seja 90.</span><span class="sxs-lookup"><span data-stu-id="e85bc-112">Set the `Second operand` field to the threshold you want - say 90.</span></span>
        <span data-ttu-id="e85bc-113">![Ilustre o mapa de calor de uma CPU](cpu-heatmap-column-settings.png)</span><span class="sxs-lookup"><span data-stu-id="e85bc-113">![Image a CPU heatmap](cpu-heatmap-column-settings.png)</span></span>
    2. <span data-ttu-id="e85bc-114">Clique em op no pop-up.</span><span class="sxs-lookup"><span data-stu-id="e85bc-114">Click op in the popup.</span></span>
6. <span data-ttu-id="e85bc-115">Clique em 'Salvar e fechar'</span><span class="sxs-lookup"><span data-stu-id="e85bc-115">Click 'Save and close'</span></span>
7. <span data-ttu-id="e85bc-116">Escolha `Done Editing` na barra de ferramentas da pasta de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e85bc-116">Choose `Done Editing` in the workbook toolbar.</span></span>
