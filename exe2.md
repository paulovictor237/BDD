### História de Usuário

**COMO** um usuário do painel do cliente,  
**QUERO** gerar tokens em massa para todos os ajudantes que iniciarão e terminarão o serviço hoje e amanhã,  
**PARA QUE** eu possa disponibilizar esses tokens de forma prática a um representante responsável por validar os check-ins e check-outs no local do serviço. Ganhando assim agilidade na geração dos tokens.

### Critérios de Aceitação

#### Cenário 1 - Observando o botão "Gerar tokens" na tela de contratos em andamento

- **DADO QUE** estou logado e autenticado no painel do cliente
- **E** estou na tela de contratos
- **QUANDO** seleciono a aba denominada “Em andamento”
- **E** há pelo menos um contrato de ajudante listado nessa tela
- **ENTÃO** devo observar o botão denominado “Gerar tokens”
- **E** deve estar posicionado ao lado esquerdo do botão denominado “Lançar contrato”
- **E** ao passar o mouse sobre o botão, devo observar um tooltip com a seguinte informação:

> Os tokens de check-in e check-out são gerados para o dia atual e o dia seguinte.

#### Cenário 2 - Gerando os tokens de todos os contratos de ajudantes em andamento

- **DADO QUE** estou logado e autenticado no painel do cliente
- **E** estou na tela de contratos em andamento
- **QUANDO** clico no botão denominado “Gerar tokens”
- **ENTÃO** devo observar um loading em toda a tela, evitando que eu clique em qualquer lugar enquanto gera o relatório
- **E** devo observar que um arquivo em PDF foi baixado no navegador
- **E** deve estar nomeado como “Relatório de Tokens - 22/01/25 a 23/01/25”
- **E** as datas do nome do arquivo devem ser dinâmicas, conforme a data de geração do relatório (dia atual e dia seguinte).

#### Cenário 3 - Visualizando o relatório de tokens

- **DADO QUE** estou logado e autenticado no painel do cliente
- **E** acabei de gerar um relatório de tokens
- **QUANDO** clico no arquivo baixado
- **ENTÃO** devo observar as informações sobre os tokens de entrada do dia atual destacados no PDF conforme tabela abaixo:

| Item              | Tipo  | Conteúdo          | Observação                                                       |
| ----------------- | ----- | ----------------- | ---------------------------------------------------------------- |
| Título do arquivo | Texto | Lista de entradas | No cabeçalho da folha                                            |
| Subtítulo         | Texto | Número            | Data de início do serviço: **01/12/2024** (Data dinâmica)        |
| Registros         | Texto | Número            | - Horário <br> - Prestador <br> - Token <br> - Status (Dinâmico) |

- **E** devo observar as informações sobre os tokens de entrada do dia seguinte destacados no PDF (se houver).
- **E** devo observar as informações sobre os tokens de saída do dia atual destacados no PDF:

| Item              | Tipo  | Conteúdo        | Observação                                                       |
| ----------------- | ----- | --------------- | ---------------------------------------------------------------- |
| Título do arquivo | Texto | Lista de saídas | No cabeçalho da folha                                            |
| Subtítulo         | Texto | Número          | Data de início do serviço: **02/12/2024** (Data dinâmica)        |
| Registros         | Texto | Número          | - Horário <br> - Prestador <br> - Token <br> - Status (Dinâmico) |

- **E** devo observar as informações sobre os tokens de entrada e saída ordenados por ordem alfabética.

### Status dos Tokens

- **🟩 REALIZADO**: Quando o ajudante realizou o check-in ou check-out.
- **🟧 PENDENTE**: Quando o ajudante ainda não realizou o check-in ou check-out.
- **🟥 NÃO REALIZADO**: Quando o ajudante não realizou o check-in ou check-out no prazo determinado.

---

## Informações do Chamado

- **Chave:** DEV-4020
- **Resumo:** [Painel] - Gerando tokens em massa na tela de contratos em andamento.
- **Status:** Teste
- **Categoria de Status:** Indeterminado (cor: amarelo)
- **Resolução:** Não resolvido(s)
- **Responsável:** Douglas Damasceno
- **Criador:** Ricardo Silva
- **Data de Criação:** 20 Jan 2025 14:59 -0300
- **Última Atualização:** 29 Jan 2025 14:45 -0300

### Tempo de Desenvolvimento

- **Tempo estimado:** 0 minutos
- **Tempo gasto:** 2 dias, 5 horas, 49 minutos
- **Tempo agregado gasto:** 1 semana, 1 dia, 6 horas, 13 minutos

### Comentários

**Douglas Damasceno (29 Jan 2025 10:35 -0300)**  
[PX - Login](https://epic-dev-4014-generate-tokens-px-painel.motoristapx.vercel.app/)

---

## Subtarefas

- **DEV-4027**

---

## Campos Personalizados

- **Checklist Progress:** 2/3 (67%)
- **Data de Início:** 22 Jan 2025 17:07 -0300
- **Epic Link:** GERAÇÃO DE TOKENS EM MASSA
- **Fase:** SELECTED FOR DEV
- **Stakeholders:** Transportadoras
- **Story Points:** 2.0
- **Tester:** ID: 712020:3371de09-d255-487a-9396-97b5e0267504
- **Tempo de Resolução:** 29 Jan 2025 13:35 +0000
