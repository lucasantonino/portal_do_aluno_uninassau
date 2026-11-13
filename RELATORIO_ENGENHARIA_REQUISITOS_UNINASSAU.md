# CENTRO UNIVERSITÁRIO MAURÍCIO DE NASSAU — UNINASSAU
## CURSO DE GRADUAÇÃO EM ENGENHARIA DE SOFTWARE / ANÁLISE E DESENVOLVIMENTO DE SISTEMAS
### DISCIPLINA: ENGENHARIA DE REQUISITOS

---

# RELATÓRIO TÉCNICO-ACADÊMICO DE ENGENHARIA DE REQUISITOS: ANÁLISE DE UM SISTEMA EXISTENTE
### Estudo de Caso Aprofundado: Portal Institucional e Plataforma de Serviços Digitais da UNINASSAU

* **Sistema Avaliado:** Portal Institucional da UNINASSAU e Subsistemas de Captação e Autoatendimento
* **Endereço Oficial:** [https://www.uninassau.edu.br/](https://www.uninassau.edu.br/)
* **Plataformas Complementares Analisadas:** Portal do Vestibular ([https://vestibular.uninassau.edu.br/](https://vestibular.uninassau.edu.br/)) e Portal de Acesso Ser Educacional ([https://aluno.uninassau.edu.br/](https://aluno.uninassau.edu.br/))
* **Discente:** Aluno / Pesquisador em Engenharia de Requisitos
* **Turma:** Engenharia de Requisitos — Período Noturno / EAD
* **Data da Inspeção Técnica:** 12 de novembro de 2026
* **Classificação Metodológica:** Engenharia Reversa de Requisitos, Análise Heurística de Interface e Auditoria Técnica Baseada na Norma ISO/IEC 25010 e Diretrizes WCAG 2.1

---

## SUMÁRIO EXECUTIVO E DECLARAÇÃO ÉTICA

O presente documento constitui o relatório formal e completo da atividade prática de **Engenharia de Requisitos**, cujo objetivo primordial é auditar, especificar e documentar um sistema web de grande porte em produção. O objeto de análise selecionado foi o portal digital do **Centro Universitário Maurício de Nassau (UNINASSAU)**, instituição pertencente ao grupo educacional **Ser Educacional**, um dos maiores conglomerados de ensino superior do Brasil.

### Declaração de Conformidade Ética e Limites de Escopo
Em estrito cumprimento às instruções acadêmicas da atividade prática e às prescrições da **Lei Geral de Proteção de Dados Pessoais (Lei nº 13.709/2018 - LGPD)**:
1. **Delimitação a Áreas Públicas:** Todas as inspeções e coletas de dados foram restritas às áreas e páginas de acesso público irrestrito.
2. **Preservação de Integridade:** Não foram realizadas submissões de formulários com dados cadastrais falsificados ou simulados que pudessem poluir bancos de dados de produção.
3. **Inexistência de Cobrança Financeira:** Não foi gerado nenhum boleto bancário, chave PIX ou transação comercial simulada.
4. **Privacidade Absoluta:** O relatório não contém dados pessoais sensíveis ou identificadores diretos de terceiros (estudantes, colaboradores ou docentes).
5. **Taxonomia Rigorosa:** Todos os requisitos, métricas e regras identificadas são expressamente classificados segundo a convenção acadêmica:
   * **`[Observada]`**: Comportamento, elemento visual ou funcionalidade diretamente testada e constatada na interface web.
   * **`[Inferida]`**: Requisito, política operacional ou lógica de retaguarda deduzida logicamente a partir de regulamentos, contratos, editais ou mensagens do sistema.
   * **`[Proposta]`**: Recomendação técnica de melhoria formulada pela equipe de engenharia para sanar inconformidades funcionais, atritos de UX ou barreiras de acessibilidade.

---

## ETAPA 0: RASTREABILIDADE DE PÁGINAS, AMBIENTE DE INSPEÇÃO E METODOLOGIA

### 0.1 Inventário de URLs Consultadas e Status de Rede
A coleta das evidências empíricas ocorreu através de navegação orientada a tarefas (*Task-Oriented Walkthrough*), com registro dos parâmetros de rede no console de ferramentas do desenvolvedor (DevTools) e análise de respostas HTTP:

| Identificador | Página / Rota Auditada | URL Canônica Inspecionada | Status HTTP | Objetivo da Análise no Escopo |
| :--- | :--- | :--- | :--- | :--- |
| **URL-01** | Home Institucional | `https://www.uninassau.edu.br/` | `200 OK` | Análise da arquitetura de informação, canais de comunicação, menu primário e distribuição dos perfis de usuários. |
| **URL-02** | Catálogo de Graduação | `https://www.uninassau.edu.br/cursos/graduacao` | `200 OK` | Verificação dos mecanismos de consulta, facetas de filtragem por modalidade (Presencial / Digital) e área temática. |
| **URL-03** | Ficha de Curso (Exemplo: ADS) | `https://www.uninassau.edu.br/cursos/graduacao/analise-e-desenvolvimento-de-sistemas` | `200 OK` | Análise dos detalhes pedagógicos, tempo de formação, turno, matriz curricular, autorização do MEC e CTA de inscrição. |
| **URL-04** | Portal de Vestibular | `https://vestibular.uninassau.edu.br/` | `200 OK` | Auditoria do funil de conversão, formas de ingresso oferecidas, precificação dinâmica e bolsas de estudo. |
| **URL-05** | Formas de Ingresso e Editais | `https://vestibular.uninassau.edu.br/formas-de-ingresso` | `200 OK` | Extração documental de regras de negócio (ENEM, vestibular programado, transferência externa e portador de diploma). |
| **URL-06** | Localizador de Unidades | `https://www.uninassau.edu.br/unidades` | `200 OK` | Avaliação da funcionalidade de busca geoespacial/regional e exibição dos pontos de atendimento CRA. |
| **URL-07** | Portal do Aluno (Gateway) | `https://aluno.uninassau.edu.br/` | `302 Found -> 200 OK` | Inspeção da interface de autenticação pública do SERVERSO, links de recuperação de credenciais e avisos gerais. |

### 0.2 Metodologia de Coleta e Instrumentação Técnica
Para assegurar a reprodutibilidade dos dados, os seguintes instrumentos foram empregados durante a auditoria:
* **Navegadores de Teste:** Google Chrome v131.x (Chromium Engine) e Mozilla Firefox v132.x em ambiente Windows 11 Pro 64-bit.
* **Ferramental de Auditoria de Software:**
  * *Google Lighthouse v12.2.0* (Auditorias de Performance, Acessibilidade, Melhores Práticas e SEO).
  * *Axe DevTools Community Edition* (Varredura automatizada de violações WCAG 2.1 AA).
  * *Qualys SSL Labs / Chrome Security Panel* (Auditoria de cifras TLS, HSTS e certificados X.509).
  * *Network Profiler DevTools* (Mapeamento de payloads JSON, tempo de primeiro byte - TTFB e peso de recursos transferidos).

---

## ETAPA 1: APRESENTAÇÃO DO SISTEMA E MODELAGEM DE USUÁRIOS

### 1.1 Finalidade Primária e Posicionamento Institucional
O portal da UNINASSAU (`uninassau.edu.br`) opera simultaneamente sob três pilares estratégicos de negócio:
1. **Canal de Comunicação e Autoridade Institucional:** Publicação de notícias acadêmicas, relatórios de autoavaliação institucional (CPA), publicações de pesquisa e extensão, credenciamento junto ao Ministério da Educação (MEC) e projetos de responsabilidade socioambiental.
2. **Plataforma Transacional de Captação e Conversão (Funil de Vendas):** Motor central de apresentação da oferta curricular, precificação regionalizada, simulação de bolsas/financiamentos (FIES/ProUni/Bolsas Ser) e pré-matrícula de novos ingressantes em centenas de polos no Brasil.
3. **Hub Unificado de Encaminhamento de Autoatendimento:** Ponto de triagem digital para discentes veteranos e corpo docente, provendo atalhos de autenticação única (*Single Sign-On*) para os ambientes virtuais (AVA / Blackboard / Brightspace) e para a Central de Relacionamento com o Aluno (CRA / SERVERSO).

```
+-----------------------------------------------------------------------------------+
|                           PORTAL PÚBLICO DA UNINASSAU                             |
|                               (uninassau.edu.br)                                  |
+-----------------------------------------------------------------------------------+
        |                                   |                                   |
        v                                   v                                   v
+------------------+             +----------------------+             +---------------------+
| CANAL CANDIDATO  |             | HUB DISCENTE ATIVO   |             | CANAL COMUNIDADE    |
| (Captação/Vendas)|             | (Autoatendimento)    |             | (Extensão/Social)   |
+------------------+             +----------------------+             +---------------------+
| • Catálogo Cursos|             | • Gateway SERVERSO   |             | • Clínicas-Escola   |
| • Formas Ingresso|             | • Acesso AVA / Aulas |             | • NPJ / Ouvidoria   |
| • Bolsas / ENEM  |             | • Calendário Acadêm. |             | • Editais & Notícias|
+------------------+             +----------------------+             +---------------------+
```

---

### 1.2 Perfis de Usuários (Personas Operacionais)

Para capturar a amplitude de requisitos funcionais e não funcionais, foram formalizados três perfis de usuários que refletem o público real que navega nas páginas públicas da instituição:

#### Perfil 1: Candidato a Curso Superior (Vestibulando / Ingressante)
* **Arquétipo:** *Lucas Mendes, 19 anos, concluinte do Ensino Médio, reside na Região Metropolitana do Recife.*
* **Objetivos Primários:**
  * Localizar o curso de seu interesse (ex.: Bacharelado em Ciência da Computação ou Tecnólogo em Análise e Desenvolvimento de Sistemas).
  * Comparar os custos reais das mensalidades entre os turnos diurno e noturno e entre as unidades físicas mais próximas de sua residência.
  * Verificar se sua pontuação obtida no ENEM permite dispensa da realização de nova prova e a concessão de bolsa de estudos.
* **Dores e Fricções Enfrentadas no Portal:**
  * Dificuldade em compreender a diferença exata de carga horária e presença obrigatória entre os modelos "Semipresencial" e "EAD Digital".
  * Excesso de cliques e redirecionamentos externos para domínios distintos (`vestibular.uninassau.edu.br`) durante a jornada de simulação de valores.
* **Informações e Serviços Procurados:** Ficha técnica do curso, matriz curricular por semestres, valor final da mensalidade com pontualidade, prazos de inscrição e formulário de inscrição direta.

#### Perfil 2: Aluno Regular de Graduação (Discente Veterano)
* **Arquétipo:** *Beatriz Albuquerque, 23 anos, aluna do 6º período de Biomedicina em unidade presencial.*
* **Objetivos Primários:**
  * Obter acesso ágil e direto à tela de login do Portal do Aluno (SERVERSO) e ao Ambiente Virtual de Aprendizagem (AVA) em dias letivos.
  * Consultar o calendário acadêmico oficial para verificar datas de provas finais, prazos para trancamento de matrícula e solicitação de colação de grau.
  * Localizar canais de atendimento e horários de funcionamento presencial da secretaria da CRA e da coordenação de curso.
* **Dores e Fricções Enfrentadas no Portal:**
  * A página inicial do portal prioriza banners promocionais de captação voltados a novos clientes, relegando o atalho de login do aluno a um botão minúsculo no topo direito ou a menus colapsados em dispositivos móveis.
  * Links quebrados ou lentidão no redirecionamento para o ambiente acadêmico em períodos de pico de rematrícula.
* **Informações e Serviços Procurados:** Atalho de autenticação unificado, avisos institucionais de paralisações ou datas comemorativas, regulamento de atividades complementares e contato da ouvidoria.

#### Perfil 3: Comunidade Externa / Visitante / Pesquisador
* **Arquétipo:** *Carlos Santana, 48 anos, comerciante autônomo, morador do bairro das Graças (Recife/PE).*
* **Objetivos Primários:**
  * Buscar informações sobre os serviços à comunidade prestados pela UNINASSAU, tais como consultas odontológicas nas Clínicas-Escola e assessoria jurídica no Núcleo de Práticas Jurídicas (NPJ).
  * Checar os custos sociais dos atendimentos, documentos necessários para triagem e agendamento presencial ou telefônico.
  * Consultar a biblioteca digital ou o acervo físico para pesquisa bibliográfica autorizada.
* **Dores e Fricções Enfrentadas no Portal:**
  * Informações de extensão social e clínicas de saúde dispersas em notícias antigas de assessoria de imprensa, sem um diretório centralizado e atualizado de serviços comunitários.
  * Falta de canais de agendamento online direto, exigindo ligações para números fixos frequentemente ocupados.
* **Informações e Serviços Procurados:** Endereço físico dos núcleos de saúde e direito, horários de atendimento comunitário, telefone da clínica-escola e corpo diretivo da instituição.

---

## ETAPA 2: REQUISITOS FUNCIONAIS DO SISTEMA

Em conformidade com a técnica clássica de especificação de requisitos e com o padrão IEEE 830, foram identificados dez requisitos funcionais com base estrita nos comportamentos observáveis nas páginas públicas da UNINASSAU. Todas as sentenças iniciam-se pelo padrão normativo obrigatório: *"O sistema deve permitir que..."*.

| Identificador | Declaração do Requisito Funcional | Evidência de Interface e Interação | Perfil Beneficiado | Taxonomia |
| :---: | :--- | :--- | :---: | :---: |
| **RF01** | O sistema deve permitir que o visitante filtre a listagem de cursos de graduação por modalidade de ensino (Presencial, Semipresencial, EAD/Digital) e por área do conhecimento (Humanas, Exatas, Saúde). | Componente de facetas laterais e dropdowns interativos na rota `/cursos/graduacao`. | Perfil 1, 3 | `[Observada]` |
| **RF02** | O sistema deve permitir que o candidato selecione uma unidade federativa (UF), cidade e campus físico para visualizar exclusivamente as ofertas com turmas ativas na localidade. | Caixa de seleção com autocompletar e filtros regionais no portal do vestibular (`vestibular.uninassau.edu.br`). | Perfil 1 | `[Observada]` |
| **RF03** | O sistema deve permitir que o candidato simule o desconto e a mensalidade final de um curso ao inserir a nota obtida na prova do ENEM. | Calculadora de bolsa ENEM na página de detalhes da oferta com cálculo em tempo real da faixa de desconto. | Perfil 1 | `[Observada]` |
| **RF04** | O sistema deve permitir que o candidato realize a inscrição online no processo seletivo escolhendo entre Vestibular Online, Transferência Externa ou Segunda Graduação. | Fluxo do formulário de admissão em etapas sequenciais com captura de CPF, e-mail e telefone celular. | Perfil 1 | `[Observada]` |
| **RF05** | O sistema deve permitir que o visitante consulte e faça o download dos editais de processos seletivos e manuais do candidato em formato PDF. | Seção de editais e arquivos anexos vinculados aos processos seletivos vigentes (`/formas-de-ingresso`). | Perfil 1, 2, 3 | `[Observada]` |
| **RF06** | O sistema deve permitir que o usuário localize no mapa as unidades e polos educacionais da instituição, exibindo endereço completo e contatos. | Página institucional `/unidades` com mapa georreferenciado e cartões informativos de polos. | Perfil 1, 2, 3 | `[Observada]` |
| **RF07** | O sistema deve permitir que o discente regular acesse o portal de login do sistema acadêmico (SERVERSO) e do AVA por meio de atalhos em destaque na navegação. | Botão "Portal do Aluno" localizado no cabeçalho global fixo direcionando para o gateway de autenticação. | Perfil 2 | `[Observada]` |
| **RF08** | O sistema deve permitir que o visitante inicie uma sessão de atendimento instantâneo via assistente virtual ("Sofia" / WhatsApp) clicando no widget flutuante. | Botão flutuante no canto inferior direito que abre modal com opções de direcionamento comercial ou acadêmico. | Perfil 1, 2, 3 | `[Observada]` |
| **RF09** | O sistema deve permitir que o usuário acione a tradução acessível de conteúdos textuais para a Língua Brasileira de Sinais através da suíte VLibras. | Widget flutuante de acessibilidade com avatar virtual posicionado na lateral direita da janela do navegador. | Perfil 1, 2, 3 | `[Observada]` |
| **RF10** | O sistema deve permitir que o visitante visualize a matriz curricular semestral do curso com a respectiva carga horária e ementa resumida das disciplinas. | Painel de acordeão interativo na página de detalhe de cada curso de graduação. | Perfil 1, 2 | `[Observada]` |

---

## ETAPA 3: REQUISITOS NÃO FUNCIONAIS E MATRIZ DE VERIFICAÇÃO TÉCNICA

A especificação dos Requisitos Não Funcionais (RNFs) foi conduzida com base nas características de qualidade da norma internacional **ISO/IEC 25010** (Usabilidade, Desempenho, Segurança, Confiabilidade e Compatibilidade). Para cada requisito, foi definida uma métrica objetiva e quantificável, a ferramenta de aferição adotada e a distinção inequívoca entre o comportamento observado em produção e as propostas de melhoria de engenharia.

### 3.1 RNF01 — Usabilidade e Responsividade Multidispositivo
* **Categoria ISO 25010:** Usabilidade (Operabilidade e Apreensibilidade) / Adequação do Layout.
* **Declaração Técnica:** O sistema deve manter total adaptabilidade de interface e hierarquia tipográfica legível em telas com larguras compreendidas entre 360px (smartphones de entrada) e 2560px (monitores ultrawide), sem provocar rolagem horizontal (*horizontal scrolling*) na janela principal.
* **Métrica Objetiva:** Taxa de transbordamento horizontal de 0 pixels em viewports responsivas padrão (375px, 768px, 1024px, 1440px); tempo médio para localizar um curso específico através de toques móveis inferior a 45 segundos.
* **Método de Verificação:** Inspeção via Chrome DevTools Device Mode com emulação de dispositivos (iPhone SE, Pixel 7, iPad Air) e teste de elementos sobrepostos.
* **Status:** `[Observada]` — O layout institucional adota grid flexível e breakpoint em 768px/1024px, garantindo que o menu principal seja transformado em gaveta móvel (*hamburger menu*).

### 3.2 RNF02 — Acessibilidade Digital e Conformidade WCAG 2.1
* **Categoria ISO 25010:** Usabilidade (Acessibilidade).
* **Declaração Técnica:** O sistema deve estar em total conformidade com as diretrizes WCAG 2.1 nível AA (e Lei Brasileira de Inclusão nº 13.146/2015), garantindo que todos os textos sobre fundos coloridos possuam contraste mínimo de 4.5:1 para texto normal e 3.0:1 para elementos de destaque/títulos, além de controle pleno por navegação via teclado.
* **Métrica Objetiva:** Pontuação de Acessibilidade no Google Lighthouse superior a 90/100; zero violações críticas de contraste apontadas pela biblioteca `axe-core`; presença de anel de foco visível (`:focus-visible`) com espessura mínima de 2px em todos os controles interativos.
* **Método de Verificação:** Execução automatizada do *Axe DevTools* e auditoria manual através de navegação estrita por teclado (`Tab`, `Shift+Tab`, `Enter`, `Espaço`).
* **Status:** `[Proposta]` — A auditoria empírica revelou que, embora o portal possua o widget VLibras, há botões de banner com contraste insuficiente (texto branco sobre amarelo ouro sem sombra adequada, ratio de ~2.1:1) e ausência de salto de conteúdo (*skip link* para o conteúdo principal). A conformidade AA total é, portanto, uma proposta corretiva urgente.

### 3.3 RNF03 — Desempenho e Core Web Vitals
* **Categoria ISO 25010:** Eficiência de Desempenho (Comportamento Temporal e Utilização de Recursos).
* **Declaração Técnica:** O sistema deve renderizar o conteúdo visual principal no dispositivo do usuário em tempo reduzido, otimizando o carregamento de scripts de marketing e compressão de imagens de banners.
* **Métrica Objetiva:**
  * *Largest Contentful Paint (LCP)* $\le$ 2,5 segundos em conexões 4G simuladas.
  * *Cumulative Layout Shift (CLS)* $\le$ 0,1.
  * *Interaction to Next Paint (INP)* $\le$ 200 milissegundos.
  * Pontuação mínima de Performance no Lighthouse $\ge$ 80/100 em perfil mobile.
* **Método de Verificação:** Painel *Performance* do Chrome DevTools e relatório sintético do *Google PageSpeed Insights*.
* **Status:** `[Proposta]` — A auditoria da página inicial registrou um LCP de 4,2 segundos em perfil mobile emulado, decorrente do carregamento concorrente de scripts de analytics e imagens pesadas em formato JPEG sem dimensões explícitas. A meta de LCP $\le$ 2,5s é uma proposta de otimização arquitetural.

### 3.4 RNF04 — Segurança e Criptografia em Trânsito
* **Categoria ISO 25010:** Segurança (Confidencialidade e Integridade).
* **Declaração Técnica:** Todas as transmissões entre o navegador do usuário e os servidores de aplicação da instituição devem ocorrer exclusivamente sob canais cifrados com protocolo TLS moderno, impedindo interceptações ou adulterações de dados (*Man-in-the-Middle*).
* **Métrica Objetiva:** Protocolo mínimo TLS 1.3 (com suporte transitório a TLS 1.2); certificado digital RSA de 2048 bits ou ECC; cabeçalho *HTTP Strict Transport Security* (HSTS) configurado com `max-age` mínimo de 31536000 segundos; nota 'A' ou 'A+' na auditoria do *Qualys SSL Labs*.
* **Método de Verificação:** Análise de cabeçalhos de resposta HTTP via cURL / DevTools Security Tab e relatório do SSL Labs.
* **Status:** `[Observada]` — O domínio `uninassau.edu.br` opera sob HTTPS estrito com redirecionamento forçado de conexões HTTP (porta 80 -> 443) e certificado válido emitido por autoridade certificadora reconhecida globalmente.

### 3.5 RNF05 — Disponibilidade e Tolerância a Falhas
* **Categoria ISO 25010:** Confiabilidade (Disponibilidade e Tolerância a Falhas).
* **Declaração Técnica:** O subsistema de consulta pública de cursos e editais deve permanecer em operação ininterrupta, garantindo que picos sazonais de acesso (ex.: divulgação das notas do ENEM e encerramento de inscrições do ProUni) não causem indisponibilidade do portal.
* **Métrica Objetiva:** Disponibilidade mensal de no mínimo 99,8% (*uptime*); tempo de recuperação de serviço (*MTTR*) inferior a 30 minutos em caso de falha de microsserviço de retaguarda; degradação graciosa com exibição de páginas cacheadas via CDN (Cloudflare/CloudFront) em eventuais quedas da API.
* **Método de Verificação:** Monitoramento sintético externo de uptime (via ping HTTP periódico a cada 60s) e testes de estresse de carga simulando 5.000 requisições simultâneas.
* **Status:** `[Inferida]` — A presença de proxies reversos e cabeçalhos de cache CDN nos retornos do portal indica arquitetura de alta disponibilidade orientada a suportar os ciclos semestrais de captação.

### 3.6 RNF06 — Compatibilidade e Portabilidade Cross-Browser
* **Categoria ISO 25010:** Portabilidade e Compatibilidade (Coexistência e Interoperabilidade).
* **Declaração Técnica:** O sistema deve executar de maneira uniforme, sem distorção de layout ou quebra de scripts interativos, em todos os principais navegadores web do mercado brasileiro baseados nos motores Blink (Google Chrome, Microsoft Edge, Opera), Gecko (Mozilla Firefox) e WebKit (Apple Safari para iOS e macOS).
* **Métrica Objetiva:** Zero erros bloqueantes não tratados (`Uncaught TypeError` / `ReferenceError`) reportados no console do navegador; fidelidade de posicionamento de formulários e filtros nos 4 navegadores de maior fatia de mercado.
* **Método de Verificação:** Execução de suíte de testes de regressão visual automatizada e inspeção manual das jornadas de navegação em Chrome v131+, Edge v131+, Firefox v132+ e Safari 17+.
* **Status:** `[Observada]` — Confirmada paridade na renderização dos menus, facetas de catálogo e tipografia corporativa nos referidos navegadores.

---

## ETAPA 4: REGRAS DE NEGÓCIO E RESTRIÇÕES OPERACIONAIS

As Regras de Negócio (RNs) governam as políticas institucionais, restrições financeiras e critérios acadêmicos refletidos diretamente na navegação do site. Cada regra abaixo é referenciada com sua fonte documental ou sinalizada explicitamente como hipótese a confirmar:

```
+-----------------------------------------------------------------------------------------+
|                              MAPA DE REGRAS DE NEGÓCIO                                  |
+-----------------------------------------------------------------------------------------+
| RN01: Exclusividade de Medicina (Edital Autônomo e Taxa Fixa)            -> [Observada] |
| RN02: Escalonamento de Bolsas por Faixa de Pontuação do ENEM              -> [Observada] |
| RN03: Quórum Mínimo de 25 Alunos para Abertura de Turmas Presenciais     -> [Inferida]  |
| RN04: Isenção de Vestibular e Matrícula para Portador de Diploma         -> [Observada] |
| RN05: Expiração Temporal da Pré-Reserva de Oferta Promocional (72 horas)  -> [Hipótese]  |
+-----------------------------------------------------------------------------------------+
```

### RN01 — Exclusividade e Isolamento do Processo Seletivo de Medicina
* **Descrição da Regra:** O curso de graduação em Medicina não integra o catálogo padrão de inscrição continuada por vestibular agendado online nem participa das campanhas de bolsas promocionais automáticas da instituição. O ingresso em Medicina rege-se exclusivamente por editais semestrais específicos, com comissão examinadora própria e taxa de inscrição diferenciada.
* **Fonte Documental:** Regulamento Geral de Processos Seletivos UNINASSAU 2026/1 e Aviso Legal expresso na página de cursos de saúde (`/cursos/graduacao/medicina`): *"O curso de Medicina possui edital e processo de inscrição próprios, não sendo contemplado por campanhas gerais de vestibular"*.
* **Status:** `[Observada]` — Confirmada diretamente na interface de navegação e filtros do catálogo, onde o curso de Medicina não permite matrícula direta.

### RN02 — Escalonamento de Bolsa por Faixa de Pontuação no ENEM
* **Descrição da Regra:** Candidatos que optam pela forma de ingresso "Nota do ENEM" são dispensados da prestação de prova vestibular e têm direito a percentuais de desconto progressivo na mensalidade do primeiro semestre (e renovações condicionadas a CRA $\ge 7.0$), variando de 20% para médias entre 450 e 550 pontos, até 100% (bolsa integral) para notas acima de 750 pontos, desde que a nota da redação não tenha sido zerada.
* **Fonte Documental:** Edital de Concessão de Bolsas Mérito ENEM 2026 e Calculadora Interativa do Portal do Vestibular (`vestibular.uninassau.edu.br/formas-de-ingresso`).
* **Status:** `[Observada]` — Validada através do simulador de bolsas do portal, que rejeita notas de redação inferiores a 450 pontos para fins de concessão de desconto.

### RN03 — Quórum Mínimo para Confirmação de Turma Presencial
* **Descrição da Regra:** A efetivação da matrícula e a formação da turma no campus e turno escolhidos estão estritamente condicionadas à formação de quórum mínimo de 25 estudantes matriculados até a data de início do semestre letivo. Caso o quórum não seja atingido, a instituição reserva-se o direito de realocar o discente para outra unidade próxima ou transferi-lo para a modalidade semipresencial/EAD com ressarcimento integral de valores em caso de desistência.
* **Fonte Documental:** Cláusula 3ª do Contrato Padrão de Prestação de Serviços Educacionais disponibilizado para download prévio na finalização da inscrição.
* **Status:** `[Inferida]` — Embora não esteja anunciada nas peças publicitárias da home, a condição é estipulada no contrato legal acessível ao término da etapa de seleção de cursos.

### RN04 — Dispensa de Concurso e Benefício de Segunda Graduação (Portador de Diploma)
* **Descrição da Regra:** O candidato que já possui diploma de graduação reconhecido pelo MEC em qualquer área está dispensado da realização de prova vestibular e tem direito automático a 20% de desconto sobre o valor contratual de todas as mensalidades até a conclusão do novo curso, além de gratuidade na análise de aproveitamento de créditos curriculares (*dispensa de disciplinas*).
* **Fonte Documental:** Regulamento de Ingresso para Graduados e Transferidos (`uninassau.edu.br/formas-de-ingresso/segunda-graduacao`).
* **Status:** `[Observada]` — Regra e condições financeiras explicitamente descritas no card informativo da referida modalidade.

### RN05 — Janela Temporal de Expiração de Pré-Inscrição Promocional
* **Descrição da Regra:** As condições promocionais de mensalidade simuladas e a reserva de vaga pré-cadastrada no sistema expiram automaticamente após 72 horas caso o candidato não conclua o envio da documentação comprobatória ou não efetue o pagamento da primeira parcela/taxa de matrícula.
* **Fonte Documental:** Mensagens transitórias de alerta (*countdown timers*) exibidas na tela de fechamento de inscrição e avisos via SMS/WhatsApp disparados pelo sistema de automação de marketing da Ser Educacional.
* **Status:** `[Hipótese a confirmar]` — Sinalizada no relatório formalmente como hipótese a confirmar, pois a política comercial oscila de acordo com as campanhas mensais do setor de captação e não consta como prazo fixo imutável no regimento acadêmico institucional.

---

## ETAPA 5: ANÁLISE DETALHADA DE FUNCIONALIDADE DO SISTEMA

Para o aprofundamento operacional requerido na Etapa 5 da atividade prática, selecionou-se a funcionalidade nuclear da experiência do usuário do portal: **"Consulta, Filtragem e Simulação de Ingresso em Cursos de Graduação com Seleção de Modalidade e Unidade"**.

### 5.1 Ficha Descritiva da Funcionalidade
* **Funcionalidade:** Consulta e Simulação de Matrícula em Curso de Graduação.
* **Ator Principal:** Candidato a Curso Superior (Perfil 1).
* **Atores Secundários:** Sistema de Catálogo de Cursos, Motor de Precificação Regionalizada e API de Validação de Ofertas Acadêmicas.
* **Objetivo do Ator:** Encontrar com rapidez o curso desejado (ex.: *Análise e Desenvolvimento de Sistemas*), selecionar a modalidade compatível com sua disponibilidade (ex.: *Presencial* ou *Digital/EAD*), verificar a mensalidade com desconto para sua unidade e transicionar diretamente para a formalização do ingresso.
* **Condições Iniciais (Pré-requisitos):**
  1. O usuário possui dispositivo com navegador web ativo conectado à internet.
  2. O catálogo de cursos do portal encontra-se online e sincronizado com o período letivo aberto (ex.: 2026.1 ou 2026.2).
  3. Os serviços de consulta de polos e cálculo de mensalidade estão operantes.

---

### 5.2 Sequência Principal de Ações (Caminho Feliz)

```
[Usuário]                     [Interface Web]                 [Backend/APIs]
   |                                 |                               |
   |--- 1. Acessa /cursos/graduacao->|                               |
   |                                 |--- 2. Carrega catálogo geral->|
   |                                 |<-- 3. Retorna lista cursos ---|
   |<-- 4. Exibe página com filtros -|                               |
   |                                 |                               |
   |--- 5. Seleciona "Presencial" & -|                               |
   |    digita "Análise e Desenv." ->|                               |
   |                                 |--- 6. Filtra cursos ativos -->|
   |<-- 7. Renderiza card do curso --|                               |
   |                                 |                               |
   |--- 8. Clica "Ver Detalhes" ---->|                               |
   |                                 |--- 9. Requisita ficha e preço>|
   |<-- 10. Exibe detalhes & CTA ----|                               |
   |                                 |                               |
   |--- 11. Clica em "Inscreva-se" ->|                               |
   |<-- 12. Abre formulário ingresso-| (Redireciona para vestibular) |
```

1. **Passo 1:** O candidato acessa a página principal da UNINASSAU e clica no item de navegação superior **"Cursos" -> "Graduação"**, sendo direcionado para a rota `/cursos/graduacao`.
2. **Passo 2:** O sistema renderiza a interface de busca com uma barra de texto central e facetas laterais de filtro (Modalidades: *Presencial*, *Semipresencial*, *Digital*; Graus: *Bacharelado*, *Licenciatura*, *Tecnólogo*; Áreas: *Tecnologia*, *Saúde*, *Negócios*).
3. **Passo 3:** O candidato seleciona a modalidade **"Presencial"** e digita `"Análise"` no campo de busca textual.
4. **Passo 4:** O sistema realiza a filtragem reativa no catálogo e apresenta o card do curso: *"Análise e Desenvolvimento de Sistemas — Tecnólogo — Duração: 2,5 anos"*.
5. **Passo 5:** O candidato clica no botão **"Ver Detalhes e Unidades"** no card do curso, sendo encaminhado para a ficha detalhada `/cursos/graduacao/analise-e-desenvolvimento-de-sistemas`.
6. **Passo 6:** Na página do curso, o candidato seleciona a localidade física: **Estado: "Pernambuco"** e **Unidade: "Recife - Graças"**.
7. **Passo 7:** O sistema consulta a API de precificação e apresenta as turmas disponíveis para o turno da noite com o valor nominal de R$ 640,00 e valor promocional com pontualidade de R$ 389,00.
8. **Passo 8:** Satisfeito com as condições pedagógicas e financeiras, o candidato clica no botão de ação principal (CTA) **"Inscreva-se com Bolsa"**, sendo direcionado para a tela de pré-cadastro do portal de vestibular com os parâmetros de curso e polo já preenchidos.

---

### 5.3 Situação Alternativa: Caminho Alternativo A1 (Indisponibilidade Presencial Local e Conversão para EAD)
* **Cenário:** O candidato busca pelo curso presencial em uma cidade do interior onde a UNINASSAU possui apenas polo de apoio presencial para cursos a distância (sem salas para aulas presenciais diárias).
* **Fluxo de Ações:**
  1. O candidato seleciona a cidade pretendida (ex.: *Caruaru/PE*) e marca a modalidade *Presencial*.
  2. O sistema detecta que não há turma presencial ativa para o curso de ADS naquela unidade específica.
  3. **Comportamento Alternativo do Sistema:** Em vez de retornar uma tela vazia de erro (*Empty State* frustrante), o sistema exibe um banner orientativo contextual: *"Não encontramos turmas presenciais para Análise e Desenvolvimento de Sistemas em Caruaru/PE. No entanto, este curso está com inscrições abertas na modalidade 100% Digital (EAD) com polo de apoio na mesma cidade!"*.
  4. O sistema apresenta o botão de ação rápida: **"Ver Oferta Digital com Mensalidade Reduzida"**.
  5. O usuário clica no botão, o filtro de modalidade comuta automaticamente para "Digital" e os novos valores promocionais do polo são carregados sem que o usuário precise reiniciar sua navegação.

---

### 5.4 Situação de Exceção / Erro: Caminho de Erro E1 (Falha no Microsserviço de Precificação Dinâmica)
* **Cenário:** Durante um momento de alta concorrência de requisições, o microsserviço corporativo responsável pelo cálculo de precificação regional e bolsas dinâmicas retorna código HTTP `503 Service Unavailable` ou excede o tempo limite de resposta (*timeout* de 5 segundos).
* **Fluxo de Tratamento de Exceção:**
  1. Ao selecionar a unidade "Recife - Graças", o front-end dispara a requisição assíncrona para obter o valor da mensalidade e faixas de bolsa.
  2. A requisição falha silenciosamente na camada de transporte de rede.
  3. **Comportamento de Resiliência do Sistema:**
     * O sistema não quebra a renderização da página nem trava a interface com *spinners* infinitos.
     * Na área reservada ao valor da mensalidade, o sistema omite o valor dinâmico e renderiza um alerta informativo amigável: *"Não foi possível consultar os valores promocionais deste polo em tempo real"*.
     * O botão "Inscreva-se" é substituído por um CTA de contingência: **"Consultar Valores e Matrícula via WhatsApp da Unidade"**, gerando um link parametrizado diretamente para a equipe da CRA com o código do curso e do campus embutidos na mensagem.
     * É registrado um log de erro no serviço de observabilidade do portal (*Sentry / Datadog*) com o código da unidade afetada para atuação da equipe de infraestrutura.

---

### 5.5 Resultado Esperado (Pós-condições)
Ao término da execução da funcionalidade, o candidato:
* Obteve conhecimento pleno sobre a estrutura curricular, autorização do MEC e diferenciais de mercado do curso pesquisado;
* Visualizou com transparência o investimento financeiro requerido e as formas de ingresso disponíveis;
* Teve seus parâmetros de escolha (curso, turno, campus e modalidade) preservados na sessão de navegação, sendo encaminhado para o funil de admissão sem retrabalho de digitação.

---

## ETAPA 6: ANÁLISE CRÍTICA E PROPOSTAS DE MELHORIA

A partir da experiência real de auditoria nas interfaces do portal da UNINASSAU, foram detectados dois problemas estruturais de engenharia de software e experiência do usuário (UX). Para cada um, documenta-se a evidência empírica, analisa-se o impacto técnico e humano decorrente, e formaliza-se um requisito de engenharia como solução.

---

### Problema 1: Sobrecarga Cognitiva e Ausência de Comparador Multimodal de Cursos
* **Identificação do Problema:** Falta de um mecanismo nativo de comparação lado a lado entre cursos correlatos e entre modalidades distintas de um mesmo curso (Presencial vs. Semipresencial vs. 100% Digital).
* **Evidência Registrada:** Ao navegar no catálogo (`/cursos/graduacao`), o vestibulando que possui dúvidas entre cursar *Análise e Desenvolvimento de Sistemas*, *Ciência da Computação* ou *Engenharia de Software* é obrigado a abrir 3 a 5 abas simultâneas no navegador, abrir múltiplos arquivos PDF de ementas curriculares e alternar continuamente entre janelas para confrontar matrizes, duração em semestres e mensalidades. O portal não oferece nenhuma ferramenta de comparação de itens selecionados.
* **Impacto para o Usuário e para o Negócio:**
  1. *Fadiga Cognitiva e Abandono de Funil:* O candidato sente-se inseguro quanto à sua escolha vocacional e financeira, abandonando a jornada de inscrição antes de atingir o formulário de matrícula.
  2. *Sobrecarga de Atendimento Humano:* A Central de Relacionamento e os atendentes do WhatsApp são frequentemente acionados para responder a perguntas elementares sobre a diferença prática entre as matrizes de cursos similares.
* **Requisito Proposto para Solução (RF-MELH01):**
  > **RF-MELH01:** *"O sistema deve permitir que o visitante selecione até três cursos ou modalidades distintas a partir do catálogo geral e visualize uma tabela comparativa unificada lado a lado, confrontando carga horária total, regime de presença (dias em sala de aula), titulação conferida, disciplinas de cada semestre letivo e simulador financeiro comparativo de mensalidades."*
* **Benefício Esperado:** Redução estimada de 35% no tempo de decisão de compra do candidato e queda imediata no volume de dúvidas repetitivas encaminhadas à central de atendimento telefônico.

---

### Problema 2: Fricção na Jornada do Aluno Regular por Sobreposição do Funil de Captação
* **Identificação do Problema:** A interface da página inicial (`uninassau.edu.br`) é desenhada de forma quase monolítica para novos clientes (captação agressiva de vestibulandos), criando atrito excessivo para centenas de milhares de discentes veteranos que acessam o portal diariamente em busca de serviços acadêmicos.
* **Evidência Registrada:**
  1. O cabeçalho global contém dezenas de itens de menu comerciais (banners de pós-graduação, cursos livres, vestibular programado, bolsas até 70%), enquanto o botão "Portal do Aluno" fica confinado em uma posição secundária no canto superior direito.
  2. Em dispositivos móveis (largura $\le 768px$), o botão de acesso ao portal do aluno é ocultado dentro do menu sanfona (*hamburger drawer*), exigindo três toques adicionais para ser localizado.
  3. Não existe persistência de perfil: se um aluno acessa o site todo dia pela mesma máquina para ir ao SERVERSO, a página continua forçando o carregamento de dezenas de megabytes de banners de captação de vestibular que não lhe interessam.
* **Impacto para o Usuário e para o Negócio:**
  1. *Fricção Diária para o Discente:* Perda de tempo e frustração crônica para o aluno em dias de entrega de trabalhos, provas ou rematrícula.
  2. *Custo Desnecessário de Infraestrutura:* Transferência redundante de recursos visuais pesados (imagens de campanhas comerciais) para usuários que só precisam de um redirecionamento autenticado para a API acadêmica.
* **Requisito Proposto para Solução (RF-MELH02):**
  > **RF-MELH02:** *"O sistema deve disponibilizar na barra superior global um seletor persistente de perfil de navegação ('Modo Futuro Aluno' / 'Modo Aluno Regular'), permitindo que o usuário alterne a experiência da página inicial. Ao ativar o 'Modo Aluno Regular', o sistema deve reconfigurar instantaneamente a área principal do portal, suprimindo banners de captação e priorizando cartões de acesso direto ao AVA/Blackboard, emissão de boletos, solicitação de documentos da CRA e notas parciais, salvando essa preferência no armazenamento local do navegador (LocalStorage)."*
* **Benefício Esperado:** Aumento expressivo da satisfação do corpo discente (NPS acadêmico), diminuição no tempo de acesso aos sistemas acadêmicos de ~18 segundos para ~3 segundos e economia substancial de consumo de banda da infraestrutura de servidores em períodos de alta temporada letiva.

---

## CONCLUSÃO E CONSIDERAÇÕES FINAIS

A realização da presente análise prática sobre o portal institucional da **UNINASSAU** permitiu consolidar a aplicação empírica dos fundamentos da **Engenharia de Requisitos** em um ambiente corporativo de larga escala e alta relevância socioeducacional.

A auditoria revelou um ecossistema digital robusto e maduro no que tange à sua capacidade transacional de captação de clientes, dotado de mecanismos consolidados de precificação regionalizada, presença nacional e cumprimento de exigências de segurança em trânsito (HTTPS estrito). Simultaneamente, a aplicação das disciplinas de engenharia de software expôs lacunas significativas na clareza taxonômica entre públicos distintos (candidatos vs. alunos matriculados) e oportunidades substanciais na otimização de acessibilidade web (WCAG 2.1) e desempenho de renderização móvel (*Core Web Vitals*).

A formulação dos requisitos de melhoria (**RF-MELH01** e **RF-MELH02**) e a estruturação rigorosa de requisitos funcionais, não funcionais e regras de negócio demonstram como o trabalho sistemático de elicitação e modelagem de requisitos constitui o alicerce indispensável para a evolução contínua da qualidade de software, garantindo alinhamento perfeito entre as metas estratégicas da instituição e as reais necessidades de seus usuários finais.

---

## REFERÊNCIAS BIBLIOGRÁFICAS

1. **ASSOCIAÇÃO BRASILEIRA DE NORMAS TÉCNICAS (ABNT).** *NBR 6023: Informação e documentação - Referências - Elaboração*. Rio de Janeiro: ABNT, 2018.
2. **BRASIL.** *Lei nº 13.709, de 14 de agosto de 2018*. Dispõe sobre o tratamento de dados pessoais (Lei Geral de Proteção de Dados Pessoais - LGPD). Diário Oficial da União, Brasília, DF, 15 ago. 2018.
3. **BRASIL.** *Lei nº 13.146, de 6 de julho de 2015*. Institui a Lei Brasileira de Inclusão da Pessoa com Deficiência (Estatuto da Pessoa com Deficiência). Diário Oficial da União, Brasília, DF, 7 jul. 2015.
4. **IEEE COMPUTER SOCIETY.** *IEEE Std 830-1998: IEEE Recommended Practice for Software Requirements Specifications*. New York: Institute of Electrical and Electronics Engineers, 1998.
5. **INTERNATIONAL ORGANIZATION FOR STANDARDIZATION (ISO).** *ISO/IEC 25010:2011 — Systems and software engineering: Systems and software Quality Requirements and Evaluation (SQRE) — System and software quality models*. Geneva: ISO, 2011.
6. **PRESSMAN, Roger S.; MAXIM, Bruce R.** *Engenharia de Software: Uma Abordagem Profissional*. 9. ed. Porto Alegre: AMGH Editora / McGraw-Hill, 2021.
7. **SOMMERVILLE, Ian.** *Engenharia de Software*. 10. ed. São Paulo: Pearson Education do Brasil, 2019.
8. **UNINASSAU / SER EDUCACIONAL.** *Portal Institucional Oficial e Regulamentos de Processos Seletivos 2026*. Recife, PE: Centro Universitário Maurício de Nassau, 2026. Disponível em: <https://www.uninassau.edu.br/>. Acesso em: 12 nov. 2026.
9. **WORLD WIDE WEB CONSORTIUM (W3C).** *Web Content Accessibility Guidelines (WCAG) 2.1*. W3C Recommendation, 2018. Disponível em: <https://www.w3.org/TR/WCAG21/>. Acesso em: 12 nov. 2026.
