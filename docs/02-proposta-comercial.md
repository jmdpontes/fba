# Proposta Comercial
## Desenvolvimento da Plataforma Tecnológica do Observatório FBA do Esporte Social e da Mobilidade

| Campo | Informação |
|---|---|
| Destinatário | Federal Brasil Automobilidade Global – FBA Global (CNPJ 57.850.031/0001-59) |
| Proponente | NatGED |
| Referência | Termo de Referência para Cotação — Plataforma Tecnológica do Observatório FBA (Goiânia/GO, 2026) |
| Documento técnico anexo | [Requisitos Refinados v0.1](01-requisitos-refinados.md) |
| Data | 25/09/2026 |
| Validade da proposta | 60 dias |
| Versão | 0.1 — rascunho para revisão interna |

---

## 1. Apresentação

A NatGED apresenta sua proposta para levantamento de requisitos, UX/UI, desenvolvimento, testes, implantação, documentação, treinamento, hospedagem, backup, suporte e manutenção da Plataforma Tecnológica do Observatório FBA. A proposta cobre integralmente o escopo do Termo de Referência (TR), conforme TR §18.

A modalidade proposta é **desenvolvimento sob encomenda**, com entrega à FBA Global do código-fonte, banco de dados, documentação, credenciais e direitos patrimoniais sobre o código desenvolvido. Isso atende à preferência expressa no TR §9 e garante a operação independente da plataforma.

A solução usa exclusivamente **tecnologias open source consolidadas**. Não há licença de software com custo recorrente. Os únicos custos recorrentes são a infraestrutura em nuvem e os serviços de operação, discriminados nas seções 5 e 6.

## 2. Solução proposta (resumo)

| Item | Solução |
|---|---|
| Portal público | Institucional, organizações, projetos, eventos, mapa, calendário, indicadores, publicações, notícias e contato, com CMS para a equipe FBA publicar sem programador |
| Área restrita | Autocadastro e perfil da organização, projetos, eventos, atividades, capacitações, perfil de mobilidade, evidências, formulários e relatórios dos próprios dados |
| Painel administrativo | Fila de validação (enviar → analisar → aprovar → publicar), gestão de cadastros, construtor de formulários, indicadores, relatórios, usuários, grupos, parâmetros e auditoria |
| Indicadores | Catálogo de até 30 indicadores pré-definidos, com filtros dinâmicos, dashboard público e interno, calculados sobre registros validados |
| Segurança e LGPD | HTTPS, senhas com Argon2, 2FA obrigatório para a equipe FBA, controle por perfil e por objeto, trilha de auditoria imutável, canal do titular, dados de beneficiários apenas agregados |
| Acessibilidade | WCAG 2.1 AA no portal e na área restrita, testes com leitores de tela, VLibras |
| API | REST documentada (OpenAPI 3), com autenticação por token e endpoints públicos de dados abertos |

O detalhamento completo, com requisitos numerados e critérios de aceite, está no documento [Requisitos Refinados](01-requisitos-refinados.md), que integra esta proposta.

## 3. Arquitetura e tecnologias

| Camada | Tecnologia | Licença |
|---|---|---|
| Backend | Python 3.12, Django 5 | BSD — sem custo |
| CMS | Wagtail | BSD — sem custo |
| API | Django REST Framework + OpenAPI 3 | BSD — sem custo |
| Banco de dados | PostgreSQL 16 + PostGIS (relacional, com extensão geoespacial) | PostgreSQL/GPL — sem custo |
| Frontend | HTML semântico + HTMX + Alpine.js + Tailwind CSS | MIT/BSD — sem custo |
| Mapa | MapLibre/Leaflet + OpenStreetMap; geocodificação Nominatim | BSD/ODbL — sem custo |
| Calendário e gráficos | FullCalendar, Apache ECharts | MIT/Apache — sem custo |
| Formulários | SurveyJS Form Library (ou Form.io) + construtor próprio | MIT — sem custo |
| Relatórios PDF | WeasyPrint | BSD — sem custo |
| Tarefas assíncronas | Celery + Redis | BSD — sem custo |
| Infraestrutura | Containers Docker em nuvem pública, **região São Paulo** (AWS ou equivalente), com infraestrutura como código (Terraform) | Serviço de nuvem — custo recorrente (item 18) |

