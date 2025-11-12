
<div align="center">

# 🧠 n8n-json2toon-converter  
### 🚀 Conversão de JSON → TOON (Token-Oriented Object Notation) no [n8n](https://n8n.io/)

![n8n](https://img.shields.io/badge/n8n-workflow-orange?logo=n8n)
![Status](https://img.shields.io/badge/status-active-success)
![Made with](https://img.shields.io/badge/made%20with-JavaScript-yellow)
![LLM Ready](https://img.shields.io/badge/optimized%20for-LLMs-green)

</div>

---

## 🧩 Visão Geral

Este projeto contém um **workflow para n8n** que demonstra a conversão de dados do formato **JSON** para o formato **TOON (Token-Oriented Object Notation)** — um formato de serialização otimizado para **reduzir o uso de tokens** ao enviar dados estruturados para **Modelos de Linguagem Grandes (LLMs)**.

O objetivo é mostrar, de forma prática, como o TOON pode diminuir custos e aumentar a eficiência de prompts em IA.

---

## 🌀 O que é o Formato TOON?

**TOON (Token-Oriented Object Notation)** é um formato de serialização compacto, legível e projetado para **máxima eficiência de tokens**.  
Ele combina a **estrutura hierárquica do YAML** com o **formato tabular do CSV**, eliminando redundâncias como chaves, colchetes e aspas.

### 🔍 Exemplo Comparativo

**JSON (minificado) — 138 caracteres**
```json
{"categories":[{"id":1,"name":"financeiro"},{"id":2,"name":"compras"},{"id":3,"name":"medicina"},{"id":4,"name":"segurança do trabalho"}]}
````

**TOON — 85 caracteres**

```toon
categories[4]{id,name}:
  1,financeiro
  2,compras
  3,medicina
  4,segurança do trabalho
```

---

## ⚡ Vantagens do TOON para LLMs

| 💡 Benefício                         | 🧾 Descrição                                                                                |
| ------------------------------------ | ------------------------------------------------------------------------------------------- |
| 💸 **Economia de Tokens**            | Redução de **30% a 60%** no uso de tokens em relação ao JSON.                               |
| 🚀 **Maior Velocidade e Precisão**   | Menos tokens = respostas mais rápidas e precisas.                                           |
| 🧱 **Estrutura Segura (Guardrails)** | Inclui metadados explícitos (`users[3]{id,name}`), úteis para LLMs verificarem integridade. |
| 👓 **Legibilidade Humana**           | Sintaxe clara, leve e visualmente limpa, unindo YAML + CSV.                                 |

> 📊 *Em benchmarks, o TOON atingiu **73.9% de acurácia** na recuperação de dados — superior ao JSON formatado (69.7%).*

---

## 🔧 Sobre este Workflow n8n

O workflow demonstra o funcionamento do TOON com uma **prova de conceito prática**:

1. **🕹️ Manual Trigger:** Inicia o fluxo manualmente.
2. **🌎 Get Feriados BR 2026 (HTTP Request):** Obtém dados da API pública `https://brasilapi.com.br/api/feriados/v1/2026`.
3. **🧮 Aggregate:** Agrupa os resultados em um único item.
4. **🧠 Json → Toon Converter (Code):**

   * Contém a função `jsonToToon` (recursiva).
   * Usa `convertArrayToToon` para transformar arrays de objetos em formato tabular TOON.
   * Retorna o resultado convertido.
5. **📊 Nós de Comparação:**

   * Estimam a contagem de tokens do **JSON original** e do **TOON convertido**.
   * Permitem observar diretamente a diferença de custo/token.

---

## 🧭 Como Usar

1. **⬇️ Baixe o Workflow:**
   Faça o download do arquivo [`Json2Toon.json`](./Json2Toon.json).
2. **📥 Importe no n8n:**
   Em sua instância n8n, vá em **Import → From File** e selecione o arquivo.
3. **▶️ Execute:**
   Abra o workflow e clique em **Execute Workflow**.
4. **📈 Compare os Resultados:**
   Verifique a diferença de tokens entre os nós “Estima tokens (JSON)” e “Estima tokens (TOON)”.

---

## 🧰 Personalização

Quer usar com seus próprios dados?

➡️ Basta substituir o nó **“Get Feriados BR 2026”** por:

* Um **Webhook**,
* Um **Read File**, ou
* Uma **outra API** que retorne JSON.

Conecte essa fonte ao nó **Aggregate** e mantenha o conversor ativo.

---

## ⚠️ Limitações (Quando *não* usar TOON)

| ❌ Cenário                                   | 💬 Alternativa          |
| ------------------------------------------- | ----------------------- |
| Estruturas muito aninhadas ou não uniformes | Use **JSON minificado** |
| Dados tabulares simples                     | Use **CSV**             |

---

## 👨‍💻 Autor

**Daniel Dias Pereira**

[![GitHub](https://img.shields.io/badge/GitHub-DanielDPereira-181717?logo=github)](https://github.com/DanielDPereira)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Daniel%20Dias%20Pereira-blue?logo=linkedin)](https://www.linkedin.com/in/daniel-dias-pereira-40219425b/)

---

## 📚 Referências

* 🧾 [Repositório Oficial do TOON](https://github.com/toon-format/toon)
* 📰 [Artigo no TabNews: *TOON — Leve, Rápido e as IAs Adoram!*](https://www.tabnews.com.br/wpbarcelos/toon-leve-rapido-e-as-ias-adoram)

---

<div align="center">

💡 *“Menos tokens, mais inteligência.”*
Feito com ❤️ por [Daniel Dias Pereira](https://github.com/DanielDPereira)

</div>


---
