### História de Usuários

**DADO QUE** sou um usuário da Torre, com permissão de edição no menu de Cadastros  
**QUERO** enviar um lead para o fluxo de qualificação sem a necessidade de criar um filtro  
**PARA** qualificação imediata de específica

### Critérios de Aceitação

#### Cenário 01 - Apresentar action de qualificação

**DADO QUE** acesso a página Cadastro → Motoristas e Ajudantes  
**QUANDO** selecionar um registro na tabela, mesmo ele não contendo registrado Cidade e Estado  
**E** estar com o status “Lead“  
**E** estar com a etapa “Aguardando filtro“  
**E** clicar em “Ações"  
**ENTÃO** observo uma opção com o texto “Enviar para Qualificação"

#### Cenário 02 - Criar filtro default “Leads recomendados“

**DADO QUE** acesso a página Cadastro → Filtros de Leads  
**QUANDO** visualizar as informações da página  
**ENTÃO** observo um novo filtro criado com as seguintes informações nas colunas:

| Campos            | Conteúdo em tela                                                                   |
| ----------------- | ---------------------------------------------------------------------------------- |
| ID                | Incremental conforme registro na tela                                              |
| Status            | Ativo                                                                              |
| Tipo de Prestador | –                                                                                  |
| Tipo de Veículo   | –                                                                                  |
| Estado            | –                                                                                  |
| Nome              | Leads recomendados                                                                 |
| Solicitante       | –                                                                                  |
| Total de Lead     | Incremental, sempre somar o lead enviado com a quantidade anterior                 |
| Meta              | –                                                                                  |
| Qualificados      | Adicionar quantidade de prestadores que passaram neste filtro e foram qualificados |
| Prioridade        | Alta                                                                               |
| Data de início    | Preencher com a data que criou o filtro default                                    |
| Data final        | –                                                                                  |

**E** não apresentar informação na coluna “Estado” do Filtro, mostrar somente “--"  
**E** na tabela da página Priorização Cadex apresentar o Estado que foi cadastrado pelo Lead, caso não houver, apresentar “--"  
**E** na tabela da página Priorização Cadex, apresentar a Cidade que foi cadastrado pelo Lead, caso não houver, apresentar “--"

**Informações no banco:**

| Campos         | Obrigatório? | Opção                                           |
| -------------- | ------------ | ----------------------------------------------- |
| Nome           | Sim          | Leads recomendados                              |
| Data de início | Sim          | Preencher com a data que criou o filtro default |
| Data final     | Sim          | Sem data                                        |
| Meta           | Não          | Sem meta                                        |
| Prioridade     | Sim          | Alta                                            |
| Estado         | Sim          | Preencher no banco com um Estado SC.            |
| Cidade         | Sim          | Preencher no banco com uma cidade default.      |

#### Cenário 03 - Comportamento da opção “Enviar para qualificação" - Motorista e Ajudante

**DADO QUE** selecionar um prestador na página Motoristas e Ajudantes, mesmo ele não contendo registrado Cidade e Estado  
**E** ter no status “Lead“  
**E** ter a etapa “Aguardando filtro“  
**E** clicar em “Ações”  
**QUANDO** clicar na opção com o texto “Enviar para qualificação"  
**ENTÃO** observo que é apresentado uma modal com as seguintes informações:

| Informação           | Conteúdo em tela                              | Comportamento                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------------------- | --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Título               | Enviar para Qualificação                      | Nenhum                                                                                                                                                                                                                                                                                                                                                                                                          |
| Texto de confirmação | Tem certeza de que deseja executar esta ação? | Nenhum                                                                                                                                                                                                                                                                                                                                                                                                          |
| CTA de cancelamento  | Cancelar                                      | Fechar janela desconsiderando a execução da ação                                                                                                                                                                                                                                                                                                                                                                |
| CTA de confirmação   | Executar ação                                 | - Exibir a mensagem de confirmação na tela "Profissional enviado para qualificação com sucesso!“ <br> - Vincular os registros ao filtro default “Lead recomendado“ na página “Cadastro → Filtros de Leads“ <br> - Alterar os status do lead para “Em qualificação" <br> - Alterar a etapa do lead para “Aguardando Priorização” <br> - Apresentar os registros selecionados na página Cadex → Priorização Cadex |

**Importante:**

- Como o Job do filtro roda a cada hora, seria importante na hora da ação da action validar se já tem uma campanha ativa que o lead se encaixa e enviá-lo para ela.
- Considerar que existe uma rotina/job que roda para validar leads para o filtro. No flitro default não deve ser considerado neste job.