Justificativa do banco relacional (TR §8): os dados do Observatório são fortemente relacionados (organizações → projetos → atividades → evidências), exigem integridade referencial, trilha de auditoria e consultas analíticas. O PostGIS dá consultas geoespaciais nativas para o mapa e os indicadores territoriais.

## 4. Equipe e forma de execução

| Papel | Dedicação estimada |
|---|---|
| Gerente de projeto | 245 h |
| Tech lead / arquiteto | 420 h |
| Desenvolvedores full-stack (2) | 1.270 h |
| Designer UX/UI | 300 h |
| Analista de testes (QA) e acessibilidade | 290 h |
| DevOps / infraestrutura | 170 h |
| **Total** | **2.695 h** |

- **Método:** entregas incrementais em sprints de 2 semanas, com ambiente de homologação atualizado e demonstrações quinzenais à FBA.
- **Valor-hora:** único (*blended*) de **R$ 160,00** para todos os perfis.
- **Produtividade:** as estimativas consideram o uso de recursos nativos do Django e do Wagtail (painel administrativo, CMS, permissões, versionamento e auditoria) e de bibliotecas prontas para formulários, mapas e gráficos. Isso reduz o esforço de desenvolvimento sem reduzir o escopo.
- **Execução:** todo o desenvolvimento é feito por equipe própria da NatGED. Os únicos serviços contratados de terceiros são os de nuvem e e-mail, listados na seção 7.

---

## 5. Proposta de preços — estrutura do TR §15

### 5.1 Desenvolvimento e implantação (valores não recorrentes)

As horas de cada componente já incluem a parcela proporcional de gestão do projeto.

| Nº | Componente | Horas | Valor (R$) |
|---:|---|---:|---:|
| 1 | Levantamento e arquitetura da informação | 132 | 21.120,00 |
| 2 | UX/UI e protótipo | 220 | 35.200,00 |
| 3 | Desenvolvimento do portal público | 198 | 31.680,00 |
| 4 | Área restrita das organizações ¹ | 231 | 36.960,00 |
| 5 | Painel administrativo ² | 231 | 36.960,00 |
| 6 | Banco de dados | 88 | 14.080,00 |
| 7 | Módulo de projetos e eventos ³ | 198 | 31.680,00 |
| 8 | Calendário | 66 | 10.560,00 |
| 9 | Mapa e georreferenciamento | 110 | 17.600,00 |
| 10 | Indicadores e dashboards | 198 | 31.680,00 |
| 11 | Relatórios e exportações (inclui API) | 154 | 24.640,00 |
| 12 | Formulários e pesquisas | 220 | 35.200,00 |
| 13 | LGPD, segurança e logs | 154 | 24.640,00 |
| 14 | Acessibilidade digital | 110 | 17.600,00 |
| 15 | Testes e homologação | 198 | 31.680,00 |
| 16 | Documentação e treinamento | 121 | 19.360,00 |
| 17 | Implantação ⁴ | 66 | 16.560,00 |
| | **Subtotal — desenvolvimento e implantação** | **2.695** | **437.200,00** |

¹ Inclui cadastro de organizações e gestão de evidências (itens do TR sem linha própria na tabela).
² Inclui workflow de validação, notificações por e-mail, gestão de usuários e parâmetros.
³ Inclui atividades, capacitações e perfil de mobilidade.
⁴ 66 h (R$ 10.560,00) + R$ 6.000,00 de infraestrutura de homologação durante o desenvolvimento (6 meses).

### 5.2 Operação por 24 meses (valores recorrentes)

