# Tema — Presença no Campus & Engajamento (Gamificado)

Crie uma solução **campus-first** para tornar a presença **visível e motivadora**, usando mecânicas simples de jogo (badges, ranking, missões).

## 📌 Problema
A Staff da 42 Rio não tem uma visão simples de quem frequenta o campus (apenas laboratório), por quanto tempo e com que constância — e não existe um incentivo claro para manter rotina presencial.

## 🎯 Objetivo
- Tornar a presença **fácil de registrar** (check-in/out simples).
- Dar **feedback e motivação** (ranking/badges).
- Entregar **visibilidade imediata** para a Staff (horas/dia/semana, picos/vales).

## 🧪 MVP (usável já na segunda-feira)
- **Check-in/Check-out** local (QR/NFC/kiosk simples).
- **Ranking semanal** + **badges** automáticas (ex.: “Madrugador”, “Maratonista”).
- **Painel** com métricas-chave (presentes/dia, horas por pessoa/semana).
- **Export** (CSV/Sheets) + **instruções de uso** (1 página).

## 🧩 Exemplos de solução (opcionais)
- Rotação diária de QR + hash/nonce para antifraude básico.
- “Missões de campus”: ex. participar de 1 study group + 1 mentoria + 1 correção.
- Bot no Discord apenas para **divulgar** rankings/insígnias (sem dados sensíveis).

## 🧠 O que será avaliado

| Critério | Descrição |
|---|---|
| **Qualidade Técnica** | Código sólido, simples de manter. |
| **ENTREGA MVP** | Funciona, dá pra usar **no campus** imediatamente. |
| **Integração Técnica** | Conexões leves (Sheets/Discord opcional). Sem dependências críticas. |
| **Eficiência e Impacto** | Reduz atrito operacional e **aumenta presença**. |
| **Demonstração Prática** | Check-in real, painel atualiza, export funciona. |
| **Apresentação** | Fluxo claro, onboarding em **1 min**. |

## 🏅 Também valorizaremos
- Antifraude simples (QR rotativo).
- UX polida (1 clique pro check-in).
- Métricas úteis pra Staff (visões por dia/semana, picos).
- Documentação de deploy e operação (curta e objetiva).

## ✅ Sucesso na demo
Alguém faz check-in real → painel atualiza → ranking/badge aparece → Staff exporta CSV.
