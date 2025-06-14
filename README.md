# 📦 Controle de Estoque – Sprint de Programação Dinâmica (DASA)

---

## 👥 Equipe

- 554608 (Lucca Borges),
- 557599 (Ruan Vieira),
- 558148 (Rodrigo Carnevale)

---
## 📖 Visão Geral
Este projeto implementa, em Python, um **sistema de controle de estoque** usando dados de células de carga (ESP32 + MQTT).  
Você encontrará neste repositório:
- Código-fonte completo em `dasa.ipynb`
- Relatório acadêmico em `docs/relatorio.pdf`
- Instruções de instalação e uso (neste README)

---

## 🛠️ Bibliotecas Utilizadas
- `heapq`  
- `random`  
- `datetime`  
- `collections`  
- `functools.lru_cache` (memoização)  
- `paho-mqtt` (opcional, para receber JSON via MQTT)  
- `json`, `csv`

## 🔧 Estruturas de Dados e Conceitos
- **Listas**  
- **Dicionários**  
- **Funções** (`def`)  
- **Classes** (`class`)  
- **Repetição** (`for` / `while`)  
- **Condição** (`if` / `else`)  
- **Recursão + Memoização**  
- **Ordenação** e **Busca Binária**  
- **Análise O-Grande**

---

## 📂 Organização do Repositório
```
.
├── dasa/
├── docs/
│   └── relatorio.pdf             # Documento de envoltória e relatório acadêmico
├── README.md                     # Este arquivo
```

---


## ⚙️ Explicação das Funções e Classes

### 1. `diferenca(item: str, estoque: Dict[str, List[float]]) → float`
Calcula:  
```python
peso_ideal – peso_atual
```  
- Se **positivo**, produto está em **falta**  
- Se **negativo**, produto está em **excesso**

---

### 2. `produtos_em_falta(estoque: Dict[str, List[float]]) → Dict[str, float]`
- Percorre **todos** os itens do `estoque`  
- Retorna um dicionário `{produto: quantidade_em_falta}`  
- Complexidade: **O(n)**

---

### 3. `produtos_sobrando(estoque: Dict[str, List[float]]) → Dict[str, float]`
- Percorre **todos** os itens do `estoque`  
- Retorna `{produto: quantidade_em_excesso}`  
- Complexidade: **O(n)**

---

### 4. `busca_binaria(lista: List[T], alvo: T) → int`
- Recebe uma **lista ordenada**  
- Retorna o **índice** de `alvo` em **O(log n)**  
- Retorna `-1` se não encontrar

---

### 5. Decorador `@memoize` (em `memoizacao.py`)
- Usa `functools.lru_cache`  
- **Cache** de resultados para funções recursivas  
- Reduz complexidade de **exponencial** para **linear**, quando aplicável

---

### 6. `class Estoque` (em `controle_estoque.py`)
```python
class Estoque:
    def __init__(self, dados: Dict[str, List[float]]):
        # inicializa com {produto: [peso_atual, peso_ideal]}
    def produtos_em_falta(self) -> Dict[str, float]:
        # delega à função produtos_em_falta
    def produtos_sobrando(self) -> Dict[str, float]:
        # delega à função produtos_sobrando
```

---

## 📊 Análise de Complexidade

| Operação                       | Complexidade      |
|-------------------------------:|-------------------|
| `diferenca`                    | O(1)              |
| `produtos_em_falta/sobrando`   | O(n)              |
| `busca_binaria`                | O(log n)          |
| Ordenação inicial de chaves    | O(n log n)        |
| Funções recursivas + memoize   | Exponencial → O(n)|



---

## 📄 Relatório
Veja o relatório acadêmico em PDF em:  
```
relatorio.pdf
```

---