| Nº | Componente | Valor mensal (R$) | Meses | Valor total (R$) |
|---:|---|---:|---:|---:|
| 18 | Hospedagem cloud — 24 meses | 1.300,00 | 24 | 31.200,00 |
| 19 | Backup e segurança — 24 meses | 640,00 | 24 | 15.360,00 |
| 20 | Suporte e manutenção — 24 meses | 2.400,00 | 24 | 57.600,00 |
| | **Subtotal — operação** | **4.340,00** | | **104.160,00** |

### 5.3 Total

| Grupo | Valor (R$) |
|---|---:|
| Desenvolvimento e implantação (itens 1–17) | 437.200,00 |
| Operação por 24 meses (itens 18–20) | 104.160,00 |
| **TOTAL** | **541.360,00** |

**Valor total: R$ 541.360,00** (quinhentos e quarenta e um mil, trezentos e sessenta reais).

### 5.4 Composição dos itens recorrentes

**Item 18 — Hospedagem cloud (R$ 1.300,00/mês)**

- Ambiente de produção: 2 containers de aplicação, 1 worker, PostgreSQL gerenciado, Redis, storage de objetos (≥ 10 GB, elástico), balanceador HTTPS e CDN/WAF.
- Ambiente de homologação reduzido.
- E-mail transacional (até 10 mil envios por mês).
- Custo de nuvem repassado mais a administração da infraestrutura.
- Contas abertas em nome da FBA Global.

**Item 19 — Backup e segurança (R$ 640,00/mês)**

- Backup diário do banco e dos arquivos, com retenção de 30 dias diários e 12 mensais, em conta/região separada e criptografado.
- Monitoramento 24×7 de disponibilidade e erros.
- Aplicação mensal de atualizações de segurança (críticas em até 72 h) e varredura de vulnerabilidades.
- Teste semestral de restauração.
- Relatório mensal.
- Inclui 3 h/mês de atividades técnicas.

**Item 20 — Suporte e manutenção (R$ 2.400,00/mês)**

- Franquia de **15 h/mês** para atendimento a usuários e à equipe FBA, manutenção corretiva fora da garantia, pequenos ajustes, apoio operacional e atualização de versões de frameworks.
- Horas não utilizadas acumulam dentro do trimestre.
- Horas excedentes: R$ 160,00/h, mediante aprovação prévia.
- SLA conforme a seção 9.

---

## 6. Serviços opcionais (fora do total)

Estes serviços não fazem parte do total e podem ser contratados a qualquer momento (TR §15).

| ID | Serviço opcional | Horas | Valor (R$) | Recorrente |
|---|---|---:|---:|---|
| O-01 | Construtor de indicadores: criação de novos indicadores pelo administrador, com fórmulas sobre campos e respostas | 160 | 25.600,00 | — |
| O-02 | BI avançado: Metabase embarcado para análises livres da equipe FBA | 80 | 12.800,00 | + R$ 300,00/mês de infraestrutura |
| O-03 | Pentest independente: teste de intrusão por empresa terceira especializada, antes da produção, com correções | 16 | 22.560,00 ⁵ | — |
| O-04 | Notificações por WhatsApp (WhatsApp Business API) | 80 | 12.800,00 | + tarifas da Meta por conversa |
| O-05 | Migração de dados legados: levantamento, limpeza e carga | sob demanda | R$ 160,00/h (estimativa após análise da base) | — |
| O-06 | Login com conta Gov.br | 60 | 9.600,00 | — |
| O-07 | PWA com preenchimento offline de formulários e sincronização | 160 | 25.600,00 | — |
| O-08 | Treinamento adicional: turma de 3 h, remota e gravada, incluindo preparação | 6 | 960,00 por turma | — |
| O-09 | Banco de horas para manutenção evolutiva | sob demanda | R$ 160,00/h | — |

⁵ R$ 20.000,00 do serviço terceirizado + 16 h de coordenação e correções (R$ 2.560,00).

---

## 7. Serviços de terceiros, licenças e natureza do fornecimento (TR §18)

