### História de Usuário

**EU COMO** analista de cadastro da empresa, com permissão de edição no menu Cadastro da Torre  
**QUERO** um fluxo estruturado na ferramenta Torre para validar as atualizações cadastrais  
**PARA** eu possa validar se as informações atualizadas estão conforme os requisitos, acompanhar o status das tratativas e garantir a qualidade do processo

### Critérios de Aceitação

#### Cenário 01 - Adicionar ação Informar Impedimento

**DADO QUE** acesso a página Cadastro → Atualização Cadastral  
**E** selecionar um ou mais registros na tabela  
**QUANDO** acionar a opção “Ações”  
**ENTÃO** observo a opção “Informar Impedimento”

#### Cenário 02 - Comportamento da ação Informar Impedimento

**DADO QUE** selecionar um ou mais registros na tabela da pagina Atualização Cadastral  
**QUANDO** selecionar “Informar Impedimento" em mais “Ações”  
**ENTÃO** observo uma modal com as seguintes informações:

| Campos                                                 | Conteúdo em tela                              | Comportamento                                                                                                                                                                                                                                                                                                                                                                                                    |
| ------------------------------------------------------ | --------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Título da modal                                        | Informar Impedimento                          | Nenhum                                                                                                                                                                                                                                                                                                                                                                                                           |
| Texto de confirmação sobre a ação                      | Tem certeza de que deseja executar esta ação? | Nenhum                                                                                                                                                                                                                                                                                                                                                                                                           |
| Campo para informar um texto livre sobre o impedimento | Observação                                    | Campo obrigatório<br> Permitir adicionar texto, manter quantidade de caracteres padrão da Torre para este tipo de campo<br> Ser possível Editar o campo Observação                                                                                                                                                                                                                                               |
| CTA para confirmar a ação                              | Executar ação                                 | Alterar o status do registro para “Impedimento”<br> Adicionar o campo Observação e o conteúdo informado na visualização do registro<br> Caso o campo não for preenchido e confirmado a execução, apresentar o campo em destaque com o texto “**O campo Observação é obrigatório.**"<br> O campo Observação sendo preenchido, apresentar confirmação em tela com o texto “**Impedimento informado com sucesso.**" |
| CTA para Cancelar a ação                               | Cancelar                                      | Fechar a modal<br> Não registrar as informações do campo Observação                                                                                                                                                                                                                                                                                                                                              |

#### Cenário 03 - Adicionar ação “Enviar para Validação”

**DADO QUE** acesso a página Cadastro → Atualização Cadastral  
**E** selecionar um ou mais registros na tabela  
**QUANDO** acionar a opção “Ações”  
**ENTÃO** observo a opção “Enviar para Validação”

#### Cenário 04 - Comportamento da ação Enviar para Validação

**DADO QUE** selecionar um ou mais registros na tabela da pagina Atualização Cadastral  
**QUANDO** selecionar “Enviar para validação" em mais “Ações”  
**ENTÃO** observo uma modal com as seguintes informações:

| Informações             | Conteúdo em tela                              | Comportamento                                                                                                                                                                                                                                                                                                                                                         |
| ----------------------- | --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Título                  | Enviar para Validação Cadastral               | Nenhum                                                                                                                                                                                                                                                                                                                                                                |
| Mensagem de confirmação | Tem certeza de que deseja executar esta ação? | Nenhum                                                                                                                                                                                                                                                                                                                                                                |
| CTA de confirmação      | Executar ação                                 | - Apresentar os registros na página “Validação de Prestadores” com status de página “Pendente"<br> - Manter os status como “Qualificado"<br> - Alterar a etapa dos registros para “Atualização Cadastral”<br> - Ocultar os registros da página “Atualização Cadastral”<br> - Apresentar mensagem de confirmação em tela com o texto "**Ação executada com sucesso!**“ |
| CTA de cancelamento     | Cancelar                                      | - Fechar a modal<br> - Não executar a ação iniciada.                                                                                                                                                                                                                                                                                                                  |

**Etapa Atualização Cadastral na página Validação de Prestadores**

