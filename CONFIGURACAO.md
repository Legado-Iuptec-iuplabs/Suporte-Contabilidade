# 📋 Central de Atendimento - Guia de Configuração

## 🎯 Sobre o Projeto

Esta é uma página de suporte profissional integrada com Chatwoot, desenvolvida especialmente para empresas de contabilidade. A página é totalmente responsiva e permite que clientes solicitem serviços, tirem dúvidas e acompanhem novidades da empresa.

---

## ⚙️ Configuração Inicial do Chatwoot

### Passo 1: Obter o Website Token

1. Acesse sua instância do Chatwoot
2. Vá em **Settings** (Configurações)
3. Clique em **Inboxes** (Caixas de entrada)
4. Selecione ou crie um inbox do tipo **Website**
5. Copie o **Website Token** (algo como: `abcd1234efgh5678`)

### Passo 2: Configurar na Página

Abra o arquivo `suporte-contabilidade.html` e localize a linha **469**:

```javascript
const CHATWOOT_CONFIG = {
    websiteToken: 'SEU_WEBSITE_TOKEN_AQUI', // ← COLE SEU TOKEN AQUI
    baseUrl: 'https://sua-instancia.chatwoot.com', // ← COLE SUA URL AQUI
    position: 'right',
    locale: 'pt_BR',
    type: 'standard'
};
```

**Exemplo de configuração preenchida:**
```javascript
const CHATWOOT_CONFIG = {
    websiteToken: 'xK8Pq2mNvB3rT9wL',
    baseUrl: 'https://chatwoot.minhacontabilidade.com.br',
    position: 'right',
    locale: 'pt_BR',
    type: 'standard'
};
```

---

## 🎨 Personalização da Marca

### Alterar Nome da Empresa

Linha **477**:
```javascript
const COMPANY_CONFIG = {
    name: 'Contabilidade Exemplo', // ← ALTERE AQUI
    logo: 'C'
};
```

### Alterar Logo

**Opção 1 - Usar imagem:**
Na linha **371**, substitua:
```html
<div class="logo">C</div>
```

Por:
```html
<img src="img/logo.png" alt="Logo" class="logo">
```

**Opção 2 - Manter letra inicial:**
Mantenha o código atual e apenas altere a letra no `COMPANY_CONFIG.logo`

### Alterar Cores

Linhas **14-21**, ajuste as variáveis CSS:
```css
:root {
    --cor-primaria: #2563eb;     /* Azul principal */
    --cor-secundaria: #1e40af;   /* Azul escuro */
    --cor-destaque: #3b82f6;     /* Azul claro */
    --cor-texto: #1f2937;        /* Texto escuro */
    --cor-texto-claro: #6b7280;  /* Texto cinza */
    --cor-fundo: #f9fafb;        /* Fundo claro */
    --cor-card: #ffffff;         /* Cards brancos */
    --cor-sucesso: #10b981;      /* Verde */
    --cor-alerta: #f59e0b;       /* Laranja */
}
```

**Sugestões de paletas para contabilidade:**

**Paleta Azul Confiança:**
```css
--cor-primaria: #1e40af;
--cor-secundaria: #1e3a8a;
--cor-destaque: #3b82f6;
```

**Paleta Verde Prosperidade:**
```css
--cor-primaria: #059669;
--cor-secundaria: #047857;
--cor-destaque: #10b981;
```

**Paleta Cinza Profissional:**
```css
--cor-primaria: #4b5563;
--cor-secundaria: #374151;
--cor-destaque: #6b7280;
```

---

## 📝 Editando Conteúdo

### Adicionar/Editar Serviços

Os cards de serviços estão na linha **263**. Para adicionar um novo serviço, copie este bloco:

```html
<div class="service-card" onclick="abrirChatComMensagem('Sua mensagem aqui')">
    <div class="service-icon">
        <i class="fas fa-seu-icone"></i>
    </div>
    <h3>Título do Serviço</h3>
    <p>Descrição do serviço oferecido.</p>
</div>
```