| Serviço | Natureza | Fornecedor | Valor | Periodicidade | Incluído em |
|---|---|---|---|---|---|
| Desenvolvimento, testes, documentação e treinamento | Próprio | NatGED | Conforme itens 1–17 | Único | Itens 1–17 |
| Suporte, manutenção e operação | Próprio | NatGED | Conforme itens 19–20 | Mensal | Itens 19–20 |
| Computação, banco, storage, balanceador | Contratado em nuvem | AWS (região São Paulo) ou equivalente | Até R$ 1.100,00/mês | Mensal | Item 18 |
| CDN / WAF | Contratado em nuvem | Cloudflare | R$ 0 a R$ 120,00/mês | Mensal | Item 18 |
| E-mail transacional | Contratado em nuvem | Amazon SES ou Brevo | Até R$ 80,00/mês | Mensal | Item 18 |
| Monitoramento de erros | Contratado em nuvem | Sentry | R$ 0 (plano gratuito) | Mensal | Item 19 |
| Mapas (tiles) e geocodificação | Terceiro gratuito | OpenStreetMap / Nominatim | **R$ 0** | — | — |
| Certificado SSL | Terceiro gratuito | Let's Encrypt / AWS ACM | R$ 0 | — | — |
| Tradução em Libras | Terceiro gratuito | VLibras (Gov.br) | R$ 0 | — | — |
| Licenças de software | — | — | **R$ 0** (stack 100% open source) | — | — |
| Domínio | Responsabilidade da FBA | Registro.br | ~R$ 40,00 | Anual | Não incluído |

**Custo recorrente de API de mapas (TR §6.5): zero.**

---

## 8. Cronograma

O prazo é de **24 semanas** até o aceite definitivo, seguido de **24 meses de operação assistida**.

O cronograma de referência do TR previa 22 semanas. Ajustamos para 24 porque a fase 4 do TR concentrava cinco módulos (mapa, calendário, dashboards, relatórios e pesquisas) em apenas 2 semanas. Nesta proposta, esses módulos avançam em paralelo ao desenvolvimento base.

| Fase | Semanas | Produto | Marco |
|---|---|---|---|
| 1. Descoberta e requisitos | 1–4 | Requisitos, arquitetura da informação, catálogo de indicadores | Aceite dos requisitos |
| 2. UX/UI e protótipo | 4–8 | Protótipo navegável e design system acessível | Homologação do protótipo |
| 3. Desenvolvimento base | 7–15 | Banco, autenticação, área restrita, painel, projetos, eventos, workflow | Entrega da versão base |
| 4. Portal e módulos analíticos | 11–20 | Portal/CMS, mapa, calendário, formulários, evidências, dashboards, relatórios | Entrega funcional completa |
| 5. Testes e homologação | 20–22 | Testes funcionais, de segurança, de acessibilidade e de carga | Versão homologável aceita |
| 6. Implantação e treinamento | 23–24 | Produção, documentação, treinamentos, entrega de código e credenciais | **Aceite definitivo** |
| 7. Operação assistida | Mês 7 ao mês 30 | Hospedagem, backup, monitoramento, suporte e manutenção | Relatórios mensais |

O cronograma depende do cumprimento dos prazos da FBA Global (seção 12). Atrasos nessas dependências deslocam o cronograma na mesma proporção.

---

## 9. Garantia e SLA

### 9.1 Garantia

- **24 meses** contados do aceite definitivo, para correção sem custo de defeitos e não conformidades em relação aos requisitos aceitos (TR §13).
- Não estão cobertos pela garantia:
  - novas funcionalidades e mudanças de regra de negócio;
  - falhas causadas por alterações de terceiros no código ou na infraestrutura;
  - custos de infraestrutura após o período contratado no item 18.

### 9.2 SLA de suporte

