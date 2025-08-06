# Teste_Software_LLM_2025_Santos_Augusto_Silva_David_Lima_Giulian_Lima_Yasmim

# 📄 Tutorial — Uso de LLMs para Geração de Testes Baseados em Propriedades (PBT)

Este tutorial foi elaborado para atender aos requisitos da atividade proposta, explorando o uso de **Large Language Models (LLMs)** na geração de **Property-Based Tests (PBT)**, com base no artigo:

> **[Can Large Language Models Write Good Property-Based Tests?](https://arxiv.org/abs/2307.04346)**

O documento cobre desde a escolha do artigo até a sugestão de melhorias e identificação de um problema relevante no Stack Overflow.

---

## 📌 a) Qual artigo escolhemos?

- **Título:** Can Large Language Models Write Good Property-Based Tests?  
- **Seção:** Unit Test Case Generation  
- **Link:** [arxiv:2307.04346](https://arxiv.org/abs/2307.04346)  

---

## 🎯 b) Qual o problema que esse artigo tenta resolver?

Escrever bons testes de software é essencial, mas trabalhoso.  
O artigo aborda um tipo específico: **Property-Based Testing (PBT)**.  

Ao contrário dos testes tradicionais, que validam entradas específicas, o PBT verifica **propriedades invariantes** de uma função em múltiplas entradas.  
O problema é que criar esses testes exige **tempo, conhecimento técnico e criatividade**.

---

## 💡 c) Qual a solução proposta?

O artigo apresenta a **PBT-GPT**, uma ferramenta baseada em LLMs (como GPT-4) que gera automaticamente testes PBT a partir da **descrição de funções**.  
O modelo detecta propriedades como **simetria, comutatividade, idempotência**, entre outras.

📌 **Objetivo:** automatizar a criação de testes inteligentes sem exigir que o desenvolvedor escreva manualmente cada caso.

---

## 🧠 d) Modelos utilizados

- **GPT-4** — [OpenAI](https://platform.openai.com)  
- **Claude 2.1** — [Anthropic](https://www.anthropic.com)  
- **Gemini 1.5 Pro** — [Google](https://ai.google.dev/gemini/)  

Todos são modelos **decoder-only**, baseados na arquitetura **Transformers**.

---

## 🗂 e) Dataset e código

- **Dataset:** 40 funções populares de bibliotecas Python  
  - NumPy  
  - datetime  
  - networkx  

- **Código:** [GitHub - PBT-GPT](https://github.com/engineeringforresearch/PBT-GPT)  

---

## 🧪 f) Como testaram a solução?

Critérios de avaliação:

1. **Validez:** o teste executa sem erros?  
2. **Soundness:** o teste detecta erros reais?  
3. **Cobertura:** o teste verifica propriedades realmente úteis?  

📊 **Resultado:** GPT-4 apresentou o melhor desempenho, com **>60% de testes válidos** e boa cobertura.

---

## 📝 g) Exemplo prático

Função: `sorted(lst)`  
Teste gerado usando **Hypothesis**:

```python
from hypothesis import given
import hypothesis.strategies as st

@given(st.lists(st.integers()))
def test_sorted_is_idempotent(lst):
    assert sorted(sorted(lst)) == sorted(lst)
```
📌 Propriedade testada: Idempotência — aplicar sorted mais de uma vez retorna o mesmo resultado que aplicar apenas uma vez.

⚙️ h) Como isso pode ajudar no dia a dia?
Garantia de qualidade para novas bibliotecas e funções

Detecção de bugs antes de chegarem ao usuário

Redução de tempo na criação de testes

Ideal para equipes com pouco conhecimento prévio de PBT

Aplicável em pipelines CI/CD

⚠️ i) Limitações
Nem todos os testes gerados são válidos

Possibilidade de repetição ou pouca utilidade nos testes

Alto custo de uso contínuo de modelos como GPT-4

Qualidade depende fortemente do prompt

Testes nem sempre são fáceis de entender

🚀 j) Possíveis melhorias
Fine-tuning com mais exemplos reais de testes

Uso de few-shot prompting para fornecer exemplos ao modelo

Integração com mutation testing para validar automaticamente a utilidade dos testes gerados

💬 k) Problema do Stack Overflow relacionado
Título: How can I generate property-based tests for a Python function using Hypothesis?

Motivo da escolha: o problema é exatamente o que o artigo resolve — gerar testes PBT de forma automática a partir de uma descrição de função.

📚 Referência
Spruit, N., Wesselink, W., & others. (2023). Can Large Language Models Write Good Property-Based Tests? arXiv:2307.04346.
Disponível em: https://arxiv.org/abs/2307.04346