Esta etapa deve ser criada considerando não fazer para do fluxo de qualificação (automações) mas sim, ser uma etapa do fluxo independente criada para validar o fluxo de Atualização Cadastral.

#### Cenário 05 - Informações do registro a serem listadas na página Validação de Prestadores

**DADO QUE** acesso a página Validação de Prestadores  
**QUANDO** visualizar um registro na etapa “Atualização Cadastral"  
**ENTÃO** observo foi criado um novo registro nesta página (novo ID)  
**E** as informações de cada coluna foram preenchida conforme padrão da página

#### Cenário 06 - Adicionar o motivo da Atualização Cadastral na visualização da página Validação de Prestadores

**DADO QUE** acesso a página Validação de Prestadores  
**E** observo na listagem os registros com a “Etapa 5 - Atualização Cadastral"  
**QUANDO** visualizar as informações na coluna “Motivo da Atualização cadastral"  
**ENTÃO** observo os gatilhos identificados pelo Job de requalificação de prestadores, apenas para os registros com a “Etapa 5 - Atualização Cadastral” apresentados por escrito limitados a 25 caracteres  
**E** os registros que ultrapassarem 25 caractares, apresentar três pontos no final, informando que tem mais informações  
**E** ao posicionar o mouse sobre a informação que ultrapassou esta quantidade, apresentar um _tooltip_ com o texto completo

**Considerar o mesmo comportamento da coluna “Motivo da Atualização cadastral" nas de “Observação” e "Motivos”.**

#### Cenário 07 - Comportamento ao Aprovar qualificação na página Validação de Prestadores

**DADO QUE** acesso a página “Validação de Prestadores”  
**QUANDO** aprovar a qualificação de um ou mais registros na “Etapa 5 - Atualização Cadastral"  
**ENTÃO** observo a apresentação da modal de confirmação de execução  
**E** devo selecionar se teve a atuação de um Cadex nesta validação (devo pagar o Cadex)  
**E** dever ser possível executar a ação conforme comportamento padrão do fluxo de qualificação  
**E** apresentar a mensagem de confirmação em tela com o texto "**Qualificações de motoristas verificadas com sucesso!**“

#### Cenário 08 - Comportamento do fluxo de Validação ao Aprovar qualificação na página Validação de Prestadores

**DADO QUE** acesso a página Validação de Prestadores  
**QUANDO** aprovar a qualificação de um ou mais registros na “Etapa 5 - Atualização Cadastral"  
**ENTÃO** observo que o registro foi **oculto** da página “Validação de Prestadores”  
**E** os registros foram apresentados na página “Atualização Cadastral”  
**E** o status da página deve ser alterado para “Concluído”  
**E** exibir a data da conclusão no formato “DD/MM/AAAA"

**Automação do status de página Concluído na página Atualização Cadastral**

Ao passar um registro para o status de página “Concluído", a etapa da jornada é alterada para “Disponível". Esta automação deve continuar funcionando para estes registros vindos da validação cadastral.

#### Cenário 09 - Comportamento ao Reprovar qualificação na página Validação de Prestadores

**DADO QUE** acesso a página “Validação de Prestadores”  
**QUANDO** reprovar a qualificação de um ou mais registros na “Etapa 5 - Atualização Cadastral"  
**ENTÃO** observo a apresentação da modal de confirmação de execução  
**E** deve ser possível selecionar um motivo para esta reprovação (Nova lista de motivos abaixo)  
**E** devo selecionar se teve a atuação de um Cadex nesta validação (devo pagar o Cadex)  
**E** dever ser possível executar a ação conforme comportamento padrão do fluxo de qualificação  
**E** apresentar a mensagem de conformação em tela com o texto "**Qualificações de motoristas reprovadas com sucesso!**“

**Lista de motivos de reprovação da Atualização Cadastral**