| Severidade | Exemplo | Primeiro atendimento | Solução ou contorno |
|---|---|---|---|
| Crítica | Plataforma fora do ar, incidente de segurança | 2 h úteis | 8 h úteis |
| Alta | Funcionalidade principal indisponível, sem contorno | 4 h úteis | 2 dias úteis |
| Média | Falha com contorno disponível | 1 dia útil | 5 dias úteis |
| Baixa | Dúvida, ajuste visual | 2 dias úteis | Próxima versão |

- **Atendimento:** dias úteis, das 8h às 18h (horário de Brasília), por e-mail e sistema de chamados.
- **Monitoramento automatizado:** 24×7, com alerta para incidentes críticos.
- **Disponibilidade alvo:** 99,5% ao mês.

---

## 10. Condições de pagamento

### 10.1 Desenvolvimento e implantação (R$ 437.200,00), por marcos

| Marco | % | Valor (R$) |
|---|---:|---:|
| Assinatura do contrato | 10% | 43.720,00 |
| Aceite dos requisitos e homologação do protótipo (semana 8) | 15% | 65.580,00 |
| Entrega da versão base (semana 15) | 20% | 87.440,00 |
| Entrega funcional completa (semana 20) | 20% | 87.440,00 |
| Versão homologável aceita (semana 22) | 20% | 87.440,00 |
| Aceite definitivo (semana 24) | 15% | 65.580,00 |
| **Total** | **100%** | **437.200,00** |

### 10.2 Operação (itens 18 a 20)

Mensalidade de **R$ 4.340,00**, com faturamento mensal a partir do mês seguinte à implantação em produção.

### 10.3 Condições gerais

- Pagamento em até 15 dias após a emissão da nota fiscal.
- Reajuste anual dos valores recorrentes pelo IPCA.
- O item 18 poderá ser revisto se a variação cambial acumulada ultrapassar 10%, mediante comprovação, porque os custos de nuvem são cotados em dólar.
- Valores em reais, com todos os tributos incidentes incluídos.

---

## 11. Premissas comerciais

As premissas técnicas completas (P-01 a P-19) estão no documento de Requisitos Refinados. As que mais afetam o preço são:

1. **Beneficiários apenas em números agregados:** quantidades por faixa etária, gênero e PCD, sem cadastro nominal de beneficiários.
2. **Indicadores:** catálogo pré-definido de até 30 indicadores, configurável pelo administrador. A criação de novos indicadores é o opcional O-01.
3. **Testes de segurança:** varredura automatizada mais checklist OWASP ASVS nível 1. O pentest independente é o opcional O-03.
4. **Homologação do protótipo:** até 2 ciclos de ajuste.
5. **Conteúdo:** textos, imagens, publicações e textos jurídicos finais são fornecidos pela FBA. A NatGED entrega minutas técnicas da política de privacidade e dos termos de uso.
6. **Carga de dados:** somente por planilha-modelo de organizações. Migração de bases legadas é o opcional O-05.
7. **Treinamentos:** 2 turmas de 3 h, remotas e gravadas.
8. **Contas:** contas de nuvem, domínio e repositório de código em nome da FBA Global.
9. **Prazo da operação:** 24 meses de operação contados da implantação em produção. Se a FBA entender que os 24 meses se contam desde a assinatura do contrato (TR §17), os itens 18 a 20 passam a 18 meses, totalizando **R$ 78.120,00**.

## 12. Dependências da FBA Global

- Designar ponto focal e encarregado de dados (DPO) na semana 1.
- Fornecer manual de marca até a semana 2.
- Validar requisitos e catálogo de indicadores até a semana 4.
- Homologar entregas em até 5 dias úteis (protótipo) e 10 dias úteis (versões).
- Fornecer conteúdo do portal e textos jurídicos até a semana 16.
- Providenciar domínio e contas de nuvem até a semana 12.
- Mobilizar os participantes dos treinamentos.

## 13. Entregáveis obrigatórios (TR §10) — atendimento

