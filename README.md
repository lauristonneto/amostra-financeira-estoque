📈 Dashboard de Performance Comercial e Classificação Curva ABC (Pareto)
Solução de Business Intelligence (BI) voltada para análise de faturamento, margem de lucro e eficiência de portfólio de produtos em escala global (dados transacionais multinacionais). O projeto foca na identificação de produtos críticos da empresa com base no Princípio de Pareto (Regra 80/20).
🔗 **[ACESSE O DASHBOARD INTERATIVO – POWER BI] - https://app.powerbi.com/view?r=eyJrIjoiYzBmZTViOWYtZTg3NC00ZGJjLTgzNTktYmFiMjMzMGQ0NTllIiwidCI6IjY1OWNlMmI4LTA3MTQtNDE5OC04YzM4LWRjOWI2MGFhYmI1NyJ9 **

🎯 Desafio de Negócio: O Princípio de Pareto
O objetivo deste projeto foi isolar o portfólio de produtos comercializados pela organização e classificá-los dinamicamente por relevância de margem líquida. 
*   **Classe A:** Os produtos de altíssima rentabilidade que, combinados, representam até 70% do lucro total da organização (ex: Paseo, VTT, Amarilla).
*   **Classe B:** Produtos de média importância (até 90% do lucro acumulado).
*   **Classe C:** Produtos de baixa rentabilidade ou cauda longa (os 10% restantes do lucro).

📐 Engenharia e Lógica de Modelagem (DAX Avançado)
Diferente de visuais estáticos, o projeto foi estruturado para demonstrar a diferença entre **Medidas de Contexto** e **Colunas de Massa Transacional**. 
Para viabilizar a exibição explícita de percentuais de representatividade nas legendas e eixos sem depender puramente de balões flutuantes de dicas de ferramentas (*Tooltips*), implementou-se a seguinte lógica de classificação baseada no percentual acumulado de lucro (`[ABC_ACUM]`) importado da modelagem original:
```dax
Nova_Curva_ABC = 
SWITCH(
    TRUE();
    [ABC_ACUM] <= 0.70; "Classe A";
    [ABC_ACUM] <= 0.90; "Classe B";
    "Classe C"
)
```
Essa abordagem permitiu mapear o comportamento da massa de transações e agrupar milhares de linhas transacionais sob categorias inteligíveis para filtros globais.
---
📊 Estrutura e Design do Dashboard
O layout foi desenhado para facilitar análises cruzadas de margem e impacto de descontos:
* Visão de Topo: Cards de controle de Lucro Líquido total e Volume de Unidades Comercializadas globalmente.
* Geografia do Lucro: Gráfico de colunas empilhadas segmentando a lucratividade por país (`Country`) e permitindo a abertura imediata de canais de venda (`Segment` - Government, Small Business, Enterprise).
* Gráfico de Pareto Avançado: Gráfico combinado de linhas e colunas exibindo o lucro decrescente por produto em paralelo com a curva ascendente do percentual acumulado, gerando leitura imediata sem poluição visual.
* Análise de Elasticidade de Preço: Segmentadores interativos de Faixas de Desconto (`Discount Band`) e Produtos, permitindo simular instantaneamente como concessões de descontos altos afetaram o lucro final em cada território.

🛠️ Tecnologia Utilizada
**Microsoft Excel**
- Power Pivot / Power BI (Armazenamento e Funções Avançadas).
- Arquivos incluídos neste repositório: O arquivo `.pbix` do Power BI e a base simulada em formato Excel.

📊 Prints do Projeto:

<img width="1919" height="1032" alt="Captura_financial_01" src="https://github.com/user-attachments/assets/7f0a47ae-2e12-4ff7-ad0d-d8dec2aa2162" />

<img width="1919" height="1031" alt="Captura_financial_02" src="https://github.com/user-attachments/assets/6fa06382-b255-41ee-98c0-ad4111f442e3" />

<img width="1919" height="1030" alt="Captura_BI" src="https://github.com/user-attachments/assets/e041f99b-02fd-4d52-9170-0deb1252e301" />


