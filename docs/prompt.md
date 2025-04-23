# Prompt para Conversão de Texto em BDD

**Instruções:**  
Converta o texto fornecido abaixo para o formato BDD (Behavior-Driven Development), seguindo rigorosamente a estrutura e padrões descritos.

---

## Formato Esperado da Saída:

### Links Relacionados

**Base URL:** [Inserir URL base da aplicação]  
**Páginas:**

- [Nome da Página 1] : [Base_url/URL_1]
- [Nome da Página 2] : [Base_url/URL_2]

### # Contexto

[Descreva brevemente o objetivo geral da funcionalidade ou recurso em linguagem simples e direta.]

### História de Usuário

**COMO** [papel do usuário]  
**QUERO** [ação desejada]  
**PARA** [motivo/benefício]

### Critérios de Aceitação

#### Cenário [Número Ordenado] - [Título Descritivo]

**DADO QUE** [pré-condição]  
**QUANDO** [ação do usuário/sistema]  
**ENTÃO** [resultado esperado]  
**E** [complemento opcional]

---

## Regras Obrigatórias:

1.  **Nomenclatura de Usuários:**

    - `AcademiaPx-Student` = Usuário estudante do painel da academia-px.
    - `AcademiaPx-Admin` = Usuário administrador (empresa) do painel da academia-px.
    - `AcademiaPx-TowerOperator` = Usuário operador do painel da torre-academia.
    - `TransportadoraPx-PanelUser` = Usuário do painel da transportadora.
    - `TransportadoraPx-TowerOperator` = Usuário operador da torre-core.
    - `MotoristaPx-Driver` = Usuário motorista utilizando o aplicativo.

2.  **Links:**

    - `AcademiaPx-Student`: `https://staging-academy-px.motoristapx.vercel.app`
    - `AcademiaPx-Admin`: `https://staging-academy-px.motoristapx.vercel.app`
    - `AcademiaPx-TowerOperator`: `https://academia-stg.px.center/nova`
    - `TransportadoraPx-PanelUser`: `https://staging-px-painel.motoristapx.vercel.app`
    - `TransportadoraPx-TowerOperator`: `https://staging.motoristapx.com.br/torrepx`
    - `MotoristaPx-Driver`: (telas do aplicativo)

    - Incluir sempre que relevante
    - Adicionar URLs específicas de páginas sob a seção **Links Relacionados**.

3.  **Ordenação de Cenários:**

    - Renumerar cenários sequencialmente (ex: Cenário 01, 02, 03) mesmo após adições/remoções.

4.  **Clareza:**

    - Evitar jargões técnicos no **Contexto**.
    - Usar verbos no infinitivo (ex: "selecionar", "visualizar").

5.  **Links Dinâmicos:**
    - Caso o link contenha um número ou identificador dinâmico, substituí-lo por `@dynamic@`.
      - Exemplo:  
        `https://staging-academy-px.motoristapx.vercel.app/contracts/123/update`  
        deve ser convertido para:  
        `- Atualização de Contrato (@dynamic@): https://staging-academy-px.motoristapx.vercel.app/contracts/@dynamic@/update`

---

## Exemplo de Saída:

```
# [Nome do Recurso/Funcionalidade]

### Links Relacionados

**Base URL:** https://staging-academy-px.motoristapx.vercel.app
**Páginas:**

- Criação de Contrato: https://staging-academy-px.motoristapx.vercel.app/contracts/new
- Histórico de Contratos: https://staging-academy-px.motoristapx.vercel.app/contracts/history
- Atualização de Contrato (@dynamic@): https://staging-academy-px.motoristapx.vercel.app/contracts/@dynamic@/update

### Contexto

Garantir que motoristas concluam a integração pré-contrato antes de iniciar serviços, com flexibilidade para liberação excepcional.

### História de Usuário
**COMO** um MotoristaPx-Driver,
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

#### Cenário 5 - Atualizar Status do Contrato e Liberar Botão "Iniciar Serviço"

**DADO QUE** a motorista PX forçou a liberação do contrato,
**QUANDO** o contrato for atualizado,
**ENTÃO** o status do contrato deve refletir que a liberação foi forçada
**E** o botão "iniciar serviço" deve estar liberado para o motorista, mesmo sem a conclusão da integração.
```

---

**Texto para Conversão:**

Projeto-Usuário: [Insira aqui o tipo de usuário]
Para inserir o usuário, consulte a seção [## Regras Obrigatórias - Nomenclatura de Usuários](#regras-obrigatórias) .

[Insira aqui o texto a ser convertido para BDD]
