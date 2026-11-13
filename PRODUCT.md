# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Stack

SPA autossuficiente em HTML5, CSS moderno estruturado com tokens em `:root` e JavaScript vanilla (zero dependências de npm/build, portável e pronto para execução direta no navegador).

## Users

1. **Discente Universitário (Usuário Primário):**
   - Perfil real: Aluno do Centro Universitário Maurício de Nassau (UNINASSAU / Grupo Ser Educacional), ex.: Lucas Freitas (matrícula `01548922`), cursando Tecnologia em Análise e Desenvolvimento de Sistemas (TADS - 2º Período Noturno).
   - Situação e objetivos: Consulta diária de disciplinas matriculadas, notas parciais (AV1/AV2), monitoramento de faltas regimentais em relação ao teto de 25%, acesso à sala de aula virtual (Microsoft Teams/M365), abertura de requerimentos na CRA Digital (ex.: 2ª chamada) e gestão de mensalidades com desconto pontualidade na Carteira Digital.

2. **Avaliador / Docente de Engenharia de Requisitos (Público Secundário):**
   - Situação e objetivos: Análise técnica do cumprimento dos requisitos funcionais, não funcionais e regras de negócio da atividade acadêmica através do dossiê interativo e do relatório normativo formal.

## Product Purpose

Disponibilizar um ecossistema digital duplo e coeso:
- Uma réplica funcional e de alta fidelidade do **Portal do Aluno (SERVERSO)** que reproduz em nível de produção a experiência de dashboard discente, CRA Digital, carteira financeira e assistente virtual Sofia.
- Uma central integrada de documentação de Engenharia de Requisitos (dossiê interativo e relatório ABNT) para fins de auditoria acadêmica e técnica.

Sucesso significa uma experiência de usuário fluida, sem erros de script, visualmente indistinguível da aplicação oficial e completamente autônoma para distribuição e visualização local.

## Positioning

Ecossistema híbrido educacional que une uma réplica operacional do SERVERSO com a rastreabilidade integral da especificação de requisitos da UNINASSAU, permitindo navegar simultaneamente entre a aplicação prática discente e a engenharia de requisitos subjacente.

## Operating Context

- **Ecossistema:** Plataforma SERVERSO integrada ao Grupo Ser Educacional / UNINASSAU (Campus Recife - Graças).
- **Rotinas Acadêmicas:** Semestre letivo 2026.2, avaliação continuada (AV1 consolidada, AV2 pendente), teto regimental de 25% de faltas por disciplina e desconto contratual de pontualidade até o dia 05 de cada mês.
- **Canais Conectados:** Microsoft 365 Educacional (Teams, OneDrive, Outlook), assistente virtual Sofia e Central de Relacionamento com o Aluno (CRA Digital).

## Capabilities and Constraints

### Capacidades Confirmadas:
- **Dashboard Discente:** Indicadores de matrícula, período, rendimento (CRG 8.9), progresso curricular e grid com as 7 disciplinas ativas de TADS com professores, notas e faltas.
- **Central de Serviços (CRA Digital):** Busca preditiva, filtros categóricos (*Todos*, *Acadêmico*, *Financeiro*, *Documentos*, *Estágio*, *Outros*) e protocolo dinâmico de 2ª chamada com inserção em tempo real na tabela de chamados.
- **Carteira Digital:** Gestão de mensalidades do semestre, banner oficial de pontualidade (dia 05), simulação interativa de pagamento Pix com QR Code SVG dinâmico e cópia de chave, além de código de barras de boleto bancário e recibos com autenticação.
- **Assistente Sofia:** Botão flutuante e gaveta conversacional interativa com respostas automáticas inteligentes sobre rotinas acadêmicas.
- **Acesso Documental:** Atalho direto para o Dossiê Técnico de Requisitos (`dossier_requisitos.html`).

### Restrições Técnicas:
- **Zero Tooling de Build:** O projeto é estritamente cliente estático, sem necessidade de servidores Node.js, empacotadores ou dependências externas frágeis.
- **Fidelidade Visual SaaS:** Utilização de tokens CSS semânticos em `:root`, layout flexível e responsivo, prevenção de overflow horizontal via `@supports (overflow: clip)` e tipografia com numerais tabulares em contadores e tabelas.
- **WCAG 2.1 AA:** Garantia de contraste, etiquetas semânticas em formulários, indicação de foco nítida e ausência de bloqueios em navegação por teclado.

## Brand Commitments

- **Marcas Oficiais:** SERVERSO, UNINASSAU e Grupo Ser Educacional.
- **Identidade Estética:** Design moderno estilo SaaS contemporâneo: fundo neutro claro (`#F8FAFC`), cartões brancos com bordas suaves (`#E2E8F0`), acentos em azul institucional (`#0284C7`), azul corporativo profundo (`#002B66`), verde de status (`#16A34A`) e amarelo ouro de destaque (`#FFB800`).
- **Tom de Voz:** Institucional educacional acolhedor, objetivo, com microcopy precisa e sem sobrecarga cognitiva.

## Evidence on Hand

- `index.html`: Aplicação web principal do Portal do Aluno SERVERSO.
- `dossier_requisitos.html`: Dossiê interativo da atividade de Engenharia de Requisitos.
- `RELATORIO_ENGENHARIA_REQUISITOS_UNINASSAU.md`: Relatório acadêmico formal estruturado conforme normas ABNT.
- `atividade_engenharia_de_requisitos_uninassau.pdf`: Enunciado e diretrizes normativas da universidade.
- Dados empíricos coletados via inspeção em tempo real no navegador no domínio `https://www.serverso.com.br/home`.

## Product Principles

1. **Veracidade e Rigor de Domínio:** Todas as regras de negócio, nomes de matérias, notas e fluxos de serviço devem espelhar com exatidão a realidade da UNINASSAU.
2. **Autonomia e Portabilidade:** O código deve ser 100% autossuficiente e abrir de imediato em qualquer navegador moderno sem requisições externas bloqueantes.
3. **Simplicidade e Operabilidade (Operate Mode):** A interface privilegia a rápida localização de notas, horários e serviços, sem firulas visuais que atrasem a conclusão das tarefas do aluno.
4. **Respeito à Acessibilidade e Inclusão:** Todo componente interativo deve oferecer contraste legal (WCAG 2.1 AA), navegação por teclado previsível e feedback acessível.

## Accessibility & Inclusion

- Conformidade com as diretrizes WCAG 2.1 nível AA.
- Contraste mínimo de 4.5:1 para texto padrão e 3:1 para elementos de interface/títulos.
- Rótulos semânticos explícitos em campos de busca e formulários de protocolo.
- Anéis de foco claros com `:focus-visible`.
- Skip-link no topo da página para facilitar navegação via leitores de tela.
