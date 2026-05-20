# Chatbot GoodWe

Chatbot com IA para auxiliar na gestão de eletropostos de recarga de veículos elétricos, desenvolvido para o EV Challenge 2026 (FIAP + GoodWe).

**Sprint 1 — Exploração e Planejamento**

---

## Integrantes

| Nome | RM |
|------|----|
| Davi Simoncelo | 571738 |
| Augusto de Souza Ávila | 570839 |
| João Pedro Sousa | 573962 |
| Matheus Evangelista Silva | 568593 |
| Murilo Lima de Carvalho | 570156 |

**Turma:** 1CCPK

---

## Problema Abordado

O EV Challenge 2026 traz como problema central a falta de sistemas integrados nos eletropostos para controlar potência, registrar sessões de recarga, realizar cobranças e se comunicar com um sistema central. Hoje, os postos de recarga não têm uma forma inteligente de lidar com tudo isso junto.

Com o crescimento dos carros elétricos, surgem alguns problemas práticos:
- Risco de sobrecarga na rede elétrica se não houver controle da potência distribuída
- Dificuldade em registrar e acompanhar os dados de cada recarga
- Cobrança manual ou desorganizada, gerando perda de receita
- Falta de comunicação padronizada entre os eletropostos e o sistema de gestão

---

## Proposta do Chatbot

O Chatbot GoodWe é um chatbot que funciona como assistente para o operador do eletroposto. A ideia é que ele consiga tirar dúvidas, ajudar com diagnósticos e dar informações sobre o funcionamento do posto usando linguagem natural.

**O que ele faz:**
- Informa o status dos eletropostos (disponível, ocupado, com erro)
- Auxilia na configuração de tarifas
- Explica dados das sessões de recarga
- Ajuda em diagnósticos técnicos básicos
- Responde sobre protocolos como OCPP e MODBUS

**O que ele não faz:**
- Não envia comandos direto para os equipamentos
- Não processa pagamentos
- Não substitui o painel de controle do sistema

---

## Persona Atendida

Escolhemos o **operador comercial de eletropostos** como persona principal.

Esse profissional é responsável pela gestão diária dos pontos de recarga em ambientes comerciais (shoppings, estacionamentos, postos). Ele entende do negócio mas não é especialista em protocolos de comunicação, então precisa de respostas práticas e diretas. Escolhemos esse perfil porque é quem mais se beneficia de um assistente que traduz informação técnica em ações concretas.

---

## Tecnologias Selecionadas

| Tecnologia | Função no projeto |
|------------|-------------------|
| Google Gemini API | LLM do chatbot (modelo Gemini 2.0 Flash) |
| LangChain | Framework para integração da IA com os documentos |
| Python | Linguagem de desenvolvimento |
| FastAPI | Backend/API do sistema |
| ChromaDB | Banco vetorial para armazenar a base de conhecimento |
| Streamlit | Interface de chat (frontend) |

**Justificativa:** Optamos pelo Gemini por ter um plano gratuito com boa capacidade. LangChain + ChromaDB permitem implementar RAG (Retrieval-Augmented Generation), que faz o chatbot consultar nossos documentos técnicos antes de gerar uma resposta, melhorando a precisão. Python é a linguagem padrão para projetos de IA, e Streamlit permite criar a interface de forma rápida.

---

## Documentos da Sprint 1

- [Fluxograma de Funcionamento](docs/fluxograma.md)
- [Modelo de Teste](docs/modelo-de-teste.md)
- [System Prompt](docs/system-prompt.md)

---

## Estrutura do Repositório

```
goodwe-chatbot/
├── README.md
├── docs/
│   ├── fluxograma.md
│   ├── modelo-de-teste.md
│   └── system-prompt.md
├── src/                    (Sprint 2)
├── tests/                  (Sprint 2)
└── .gitignore
```
