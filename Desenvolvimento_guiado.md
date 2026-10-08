# DESENVOLVIMENTO GUIADO — MISSION ARCHITECT

## 1. ENTRADA
Antes de implementar, leia: `Contexto.md → Arquitetura.md`.

## 2. REGRA PRINCIPAL
Autonomia de implementação ≠ autonomia de escopo.

Pode criar/refatorar código, corrigir bugs, criar testes, instalar dependências justificadas e executar comandos.

Não pode, sem justificativa: aumentar escopo, trocar stack, criar banco/auth/microserviços ou infraestrutura desnecessária.

## 3. PRIMEIRO PASSO
Inspecione stack, `package.json`, configs, scripts, estrutura, código existente e erros atuais. Preserve código funcional.

## 4. ORDEM
### P0
Tipos, dados, validação, engine, score, eventos, resultado.

### P1
Seleção, designer, métricas, simulação, resultado.

### P2
NASA/JPL, normalização, visualização, fallback.

### P3
Animações, acessibilidade, polimento, IA opcional.

Não iniciar P3 antes de P0/P1.

## 5. CICLO
`inspecionar → planejar → implementar → testar → executar → revisar → corrigir`

Validar cada incremento.

## 6. DOMÍNIO
Regras importantes devem ter uma única fonte de verdade.
```ts
validateMission()
simulateMission()
calculateScore()
```
Evitar regras duplicadas na UI.

## 7. SIMULAÇÃO
`validar → calcular recursos → avaliar restrições → métricas → eventos → resultado → score`

Resultado estruturado e reproduzível. Não usar aleatoriedade não controlada.

## 8. NASA/JPL
Implementar após MVP funcional:
```text
UI
↓
Route Handler
↓
Adapter
↓
NASA/JPL
↓
dados normalizados
```
Se falhar, usar fallback local.

## 9. DADOS OFICIAIS
Antes de usar regra baseada em documento NASA:
1. conferir `Contexto.md`;
2. identificar fonte;
3. classificar como requisito, dado ou hipótese;
4. registrar origem quando necessário.

Não inventar dados. Informação ausente vira pendência.

## 10. TESTES
Testar missão válida/inválida, limites, incompatibilidades, score, sucesso/falha, eventos e determinismo.

## 11. SEGURANÇA
Verificar inputs, parâmetros, APIs, secrets, dados externos e HTML. Nunca versionar secrets.

## 12. DEPENDÊNCIAS
Antes de instalar: verificar existente, capacidade do framework, custo e necessidade.

## 13. BANCO / AUTH
Não criar sem requisito explícito.

## 14. IA
P3. Só após MVP estável e se houver benefício claro. Engine não depende dela.

## 15. FEATURE GATE
Para qualquer feature: `problema? necessidade? benefício? custo? risco? alternativa menor?`
Sem justificativa proporcional: não implementar.

## 16. ESTADO
Se `PROJECT-STATE.md` existir, atualizar fase, concluído, andamento, próximo passo, decisões, bugs e fora do MVP. Criar somente se necessário.

## 17. DEFINITION OF DONE
Implementada, integrada, executada, testada, sem erro crítico conhecido, compatível com arquitetura e sem complexidade desnecessária.

## 18. REVISÃO FINAL
Arquitetura, código, segurança, performance, UX e demo.

## 19. PRIORIDADE
`funcionar > estabilidade > clareza > UX > dados científicos > polimento > extras`

Quando o MVP estiver completo, não adicione complexidade sem retorno.
