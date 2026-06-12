# Chatbot GoodWe - ChargeGrid Intelligence

Chatbot conversacional desenvolvido para o EV Challenge 2026 (FIAP x GoodWe),
disciplina Prompt and Artificial Intelligence - 1º Ano de Ciência da Computação.

## Integrantes

- Davi Simoncelo - RM 571738 - turma 1CCPK
- Augusto de Souza Ávila - RM 570839 - turma 1CCPK
- João Pedro Sousa - RM 573962 - turma 1CCPK
- Matheus Evangelista Silva - RM 568593 - turma 1CCPK
- Murilo Lima de Carvalho - RM 570156 - turma 1CCPK

## Problema abordado

Operadores comerciais de eletropostos GoodWe ChargeGrid não têm uma ferramenta integrada de suporte em linguagem natural. Dúvidas sobre tarifas ANEEL, erros OCPP e sessões de recarga exigem contato com suporte técnico mesmo para questões básicas. O chatbot resolve esse gargalo com respostas práticas contextualizadas no ChargeGrid Intelligence.

## Persona atendida

Operador comercial de eletropostos — responsável pela gestão diária dos pontos de recarga em shoppings, estacionamentos e empresas. Conhecimento intermediário: entende kW e kWh, mas não domina OCPP ou MODBUS. Escolhido por ser quem mais se beneficia de um assistente que traduz informação técnica em ações concretas.

## Tecnologias utilizadas

- Modelo: Qwen/Qwen2.5-7B-Instruct via Hugging Face Inference API (gratuito)
- Linguagem: Python 3.10+
- Bibliotecas principais: huggingface-hub, python-dotenv

## Justificativa técnica

Modelo planejado inicialmente: Google Gemini 2.0 Flash. Descartado por cota gratuita esgotada durante os testes (erro 429). Alternativas testadas: Mistral-7B-Instruct-v0.3 (descontinuado no HF) e zephyr-7b-beta (sem suporte no free tier). Modelo adotado: Qwen/Qwen2.5-7B-Instruct — compatível com chat no free tier e boa qualidade em PT-BR.

## Como executar

### Pré-requisito

Crie uma conta gratuita em huggingface.co → Settings → Access Tokens → New Token (tipo Read). Copie o token gerado.

---

### Em Google Colab

1. Abra `notebooks/chatbot_notebook.ipynb` no Colab
2. No menu lateral, clique no ícone de chave (**Secrets**) e adicione:
   - Nome: `HF_TOKEN`
   - Valor: seu token gerado em huggingface.co/settings/tokens
3. Execute as células 1, 2, 3 e 4 em ordem
4. Para conversar: execute a Célula 5
5. Para rodar os testes: pule a Célula 5 e execute a Célula 6

> Não execute as Células 5 e 6 juntas — o loop da Célula 5 trava o kernel.

---

### Localmente — macOS e Linux

> Se aparecer o erro `externally-managed-environment`, crie um ambiente virtual antes de instalar as dependências:

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

Crie o arquivo `.env` na raiz do projeto:
```
HF_TOKEN=hf_sua_chave_aqui
```

Execute o chatbot:
```bash
python3 src/chatbot.py
```

---

### Localmente — Windows

```bash
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

Crie o arquivo `.env` na raiz do projeto:
```
HF_TOKEN=hf_sua_chave_aqui
```

Execute o chatbot:
```bash
python src/chatbot.py
```

---

### Pelo notebook (local)

1. Abra `notebooks/chatbot_notebook.ipynb`
2. Confirme que o `.env` está na raiz com o `HF_TOKEN`
3. Execute as células 1, 2, 3 e 4 em ordem
4. Para conversar: execute a Célula 5
5. Para rodar os testes: pule a Célula 5 e execute a Célula 6

> Não execute as Células 5 e 6 juntas — o loop da Célula 5 trava o kernel.

---

## System prompt

docs/system-prompt.md

## Modelo de teste

tests/modelo-de-teste.md (casos) e tests/resultados.md (respostas obtidas e avaliação)

## Vídeo

https://youtu.be/s71PuRn5O6Y

## Fluxograma

docs/fluxograma.svg

## Licença

Trabalho acadêmico — distribuição livre para fins educacionais.