| Motivo da reprovação                          |
| --------------------------------------------- |
| Sem foto de perfil                            |
| Sem comprovante de endereço                   |
| Sem CTPS                                      |
| Sem anexo CCMEI                               |
| Endereço cadastrado divergente do comprovante |
| Documentos em nome de outro prestador         |
| Sem arquivos em anexo                         |
| Sem foto da CNH                               |
| Sem RG                                        |
| Sem pesquisa "Verificar CPF"                  |
| Sem endereço no novo campo de endereço        |
| Sem comprovação de saída da atual empresa     |
| Comprovante de endereço vencido               |
| Comprovante de endereço fora do padrão        |
| Comprovante de endereço ilegível              |
| CNH ilegível                                  |
| CNH sem EAR                                   |
| CNH vencida                                   |
| Sem consulta BIG                              |

#### Cenário 10 - Comportamento do fluxo de Validação ao Reprovar qualificação na página Validação de Prestadores

**DADO QUE** acesso a página Validação de Prestadores  
**QUANDO** reprovar a qualificação de um ou mais registros na “Etapa 5 - Atualização Cadastral"  
**ENTÃO** observo que o registro foi **oculto** da página “Validação de Prestadores”  
**E** os registros foram apresentados na página “Atualização Cadastral”  
**E** o status da página deve ser alterado para “Em andamento”  
**E** o responsável deve ser preenchido com o nome do operador que enviou para validação  
**E** apresentar o motivo da reprovação separados com ponto e vírgula (;) como uma tratativa na visualização do registra na página Atualização Cadastral da seguinte forma "Reprovado: Motivo da reprovação1; Motivo 2…”

#### Cenário 11 - Adicionar filtro “Por status” na página Atualização Cadastral

**DADO QUE** acesso a página “Atualização Cadastral"  
**QUANDO** acessar o Filtro Avançado  
**ENTÃO** observo uma opção com o título “Por Status"

#### Cenário 12 - Comportamento do filtro “Por status” na página Atualização Cadastral

**DADO QUE** acesso o Filtro Avançado na página “Atualização Cadastral"  
**QUANDO** clicar no campo  
**ENTÃO** deve apresentado os status da página como opções (Pendente, Em andamento, Impedimento e Concluído)  
**E** ser possível selecionar uma ou mais opções  
**E** deve ser apresentado na listagem apenas os registros que atentem os status selecionados

#### Cenário 13 - Adicionar filtro “Por Cadex” na página Atualização cadastral

**DADO QUE** acesso a página “Atualização Cadastral"  
**QUANDO** acessar o Filtro Avançado  
**ENTÃO** observo uma opção com o título “Por Cadex"

#### Cenário 14 - Comportamento do filtro “Por Cadex” na página Atualização Cadastral

**DADO QUE** acesso o Filtro Avançado na página “Atualização Cadastral"  
**QUANDO** clicar no campo  
**ENTÃO** deve apresentado o nome completo dos usuários como opção (Listagem de alterar responsável)  
**E** ser possível selecionar um ou mais opções por vez  
**E** deve ser apresentado na listagem apenas os registros que atentem o nome selecionado

#### Cenário 15 - Remover campo Status da edição do registro na página Atualização Cadastral

**DADO QUE** acesso a página “Atualização Cadastral"  
**QUANDO** edito algum registro  
**ENTÃO** não deve observar o campo Status

#### Cenário 16 - Adicionar a etapa Atualização Cadastral no filtro da página Validação de Prestadores

**DADO QUE** acesso a página “Validação de Prestadores"  
**E** acessar o Filtro Avançado  
**QUANDO** clicar para ver as opções de “Etapa”  
**ENTÃO** observo a opção “Atualização Cadastral"

#### Cenário 17 - Adicionar filtro "Motivos da Atualização cadastral" na página Validação de Prestadores

**DADO QUE** acesso a página “Validação de Prestadores"  
**E** acessar o Filtro Avançado  
**QUANDO** clicar para ver as opções  
**ENTÃO** observo a opção “Motivos da Atualização Cadastral"  
**E** exibir os gatilhos da Atualização cadastral como opção para filtrar em conjunto com os demais filtros (Mesmo filtro “Por Motivo" apresentado na página Atualização Cadastral)

- **Environment**:
- **Key**: AQ-15
- **Summary**: [Torre] Criar fluxo de validação cadastral
- **Type**: História
- **Parent**: AQ-6
- **Priority**: Medium
- **Status**: Conclu

```

```
