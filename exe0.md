# Epic: Integração Pré-Contrato

## Criação de Contrato com Integração Pré-Contrato

### História de Usuário

**COMO** um administrador da transportadora,  
**QUERO** criar um contrato com a funcionalidade de integração pré-contrato,  
**PARA** garantir que os motoristas realizem a integração antes de iniciar o serviço.

### Critérios de Aceitação

#### Cenário 01 - Adicionar Integração ao Contrato

**DADO QUE** estou criando um novo contrato,  
**QUANDO** preencher os detalhes do contrato,  
**ENTÃO** devo ter a opção de selecionar um curso de integração pré-contrato.

#### Cenário 02 - Editar Contrato com Integração

**DADO QUE** selecionei um curso de integração pré-contrato,  
**QUANDO** ao editar o contrato,  
**ENTÃO** o contrato deve incluir o ID do curso de integração selecionado anteriormente.

---

## Candidatura do Motorista no App

### História de Usuário

**COMO** um motorista,  
**QUERO** me candidatar a um contrato com integração pré-contrato,  
**PARA** poder iniciar o serviço após concluir a integração.

### Critérios de Aceitação

#### Cenário 03 - Exibir Modal de Confirmação de Comprometimento

**DADO QUE** estou na tela de detalhes do contrato,  
**QUANDO** clicar no botão "me candidatar",  
**ENTÃO** devo ver um modal de confirmação de comprometimento com a integração pré-contrato.

#### Cenário 04 - Direcionar para Tela de Confirmação de Comprometimento

**DADO QUE** confirmei meu comprometimento,  
**QUANDO** o contrato requer integração,  
**ENTÃO** devo estar candidatado para esse contrato que possui uma integração.

---

## Execução do Curso de Integração

### História de Usuário

**COMO** um motorista,  
**QUERO** realizar o curso de integração pré-contrato,  
**PARA** poder iniciar o serviço.

### Critérios de Aceitação

#### Cenário 05 - Navegar para Tela do Curso

**DADO QUE** estou na tela de contrato em andamento (já foi aceito pela transportadora e liberado pela GR),  
**QUANDO** clicar no botão para iniciar o curso,  
**ENTÃO** devo ser direcionado para a tela do curso.

#### Cenário 06 - Bloquear Botão "Iniciar Serviço" Durante o Curso

**DADO QUE** estou realizando o curso de integração,  
**QUANDO** o curso ainda não foi concluído,  
**ENTÃO** o botão "iniciar serviço" deve permanecer bloqueado.

---

## Liberação do Botão "Iniciar Serviço"

### História de Usuário

**COMO** um motorista,  
**QUERO** ver o botão "iniciar serviço" liberado após concluir a integração,  
**PARA** poder iniciar o serviço e realizar o checklist.

### Critérios de Aceitação

#### Cenário 07 - Exibir Modal de Integração Necessária

**DADO QUE** estou na tela de contrato em andamento,  
**QUANDO** clicar no botão "iniciar serviço" sem concluir a integração,  
**ENTÃO** devo ver um modal informando que o curso de integração é necessário.

#### Cenário 08 - Liberar Botão "Iniciar Serviço"

**DADO QUE** concluí o curso de integração,  
**QUANDO** retornar à tela de contrato em andamento,  
**ENTÃO** o botão "iniciar serviço" deve estar liberado.

---

## Forçar Liberação com `force_enable_contract`

### História de Usuário

**COMO** um administrador da transportadora,  
**QUERO** solicitar a liberação de um contrato sem a conclusão da integração,  
**PARA** permitir que o motorista inicie o serviço em casos excepcionais.

### Critérios de Aceitação

#### Cenário 09 - Solicitar Liberação do Contrato

**DADO QUE** sou um administrador da transportadora,  
**QUANDO** entrar em contato com a motorista PX,  
**ENTÃO** a motorista PX deve forçar a liberação do contrato por dentro da Torre.

#### Cenário 10 - Atualizar Status do Contrato e Liberar Botão "Iniciar Serviço"

**DADO QUE** a motorista PX forçou a liberação do contrato,  
**QUANDO** o contrato for atualizado,  
**ENTÃO** o status do contrato deve refletir que a liberação foi forçada  
**E** o botão "iniciar serviço" deve estar liberado para o motorista, mesmo sem a conclusão da integração.

---

## Histórico de Contrato

### História de Usuário

**COMO** um motorista,  
**QUERO** ver o status da integração no histórico de contrato,  
**PARA** saber se posso anexar a nota fiscal.

### Critérios de Aceitação

#### Cenário 11 - Bloquear Anexação de Nota Fiscal

**DADO QUE** a transportadora forçou a liberação do contrato e pude iniciar o serviço sem ter feito a integração, também finalizei o serviço e já estou na tela de histórico de contratos,  
**QUANDO** tentar anexar uma nota fiscal sem concluir a integração,  
**ENTÃO** devo ver um modal alertando que devo concluir a integração antes de anexar a nota fiscal  
**E** o botão de anexar nota fiscal deve permanecer bloqueado até a conclusão da integração.

#### Cenário 12 - Exibir Botão "Acessar Integração"

**DADO QUE** estou na tela de histórico de contrato,  
**QUANDO** visualizar um contrato que foi liberado sem a conclusão da integração,  
**ENTÃO** devo ver um botão "Acessar integração" que direciona ao curso de integração necessário para anexar a nota fiscal.

#### Cenário 13 - Liberar Botão "Anexar Nota Fiscal"

**DADO QUE** concluí o curso de integração,  
**QUANDO** retornar à tela de histórico de contratos,  
**ENTÃO** o botão de anexar nota fiscal deve estar liberado.

---

## Instructions

### História de Usuário

**COMO** um administrador da transportadora,  
**QUERO** selecionar uma integração pré-contrato como template na criação de uma operação,  
**PARA** garantir que a integração seja aplicada automaticamente ao criar um contrato.

### Critérios de Aceitação

#### Cenário 14 - Selecionar Integração na Criação de Operação

**DADO QUE** estou criando uma nova operação,  
**QUANDO** preencher os detalhes da operação,  
**ENTÃO** devo ter a opção de selecionar um curso de integração pré-contrato como template.

#### Cenário 15 - Editar Operação com Integração

**DADO QUE** selecionei um curso de integração pré-contrato na criação da operação,  
**QUANDO** editar a operação,  
**ENTÃO** a operação deve incluir o ID do curso de integração selecionado anteriormente.

#### Cenário 16 - Aplicar Template de Operação na Criação de Contrato

**DADO QUE** estou criando um novo contrato,  
**QUANDO** selecionar um template de operação que possui uma integração pré-contrato,  
**ENTÃO** o contrato deve automaticamente incluir o ID do curso de integração selecionado no template.
