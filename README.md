# 🧬 Tech Challenge - 5IADT - Fase 2

**Algoritmo Genético para Otimização Nutricional**

## 🎯 Definição do Problema

### Descrição do Problema
O planejamento nutricional consiste em:
- Selecionar alimentos de uma base de dados nutricional
- Combinar esses alimentos em três refeições (café da manhã, almoço e jantar)
- Otimizar simultaneamente múltiplos nutrientes (energia, proteína, carboidratos, lipídeos)
- Manter 3 alimentos por refeição

### Objetivo
Encontrar combinações de alimentos que minimizem o desvio das metas nutricionais estabelecidas usando algoritmos genéticos.

### Metas Nutricionais
| Nutriente | Meta Diária |
|-----------|-------------|
| Energia | 2000 kcal |
| Proteína | 75g |
| Carboidrato | 275g |
| Lipídeos | 70g |

### Base de Dados Nutricional
A base de dados utilizada provém da **Tabela Brasileira de Composição de Alimentos (TACO 2011)**, desenvolvida pelo NEPA (Núcleo de Estudos e Pesquisas em Alimentação) da UNICAMP.

- **Fonte oficial**: [TACO 2011 - Gov.br](https://www.gov.br/agricultura/pt-br/assuntos/inspecao/produtos-vegetal/legislacao-de-produtos-origem-vegetal/biblioteca-de-normas-vinhos-e-bebidas/tabela-brasileira-de-composicao-de-alimentos_taco_2011.pdf)
- **Repositório**: [GitHub - machine-learning-mocha/taco](https://github.com/machine-learning-mocha/taco/blob/main/formatados/alimentos.csv)

## 🧬 Abordagem da Solução

### Algoritmo Genético
Utilização de computação evolutiva para otimizar cardápios através de:
- **Representação**: Cardápio com 3 refeições, cada uma com 3 alimentos
- **Seleção**: Torneio com 3 competidores
- **Cruzamento**: Herança aleatória de refeições dos pais
- **Mutação**: Por refeição completa ou por alimento individual
- **Elitismo**: 10% dos melhores indivíduos preservados

### Variações Implementadas
1. **Algoritmo Genético Básico** - Implementação padrão com seleção por torneio e mutação por refeição completa
2. **Algoritmo com Elitismo** - Preserva os 10% melhores indivíduos por geração
3. **Elitismo + Mutação por Alimento** - Elitismo com mutação granular (substitui alimentos individuais)

## 🛠️ Implementação

### Tecnologias Utilizadas
- **Python 3.8+** - Linguagem principal
- **Pandas** - Manipulação da base de dados nutricional
- **Matplotlib** - Visualização de resultados
- **Jupyter Notebook** - Ambiente de desenvolvimento

### Parâmetros do Sistema
```python
TAMANHO_POPULACAO = 30      # Indivíduos por geração
NUMERO_GERACOES = 1000      # Limite de evolução
TAXA_MUTACAO = 0.5          # Probabilidade de mutação
TAMANHO_TORNEIO = 3         # Seleção por torneio
ALIMENTOS_POR_REFEICAO = 3  # Restrição prática
```

### Estrutura do Projeto
```
IADT-Fase-2/
├── IADT_Fase_2.ipynb     # Implementação completa dos algoritmos
├── alimentos.csv         # Base de dados nutricional (TACO 2011)
├── requirements.txt      # Dependências do sistema
└── README.md             # Documentação do projeto
```

## 🚀 Como Executar

```bash
# 1. Instale as dependências
pip install -r requirements.txt

# 2. Execute o notebook
jupyter notebook IADT_Fase_2.ipynb
```

### Funcionalidades do Notebook
- Executar os três algoritmos implementados
- Visualizar a evolução da aptidão por geração
- Comparar resultados entre as variações
- Examinar cardápios gerados e seus valores nutricionais

## 📊 Resultados e Análise

### Metodologia de Testes
- Mesma população inicial para todas as variações (comparação justa)
- Função de aptidão baseada no desvio das metas nutricionais
- Gráficos de evolução da aptidão ao longo das gerações

### Saídas do Sistema
- Melhor cardápio encontrado para cada algoritmo
- Valores nutricionais calculados vs. metas
- Gráficos comparativos de evolução
- Resumo quantitativo de performance
