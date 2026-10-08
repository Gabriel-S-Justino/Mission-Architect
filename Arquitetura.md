# ARQUITETURA — MISSION ARCHITECT

## 1. FLUXO
Entrada: `Contexto.md`. Saída: arquitetura mínima. Depois: `Desenvolvimento_guiado.md`.

## 2. REQUISITOS DERIVADOS
**Funcionais:** [preencher]  
**Técnicos:** [preencher]  
**Dados NASA:** [preencher]  
**Critérios que afetam arquitetura:** [preencher]  
**Restrições:** [preencher]

## 3. STACK
Preferencial: Next.js, React, TypeScript, Tailwind, SVG/Canvas quando necessário. Dependências somente com justificativa.

## 4. ARQUITETURA
```text
UI
 ↓
Application
 ↓
Mission Domain / Simulation Engine
 ↓
Data Providers
```
Domínio não depende da UI.

## 5. DOMÍNIO
Mission, MissionConstraints, MissionDesign, Launcher, PowerSystem, Instrument, Protection, Communication, MissionResult, MissionEvent, OrbitalData.

Adaptar aos requisitos oficiais.

## 6. MISSÕES
Usar um engine:
```ts
simulateMission(mission, design)
```
Missões são dados/configuração, não engines separados.

**Missões obrigatórias:** [preencher]  
**Parâmetros específicos:** [preencher]

## 7. ENGINE
Separar `validation`, `simulation`, `scoring`, `events`.

Funções possíveis:
```ts
validateMission()
calculateMass()
calculateCost()
calculatePower()
calculateScience()
calculateReliability()
calculateRisk()
calculateScore()
generateEvents()
simulateMission()
```
Criar somente as necessárias.

## 8. REGRAS CIENTÍFICAS
**Modelos/fórmulas:** [preencher]  
**Fontes:** [preencher]  
**Simplificações:** [preencher]  
**Precisão esperada:** [preencher]

Não transformar aproximações em alta precisão.

## 9. NASA/JPL
```text
Next.js Route Handler
 ↓
NASA/JPL Adapter
 ↓
Dados normalizados
 ↓
Engine / Orbital View
```
**Providers:** [preencher]  
**Endpoints:** [preencher]  
**Dados necessários:** [preencher]  
**Fallback:** [preencher]

Domínio não conhece formato bruto da API.

## 10. FRONTEND
Possíveis componentes: `MissionSelector`, `MissionDesigner`, `ComponentCard`, `MissionStats`, `Simulation`, `SimulationTimeline`, `MissionResult`, `OrbitalView`.

Não colocar regras complexas nos componentes.

## 11. ESTADO
Preferir React state, props e hooks simples. Estado: `selectedMission`, `missionDesign`, `simulationState`, `missionResult`.

## 12. PERSISTÊNCIA
**Necessária:** [sim/não]  
**Motivo:** [preencher]  
Sem requisito real, usar memória.

## 13. ESTRUTURA
Preservar a existente. Base:
```text
app/
components/
game/
data/
services/
types/
tests/
```

## 14. SEGURANÇA
Inputs, parâmetros, APIs externas, secrets e respostas externas. Não expor secrets.

## 15. TESTABILIDADE
Prioridade: validação, cálculos, score, sucesso/falha, eventos, determinismo, integrações.

## 16. PERFORMANCE
Evitar chamadas repetidas, payloads desnecessários e processamento excessivo. Não otimizar prematuramente.

## 17. YAGNI GATE
Antes de adicionar: é requisito? é MVP? há solução menor? pode esperar? aumenta risco? Sem justificativa: não implementar.

## 18. PLANO
**P0:** domínio + validação + engine + resultado  
**P1:** UI + fluxo completo  
**P2:** NASA/JPL + visualização + fallback  
**P3:** polimento + IA opcional

**Próximo: `Desenvolvimento_guiado.md`.**
