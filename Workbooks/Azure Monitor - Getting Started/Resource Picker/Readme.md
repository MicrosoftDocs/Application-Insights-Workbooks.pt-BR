# <a name="picking-a-set-of-resources-to-analyze-in-workbooks"></a>Escolhendo um conjunto de recursos para analisar em pastas de trabalho

O modelo de `Resource Picker` é iniciado com a assinatura, o grupo de recursos e os parâmetros de recurso para configurar o contexto de entrada da pasta de trabalho. Os parâmetros padrão são definidos para escolher máquinas virtuais, mas é possível configurá-lo para escolher qualquer tipo de recurso. O modelo também tem um controle de consulta de ARG que mostra como usar os parâmetros em suas análises.

![Imagem](Full.png)

## <a name="setting-up-the-resource-type-to-pick"></a>Configurando o tipo de recurso a ser escolhido

1. Clique em `Edit` na barra de ferramentas da pasta de trabalho.
2. Agora, você poderá ver uma lista suspensa `Resource type` antes de `Subscriptions`:

    ![Imagem](Parameter.png)
3. Expanda a lista suspensa e selecione os tipos de recursos que você deseja separar. Isso atualizará a lista suspensa de assinatura, o grupo de recursos e os recursos para corresponder à sua seleção.
4. Clique no botão `Edit` na parte inferior direita do controle de parâmetro.
5. Na grade de parâmetros, para a linha `Resources`, altere a coluna `Display name` de _Máquinas virtuais_ para o nome amigável do tipo de recurso selecionado (por exemplo, _Contas de Armazenamento_)
6. Clique em `Done Editing` na barra de ferramentas das pastas de trabalho.

## <a name="selecting-more-or-less-than-10-resources-by-default"></a>Selecionando mais ou menos de 10 recursos por padrão

1. Clique em `Edit` na barra de ferramentas da pasta de trabalho.
2. Clique no botão `Edit` na parte inferior direita do controle de parâmetro.
3. Na grade de parâmetros, selecione a linha para `Resources`
4. Clique na barra de ferramentas de controle de ícone `Edit` (ou no lápis).
5. No painel de `Edit Parameter` que aparece, role para baixo até o editor de `Azure Resource Graph Query`. Ele deve ter uma consulta parecida com esta:
    ```sql
    Resources
    | where type in~({ResourceTypes})
    | extend resourceGroupId = strcat('/subscriptions/', subscriptionId, '/resourceGroups/', resourceGroup)
    | where resourceGroupId in~({ResourceGroups}) or '*' in~({ResourceGroups})
    | order by name asc
    | extend Rank = row_number()
    | project value = id, label = name, selected = Rank <= 10, group = resourceGroup
    ```
    O código para a seleção de recursos está na última linha da consulta: `selected = Rank <= 10`. 

6. Altere o valor de 10 para um diferente a fim de alterar a seleção padrão