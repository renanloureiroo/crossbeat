# Specs

O Crossbeat é desenvolvido **spec-first**: nenhuma funcionalidade é implementada sem uma spec aprovada nesta pasta.

## Convenção

- Arquivo: `NNNN-nome-curto.md` (ex.: `0001-ancs-notificacoes.md`)
- Uma spec por funcionalidade ou mudança de protocolo
- Uma spec aprovada vira a referência para a implementação e para os testes

## Template

```markdown
# NNNN: Título

- **Status:** rascunho | aprovada | implementada
- **Componentes:** wear | ios | android-bridge | protocol

## Problema
O que o usuário não consegue fazer hoje.

## Comportamento esperado
Cenários em Dado/Quando/Então.

## Fora de escopo

## Desenho técnico
Componentes envolvidos, mensagens do protocolo, permissões.

## Critérios de aceite
- [ ] ...

## Questões em aberto
```
