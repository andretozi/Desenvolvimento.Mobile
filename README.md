# HABIT — Protótipo e Organização dos Estilos com BEM

Atividade de **Desenvolvimento Mobile** — construção das 14 telas do aplicativo **HABIT**,
identificação dos elementos de interface recorrentes e organização dos estilos CSS com o padrão
**BEM (Block, Element, Modifier)**, preparando o projeto para a futura implementação em **React**.

O trabalho é feito em duas etapas:

1. **Etapa 1 — Desktop:** modelagem visual das telas para tela larga (reproduzindo os wireframes).
2. **Etapa 2 — Mobile:** adaptação do mesmo visual para telas pequenas, com *media queries*.

- **Aplicação:** HABIT (plataforma de conteúdo / blog)

---

## 1. Integrantes do grupo

| Nome                 | GitHub       |
|----------------------|--------------|
| André Tozi Magalhães | @andretozi   |
| Guilherme D. Sanches | @gui-sanchess|


---

## 2. Descrição da aplicação

O **HABIT** é uma plataforma de conteúdo (blog) onde os usuários navegam por **categorias**, leem
**postagens em destaque**, acompanham as **escolhas do editor**, assinam uma **newsletter** e usam a
**busca**. Usuários autenticados têm um **perfil** com suas postagens e comentários em diferentes
estados. A aplicação também tem uma **área administrativa**, com indicadores gerais e telas para
gerenciar categorias, criar postagens, definir escolhas do editor, administrar usuários e moderar as
filas de revisão e de comentários.

### Fluxos de navegação

- **Público:** `tela_01` (Home) → categorias (`tela_02`), destaques (`tela_03`), newsletter (`tela_04`), busca (`tela_11`).
- **Autenticação:** `tela_12` (Entrar) → `tela_13` (Criar conta) → `tela_14` (Perfil).
- **Administrativo:** `tela_05` a `tela_10`.
- **Conteúdo:** `tela_06` (Criar Post) → `tela_09` (Fila de revisão) → aprovação → publicação.

---

## 3. Telas elaboradas (14)

Wireframes de referência em [`src/wireframes/`](src/wireframes) e implementação em HTML em
[`src/pages/`](src/pages).

| # | Tela | Wireframe | HTML |
|---|------|-----------|------|
| 01 | Home | `src/wireframes/tela_01_home.png` | `src/pages/tela_01_home.html` |
| 02 | Categoria (Techno) | `src/wireframes/tela_02_categoria.png` | `src/pages/tela_02_categoria.html` |
| 03 | Destaques | `src/wireframes/tela_03_destaques.png` | `src/pages/tela_03_destaques.html` |
| 04 | Newsletter | `src/wireframes/tela_04_newsletter.png` | `src/pages/tela_04_newsletter.html` |
| 05 | Admin — Categorias | `src/wireframes/tela_05_admin_categorias.png` | `src/pages/tela_05_admin_categorias.html` |
| 06 | Admin — Criar Post | `src/wireframes/tela_06_admin_criar_post.png` | `src/pages/tela_06_admin_criar_post.html` |
| 07 | Admin — Escolhas do Editor | `src/wireframes/tela_07_admin_escolhas_editor.png` | `src/pages/tela_07_admin_escolhas_editor.html` |
| 08 | Admin — Usuários | `src/wireframes/tela_08_admin_usuarios.png` | `src/pages/tela_08_admin_usuarios.html` |
| 09 | Admin — Fila de revisão | `src/wireframes/tela_09_admin_fila_revisao.png` | `src/pages/tela_09_admin_fila_revisao.html` |
| 10 | Admin — Fila de comentários | `src/wireframes/tela_10_admin_fila_comentarios.png` | `src/pages/tela_10_admin_fila_comentarios.html` |
| 11 | Busca | `src/wireframes/tela_11_busca.png` | `src/pages/tela_11_busca.html` |
| 12 | Login | `src/wireframes/tela_12_login.png` | `src/pages/tela_12_login.html` |
| 13 | Cadastro | `src/wireframes/tela_13_cadastro.png` | `src/pages/tela_13_cadastro.html` |
| 14 | Perfil | `src/wireframes/tela_14_perfil.png` | `src/pages/tela_14_perfil.html` |

---

## 4. Componentes identificados

