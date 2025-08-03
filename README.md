# Tech Challenge - 5IADT - Fase 2

## 🎯 Descrição do Problema

Este projeto aborda a **otimização de cardápios nutricionais** usando algoritmos genéticos, onde o objetivo é encontrar combinações de alimentos que minimizem o desvio das metas nutricionais estabelecidas.

### Desafio
- Selecionar alimentos da base TACO 2011 (Tabela Brasileira de Composição de Alimentos)
- Combinar 3 alimentos por refeição em cardápios de 3 refeições diárias
- Otimizar simultaneamente 4 nutrientes: energia, proteína, carboidratos e lipídeos

### Metas Nutricionais
| Nutriente | Meta Diária | 
|-----------|-------------|
| Energia | 2000 kcal |
| Proteína | 75g (15% VET) |
| Carboidrato | 275g (55% VET) |
| Lipídeos | 70g (30% VET) |

**Base de Dados**: [TACO 2011 - UNICAMP](https://www.gov.br/agricultura/pt-br/assuntos/inspecao/produtos-vegetal/legislacao-de-produtos-origem-vegetal/biblioteca-de-normas-vinhos-e-bebidas/tabela-brasileira-de-composicao-de-alimentos_taco_2011.pdf)

## 🧬 Implementação

### Representação Genética
- **Gene**: Alimento específico (ex: "Arroz, tipo 1, cozido")
- **Cromossomo**: Refeição com 3 alimentos 
- **Indivíduo**: Cardápio completo (café da manhã, almoço, jantar)

### Algoritmo Genético

**Função de Fitness**
```python
fitness = -Σ|valor_atual - meta| para todos os nutrientes
```

**Operadores Implementados**
- **Seleção**: Torneio (k=3)
- **Cruzamento**: Herança completa de refeições entre pais
- **Mutação**: Por refeição completa ou por alimento individual
- **Elitismo**: Preserva 10% dos melhores indivíduos

### Variações Testadas

| Variação | Elitismo | Mutação | Objetivo |
|----------|----------|---------|----------|
| **AG Básico** | ❌ | Por refeição | Exploração ampla |
| **AG + Elitismo** | ✅ | Por refeição | Preservar melhores |
| **AG + Granular** | ✅ | Por alimento | Refinamento fino |

## 📊 Resultados

### Parâmetros de Teste
```python
POPULACAO = 30 | GERACOES = 1000 | MUTACAO = 50% | ELITISMO = 10%
```

### Performance dos Algoritmos

| Algoritmo | Fitness | Energia | Proteína | Carboidrato | Lipídeos |
|-----------|---------|---------|----------|-------------|----------|
| **AG Básico** | -14.20 | 100.0% | 97.3% | 96.5% | 96.1% |
| **AG + Elitismo** | -7.20 | 100.0% | 93.6% | 99.7% | 99.1% |
| **AG + Granular** | -8.10 | 100.0% | 97.3% | 99.7% | 92.4% |

### Principais Achados
- **Elitismo** melhorou consistentemente a qualidade das soluções (49% melhor fitness)
- **Mutação granular** permitiu refinamentos incrementais
- Todos os algoritmos atingiram **>92% de precisão** em todos os nutrientes
- **Convergência** demonstrada ao longo de 1000 gerações

## 🔬 Conclusão

### Eficácia dos Algoritmos Genéticos
Os resultados demonstram que **algoritmos genéticos são altamente eficazes** para otimização nutricional, atingindo **>92% de precisão** em todos os nutrientes com convergência consistente.

### Insights Principais
- **Elitismo**: Estratégia mais impactante, melhorando fitness em 49%
- **Mutação granular**: Eficaz para refinamentos incrementais
- **Múltiplas estratégias**: Diferentes abordagens podem ser eficazes dependendo do contexto

## 🛠️ Execução

### Tecnologias
- **Python 3.8+** | **Pandas** | **Matplotlib** | **Jupyter Notebook**

### Estrutura
```
IADT-Fase-2/
├── IADT_Fase_2.ipynb     # Implementação dos algoritmos
├── alimentos.csv         # Base TACO 2011
├── requirements.txt      # Dependências
└── README.md             # Documentação
```

### Como Executar
```bash
# Instalar dependências
pip install -r requirements.txt

# Executar notebook
jupyter notebook IADT_Fase_2.ipynb
```
