# Tema — Sistema de Atendimento / Tickets para Estudantes (Staff Hub)

Construa um **hub simples de atendimento** para estudantes abrirem chamados à Staff, com **triagem**, **acompanhamento** e **arquivamento** — sem depender do limite de canais do Discord.

## 📌 Problema
Hoje o fluxo de atendimento via bot/canais do Discord é limitado (limite/organização/arquivo), difícil de auditar e de consultar histórico.

## 🎯 Objetivo
- Oferecer um **ponto único** para abrir, acompanhar e encerrar chamados.
- Permitir **triagem por área** (Pedago, Tech, Comunidade, Assistência Campus, Freeze, Bolsa Auxílio, TIGs, Psicóloga, etc.).
- Entregar **visibilidade operacional** (fila, SLA simples, histórico) e **arquivamento** pesquisável.

## 🧪 MVP (usável já na segunda-feira)
- **Abertura de ticket** (nome/ID do estudante, categoria, descrição, anexos opcionais).
- **Triagem** (auto-roteamento por categoria; reatribuição manual).
- **Status** do ticket (aberto → em atendimento → aguardando estudante → resolvido → arquivado).
- **Notificações leves** (e-mail/Discord DM opcional ou link de acompanhamento).
- **Lista para Staff** com filtros (categoria, status, data) e **busca**.
- **Arquivamento** com **permalink** e export (CSV/Sheets).
- **Guia de operação** (1 página).

## 🧩 Exemplos de solução (opcionais)
- **SLA simples** por categoria (ex.: Pedago 3d úteis; Tech 5d úteis) com indicador de atraso.
- **Macros/Respostas-padrão** por área; campos obrigatórios por tipo de ticket.
- **Etiquetas** (prioridade, sensível, recorrente) e **métricas** (tempo até 1ª resposta, tempo de resolução).
- **Denúncia**: botão com redirecionamento externo (form oficial) — **fora do hub** se exigir confidencialidade extra.

## 🛡️ Importante
- **Privacidade**: tickets sensíveis (ex.: psicóloga/denúncia) devem ter **visibilidade restrita** (escopos/grupos).
- **Persistência leve**: SQLite/Sheets/Postgres (a critério do time), com **export** sempre disponível.

## ⚙️ Configuração (YAML de exemplo)
```yaml
categorias:
  - id: pedago
    nome: "Pedago"
    responsaveis: ["@rodrigo"]
    sla_dias_uteis: 3
  - id: tech
    nome: "Tech"
    responsaveis: ["@lucas"]
    sla_dias_uteis: 5
  - id: comunidade
    nome: "Comunidade"
    responsaveis: ["@mirian"]
    sla_dias_uteis: 4
  - id: assistencia
    nome: "Assistência Campus"
    responsaveis: ["@mirian"]
    sla_dias_uteis: 3
  - id: freeze
    nome: "Freeze"
    responsaveis: ["@rodrigo"]
    sla_dias_uteis: 2
  - id: bolsa
    nome: "Bolsa Auxílio"
    responsaveis: ["@mirian"]
    sla_dias_uteis: 5
  - id: tigs
    nome: "TIGs"
    responsaveis: ["@julia"]
    sla_dias_uteis: 5
  - id: psicologa
    nome: "Psicóloga"
    responsaveis: ["@dani"]
    sla_dias_uteis: 7
  - id: denuncia
    nome: "Denúncia"
    tipo: "link_externo"
    url: "https://exemplo.form/denuncia"
```

## 🧠 O que será avaliado

| Critério | Descrição |
|---|---|
| **ENTREGA MVP** | Fluxo abrir→atender→encerrar→arquivar funcionando. |
| **Clareza de UX** | Estudante abre em 1 min; Staff faz triagem sem atrito. |
| **Visibilidade Operacional** | Filtros/busca, métricas simples, export. |
| **Integração leve** | E-mail/Discord gateway opcional, sem dependências pesadas. |
| **Manutenibilidade** | Config por ENV/arquivos simples; logs mínimos; backup fácil. |

## 🏅 Também valorizaremos
- **Respostas-padrão** por categoria.
- **Rate-limit/anti-spam** básico.
- **Controle de acesso** por área (visibilidade restrita).
- **Webhooks** (ex.: postar atualização no canal privado da área).

## ✅ Sucesso na demo
Abrir 2 tickets (categorias diferentes) → triagem automática → 1 recebe 1ª resposta (SLA ok), outro é reatribuído → resolver e **arquivar** → **export** CSV + abrir **permalink** do ticket arquivado.
