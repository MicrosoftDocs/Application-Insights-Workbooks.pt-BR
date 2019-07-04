# <a name="cpu-heatmap"></a>mapa de calor da CPU

Esta pasta de trabalho é uma boa maneira de visualizar os pontos de acesso no uso da CPU de suas máquinas virtuais.

![Ilustre o mapa de calor de uma CPU](cpu-heatmap.png)

## <a name="changing-the-cpu-threshold"></a>Alteração do limite da CPU
Por padrão, esta pasta de trabalho destaca as máquinas virtuais com `Percentage CPU` médio maior que 75%. Se você quiser que esse limite seja maior ou menor, eis as etapas a serem seguidas:

1. Clique no item `Edit` da barra de ferramentas.
2. Clique no botão `↑ Edit`, na parte inferior direita do controle de hive.
3. Na lista `Columns Available After Merge`, role para baixo e selecione o item `[Added column] - Cell Color`.
4. Clique no botão `Edit added item` da barra de ferramentas de controles de hive.
5. No painel que se abre, clique em `Edit`, no item que diz `Percentage CPU > 75 Result is E8976A`, para ver um pop-up de configurações
    1. Defina o campo `Second operand` com o limite desejado – digamos que seja 90.
        ![Ilustre o mapa de calor de uma CPU](cpu-heatmap-column-settings.png)
    2. Clique em op no pop-up.
6. Clique em 'Salvar e fechar'
7. Escolha `Done Editing` na barra de ferramentas da pasta de trabalho.