| # | Entregável | Atendido em | # | Entregável | Atendido em |
|---:|---|---|---:|---|---|
| 1 | Levantamento e refinamento dos requisitos | Item 1 | 14 | Dashboards e indicadores | Item 10 |
| 2 | Arquitetura da informação | Item 1 | 15 | Formulários e pesquisas | Item 12 |
| 3 | Protótipo navegável | Item 2 | 16 | Gestão de evidências | Item 4 |
| 4 | UX/UI | Item 2 | 17 | Relatórios e exportações | Item 11 |
| 5 | Front-end | Itens 3–5, 7–12 | 18 | Segurança, LGPD, logs e auditoria | Item 13 |
| 6 | Back-end | Itens 4–7, 10–13 | 19 | Testes funcionais | Item 15 |
| 7 | Banco de dados | Item 6 | 20 | Testes de segurança | Itens 13, 15 |
| 8 | Portal público | Item 3 | 21 | Testes de acessibilidade | Itens 14, 15 |
| 9 | Área restrita das organizações | Item 4 | 22 | Implantação em produção | Item 17 |
| 10 | Painel administrativo | Item 5 | 23 | Documentação técnica | Item 16 |
| 11 | Módulos de projetos e eventos | Item 7 | 24 | Treinamento da equipe | Item 16 |
| 12 | Calendário | Item 8 | 25 | Código-fonte e credenciais | Item 17 |
| 13 | Mapa e georreferenciamento | Item 9 | 26 | Período de garantia | Seção 9.1 (sem custo) |

**Limitações técnicas declaradas (TR §18):**

- A geocodificação automática por OpenStreetMap pode ter precisão menor em áreas rurais ou periféricas. Por isso existe o ajuste manual do pino.
- Tiles gratuitos seguem política de uso justo. Se o tráfego crescer muito, pode ser necessário um servidor de tiles próprio (estimado em R$ 150,00/mês).

---

## 14. Informações complementares (TR §16)

| Informação | Preenchimento |
|---|---|
| Razão social | **[preencher — NatGED]** |
| CNPJ | **[preencher]** |
| Endereço | **[preencher]** |
| Responsável pela proposta | **[preencher]** |
| E-mail / telefone | **[preencher]** |
| Validade da proposta | 60 dias |
| Prazo estimado para desenvolvimento | 22 semanas (fases 1 a 5) |
| Prazo estimado para implantação | 2 semanas (fase 6); aceite definitivo na semana 24 |
| Tecnologias utilizadas | Python/Django, Wagtail (CMS), Django REST Framework, HTMX, Alpine.js, Tailwind CSS, MapLibre/Leaflet, FullCalendar, ECharts, SurveyJS Form Library, Celery, Docker, Terraform |
| Banco de dados | PostgreSQL 16 + PostGIS |
| Infraestrutura / cloud | Nuvem pública, região São Paulo (AWS ou equivalente); CDN/WAF Cloudflare; contas em nome da FBA |
| Licenças ou APIs com custo recorrente | Nenhuma licença de software. Recorrentes apenas os serviços de nuvem (item 18). API de mapas sem custo |
| Prazo de garantia | 24 meses após o aceite definitivo |
| SLA de suporte | Crítico 2 h / 8 h; Alto 4 h / 2 d; Médio 1 d / 5 d; Baixo 2 d / próxima versão (seção 9.2) |
| Condições de pagamento | Desenvolvimento em 6 marcos (10/15/20/20/20/15%); operação mensal de R$ 4.340,00; pagamento em 15 dias da NF |
| Observações | Proposta integral ao escopo do TR, com premissas na seção 11 e opcionais na seção 6. Documento de Requisitos Refinados anexo |

---

## 15. Declaração de ciência do escopo (TR §19)

A NatGED declara ter recebido e analisado o Termo de Referência, compreendido o escopo solicitado e considerado na formação de preço os requisitos, entregáveis e responsabilidades necessários à execução, observadas as premissas desta proposta.

<br>

______________________________________________
**[Nome do responsável]**
**[Cargo]** — NatGED
[Cidade], ___ de ______________ de 2026.