**Ícones disponíveis (FontAwesome):**
- `fa-calculator` - Calculadora
- `fa-file-invoice` - Documento/Guia
- `fa-money-check-alt` - Dinheiro/Pagamento
- `fa-question-circle` - Dúvidas
- `fa-briefcase` - Serviços
- `fa-bolt` - Urgente
- `fa-chart-line` - Gráficos/Relatórios
- `fa-handshake` - Consultoria
- `fa-building` - Empresa
- `fa-balance-scale` - Jurídico

Veja mais em: https://fontawesome.com/icons

### Editar Novidades

Seção começa na linha **298**. Estrutura de cada card:

```html
<div class="news-card">
    <div class="news-badge">TIPO</div> <!-- NOVO, IMPORTANTE, DICA -->
    <div class="news-content">
        <div class="news-date">
            <i class="fas fa-calendar"></i> Data
        </div>
        <h3>Título da Novidade</h3>
        <p>Descrição da novidade ou aviso importante.</p>
    </div>
</div>
```

**Tipos de Badge:**
- `NOVO` (azul) - Para novidades
- `IMPORTANTE` (laranja) - Para avisos
- `DICA` (verde) - Para dicas

### Editar FAQ

Seção começa na linha **339**. Estrutura de cada item:

```html
<div class="faq-item">
    <div class="faq-question" onclick="toggleFAQ(this)">
        <span>Pergunta aqui?</span>
        <i class="fas fa-chevron-down faq-icon"></i>
    </div>
    <div class="faq-answer">
        Resposta detalhada aqui.
    </div>
</div>
```

### Editar Rodapé

Seção começa na linha **374**. Altere:

- **Telefone:** Linha 383
- **E-mail:** Linha 384
- **Endereço:** Linha 385
- **Links de Serviços:** Linhas 391-395
- **Horário:** Linha 402

**Redes Sociais (linha 386):**
```html
<a href="https://facebook.com/suapagina"><i class="fab fa-facebook-f"></i></a>
<a href="https://instagram.com/suapagina"><i class="fab fa-instagram"></i></a>
<a href="https://linkedin.com/company/suaempresa"><i class="fab fa-linkedin-in"></i></a>
<a href="https://wa.me/5500000000000"><i class="fab fa-whatsapp"></i></a>
```

---

## 🚀 Como as Mensagens Funcionam

Quando o usuário clica em um card de serviço, a função `abrirChatComMensagem()` é chamada:

```javascript
onclick="abrirChatComMensagem('Olá! Gostaria de solicitar um recálculo.')"
```

Isso:
1. Abre o widget do Chatwoot
2. Pré-preenche uma mensagem contextual
3. Facilita o atendimento categorizando a solicitação

**Dica:** Personalize essas mensagens para cada tipo de serviço para melhorar o fluxo de atendimento!

---

## 🤖 Preparando para Bot (Futuro)

A estrutura já está preparada para integração com bot. As mensagens pré-definidas ajudam a:

1. **Categorizar** automaticamente as solicitações
2. **Rotear** para o departamento correto
3. **Criar regras** de automação no Chatwoot

### Como configurar bot no Chatwoot:

1. Vá em **Settings > Automation**
2. Crie regras baseadas nas mensagens iniciais
3. Configure respostas automáticas
4. Direcione para equipes específicas

**Exemplo de regra:**
```
SE mensagem contém "recálculo"
ENTÃO atribuir para "Equipe Fiscal"
E responder "Recebemos sua solicitação de recálculo..."
```

---

## 📱 Responsividade

A página é **totalmente responsiva** e se adapta a:

- ✅ Smartphones (320px+)
- ✅ Tablets (768px+)
- ✅ Desktops (1024px+)
- ✅ Telas grandes (1920px+)

---

## 🎯 Recursos da Página

