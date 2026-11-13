---
name: SERVERSO Design System
description: Sistema visual e de interface do ecossistema digital integrador do Grupo Ser Educacional / UNINASSAU
colors:
  primary: "#002B66"
  primary-hover: "#001A3D"
  accent-blue: "#0369A1"
  accent-blue-hover: "#075985"
  accent-blue-soft: "#E0F2FE"
  accent-gold: "#FFB800"
  neutral-bg: "#F8FAFC"
  neutral-surface: "#FFFFFF"
  neutral-subtle: "#F1F5F9"
  border-default: "#E2E8F0"
  text-main: "#0F172A"
  text-secondary: "#475569"
  text-muted: "#64748B"
  status-success: "#166534"
  status-success-bg: "#DCFCE7"
  status-warning: "#92400E"
  status-warning-bg: "#FEF3C7"
  status-danger: "#991B1B"
  status-danger-bg: "#FEE2E2"
typography:
  display:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif"
    fontSize: "1.85rem"
    fontWeight: 800
    lineHeight: 1.2
    letterSpacing: "-0.02em"
  headline:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif"
    fontSize: "1.25rem"
    fontWeight: 800
    lineHeight: 1.3
  title:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif"
    fontSize: "1rem"
    fontWeight: 700
    lineHeight: 1.35
  body:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif"
    fontSize: "0.88rem"
    fontWeight: 400
    lineHeight: 1.5
  label:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif"
    fontSize: "0.75rem"
    fontWeight: 700
    lineHeight: 1.2
    letterSpacing: "0.04em"
rounded:
  sm: "8px"
  md: "12px"
  lg: "16px"
  pill: "9999px"
spacing:
  xs: "4px"
  sm: "8px"
  md: "16px"
  lg: "24px"
  xl: "32px"
components:
  button-primary:
    backgroundColor: "{colors.accent-blue}"
    textColor: "{colors.neutral-surface}"
    rounded: "{rounded.pill}"
    padding: "8px 16px"
  button-primary-hover:
    backgroundColor: "{colors.accent-blue-hover}"
  button-secondary:
    backgroundColor: "{colors.neutral-surface}"
    textColor: "{colors.text-main}"
    rounded: "{rounded.pill}"
    padding: "8px 16px"
  card-default:
    backgroundColor: "{colors.neutral-surface}"
    rounded: "{rounded.md}"
    padding: "20px 24px"
---

# Design System: SERVERSO

## Overview

**Creative North Star: "The Frictionless Academic Cockpit"**

O SERVERSO foi projetado para ser o centro de comando limpo, responsivo e desobstruído da vida acadêmica do estudante da UNINASSAU. Afastando-se de portais acadêmicos densos, burocráticos e visualmente caóticos, o sistema adota uma linguagem visual contemporânea do tipo SaaS, priorizando escaneabilidade rápida, tipografia austera e cartões com limites bem definidos.

Toda a experiência é estruturada em torno de micro-tarefas imediatas: verificar notas sem esforço de navegação, checar se a frequência está segura em relação ao limite regimental, validar prazos de avaliações e liquidar mensalidades com benefício de pontualidade com o mínimo de cliques. O tom é acolhedor, profissional e institucional, mantendo o estudante focado em seu desempenho sem ruídos decorativos.

**Key Characteristics:**
- Superfícies claras e neutras (`#F8FAFC`) com cartões brancos puros elevados por sombras suaves.
- Uso cirúrgico do azul institucional da UNINASSAU (`#002B66`) e azul de ação (`#0284C7`), evitando saturação cromática excessiva.
- Numerais tabulares obrigatórios em notas, faltas, códigos de matrícula e valores monetários.
- Componentes com cantos suavemente curvados (`12px` em containers, pílula `9999px` em tags e botões operacionais).

## Colors

A paleta equilibra a sobriedade institucional da UNINASSAU com a vivacidade moderna de plataformas digitais ágeis.