#### Cenário 04 - Comportamento da opção “Enviar para qualificação" ao selecionar mais de uma opção - Motoristas e Ajudantes

**DADO QUE** selecionar um ou mais prestadores na página Motoristas e Ajudantes  
**E** estar com o status “Lead“  
**E** estar com a etapa “Aguardando filtro“  
**E** clicar em “Ações”  
**QUANDO** visualizar as informações  
**ENTÃO** a opção “Enviar para Qualificação" **NÃO** deve ser apresentada

#### Cenário 05 - Restringir Visualização do filtro "Leads Recomendados“

**DADO QUE** acesso a página “Cadastro → Filtro de Leads"  
**QUANDO** visualizar registro do filtro  
**ENTÃO** deve ser removido a possibilidade de visualização dos detalhes do registro, tando ao clicar na linha como também ao acionar o ícone de visualização (olhinho)

#### Cenário 06 - Restringir Edição no filtro "Leads Recomendados“

**DADO QUE** acesso a página “Cadastro → Filtro de Leads"  
**QUANDO** visualizar registro do filtro  
**ENTÃO** deve ser removido a possibilidade de edição do registro ao acionar o botão editar

#### Cenário 07 - Restringir Ação de “Iniciar” para o filtro "Leads Recomendados“

**DADO QUE** acesso a página “Cadastro → Filtro de Leads"  
**E** selecionar o filtro "Leads Recomendados“, sendo único registro selecionado  
**E** clicar na opção de “Ações"  
**QUANDO** acionar as opção “Iniciar campanha"  
**ENTÃO** observo uma mensagem de erro com o seguinte texto:

> Não é possível executar esta ação no filtro Leads Recomendados

#### Cenário 08 - Restringir Ação de “Iniciar” em massa para o filtro "Leads Recomendados“

**DADO QUE** acesso a página “Cadastro → Filtro de Leads"  
**E** selecionar o filtro "Leads Recomendados“ em conjunto com outros filtros  
**E** clicar na opção de “Ações"  
**QUANDO** acionar as opção “Iniciar campanha"  
**E** o filtro **"Leads Recomendados“** é o primeiro da listagem selecionado  
**ENTÃO** observo uma mensagem de erro com o seguinte texto:

> Apenas um filtro pode ser iniciado por vez.

#### Cenário 09 - Restringir Ação de “Parar” para o filtro "Leads Recomendados“

**DADO QUE** acesso a página “Cadastro → Filtro de Leads"  
**E** selecionar o filtro "Leads Recomendados“, sendo único registro selecionado  
**E** clicar na opção de “Ações"  
**QUANDO** acionar as opção “Parar campanha"  
**ENTÃO** observo uma mensagem de erro com o seguinte texto:

> Não é possível executar esta ação no filtro Leads Recomendados

#### Cenário 10 - Restringir Ação de “Parar” em massa para o filtro "Leads Recomendados“

**DADO QUE** acesso a página “Cadastro → Filtro de Leads"  
**E** selecionar o filtro "Leads Recomendados“, sendo único registro selecionado  
**E** clicar na opção de “Ações"  
**QUANDO** acionar as opção “Parar campanha"  
**ENTÃO** observo que **NÃO** será executado a ação no filtro "Leads Recomendados“  
**E** executado a ação nos demais filtros selecionados

#### Cenário 11 - Restringir replicação no filtro "Leads Recomendados“

**DADO QUE** acesso a página “Cadastro → Filtro de Leads"  
**QUANDO** visualizar registro do filtro  
**ENTÃO** deve ser removido a possibilidade de replicação (atualizar página) ao acionar o botão Ações do registro (três pontinhos da linha) → replicate

#### Cenário 12 - Adicionar filtro de Leads Recomendados na página Prioridade Cadex

**DADO QUE** acesso a página “Cadex → Prioridades Cadex"  
**QUANDO** acionar o Filtro Avançado  
**ENTÃO** observo o título **“Leads Recomendados“**  
**E** o campo com as seguintes opções: “Sim” e “Não”  
**E** deve ser possível selecionar outros filtros e realizar a ações em conjunto com os demais entendendo seu comportamento como "E”

