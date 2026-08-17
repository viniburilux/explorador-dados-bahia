# Leitura estratégica — explorador-dados-bahia

**Data:** 17 de agosto de 2026  |  **Repositório:** [explorador-dados-bahia](https://github.com/viniburilux/explorador-dados-bahia)  |  **Autor:** Manus AI

> Este documento é uma auditoria de inventário e potencial. Ele não altera o código existente e não afirma que funcionalidades foram executadas ou validadas quando isso não aparece na evidência observada.

## Síntese executiva

Repositório muito enxuto que contém um site estático (duas cópias do mesmo HTML: index.html e docs/index.html) intitulado "Explorador de Gastos Artísticos Públicos — Bahia". O front-end usa bibliotecas via CDN (Chart.js e Leaflet) e apresenta um layout visual para dashboards e mapas, mas não há código de ingestão, ETL, back-end, dados sample ou automações dentro do repositório. Estrutura e metadados indicam intenção de publicação via GitHub Pages (.nojekyll + pasta docs).

## Domínio e propósito aparente

Domínio: transparência pública / contratações públicas com foco em contratações artísticas na Bahia. Propósito aparente: fornecer uma interface visual (gráficos e mapas) para explorar dados do Portal Nacional de Contratações Públicas (PNCP) relativos a contratações artísticas municipais (Bahia 2025).

## Indicadores do snapshot

| Indicador | Valor |
|---|---:|
| Arquivos contabilizados | 4 |
| Tamanho no snapshot | 102936 bytes |
| Último commit observado | 926db877cbe4994c9420bf3a859509fc1f5a4db9	2026-04-25T00:02:34-04:00	Ajuste final: Novo subtítulo e correção do e-mail de contato |
| Prioridade sugerida | alta |

## Evidências observadas

- Arquivos presentes: index.html (≈51 KB) e docs/index.html (≈51 KB) — duas cópias do mesmo HTML.
- HTML referencia Chart.js (https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.0/chart.umd.min.js) e Leaflet (https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.js) via CDN — evidência de intenção de gráficos e mapas.
- Meta description e textos no HTML mencionam 'Explore dados públicos de contratações artísticas pelas prefeituras da Bahia' e 'Dados do Portal Nacional de Contratações Públicas (PNCP)'.
- Há .nojekyll na raiz e em docs/ — evidência de preparação para deploy em GitHub Pages.
- Metadados do GitHub: repositório público, criado em 2026-04-24, último commit 2026-04-25; descrição 'Explorador de Dados de Contratações — Bahia 2025'.
- Não há arquivos de código fonte (JS separados), nem package.json, nem scripts de build, nem dados, nem README, nem LICENSE, nem workflows de CI no dossiê fornecido.

## Ativos e capacidades

- Site estático pronto para abrir em navegador: layout completo com masthead, hero, seções, estilos CSS inline/embutidos.
- Uso de bibliotecas de visualização: Chart.js (para gráficos) e Leaflet (para mapas) — há capacidade front-end para visualizar dados se carregados em runtime.
- Design visual e componentes de UI implementados (estatísticas, grid de perguntas, seções de exploração, estilos de tipografia e tema escuro) — fornece uma base front-end para exploração interativa.
- Estrutura compatível com GitHub Pages (pasta docs + .nojekyll) — facilita publicação estática sem infraestrutura adicional.
- Arquivos HTML de dimensões completas (~51 KB cada) indicando que o projeto está em estado de 'mockup/protótipo visual' utilizável localmente.

## Maturidade observável

Maturidade observável: protótipo visual estático / proof-of-concept. Evidência: repositório contém apenas HTML/CSS estático, referências a bibliotecas via CDN, e ausência de scripts de ingestão, amostras de dados, testes, CI/CD ou documentação técnica. Inferência: o projeto não possui pipeline de ETL, API ou backend implementado no repositório (ausência de qualquer código ou configuração que sponsore esses componentes). Conclusão: não pronto para produção — adequado como mockup de interface ou ponto de partida para desenvolvimento, mas faltam infra, automação, governança e validação de dados.

## Potencial de aproveitamento

- Usar o front-end como base visual para um Explorador integrado ao ecossistema LuxVerso/GhostWorks, adicionando um backend/API que consuma e normalize dados do PNCP.
- Adicionar pipelines ETL para transformar e enriquecer dados de contratações (geocodificação, classificação por natureza artística, agregações por município) e alimentar os gráficos/ mapas já previstos no layout.
- Publicar rapidamente como landing estática via GitHub Pages para demonstração enquanto se desenvolve o backend; útil para mostrar design e hipóteses de análise a stakeholders.
- Integrar com ferramentas de IA (ex.: geração de narrativas automatizadas sobre achados, sumarização de contratos, detecção anômala via modelos) se for disponibilizada camada de dados estruturados.
- Padronizar o front-end como template para outros estados/temas do LuxVerso, reusando componentes visuais e estruturas de página.

## Riscos e lacunas

- Falta total de ingestão/armazenamento de dados no repositório — nenhum CSV, JSON, script de fetch ou documentação sobre endpoints do PNCP foi incluída (evidência).
- Ausência de README, LICENSE e documentação de uso ou arquitetura — dificulta reprodução e contribuição por terceiros (evidência).
- Não há CI/CD, workflows ou testes automatizados; deploy automatizado e verificação são inexistentes (evidência).
- Segurança e supply chain: dependência de bibliotecas via CDN sem SRI ou políticas de integridade; ausência de Content Security Policy (CSP) — risco de injeção/manipulação de recursos em produção (inferência baseada nos arquivos estáticos).
- Governança de dados e conformidade: nenhum registro de proveniência, licença dos dados do PNCP, política de privacidade, ou tratamento/anonymização de PII (se presente nos dados) — gap grave para uso público/produção (evidência de ausência).
- Manutenção e organização: duplicação de arquivos (index.html + docs/index.html) sugere processo manual de publicação; falta modularização dos assets (CSS/JS separados) e controle de versões de dependências.
- Acessibilidade, performance e responsividade não estão validadas — não há testes de acessibilidade ou otimização documentados (evidência da ausência).

## Próximos passos recomendados

- Adicionar documentação mínima: README.md com objetivo do projeto, instruções para executar localmente (abrir index.html), roadmap e contato. Indicar claramente o estado atual (protótipo/desenvolvimento).
- Incluir LICENSE apropriada (ex.: MIT ou outra compatível com política organizacional) e arquivo NOTICE se necessário.
- Centralizar o HTML único (remover duplicação) e organizar assets: mover CSS/JS inline para arquivos separados em /assets para facilitar manutenção e versionamento.
- Documentar fonte de dados e esquema: listar endpoints do PNCP pretendidos, exemplo de payloads, dicionário de campos e licenciamento dos dados recebidos; adicionar amostra de dados (anônima) no repositório para desenvolvimento local.
- Implementar scripts de ingestão ETL minimalistas (ex.: Python ou Node) que façam fetch dos dados do PNCP, validação e normalização, e gerem artefatos JSON/CSV consumíveis pelo front-end. Versionar esses scripts no repositório.
- Configurar pipeline CI (GitHub Actions) para: lint de HTML/CSS/JS, testes básicos (validação JSON, checagem de schema), build e deploy automático para GitHub Pages (se for estratégia de publicação).
- Adicionar medidas de segurança: usar SRI (integrity) para CDNs, considerar hospedagem local de bibliotecas críticas, definir CSP em páginas geradas, revisar uso de recursos externos e políticas de CORS caso adicione APIs.
- Definir governança de dados: política de tratamento de PII, retenção, controle de acesso para dados sensíveis, registro de proveniência (quando os dados foram coletados, por quem, transformações aplicadas) e catálogo de dados integrado ao repositório (ex.: arquivo datasets.md).
- Criar especificação de API/back-end: endpoints REST/GraphQL mínimos para servir agregados, filtros por município/ano/segmento, endpoints paginados para listagem de contratos; projetar para escalabilidade (cache, query patterns).
- Prototipar integração com LuxVerso/GhostWorks: definir como os dados ETL serão disponibilizados (data lake, banco analítico, API), padronizar modelo de dados comum (taxonomias artísticas, entidades contratantes/contratadas), e documentação para integração com módulos de IA que geram narrativas/insights.
- Adicionar testes automatizados: unitários para ETL, contratos de API (schema tests), validação de consistência e testes de acessibilidade (axe, lighthouse) no CI.
- Revisar questões de UI/UX e acessibilidade: validar contraste, navegação por teclado, texto alternativo e responsividade; priorizar correções identificadas por testes automatizados de acessibilidade.
- Planejar monitoramento e observabilidade quando houver backend: métricas de ingestão, erros de parsing, contagem de registros processados e logs estruturados para auditoria.
- Curto prazo mínimo viável para demonstração: publicar a versão estática (somente front-end) no GitHub Pages com README claro, e paralelamente entregar um script ETL pequeno que puxe um subconjunto do PNCP e gere um JSON consumível pelo front-end para demo dinâmica.

## Método e limites

A leitura foi feita sobre um snapshot de profundidade 1 e sobre arquivos textuais selecionados por relevância estrutural, incluindo README, manifests e amostras de código. Dependências, notebooks, binários, dados grandes e integrações externas podem exigir uma rodada posterior de execução controlada. Nenhum código do repositório foi executado durante a auditoria.

**Fonte primária:** [explorador-dados-bahia](https://github.com/viniburilux/explorador-dados-bahia)