### Primary
- **Nassau Navy** (`#002B66`): Utilizado como ancoragem institucional no logo, cabeçalhos de destaque e elementos mestres de identificação.

### Secondary
- **Action Sky Blue** (`#0284C7`): A cor de ação primária, botões de ação e links ativos.
- **Action Sky Blue Hover** (`#0369A1`): Estado interativo escurecido com contraste aprimorado.
- **Action Sky Blue Soft** (`#E0F2FE`): Fundo de elementos selecionados, avatares de destaque e badges informativas.
- **Institutional Gold Accent** (`#FFB800`): Destaque institucional reservado a detalhes de alta prioridade.

### Neutral
- **Canvas Gray** (`#F8FAFC`): Fundo geral da aplicação, proporcionando descanso visual.
- **Pure Paper** (`#FFFFFF`): Fundo de cartões, modais e containers de dados.
- **Subtle Surface** (`#F1F5F9`): Fundo de campos de entrada, tags desmarcadas e divisórias suaves.
- **Line Border** (`#E2E8F0`): Borda padrão dos cartões e tabelas, garantindo delimitação sem peso visual.
- **Ink Primary** (`#0F172A`): Cor principal de leitura para títulos e dados de alta importância (contraste > 10:1).
- **Ink Secondary** (`#475569`): Texto secundário, rótulos e metadados com contraste garantido >= 4.5:1.
- **Ink Muted** (`#64748B`): Texto de apoio e instruções complementares.

### Status & Feedback
- **Success Forest** (`#166534` com fundo `#DCFCE7`): Notas excelentes, frequência 100% e títulos quitados.
- **Warning Amber** (`#92400E` com fundo `#FEF3C7`): Alerta de faltas próximas ao limite e parcelas em aberto.
- **Danger Crimson** (`#991B1B` com fundo `#FEE2E2`): Reprovação por falta ou pendências críticas.

### Named Rules
**The Rarity of Blue Rule.** O azul de ação (`#0284C7`) nunca deve cobrir mais de 10% de uma tela. Sua função é guiar o olhar para a ação principal imediata (ex.: "Sala Virtual", "Pagar Pix", "Solicitar").

## Typography

**Display & Body Font:** `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif`  
**Mono/Tabular Font:** `ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace`  

**Character:** Tipografia de sistema nativa, rápida para carregar, neutra e com legibilidade impecável em resoluções de desktop e mobile.

### Hierarchy
- **Display** (800, `1.85rem` / `29.6px`, line-height `1.2`, tracking `-0.02em`): Saudação principal do Hero ("Olá, Lucas ! 👋").
- **Headline** (800, `1.25rem` / `20px`, line-height `1.3`): Títulos de seções ("Disciplinas do Semestre", "Especialmente para você").
- **Title** (700, `0.98rem`–`1rem` / `16px`, line-height `1.3`): Nomes das matérias e títulos de serviços.
- **Body** (400, `0.88rem` / `14px`, line-height `1.5`): Textos descritivos, informações de docentes e tabelas.
- **Label** (700, `0.75rem` / `12px`, letter-spacing `0.04em`, uppercase): Indicadores de notas, cabeçalhos de coluna e categorias.

### Named Rules
**The Tabular Precision Rule.** Todos os números acadêmicos (matrícula, notas AV1/AV2, faltas, valores em reais e datas) devem obrigatoriamente usar `font-variant-numeric: tabular-nums;` para manter alinhamento vertical e estabilidade visual.

## Layout

O layout segue o modelo de barra lateral fixa (`240px`) à esquerda com área de conteúdo fluida centralizada e espaçamento respirável.

