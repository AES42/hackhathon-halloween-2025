# Tema — “Constelações” Gamificado (Acompanhamento Fácil + Ranking)

Crie uma aplicação simples para **acompanhar e gamificar** o desempenho das **Constelações**, com **painel para a Staff** e **visão para os membros**. Foque em métricas leves, regras claras e **parciais semanais**.

## 📌 Problema
Queremos incentivar presença, prática e colaboração entre os membros de cada constelação e, ao mesmo tempo, dar à Staff uma visão **clara e rápida** do andamento.

## 🎯 Objetivo
- Oferecer um **ranking por constelação** e **parciais semanais**.
- Tornar a regra de pontuação **configurável** (por YAML/JSON).
- Permitir à Staff **auditar** e **exportar** os dados com facilidade.

## 🧪 MVP (usável já na sexta-feira)
- **Cadastro** de constelações (nome, 6 membros) e período do “pace/rank”.
- **Registro de pontos** por métrica (manual ou via formulário/bot).
- **Cálculo automático** da pontuação por regras configuráveis.
- **Ranking** geral + **parciais de sexta** com destaque para top-3.
- **Botão/Link** no canal da constelação para ver relatório e pontuação.
- **Export** CSV/Sheets + **guia de operação** (1 página).

## 🔢 Métricas sugeridas (exemplo do pace)
> Todas devem ser **parametrizáveis**; abaixo vai um **padrão** inicial:
- **Entrega da Libft**: `nota * 1` ponto (média das notas dos integrantes ao fim do rank).
- **Exame**: `10 pts por tentativa` *(conta só se ≥ 50% do grupo tentar na semana)*.
- **Fórum de Projetos**: `2 pts por contribuição` *(apenas mensagens com ≥ 10 ⭐)*. (opcional por envolver Discord)
- **Checkpoints**: `30 pts` *(por 2 checkpoints/semana com ≥ 50% da constelação)*.
- **Logs**: `10 pts por dia por membro` *(só vale se **todos** logarem 3 dias/semana)*.
- **Voxotron (apoio entre constelações)**: `50 pts` para as **2 mais votadas** da semana.

### Exemplo de configuração (YAML)
```yaml
periodo:
  nome: "Rank 00 — Pace 24"
  inicio: "2025-03-03"
  fim: "2025-04-27"
regras:
  libft:
    tipo: "media_nota"
    fator: 1
  exame:
    tipo: "tentativas"
    pontos_por_tentativa: 10
    minimo_membros_percent: 50
  forum:
    tipo: "contribuicoes"
    pontos_por_contribuicao: 2
    minimo_estrelas: 10
  checkpoints:
    tipo: "semanal"
    pontos: 30
    quantidade: 2
    minimo_membros_percent: 50
  logs:
    tipo: "habit_week"
    pontos_por_dia_por_membro: 10
    requisito_todos_membros_dias: 3
  voxotron:
    tipo: "votacao_semana"
    pontos: 50
    vencedores: 2
parciais:
  dia_semana: "FRI"
  top_n: 3
premiacao_final:
  titulo: "Coroação da Constelação"
  recompensa: "Surpresa"
```

## 🧩 Telas/Fluxos recomendados
- **Visão Membro**: regras, pontuação da sua constelação, contribuições da semana, “o que falta para bater os 100 pts”.  
- **Visão Staff**: ranking, filtros por semana, **auditoria** (como cada ponto foi composto), export.  
- **Parciais de Sexta**: geração de resumo (Markdown/HTML) para copiar no canal + imagem do top-3 (opcional).

## 🛡️ Importante
- Regras **transparentes** e auditáveis (mostrar de onde veio cada ponto).
- Anti-abuso simples: limites por semana, verificação de critérios (% do grupo), votos únicos por cadete no Voxotron.

## 🧠 Avaliação

| Critério | Descrição |
|---|---|
| **Impacto imediato** | Staff opera na primeira semana sem suporte extra. (40%) |
| **Clareza das regras** | Configuração legível; auditoria simples. (25%) |
| **UX para membros** | Entendem “o que fazer” para pontuar. (20%) |
| **Robustez leve** | Export, logs mínimos, anti-abuso básico. (15%) |

## ✅ Sucesso na demo
Criar/editar regras → registrar uma semana de pontos → gerar **parcial de sexta** com top-3 → abrir **relatório por constelação** → exportar CSV.
