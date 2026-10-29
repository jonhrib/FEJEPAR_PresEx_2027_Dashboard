# FEJEPAR PresEx 2027 — Dashboard Estratégico

Aplicação web React + TypeScript + Vite, com dados iniciais extraídos da Proposta Eleitoral-V4.pdf e dos três roadmaps operacionais anexados.

## Executar localmente

Requisitos: Node.js 20+ e npm.

```bash
npm install
npm run dev
```

Para validar a versão de produção:

```bash
npm run build
npm run preview
```

## Funcionalidades implementadas

- Navegação entre visão executiva, diagnóstico histórico, três frentes, calendário, roadmaps, indicadores, riscos, governança e auditoria das fontes.
- 54 atividades iniciais importadas (18 por frente) da aba `Roadmap 2027` das planilhas.
- Filtros por frente, status e pesquisa; detalhamento das atividades; atualização de status e observações no modo Gestão local.
- Criação de atividades locais e de registros de carteira por frente.
- Calendário com navegação mensal, marcos estimados e atividades dos roadmaps.
- Indicadores com critérios/metas transcritos da proposta; sem falsos resultados atuais.
- Riscos com campos configuráveis; registro local de reuniões, decisões e pendências.
- Exportação CSV de atividades filtradas e exportação/importação de backup JSON.
- Persistência por `localStorage` no navegador.
- Layout responsivo e controles acessíveis com rótulos/estados básicos.

## Dados e interpretação

- O PDF é a fonte principal da narrativa estratégica e das metas propostas.
- Os roadmaps preservam código, etapa, atividade, responsável, janela, datas, entregável, critério, prioridade, status e observações.
- O histórico financeiro no PDF registra participação de eventos nas entradas de 29,7% (2022), 57,3% (2023), 59,7% (2024) e 79,2% (2025); a planilha financeira complementar usa o grupo gerencial “Eventos e produtos”, portanto não se deve interpretar como receita exclusivamente de eventos.
- A proposta registra receita operacional de Mercado de R$ 6.880 em 2026, acima da meta de R$ 5 mil.
- A proposta define metas como cobertura de mapeamento IES (100%), cobertura de contato (90%), conversão comercial (≥30%), recorrência (≥60%), entrega de contrapartidas (100%), validação de propostas (≥80%) e indicadores governamentais listados na página de Indicadores.
- Carteiras de IES, parceiros e atores nas planilhas são modelos em branco (“A definir”/“A mapear”). O dashboard não inventa os contatos nem importa linhas modelo como entidades reais.
- EDL (março), janela de planejamento ENEJ (julho–setembro) e Prêmio FEJEPAR (dezembro) são referências estimadas, sujeitas a confirmação oficial.
- O PDF contém 26 hyperlinks anotados por página; alguns são destinos Drive/Sheets sujeitos a permissão. A lista não afirma que todos foram abertos externamente.

## Persistência, privacidade e produção

O projeto não tem backend, autenticação ou sincronização multiusuário. `localStorage` é persistência local apenas nesse navegador e perfil. Os modos “Apresentação” e “Gestão local” são uma distinção de interface, **não controle de acesso de segurança**. Não publique informações privadas no bundle nem insira contatos sensíveis em uma implantação pública.

Para produção, integrar API/backend com autenticação e autorização, banco compartilhado, validação de servidor, trilha de auditoria, backups, proteção de dados pessoais e política de acesso. Antes de implantar, revisar os hyperlinks externos e confirmar datas oficiais, responsáveis, linha de base e metas ainda “a definir”.

## Estrutura

- `src/main.tsx`: componentes, páginas, interações e cálculos.
- `src/style.css`: identidade visual responsiva FEJEPAR.
- `src/data.json`: dados extraídos e normalizados da proposta/planilhas, mais referências dos hyperlinks.
- `audit-report.md`: resumo da auditoria das fontes e lacunas.