### 1. **Header Fixo**
- Logo customizável
- Nome da empresa
- Botão de chat rápido

### 2. **Hero Section**
- Título de boas-vindas
- Descrição dos serviços

### 3. **Cards de Serviços**
- 6 tipos de atendimento pré-configurados
- Ícones intuitivos
- Mensagens contextuais

### 4. **Seção de Novidades**
- 3 cards para avisos e novidades
- Badges coloridos por tipo
- Datas para cada notícia

### 5. **FAQ Expansível**
- 4 perguntas frequentes
- Expandir/colapsar ao clicar
- Fácil de adicionar novas perguntas

### 6. **Rodapé Completo**
- Informações de contato
- Links de serviços
- Redes sociais
- Botão de chat

### 7. **Botão Flutuante**
- Sempre visível
- Badge de notificação (opcional)
- Acesso rápido ao chat

---

## 📦 Arquivos Necessários

```
projeto/
│
├── suporte-contabilidade.html  (arquivo principal)
├── img/
│   └── logo.png               (sua logo - opcional)
└── README.md                  (este arquivo)
```

---

## 🌐 Publicação

### Opção 1: Hospedagem Simples

1. Faça upload do arquivo HTML para seu servidor
2. Acesse via `https://seusite.com.br/suporte.html`

### Opção 2: GitHub Pages (Grátis)

1. Crie um repositório no GitHub
2. Faça upload do arquivo
3. Ative GitHub Pages nas configurações
4. Acesse via `https://seuusuario.github.io/projeto/`

### Opção 3: Netlify/Vercel (Grátis)

1. Crie conta no Netlify ou Vercel
2. Faça upload ou conecte com GitHub
3. Deploy automático
4. SSL gratuito incluído

---

## 🔧 Manutenção

### Atualizar Novidades

Acesse regularmente as linhas **298-337** e:
- Atualize as datas
- Adicione novas novidades
- Remova avisos antigos

### Monitorar Atendimentos

No Chatwoot:
- Acompanhe métricas de atendimento
- Veja quais serviços são mais solicitados
- Ajuste as mensagens pré-definidas conforme necessário

---

## 💡 Dicas de Uso

1. **Atualize as novidades semanalmente** para manter os clientes engajados
2. **Monitore as perguntas** frequentes no chat e adicione no FAQ
3. **Teste em diferentes dispositivos** antes de publicar
4. **Use Google Analytics** para acompanhar acessos
5. **Peça feedback** dos clientes sobre a página

---

## 🆘 Solução de Problemas

### Chat não aparece?
- Verifique se o `websiteToken` está correto
- Confirme se a URL do Chatwoot está acessível
- Abra o console do navegador (F12) para ver erros

### Mensagens não são enviadas?
- Verifique a configuração do inbox no Chatwoot
- Confirme se o inbox está ativo
- Teste manualmente abrindo o widget

### Cores não mudam?
- Limpe o cache do navegador (Ctrl+Shift+R)
- Verifique se as variáveis CSS estão corretas
- Use o inspetor do navegador para debug

### Logo não aparece?
- Verifique o caminho do arquivo
- Confirme o formato (PNG, JPG, SVG)
- Teste com URL completa primeiro

---

## 📞 Suporte

Para dúvidas sobre:

- **Chatwoot:** https://www.chatwoot.com/docs
- **FontAwesome:** https://fontawesome.com/docs
- **HTML/CSS:** https://developer.mozilla.org/pt-BR/

---

## 📄 Licença

Este template é de uso livre para fins comerciais e pessoais.

---

## 🎉 Pronto!

Sua página de suporte está configurada e pronta para uso. Lembre-se de:

✅ Configurar o Chatwoot corretamente
✅ Personalizar com a identidade da sua marca
✅ Atualizar regularmente o conteúdo
✅ Monitorar o desempenho e ajustar conforme necessário

**Boa sorte com seu novo canal de atendimento!** 🚀