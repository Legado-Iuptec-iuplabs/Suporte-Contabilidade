# 🤖 Guia de Automação e Bot - Chatwoot

## 📋 Índice

1. [Configuração Básica de Automação](#configuração-básica-de-automação)
2. [Criando Respostas Automáticas](#criando-respostas-automáticas)
3. [Roteamento Inteligente](#roteamento-inteligente)
4. [Horário de Atendimento](#horário-de-atendimento)
5. [Mensagens Pré-definidas](#mensagens-pré-definidas)
6. [Macros Úteis](#macros-úteis)
7. [Relatórios e Métricas](#relatórios-e-métricas)

---

## 🎯 Configuração Básica de Automação

### Passo 1: Acessar Automações

1. Entre no Chatwoot
2. Vá em **Settings** → **Automation Rules**
3. Clique em **Add Automation Rule**

### Passo 2: Estrutura de uma Regra

Toda regra tem 3 partes:

1. **Quando** (Condições)
2. **E** (Condições adicionais - opcional)
3. **Fazer** (Ações)

---

## 💬 Criando Respostas Automáticas

### Exemplo 1: Resposta Inicial para Recálculo

**Nome da Regra:** Resposta Automática - Recálculo

**Quando:**
- Incoming Message
- Message Content → Contains → "recálculo"

**Fazer:**
- Send a Message: 
```
Olá! 👋

Recebemos sua solicitação de recálculo. 

Para agilizar o atendimento, por favor nos informe:

📋 **Tipo de recálculo:**
• INSS
• FGTS
• IRRF
• Outro (especificar)

📅 **Período:** Mês/Ano

📄 **Documento:** Anexe o documento relacionado (se possível)

Um de nossos especialistas irá atendê-lo em breve!

⏱️ Tempo médio de resposta: 15-30 minutos
```

- Assign Team → Equipe Fiscal
- Add Label → recalculo

---

### Exemplo 2: Resposta para Guias

**Nome da Regra:** Resposta Automática - Guias

**Quando:**
- Incoming Message
- Message Content → Contains → "guia"

**Fazer:**
- Send a Message:
```
Olá! 👋

Entendi que você precisa de uma guia. 

Por favor, especifique:

📑 **Tipo de guia:**
• DARF
• GPS
• GRU
• Outra (especificar)

📅 **Competência:** Mês/Ano

🏢 **Empresa:** Nome/CNPJ

Vou providenciar sua guia o mais rápido possível!
```

- Assign Team → Equipe Fiscal
- Add Label → guias

---

### Exemplo 3: Resposta para Folha de Pagamento

**Nome da Regra:** Resposta Automática - Folha

**Quando:**
- Incoming Message
- Message Content → Contains Any → "folha" OR "holerite" OR "pagamento"

**Fazer:**
- Send a Message:
```
Olá! 👋

Vi que você tem uma questão sobre folha de pagamento.

Como posso ajudar?

💰 **Dúvidas comuns:**
• Conferir holerite
• Entender descontos
• Férias e 13º
• Adicional de horas extras
• Outros

Por favor, detalhe sua dúvida para que eu possa ajudá-lo melhor!
```

- Assign Team → Departamento Pessoal
- Add Label → folha-pagamento

---

### Exemplo 4: Atendimento Urgente

**Nome da Regra:** Prioridade Alta - Urgente

**Quando:**
- Incoming Message
- Message Content → Contains Any → "urgente" OR "emergência" OR "emergencia"

**Fazer:**
- Send a Message:
```
⚠️ ATENDIMENTO PRIORITÁRIO

Identificamos que seu caso é urgente.

Estou direcionando para nossa equipe de atendimento imediato.

⏰ Aguarde até 10 minutos para resposta.

Enquanto isso, por favor descreva:
• O problema
• Prazo limite
• Documentos necessários
```

- Assign Team → Atendimento Prioritário
- Add Label → urgente
- Set Priority → Urgent

---

## 🎯 Roteamento Inteligente

### Exemplo 1: Por Horário

**Nome:** Fora do Horário Comercial

**Quando:**
- Incoming Message
- Is outside office hours

**Fazer:**
- Send a Message:
```
Olá! 👋

No momento estamos fora do horário de atendimento.

🕐 **Nosso horário:**
Segunda a Sexta: 8h às 18h

📩 Deixe sua mensagem que retornaremos assim que possível!

Para urgências, entre em contato pelo telefone:
📞 (XX) XXXX-XXXX
```

- Add Label → fora-horario

---

### Exemplo 2: Primeiro Contato

**Nome:** Boas-vindas - Novo Cliente

**Quando:**
- Conversation Created
- Contact → Custom Attribute → cliente_novo → equals → true

**Fazer:**
- Send a Message:
```
🎉 Bem-vindo(a) à nossa Central de Atendimento!

É um prazer tê-lo(a) conosco!

Como podemos ajudá-lo(a) hoje?

💼 **Principais serviços:**
• Recálculos
• Emissão de guias
• Folha de pagamento
• Consultoria
• Dúvidas gerais

Escolha uma opção ou descreva como podemos ajudar!
```

- Assign Agent → Atendente Disponível

---

## ⏰ Horário de Atendimento

### Configurar Horário Comercial

1. Vá em **Settings** → **Inboxes**
2. Selecione seu inbox
3. Clique em **Settings**
4. Configure **Working Hours**:

```
Segunda: 08:00 - 18:00
Terça:   08:00 - 18:00
Quarta:  08:00 - 18:00
Quinta:  08:00 - 18:00
Sexta:   08:00 - 18:00
Sábado:  [desabilitado]
Domingo: [desabilitado]
```

### Mensagem de Ausência

Em **Settings** → **Inboxes** → **Out of Office**:

```
Olá! 👋

No momento nossa equipe não está disponível.

🕐 Horário de atendimento:
Segunda a Sexta-feira
08:00 às 18:00

Deixe sua mensagem e retornaremos em breve!

Em caso de urgência:
📞 (XX) XXXX-XXXX
📧 urgente@contabilidade.com.br
```

---

## 📝 Mensagens Pré-definidas (Canned Responses)

### 1. Solicitar Documentos

**Shortcode:** `/docs`

**Mensagem:**
```
Para dar continuidade ao seu atendimento, preciso que você envie os seguintes documentos:

📄 Documentos necessários:
• [documento 1]
• [documento 2]
• [documento 3]

Você pode anexá-los aqui no chat ou enviar por e-mail para:
📧 documentos@contabilidade.com.br

Aguardo! 😊
```

---

### 2. Prazo de Atendimento

**Shortcode:** `/prazo`

**Mensagem:**
```
Sua solicitação foi registrada! ✅

⏱️ Prazo estimado:
• Análise inicial: 24h
• Resolução: 2-3 dias úteis

Você receberá atualizações por:
📧 E-mail
💬 WhatsApp (se cadastrado)

Precisa de algo mais urgente? Me avise!
```

---

### 3. Conclusão de Atendimento

**Shortcode:** `/concluir`

**Mensagem:**
```
Perfeito! ✅

Seu atendimento foi concluído com sucesso.

Ficou alguma dúvida? Estou à disposição!

📊 Nos ajude a melhorar:
Como você avalia nosso atendimento?
⭐⭐⭐⭐⭐

Até breve! 😊
```

---

### 4. Transferir para Especialista

**Shortcode:** `/transferir`

**Mensagem:**
```
Perfeito! Vou transferir você para um especialista na área.

⏱️ Tempo de espera: 5-10 minutos

Enquanto aguarda, aproveite para:
• Separar documentos relacionados
• Anotar suas dúvidas específicas

Obrigado pela compreensão! 😊
```

---

## 🎬 Macros Úteis

### Macro 1: Iniciar Atendimento

**Nome:** Iniciar Atendimento

**Ações:**
1. Assign to me
2. Add Label → em-atendimento
3. Set Priority → Medium
4. Send Message:
```
Olá! 👋

Meu nome é [Nome] e vou cuidar do seu atendimento.

Vamos resolver sua solicitação juntos!
```

---

### Macro 2: Aguardando Cliente

**Nome:** Aguardando Retorno do Cliente

**Ações:**
1. Add Label → aguardando-cliente
2. Set Status → Pending
3. Send Message:
```
Fico no aguardo das informações solicitadas.

Quando estiver pronto, é só responder aqui que continuamos! 😊

⏰ Este chat ficará ativo por 7 dias.
```

---

### Macro 3: Resolver e Fechar

**Nome:** Resolver e Finalizar

**Ações:**
1. Set Status → Resolved
2. Add Label → resolvido
3. Remove Label → em-atendimento
4. Send Message:
```
Atendimento concluído! ✅

Foi um prazer ajudá-lo(a)!

Precisando de algo, estamos sempre à disposição.

Até breve! 😊
```

---

## 📊 Relatórios e Métricas

### Métricas Importantes para Acompanhar

1. **Tempo Médio de Primeira Resposta**
   - Meta: < 15 minutos

2. **Tempo Médio de Resolução**
   - Meta: < 24 horas

3. **Satisfação do Cliente (CSAT)**
   - Meta: > 90%

4. **Taxa de Resolução no Primeiro Contato**
   - Meta: > 70%

### Configurar Relatórios

1. Vá em **Reports**
2. Selecione período
3. Analise:
   - Conversas por agente
   - Conversas por equipe
   - Conversas por label
   - Tempos de resposta

---

## 🏷️ Sistema de Labels

### Labels Sugeridas

**Por Tipo de Serviço:**
- `recalculo`
- `guias`
- `folha-pagamento`
- `consultoria`
- `duvidas`
- `certidoes`
- `alteracao-contratual`

**Por Status:**
- `em-atendimento`
- `aguardando-cliente`
- `aguardando-documentos`
- `em-analise`
- `resolvido`

**Por Prioridade:**
- `urgente`
- `importante`
- `normal`

**Por Origem:**
- `site-suporte`
- `whatsapp`
- `email`
- `telefone`

---

## 🤖 Próximos Passos para Bot Avançado

### 1. Integração com Dialogflow

O Chatwoot suporta integração com Dialogflow para bots mais sofisticados:

1. Crie um agente no Dialogflow
2. Configure intents para cada tipo de serviço
3. Integre com Chatwoot via webhook
4. Configure fallback para agentes humanos

### 2. Integração com WhatsApp Business API

Para atendimento omnichannel:

1. Configure WhatsApp Business API
2. Conecte com Chatwoot
3. Use as mesmas automações
4. Mantenha histórico unificado

### 3. Chatbot com IA

Considere usar:
- Rasa (open source)
- Botpress (open source)
- GPT-3/4 via API
- Claude API (nossa plataforma!)

---

## 💡 Dicas de Boas Práticas

1. **Teste todas as automações** antes de ativar
2. **Monitore as métricas** semanalmente
3. **Atualize respostas** baseado no feedback
4. **Treine a equipe** nas ferramentas
5. **Revise regras** mensalmente
6. **Mantenha tom amigável** nas mensagens
7. **Use emojis moderadamente** 😊
8. **Personalize** conforme o cliente
9. **Documente processos** internos
10. **Peça feedback** constantemente

---

## 🆘 Casos de Uso Específicos

### Período de Impostos (Busy Season)

Crie automação especial:

```
Bem-vindo! 🎉

⚠️ PERÍODO DE DECLARAÇÕES

Estamos em período intenso de entregas.

Tempo de resposta atual: 1-2 horas

Para agilizar:
• Tenha documentos em mãos
• Seja específico na dúvida
• Use nosso FAQ: [link]

Obrigado pela compreensão!
```

### Fechamento de Final de Ano

```
Olá! 🎄

Estamos no período de fechamento anual.

🗓️ Prazos importantes:
• Balanço: até dia XX
• DIRF: até dia XX
• DCTF: até dia XX

Como podemos ajudar?
```

---

## 📞 Suporte Adicional

Para configurações avançadas:
- Documentação Chatwoot: https://www.chatwoot.com/docs
- Comunidade: https://github.com/chatwoot/chatwoot
- Discord: https://discord.gg/cJXdrwS

---

**Pronto para automatizar seu atendimento! 🚀**

Implemente gradualmente, teste bastante e ajuste conforme necessário.