- **Environment**:
- **Key**: AQ-13
- **Summary**: [Torre] Possibilitar qualificar leads sem filtro
- **Type**: História
- **Parent**: AQ-6
- **Priority**: Medium
- **Status**: Concluído
- **Status Category**: Done (green)
- **Resolution**: Itens concluídos
- **Assignee**: Felipe Vieira Andrade
- **Reporter**: taciana.commandeur@px.center
- **Labels**:
- **Created**: Sun, 5 Jan 2025 17:53:54 -0300
- **Updated**: Wed, 29 Jan 2025 07:24:54 -0300
- **Resolved**: Wed, 29 Jan 2025 07:24:50 -0300
- **Votes**: 0
- **Watches**: 3
- **Time Estimate**: 0 minutes
- **Time Spent**: 1 week, 1 day, 5 hours, 48 minutes

## Comments

### Comment 1

- **Author**: taciana.commandeur@px.center
- **Created**: Fri, 10 Jan 2025 11:47:11 -0300
- **Content**:
  **Observações do refinamento:**
- O Filtro ficará visível na listagem
- Ter possibilidade de rastrear os leads que foram enviados direto da drivers
- Terá dois filtros default, um para Ajudante e um para Motoristas
- A única ação que encerra um filtro é a action
- O filtro fica ativo até a meta ser cumprida
- São duas tabelas que trabalham com o filtro ([Leandro Machado da Silva](https://motoristapx.atlassian.net/secure/ViewProfile.jspa?accountId=712020%3A8986c234-9366-4676-bb3c-c8a6f66660e9))

### Comment 2

- **Author**: Leandro Machado da Silva
- **Created**: Fri, 10 Jan 2025 11:49:03 -0300
- **Content**:
  Tabelas a serem criados registros como default: `lead_campaigns e lead_campaign_results`

### Comment 3

- **Author**: Felipe Vieira Andrade
- **Created**: Mon, 13 Jan 2025 08:36:27 -0300
- **Content**:
  **Anotações da atividade.**

Quando o Driver já estiver em algum tipo de qualificação, não deve aparecer o botão de qualificar o Driver?

Na tela Driver, será possível selecionar mais de um driver, mas como só um poderá ser qualificado por vez, o usuário receberá uma mensagem que precisa selecionar um de cada vez.

**A definir:**

| Descrição                                                                             | Provisório                                                                                                                                                                                                | Definido                                                                                                                                                                                                                              |
| ------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Texto para quando o usuário seleciona mais de um Driver para mandar para qualificação | Só pode qualificar um profissional por vez.                                                                                                                                                               | Selecione apenas um prestador para realizar essa ação                                                                                                                                                                                 |
| Action para executar a ação                                                           |                                                                                                                                                                                                           | Enviar para Qualificação                                                                                                                                                                                                              |
| Criar o nome da campanha                                                              | Utilizei o id + nome driver, exemplo <br> 11225 - Nome Driver                                                                                                                                             | Alinhado junto a Taci que o nome da campanha será “Leads recomendados“                                                                                                                                                                |
| Tabela lead_campaings                                                                 | A coluna state_id não pode ser null, sendo assim estou setando com o valor do motorista                                                                                                                   | Alinhado junto a taci que o por padrão ficara com o codigo de SC mas não será apresentado na tela a informação                                                                                                                        |
| Critério para o botão “Enviar para Qualificação“                                      |                                                                                                                                                                                                           | Para a ação “Enviar para Qualificação“ aparecer na tela Motoristas e Ajudantes para o driver selecionado, deve ter os seguintes, critérios: estar com o status como “Lead” e na etapa de “Aguardando Filtro“. - Alinhado junto a Taci |
| Campo estado do filtro defaul                                                         | Esconder                                                                                                                                                                                                  | Alinhado junto a Taci que vamos deixar com ‘--’                                                                                                                                                                                       |
| Botões de ação do filtro                                                              | Esconder ou inabilitar                                                                                                                                                                                    | Alinhado que vamos esconder ou inabilitar, estou verificando a possibildiade tecnica do framework nova                                                                                                                                |
| Botões de detalhe/replicar/editar                                                     |                                                                                                                                                                                                           | Alinhado com a Taci, que vamos deixar inabilitados                                                                                                                                                                                    |
| Leads com cidade ou estado como null no banco de dados                                |                                                                                                                                                                                                           | Alinhado com a Taci que vamos permitir que esse lead prossiga para qualificação                                                                                                                                                       |
| Para a task de esconder os botões de ação para o filtro default                       | Não foi possível realizar a ocultação, mas foi possível criar um bloqueia que quando o usuário tenta executar uma ação no filtro default ele recebe a mensagem que não pode não poderá executar essa ação |
