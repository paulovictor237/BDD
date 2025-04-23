# Prompt para Conversão de Texto em BDD

**Instruções:**  
Converta o texto fornecido abaixo para o formato BDD (Behavior-Driven Development), seguindo rigorosamente a estrutura e padrões descritos.

---

## Formato Esperado da Saída:

### Links Relacionados

**Base URL:** [Inserir URL base da aplicação]  
**Páginas:**

- [Nome da Página 1]: [Base_url/URL_1]
- [Nome da Página 2]: [Base_url/URL_2]

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

1. **Nomenclatura de Usuários:**

   - `Estudante` = Usuário do painel da academia-px.
   - `Administrador` = Usuário empresa do painel da academia-px.
   - `Operador` = Usuário operador do painel do Nova/Laravel.

2. **Links:**

   - Incluir sempre que relevante:
     - Estudante/Administrador: `https://staging-academy-px.motoristapx.vercel.app`
     - Operador: `https://academia-stg.px.center/nova`
   - Adicionar URLs específicas de páginas sob a seção **Links Relacionados**.

3. **Ordenação de Cenários:**

   - Renumerar cenários sequencialmente (ex: Cenário 01, 02, 03) mesmo após adições/remoções.

4. **Clareza:**

   - Evitar jargões técnicos no **Contexto**.
   - Usar verbos no infinitivo (ex: "selecionar", "visualizar").

5. **Links Dinâmicos:**
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

### # Contexto

Garantir que motoristas concluam a integração pré-contrato antes de iniciar serviços, com flexibilidade para liberação excepcional.

### História de Usuário

**COMO** Administrador
**QUERO** forçar a liberação de um contrato sem integração concluída
**PARA** permitir início imediato do serviço em casos urgentes.

### Critérios de Aceitação

#### Cenário 01 - Solicitar Liberação Forçada

**DADO QUE** sou um Administrador autenticado
**QUANDO** acesso a página de detalhes do contrato
**ENTÃO** devo ver a opção "Forçar Liberação"
**E** receber uma confirmação via e-mail.
```

---

**Texto para Conversão:**

[Insira aqui o texto a ser convertido para BDD]
