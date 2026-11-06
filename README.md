# Projeto do 2º bimestre: Engenharia de Software

> **Regra do projeto:** o agente propõe; o grupo decide e responde.
>
> Agentes são a ferramenta do processo, não o produto. Vocês constroem um sistema pequeno e são avaliados principalmente por como aplicam engenharia de software e controlam os agentes.

**Grupos:** 4 a 5 pessoas. **Tema:** livre.

**Entrega e prova:** 04/12/2026. A entrega é este repositório: enviem o link no Classroom.

**Defesa oral:** fora do encontro de 04/12, em data a ser divulgada no Classroom.

**Prova individual (AE):** sem IA, vocês vão auditar um pull request feito sobre uma cópia do código do grupo, tirada em 03/12 às 12h00 (horário de Brasília), com defeitos plantados. O que estiver na `main` nesse horário é o que entra na prova. Quem acompanha o código do grupo chega preparado.

## Comece aqui
1. Criem o repositório do grupo com **Use this template** e deem acesso a todo o grupo e ao professor.
2. Cada integrante ativa o **Copilot Student** com o e-mail da UEPG (extrato de matrícula, se solicitado) e localiza o **painel de uso** de créditos.
3. Escrevam, **sem usar o agente**: `specs/requisitos.md`, `specs/backlog.md` e o primeiro ADR em `docs/adr/`.
4. Escolham **Node.js ou Java** e ativem o CI: sigam `.github/exemplos-ci/LEIA-ME.md`.
5. Escrevam `docs/plano-de-teste.md`, `docs/convencao-versionamento.md`, `.github/copilot-instructions.md` e os agentes em `.github/agents/`.
6. Só então peçam a primeira história ao agente, em uma branch própria e com o teste escrito antes.

Procure por `<PREENCHER` para achar o que falta. Nenhum desses marcadores deve sobrar na entrega.

## Entregáveis
| # | Entregável | Onde |
|---|---|---|
| 1 | Repositório com histórico, branches e pull requests com revisão humana | Git e `docs/convencao-versionamento.md` |
| 2 | Spec com RF e RNF, critérios de aceitação e backlog priorizado | `specs/` |
| 3 | ADRs e diagrama de arquitetura | `docs/adr/`, `docs/arquitetura.md` |
| 4 | Pelo menos um padrão de projeto aplicado e justificado | Um ADR e o código |
| 5 | Plano de teste, testes automatizados e lint no CI | `docs/plano-de-teste.md`, testes, `.github/workflows/` |
| 6 | Configuração dos agentes: instruções e 2 agentes | `.github/copilot-instructions.md`, `.github/agents/` |
| 7 | Registro de uso de IA | `docs/registro-ia.md` |
| 8 | Relatório de smells com ao menos uma refatoração de código gerado | `docs/relatorio-smells.md` |
| 9 | README com execução e definição de pronto | Este arquivo |

## Fluxo de cada história
Critérios e teste (pessoas) → teste falhando → agente implementador → verificação local → pull request → agente revisor → revisão humana → merge.

## O que é do grupo
Requisitos, arquitetura, critérios de aceitação e o código integrado são responsabilidade do grupo. O agente pode sugerir, mas qualquer integrante precisa saber explicar qualquer decisão.

## Créditos do Copilot
- A cota é individual e mensal, não acumula e volta no dia 1º.
- Chat, CLI e cloud agent consomem créditos; as sugestões de código no editor, não.
- Conversas curtas, uma tarefa por vez, com a spec já escrita. Anote o saldo no registro de IA.
- Reservem créditos para o final do projeto. Não é preciso comprar créditos.

As regras do Copilot mudam com frequência: confiram a [documentação do GitHub](https://docs.github.com/en/copilot).

---

## Sobre o nosso sistema
*Substituam o conteúdo acima por esta seção ao final do projeto, mantendo a tabela de entregáveis.*

**Sistema:** <PREENCHER: nome e uma frase sobre o que faz>

**Grupo e papéis:** <PREENCHER: integrantes, Product Owner, Scrum Master e arquiteto técnico>

**Como executar:**
```bash
<PREENCHER: comandos para instalar, testar e executar>
```

### Definição de pronto
Uma história está pronta quando:
- [ ] <PREENCHER: de 5 a 7 itens verificáveis definidos pelo grupo>
