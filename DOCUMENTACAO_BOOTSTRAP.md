# Documentacao do Projeto - Refatoracao Bootstrap

## Descricao do Sistema

O **Secret Phase** e um portal de noticias sobre games, desenvolvido como um mini-sistema web responsivo. O site possui multiplas paginas cobrindo noticias, forum de discussao, promocoes de jogos, lancamentos futuros, formulario de contato e um painel administrativo (dashboard).

O projeto foi refatorado para utilizar **Bootstrap 5.3.3** como principal ferramenta de layout e componentes, mantendo o tema escuro original e toda a estrutura de conteudo pre-existente.

---

## Estrutura do Projeto

```
/projeto-web
  /views
    |- index.html          -> Pagina inicial (Home)
    |- contato.html        -> Pagina de contato (Formulario/Cadastro)
    |- forum.html          -> Pagina do forum (Listagem/Tabela)
    |- dashboard.html      -> Painel administrativo (Dashboard)
    |- promocoes.html      -> Pagina de promocoes
    |- faseLancamento.html -> Pagina de lancamentos
    |- noticia1-7.html     -> Paginas de noticias individuais
  /public/styles
    |- indexStyles.css      -> CSS customizado principal
    |- (demais arquivos CSS simplificados)
  /img
    |- (imagens do projeto)
```

---

## Componentes Bootstrap Utilizados

O projeto utiliza **10 componentes Bootstrap diferentes**, superando o minimo obrigatorio de 6.

### 1. Navbar (presente em TODAS as paginas)

Componente de navegacao responsivo com a classe `navbar navbar-expand-lg navbar-dark`. Inclui:
- **Logo** como `navbar-brand`
- **Botao toggler** (`navbar-toggler`) para menu mobile/tablet
- **Links de navegacao** (`navbar-nav`, `nav-item`, `nav-link`)
- **Formulario de busca** integrado (`d-flex`)
- **Collapse** (`navbar-collapse`) para responsividade

A Navbar e **identica em todas as paginas** com links funcionais para todas as secoes do site.

**Paginas:** Todas (index, contato, forum, dashboard, promocoes, faseLancamento, noticia1-7)

### 2. Carousel (index.html, forum.html, promocoes.html, faseLancamento.html)

Componente de slideshow automatico com as classes `carousel slide`. Inclui:
- **Indicadores** (`carousel-indicators`) para navegacao direta entre slides
- **Itens do carousel** (`carousel-item`) com imagens de noticias
- **Legendas** (`carousel-caption`) sobre as imagens
- **Controles prev/next** (`carousel-control-prev/next`)
- Atributo `data-bs-ride="carousel"` para rotacao automatica

**Paginas:** index.html, forum.html, promocoes.html, faseLancamento.html

### 3. Card (index.html, dashboard.html, promocoes.html, faseLancamento.html, todas as noticias)

Componente de container flexivel (`card`). Variantes utilizadas:
- **Cards horizontais** com `row g-0` e `col-md-*` (noticias na index)
- **Cards verticais** com `card-img-top` (aside/sidebar, promocoes)
- **Cards coloridos** com cores Bootstrap (dashboard - azul, verde, amarelo, vermelho)
- **Cards com header** (`card-header`) no dashboard
- Subcomponentes: `card-body`, `card-title`, `card-text`, `card-img-top`, `card-img-bottom`

**Paginas:** index.html, dashboard.html, promocoes.html, faseLancamento.html, noticia1-7.html

### 4. Alert (index.html, forum.html, dashboard.html, contato.html, faseLancamento.html)

Componente de mensagem de destaque (`alert`). Variantes:
- `alert-info` - boas-vindas na Home e destaque em lancamentos
- `alert-warning` - notificacao de exclusao no forum e alertas no dashboard
- `alert-success` - confirmacao de envio no contato e sucesso no dashboard
- `alert-dismissible` com `btn-close` para fechar

**Paginas:** index.html, forum.html, dashboard.html, contato.html, faseLancamento.html

### 5. Table (forum.html, dashboard.html)

Tabela estilizada com classes Bootstrap:
- `table` - estilo base
- `table-striped` - linhas alternadas
- `table-hover` - destaque ao passar o mouse
- `table-dark` - tema escuro
- `table-responsive` - wrapper para responsividade mobile
- Estrutura com `thead` (cabecalho) e `tbody` (corpo)
- **6 registros ficticios** no forum (topicos de discussao)

**Paginas:** forum.html (listagem principal), dashboard.html (noticias recentes)

### 6. Modal (forum.html, contato.html)

Janela de dialogo flutuante (`modal`). Utilizacoes:
- **6 modals de detalhes** no forum - cada topico tem um botao "Detalhes" que abre um modal com o conteudo completo
- **Modal de confirmacao** no contato - ao clicar "Enviar", abre modal perguntando se deseja confirmar
- **Modal de sucesso** no contato - apos confirmar, exibe modal com mensagem de sucesso
- Subcomponentes: `modal-dialog`, `modal-content`, `modal-header`, `modal-body`, `modal-footer`
- Ativacao via `data-bs-toggle="modal"` e `data-bs-target`

**Paginas:** forum.html (detalhes dos topicos), contato.html (confirmacao e sucesso)

### 7. Formulario / Form (contato.html)

Formulario Bootstrap completo com:
- **Input texto** (`form-control`, type="text") - campo nome
- **Input e-mail** (`form-control`, type="email") - campo email
- **Select** (`form-select`) - selecao de assunto com 5 opcoes
- **Textarea** (`form-control`, rows="5") - campo mensagem
- **Labels** (`form-label`) para todos os campos
- **Botao** (`btn btn-highlight`) de envio