| Componente | Onde aparece | Variações |
|------------|--------------|-----------|
| **Header** (cabeçalho) | Todas as telas | principal |
| **Navigation** (menu) | Todas as telas | principal, `--active` |
| **Search** (busca) | Cabeçalho de todas as telas | principal |
| **Button** (botão) | Login, Cadastro, Newsletter, Admin, Cards | `--primary`, `--secondary`, `--danger`, `--disabled`, `--sm` |
| **Chip** (tag/filtro) | Home, Categoria, Rodapé | padrão, `--active` |
| **Hero** | Home | principal |
| **Card** | Home, Categoria, Destaques, Busca, Perfil | padrão, `--horizontal`, `--category`, `--post`, `--compact`, `--featured` |
| **Panel** (painel) | Newsletter, Login, Cadastro, Admin | padrão, `--narrow`, `--admin` |
| **Form** (formulário) | Login, Cadastro, Newsletter, Criar Post, Perfil | login, cadastro, newsletter, post |
| **Data-list / List** | Admin (Categorias, Escolhas do Editor), Home | com ações, links simples |
| **Table** (tabela) | Usuários, Fila de revisão, Fila de comentários | principal |
| **Stats** (indicadores) | Telas administrativas | principal |
| **Badge** (selo) | Usuários, Filas, Perfil, Destaques | `--success`, `--warning`, `--danger`, `--muted`, `--feature` |
| **Menu lateral** | Telas administrativas (05–10) | principal, `--active` |
| **Profile** | Perfil | principal |
| **Footer** (rodapé) | Todas as telas | principal |

### Variações previstas para os principais componentes

- **Button:** `--primary`, `--secondary`, `--danger`, `--disabled`, `--sm`.
- **Card:** `--horizontal`, `--category`, `--post`, `--compact`, `--featured`.
- **Badge:** `--success`, `--warning`, `--danger`, `--muted`, `--feature`.
- **Panel:** `--narrow`, `--admin`.
- **Nav / Menu:** `nav__link--active`, `menu__link--active`.

> Exemplo de aplicação do BEM (botões):
> ```css
> .button { /* forma base */ }
> .button--primary { /* preenchido verde */ }
> .button--secondary { /* contornado */ }
> .button--disabled { /* cinza, inativo */ }
> ```

---

## 5. Organização dos arquivos

```
Desenvolvimento.Mobile/
├── src/
│   ├── pages/           # As 14 telas em HTML (classes BEM aplicadas)
│   ├── style/           # Estilos organizados por RESPONSABILIDADE (BEM)
│   │   ├── variables.css   # Tokens de design (cores, tipografia, espaços)
│   │   ├── base.css        # Reset + container + grades
│   │   ├── header.css      # Cabeçalho + busca
│   │   ├── navigation.css  # Menu principal
│   │   ├── button.css      # Botões
│   │   ├── chip.css        # Chips / tags / filtros
│   │   ├── hero.css        # Hero (home)
│   │   ├── card.css        # Card e variações
│   │   ├── panel.css       # Painel
│   │   ├── form.css        # Formulários
│   │   ├── list.css        # Listas (admin + links)
│   │   ├── table.css       # Tabelas
│   │   ├── stats.css       # Indicadores (KPIs)
│   │   ├── badge.css       # Selos de status
│   │   ├── admin.css       # Layout admin + menu lateral
│   │   ├── profile.css     # Perfil
│   │   ├── footer.css      # Rodapé
│   │   └── main.css        # Agrega (via @import) todos os arquivos
│   └── wireframes/      # As 14 telas de baixa fidelidade (imagens .png)
└── README.md
```

Cada arquivo CSS reúne os estilos de **um componente / responsabilidade**, em vez de concentrar tudo
em um único arquivo. Isso facilita localizar as regras, melhora a manutenção e favorece o
reaproveitamento — que depois vira componente em React.

Os HTML carregam **apenas** o `main.css`, que importa os demais na ordem correta:

```html
<link rel="stylesheet" href="../style/main.css">
```

---

## 6. Como visualizar

Abra qualquer arquivo de `src/pages/` no navegador (ex.: `src/pages/tela_01_home.html`).
A modelagem atual é **desktop** (janela larga). A adaptação **mobile** é a etapa seguinte, feita com
*media queries* (`@media`), preservando os mesmos elementos e componentes.