- **Header Fixo:** Altura de `64px`, contendo busca central em pílula com atalho `⌘ K`, botão da assistente Sofia e avatar do discente.
- **Largura Máxima:** O container principal atinge no máximo `1360px`, preservando o comprimento de linha confortável para leitura.
- **Breakpoints:**
  - `Desktop`: Sidebar expandida (`240px`) com grid de 2 a 3 colunas para cartões.
  - `Tablet (≤1024px)`: Sidebar oculta em gaveta deslizante (`translateX(-100%)`), acessada via botão de menu.
  - `Mobile (≤768px)`: Reorganização das linhas de disciplinas e metadados para fluxo vertical unificado, com padding lateral de `1rem`.

## Elevation & Depth

O sistema é predominantemente limpo e estruturado por bordas, usando sombras de forma puramente funcional para denotar elevação interativa.

### Shadow Vocabulary
- **Subtle Surface** (`box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.04), 0 1px 2px -1px rgba(0, 0, 0, 0.03)`): Aplicado a todos os cartões de disciplina e blocos em repouso.
- **Hover Lift** (`box-shadow: 0 8px 20px -4px rgba(15, 23, 42, 0.08)`): Usado ao passar o cursor sobre cartões promocionais e botões de atalho.
- **Floating Widget** (`box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1)`): Aplicado ao botão flutuante da Sofia e ao drawer lateral.

### Named Rules
**The Border-First Elevation Rule.** Em repouso, cartões e painéis utilizam borda sutil de 1px (`#E2E8F0`) em vez de sombras pesadas. A elevação é reservada para indicar estado ativo ou sobreposição temporal.

## Shapes

A linguagem de formas comunica suavidade e eficiência moderna:
- **Containers e Cartões:** Raio de `12px` (`--radius-md`).
- **Botões e Tags de Onboarding:** Formato em pílula (`--radius-pill` de `9999px`).
- **Campos de Entrada:** Arredondados com `8px` (`--radius-sm`) ou pílula completa na busca global.
- **Avatares:** Círculos perfeitos (`50%`).

## Components

### Buttons
- **Shape:** Pílula (`9999px`) ou raio sutil (`8px`).
- **Primary ("Sala Virtual" / Ações Principais):** Fundo `#0284C7` (ou `#002B66` na matéria em foco), texto `#FFFFFF`, padding `8px 16px`, transição suave de `0.15s ease`.
- **Secondary / Ghost:** Fundo `#F8FAFC`, borda `1px solid #E2E8F0`, texto `#0F172A`.

### Chips & Tags
- **Onboarding Tags:** Fundo `#FFFFFF`, borda `#E2E8F0`, texto `#475569`, raio `9999px`.
- **Status Badges:** Fundo pastel (`#DCFCE7`, `#FEF3C7`), texto escurecido de alto contraste (`#166534`, `#92400E`).

### Cards
- **Discipline Row Card:** Fundo `#FFFFFF`, borda `#E2E8F0`, padding `20px 24px`, alinhamento horizontal com avatar da letra da matéria à esquerda, notas ao centro e ação à direita.

### Sofia Assistant Drawer
- **Launcher:** Botão flutuante inferior direito (`bottom: 2rem; right: 2rem;`), com avatar com gradiente, indicador verde de presença e abertura suave em slide (`translateX(0)`).

## Do's and Don'ts

### Do:
- **Do** manter a identificação discente de Lucas Freitas e o curso TADS consistentes em todos os módulos.
- **Do** preservar as notas de AV1 reais do aluno (ex.: AV1 10.0 em Engenharia de Requisitos).
- **Do** utilizar numerais tabulares em qualquer dado numérico, monetário ou de frequência.
- **Do** fornecer atalhos acessíveis para fechamento de gavetas e modais com a tecla `Escape`.

### Don't:
- **Don't** aplicar gradientes multicoloridos em textos ou sombras coloridas com deslocamento nulo.
- **Don't** utilizar emojis soltos como substitutos de ícones vetoriais em botões operacionais.
- **Don't** quebrar a navegação mobile criando zonas mortas sem acesso ao menu.
- **Don't** sobrepor elementos flutuantes sobre links ou rodapés úteis da tela.
