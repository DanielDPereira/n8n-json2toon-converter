<div align="center">

# 🧠 n8n-json2toon-converter  
### 🚀 Conversão de JSON → TOON (Token-Oriented Object Notation) no [n8n](https://n8n.io/)

![n8n](https://img.shields.io/badge/n8n-workflow-orange?logo=n8n)
![Status](https://img.shields.io/badge/status-active-success)
![Made with](https://img.shields.io/badge/made%20with-JavaScript-yellow)
![LLM Ready](https://img.shields.io/badge/optimized%20for-LLMs-green)
![License](https://img.shields.io/badge/license-MIT-blue)

</div>

---

## 🧩 Visão Geral

Este projeto apresenta um **workflow para n8n** que demonstra a conversão de dados do formato **JSON** para **TOON (Token-Oriented Object Notation)** — um formato de serialização otimizado para **economizar tokens** e **aumentar a eficiência de prompts em LLMs (Modelos de Linguagem Grandes)**.

💡 **Objetivo:** mostrar, de forma prática, como o TOON pode reduzir custos e melhorar a velocidade de resposta de aplicações de IA.

---

## 🌀 O que é o TOON?

**TOON (Token-Oriented Object Notation)** é um formato de dados **criado para o ecossistema de IAs**.  
Ele foi desenvolvido para **reduzir o ruído estrutural** presente em formatos como JSON e YAML — eliminando chaves repetidas, aspas e delimitadores desnecessários — mantendo, ainda assim, uma estrutura legível e lógica.

> 🔬 *Segundo benchmarks recentes*, TOON pode reduzir o uso de tokens em **30–60%** em comparação ao JSON equivalente, especialmente em dados tabulares e uniformes.

---

## 🔍 Exemplo Comparativo

### 📊 JSON (minificado) — 198 caracteres
```json
{"users":[{"id":1,"name":"Alice","role":"admin","email":"alice@example.com"},{"id":2,"name":"Bob","role":"user","email":"bob@example.com"},{"id":3,"name":"Charlie","role":"editor","email":"charlie@example.com"}]}
````

### 🪶 TOON — 119 caracteres

```toon
users[3]{id,name,role,email}:
  1,Alice,admin,alice@example.com
  2,Bob,user,bob@example.com
  3,Charlie,editor,charlie@example.com
```

### ⚖️ Comparativo direto

| Métrica                   | JSON     | TOON  | Diferença               |
| ------------------------- | -------- | ----- | ----------------------- |
| Comprimento (caracteres)  | 198      | 119   | 🔽 **40% menor**        |
| Estrutura repetitiva      | Alta     | Baixa | ✅ Eliminada             |
| Leitura humana            | Moderada | Alta  | ✅ Mais limpa            |
| Tokens em LLMs (estimado) | ~140     | ~85   | 💰 **~40% de economia** |

> 🧠 TOON declara uma única vez o formato da coleção (`users[3]{id,name,role,email}`)
> e depois lista apenas os valores. Isso reduz drasticamente redundâncias e tokens.

---

## ⚡ Vantagens do TOON para LLMs

| 💡 Benefício                           | 🧾 Descrição                                                         |
| -------------------------------------- | -------------------------------------------------------------------- |
| 💸 **Economia de Tokens**              | Redução média de **30–60%** no custo de prompts.                     |
| 🚀 **Respostas mais rápidas**          | Menos tokens = inferência mais veloz e contexto mais claro.          |
| 🧱 **Estrutura explícita e limpa**     | Declarações como `users[3]{id,name}` ajudam LLMs a entender padrões. |
| 👓 **Legível para humanos e máquinas** | Inspiração híbrida entre YAML e CSV.                                 |
| 🤖 **Otimizado para IA**               | Foco em conteúdo semântico, não em sintaxe.                          |

---

## 🔧 Sobre este Workflow n8n

Este workflow implementa uma **prova de conceito funcional** da conversão JSON → TOON dentro do [n8n](https://n8n.io/).

### 🔁 Etapas do fluxo:

1. **🕹️ Manual Trigger** — Inicia o fluxo manualmente.
2. **🌎 HTTP Request (Feriados BR 2026)** — Obtém dados da API `https://brasilapi.com.br/api/feriados/v1/2026`.
3. **🧮 Aggregate** — Agrupa o JSON retornado.
4. **🧠 Json → Toon Converter (Code)** —

   * Usa a função recursiva `jsonToToon()` e `convertArrayToToon()`
   * Converte estruturas uniformes em formato TOON.
5. **📊 Estima Tokens (Comparação)** —

   * Mostra a diferença de contagem de tokens entre JSON e TOON.

---

## 🧭 Como Usar

1. **⬇️ Baixe o workflow:**
   [`Json2Toon.json`](./Json2Toon.json)

2. **📥 Importe no n8n:**
   Em sua instância, vá em **Import → From File**.

3. **▶️ Execute:**
   Clique em **Execute Workflow**.

4. **📈 Compare os resultados:**
   Veja a diferença de tokens entre o JSON e o TOON diretamente nos nós de comparação.

---

## 🧰 Personalização

Você pode adaptar o workflow para seus próprios dados:

* Substitua o nó **HTTP Request** por um **Webhook**, **Read File** ou **outra API**.
* Conecte o resultado ao nó **Aggregate** e mantenha o nó **Json → Toon Converter**.

---

## ⚠️ Limitações (Quando *não* usar TOON)

| ❌ Cenário                                        | 💬 Alternativa          |
| ------------------------------------------------ | ----------------------- |
| Estruturas muito aninhadas ou heterogêneas       | Use **JSON minificado** |
| Dados puramente tabulares (sem hierarquia)       | Use **CSV**             |
| Necessidade de compatibilidade ampla (REST APIs) | JSON ainda é o padrão   |

---

## 🧱 TOON vs JSON — Diferenças Técnicas

| Aspecto               | JSON                                         | TOON                                              |
| --------------------- | -------------------------------------------- | ------------------------------------------------- |
| Estrutura             | Baseada em chaves/valores com delimitadores. | Baseada em blocos declarativos e linhas de dados. |
| Redundância           | Alta                                         | Mínima                                            |
| Tokenização para LLMs | Ineficiente                                  | Otimizada                                         |
| Legibilidade humana   | Boa                                          | Excelente                                         |
| Compactação           | Nenhuma                                      | Implícita pela estrutura                          |
| Finalidade            | Web & APIs                                   | IA & LLMs                                         |

---

## 👨‍💻 Autor

**Daniel Dias Pereira**
[![GitHub](https://img.shields.io/badge/GitHub-DanielDPereira-181717?logo=github)](https://github.com/DanielDPereira)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Daniel%20Dias%20Pereira-blue?logo=linkedin)](https://www.linkedin.com/in/daniel-dias-pereira-40219425b/)
[![n8n](https://img.shields.io/badge/n8n.io-Automation-orange?logo=n8n)](https://community.n8n.io/u/danieldpereira/)

---

## 📚 Referências

* 🧾 [Repositório Oficial do TOON](https://github.com/toon-format/toon)
* 📰 [TabNews – *TOON: leve, rápido e as IAs adoram!*](https://www.tabnews.com.br/wpbarcelos/toon-leve-rapido-e-as-ias-adoram)
* 💬 [Zeeshan – *What is TOON? Benefits, Applications and Difference from JSON*](https://zeeshan.p2pclouds.net/blogs/what-is-toon-its-benefits-applications-and-difference-from-json/)
* 🧠 [Dev.to – *TOON vs JSON: A Modern Data Format Showdown*](https://dev.to/sreeni5018/toon-vs-json-a-modern-data-format-showdown-2ooc)
* 📖 [Medium – *TOON vs JSON for LLMs*](https://medium.com/@speaktoharisudhan/toon-vs-json-for-llms-cc541c7a1251)

---

<div align="center">

💡 *“Menos tokens, mais inteligência.”*
Feito com ❤️ por [Daniel Dias Pereira](https://github.com/DanielDPereira)

</div>