**Pagina:** contato.html

### 8. Badge (dashboard.html)

Pequenos rotulos de status usando `badge`:
- `badge bg-success` - status "Publicado"
- `badge bg-warning text-dark` - status "Revisao"

**Pagina:** dashboard.html

### 9. Button / Btn (todas as paginas)

Botoes estilizados com classes `btn`:
- `btn btn-outline-info` - botao de busca na navbar
- `btn btn-highlight` - botao customizado de envio/acao
- `btn btn-sm btn-info` - botoes "Detalhes" na tabela do forum
- `btn btn-sm btn-danger` - botoes "Excluir" na tabela do forum
- `btn btn-secondary` - botoes de cancelar/fechar
- `btn btn-success` - botao de confirmar
- `btn btn-outline-*` - botoes de acesso rapido no dashboard

**Paginas:** Todas

### 10. List Group / List Unstyled (footer de todas as paginas)

Listas sem marcadores com `list-unstyled` para os links do footer, organizadas em tres colunas responsivas.

**Paginas:** Todas

---

## Sistema de Grid Bootstrap

Todas as paginas utilizam o sistema de grid do Bootstrap:

- **`.container-fluid`** - container de largura total em todas as paginas
- **`.row`** - linhas de grid para organizar o conteudo
- **`.col-lg-9` / `.col-lg-3`** - layout principal (9 colunas conteudo + 3 colunas sidebar)
- **`.col-md-4`** - colunas do footer (3 colunas iguais)
- **`.col-md-6`** - cards de promocoes (2 por linha)
- **`.col-lg-3 .col-md-6`** - cards do dashboard (4 no desktop, 2 no tablet, 1 no mobile)
- **`.col-lg-8` / `.col-lg-4`** - layout do dashboard (tabela + painel lateral)
- **`.g-3`, `.g-4`** - gutters (espacamento entre colunas)

---

## Responsividade

O projeto e totalmente responsivo, funcionando em **mobile**, **tablet** e **desktop**:

### Mobile (< 768px)
- Navbar colapsa em menu hamburguer (`navbar-toggler`)
- Cards do dashboard empilham verticalmente (`col-lg-3 col-md-6`)
- Tabela do forum esconde colunas secundarias (`d-none d-md-table-cell`)
- Sidebar fica abaixo do conteudo principal
- Cards de promocoes ocupam largura total

### Tablet (768px - 992px)
- Navbar ainda colapsada
- Cards do dashboard ficam 2 por linha (`col-md-6`)
- Conteudo principal e sidebar ainda empilhados
- Cards de promocoes 2 por linha (`col-md-6`)

### Desktop (> 992px)
- Navbar expandida com todos os links visiveis
- Layout principal: 9 colunas + 3 colunas sidebar (`col-lg-9`, `col-lg-3`)
- Cards do dashboard 4 por linha (`col-lg-3`)
- Todas as colunas da tabela visiveis

---

## Icones Bootstrap

O projeto utiliza **Bootstrap Icons** (`bootstrap-icons@1.11.3`) para icones em todo o site:

- `bi-search` - busca
- `bi-controller` - games
- `bi-heart-fill` - curtidas
- `bi-chat-fill` / `bi-chat-dots` - comentarios
- `bi-calendar-fill` - datas
- `bi-fire` - destaques
- `bi-envelope-fill` - contato
- `bi-send` - enviar
- `bi-eye` - detalhes
- `bi-trash` - excluir
- `bi-speedometer2` - dashboard
- `bi-newspaper` - noticias
- `bi-tag` - promocoes
- `bi-rocket-takeoff` - lancamentos
- `bi-youtube`, `bi-instagram`, `bi-twitter-x`, `bi-facebook` - redes sociais
- E diversos outros icones utilizados no dashboard e alertas

---

## Mudancas Realizadas na Refatoracao

### O que mudou:
1. **Bootstrap CDN** adicionado em todas as paginas (CSS + JS + Icons)
2. **Header customizado** substituido por **Navbar Bootstrap** responsiva
3. **Grid CSS customizado** substituido por **Sistema de Grid Bootstrap** (.container-fluid, .row, .col-*)
4. **Galeria de imagens** substituida por **Carousel Bootstrap** com indicadores e controles
5. **Cards de noticias** agora usam o componente **Card** do Bootstrap
6. **Formulario de contato** refatorado com classes **Form** do Bootstrap (.form-control, .form-label, .form-select)
7. **Select** e **Textarea** adicionados ao formulario (requisito do trabalho)
8. **Modals** adicionados para confirmacao de envio (contato) e detalhes dos topicos (forum)
9. **Forum** convertido para **Table Bootstrap** com .table-striped e .table-hover
10. **Dashboard** criado como nova pagina com cards de resumo e grid responsivo
11. **Footer** refatorado usando grid Bootstrap (col-md-4) com icones de redes sociais
12. **Alerts** adicionados em varias paginas (boas-vindas, exclusao, sucesso)
13. **Badges** adicionados no dashboard para status das noticias
14. **Botoes de acao** no forum (Detalhes abre Modal, Excluir exibe Alert)
15. **Tema escuro** mantido usando `data-bs-theme="dark"` e CSS customizado

### O que foi mantido:
- Todo o **conteudo textual** original das paginas
- Todas as **imagens** originais
- A **estrutura de navegacao** entre paginas
- O **esquema de cores** escuro (azul escuro, cinza, azul claro)
- A **organizacao de arquivos** (views/, public/styles/, img/)
