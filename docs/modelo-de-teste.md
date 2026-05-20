# Modelo de Teste — Chatbot GoodWe

## Objetivo

Este documento apresenta os casos de teste do chatbot Chatbot GoodWe. São 5 perguntas com as respostas esperadas, cobrindo os principais cenários de uso de um operador comercial de eletropostos. Esse modelo vai servir como base de avaliação quando o chatbot for implementado na Sprint 2.

---

## Casos de Teste

### Teste 1 — Status do Eletroposto

**Pergunta:**
> "Qual o status atual do eletroposto FIAP-01?"

**Resposta esperada:**
> O eletroposto FIAP-01 está online e disponível para uso. Potência máxima de 22 kW, tipo AC Tipo 2, conectado via OCPP 1.6. No momento não tem nenhuma sessão em andamento. A última recarga foi hoje de manhã, com cerca de 45 kWh entregues. Nenhum alerta registrado.

---

### Teste 2 — Configuração de Tarifa

**Pergunta:**
> "Como configurar uma tarifa dinâmica por horário para o eletroposto?"

**Resposta esperada:**
> Para configurar tarifa dinâmica, acesse Configurações > Tarifas > Nova Regra e defina as faixas horárias. Exemplo de faixas baseadas na ANEEL:
>
> - 00:00 às 06:59 (fora de ponta): R$ 0,45/kWh
> - 07:00 às 17:59 (intermediária): R$ 0,75/kWh
> - 18:00 às 20:59 (ponta): R$ 1,20/kWh
> - 21:00 às 23:59 (intermediária): R$ 0,75/kWh
>
> Depois é só associar a regra ao eletroposto e ativar. Alterações não afetam sessões que já estão em andamento.

---

### Teste 3 — Erro de Comunicação OCPP

**Pergunta:**
> "O eletroposto está mostrando erro de comunicação OCPP, o que fazer?"

**Resposta esperada:**
> Um erro de comunicação OCPP significa que o eletroposto perdeu conexão com o sistema central. Para resolver, verifique:
>
> 1. Conexão de rede (cabo Ethernet ou Wi-Fi)
> 2. Se a URL do CSMS está correta (endpoint WebSocket)
> 3. Validade do certificado SSL/TLS
> 4. Se as portas 9000 ou 443 estão liberadas no firewall
> 5. Intervalo de heartbeat (mínimo recomendado: 60 segundos)
>
> Se não resolver, tente enviar um Reset (Soft) pelo painel e confira os logs em Monitoramento > Logs OCPP. Se o problema continuar, abra um chamado técnico.

---

### Teste 4 — Consumo Mensal

**Pergunta:**
> "Qual foi o consumo total de energia do último mês?"

**Resposta esperada:**
> No mês de abril/2026, o eletroposto entregou cerca de 1.250 kWh no total, em aproximadamente 190 sessões de recarga. O tempo médio por sessão ficou em torno de 50 minutos. Comparando com março, o consumo aumentou um pouco, o que faz sentido pela maior procura que a gente vem observando.

---

### Teste 5 — Diferença entre OCPP e MODBUS

**Pergunta:**
> "Qual a diferença entre OCPP e MODBUS nesse contexto?"

**Resposta esperada:**
> São dois protocolos diferentes que a gente usa no projeto. O OCPP (Open Charge Point Protocol) é o que faz a comunicação entre o eletroposto e o sistema central — ele gerencia as sessões de recarga, envia comandos e coleta os dados de cobrança. Funciona por WebSocket. Já o MODBUS é um protocolo industrial que a gente usa pra se comunicar com o inversor solar da GoodWe — basicamente lê dados como potência gerada, tensão e corrente. Funciona por serial (RS-485) ou TCP/IP. Resumindo: OCPP cuida da parte de recarga e MODBUS cuida do inversor.
