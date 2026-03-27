# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: Murilo Nogueira Avarino
RA: 24000605
Data: 26/03/2026  

---

# 1. Definição do MVP

"Meu MVP cobre o processo de operações diárias da rede de farmácias Saúde & Vida, desde a operação de vendas/atendimento ao cliente, controle de estroque com cadastro de produtos com seus saldos em estoque, com base em uma movimentação automática por saida de vendas e entradas por compras, incluindo então gestão de compra, permitindo entrada de notas de compra por XML, facilitando o cadastro e alimentação de saldo facilitada de produtos, com controles de cadastro de Fornecedores/Fabricantes, Gestão Financeira de Contas a Receber geradas a partir de vendas a prazo e Contas a Pagar geradas a partir das compras lançadas, relatórios geranciais com filtros e controle de usuários de acesso com suas permissões definidas por perfis."

O que está **dentro** do MVP:
- Cadastro, Edição e Consultas de Clientes
- Cadastro Manual, Edição, Consultas e Ajuste de Saldo de Produtos
- Controle de Estoque por Setor
- PDV Rápido para Operações de balcão
- Lançamento de Vendas A prazo e A vista (com baixa automática dos produtos no estoque)
- Vendas A prazo geram contas a receber automática conforme condição de pagamento definida
- Impressão de Comprovante de Venda
- Emissão de NFC-e
- Consulta e Recebimentos de Contas a Receber
- Impressão de Recibos
- Cadastro Manual, Edição e Consultas de Fornecedores
- Lançamento Manuel de Compras (com entrada automática dos produtos no estoque)
- Lançamento Manual de Contas a Pagar
- Consulta e Pagamentos de Contas a Pagar
- Relatórios Simplificados de Estoque, Vendas por Periodo, Contas a Receber, Contas a Pagar e Compras por Período
- Cadastro de Usuários e Senhas
- Perfis de Usuários com definições de permissões de ações no sistema
- Auditoria de Sistema para identificar ações entre usuários

O que está **fora** do MVP 
- Consulta CNPJ para Cadastro automático de Clientes/Fornecedores PJ
- Entrada de Nota de Compra por XML permitindo cadastro e atualização de produtos automático direto da nota de compra
- Relatórios e Dashboards detalhados perante todas funcionalidades do sistema permitindo uma gama diferente de filtros

Eu fiz essas escolhas definindo colocar dentro do MVP, ações que são prioridades para já implantarmos o sistema para operar nas unidades, já fora do MVP, eu deixei funcionalidades que irão auxiliar na operação, porém que sem elas o funcionamento mantém o mesmo, então o desenvolvimento delas não é de tanta urgência.

---

# 2. Regras de Negócio

**RN01 — Baixa automática de Estoque a partir do fechamento de Vendas**
Toda venda realizada (à vista ou a prazo) deve gerar automaticamente a baixa da quantidade correspondente dos produtos no estoque da unidade.

**RN02 — Atualização automática de Estoque a partir do lançamento de Compras**  
Toda compra lançada no sistema deve atualizar automaticamente o estoque, somando as quantidades dos produtos adquiridos na compra no saldo atual deles em estoque.

**RN03 — Obrigatoriedade de cliente para venda a prazo**  
Vendas à Vista podem ser realizadas sem identificação do consumidor final, porém para realizar uma venda a prazo, o cliente deve estar previamente cadastrado no sistema (no minímo o nome).

**RN04 — Geração automática de contas a receber**
Vendas realizadas a prazo devem gerar automaticamente uma conta a receber, respeitando a condição de pagamento definida (parcelas, datas de vencimento e valores).

**RN05 — Geração automática de contas a pagar**  
Toda compra registrada deve gerar automaticamente uma conta a pagar, contendo valor total, fornecedor e data de vencimento.

**RN06 — Controle de status financeiro**
Contas a pagar e contas a receber devem possuir status atualizados automaticamente conforme sua situação; Aberta, Paga/Recebida, Vencida (quando ultrapassar a data de vencimento sem quitação)

**RN07 — Controle de permissões por perfil**
O sistema deve restringir funcionalidades conforme as permissões de ações definadas no perfil vinculado ao usuário (ex: atendente, alomxarifado, financeiro, administrador), impedindo acesso a operações não autorizadas.

**RN08 — Registro de auditoria**  
Todas as operações críticas (vendas, exclusões, alterações de cadastro, pagamentos e recebimentos) devem ser registradas em log de auditoria, identificando usuário, data e ação realizada.

---

# 3. Requisitos Funcionais

**RF01 — Gerenciar Cadastros de clientes**
O sistema deve permitir o cadastro, edição, consulta, extrato e histórico de clientes.

**RF02 — Gerenciar produtos**
O sistema deve permitir o cadastro manual, edição, consulta e ajuste de saldo e preços de produtos, incluindo informações como descrição, preço, unidade de medida e fabricante/fornecedor.

**RF03 — Controlar estoque por setor**
O sistema deve controlar o estoque dos produtos por setor, mantendo quantidades atualizadas conforme movimentações de entrada e saída.

**RF04 — Operação rápida no PDV**  
O sistema deve permitir a realização de cadastro de novos clientes, busca rápida de produtos, lançamentos de vendas e recebimentos de contas no PDV tornando a operção rápido, possibilitando visualização e filtros de dados, alterações rápidas, definição de quantidades e cálculo automático do total.

**RF05 — Forma de Pagamentos de vendas à vista e a prazo**
O sistema deve obrigar a seleção de um meio de pagamento (DINHEIRO, CARTÃO DÉBITO, CARTÃO CRÉDITO, PIX E A PRAZO) para o fechamento da venda, que será definida ser uma venda à vista ou a prazo, conforme escolha do usuário operante.

**RF06 — Atualizar estoque automaticamente** 
O sistema deve atualizar automaticamente o estoque dos produtos após o fechamento de uma venda ou lançamento de compra.

**RF07 — Gerar contas a receber** 
O sistema deve gerar automaticamente registros de contas a receber para vendas realizadas a prazo, conforme condições de pagamento definidas.

**RF08 —Consultar e receber contas a receber**  
O sistema deve permitir a consulta de contas a receber e o registro de seus recebimentos, atualizando status e datas de pagamento.

---

# 🛡 4. Requisitos Não Funcionais

**RNF01 — Desempenho no atendimento (PDV)** 
O sistema deve responder às operações do PDV (adição de produtos, cálculo de total e finalização da venda) em no máximo 2 segundos, garantindo agilidade no atendimento ao cliente.

**RNF02 — Disponibilidade do sistema** 
O sistema deve estar disponível para uso no mínimo 99% do tempo durante o horário comercial, garantindo continuidade das operações nas unidades, prevendo envetualidades de quedas de rede, possibilitanto uma migração rápida para funcionamento desktop com banco local, caso precise rodar off-line.

**RNF03 — Segurança de acesso**  
O sistema deve garantir autenticação por login e senha, além de controle de acesso baseado em perfis, impedindo que usuários acessem funcionalidades não autorizadas.

**RNF04 — Integridade dos dados** 
O sistema deve garantir que os dados de vendas, estoque e financeiro sejam consistentes, evitando perdas ou divergências mesmo em casos de falhas.

---

# 5. Casos de Uso

- **UC01 - Realizar Venda**
- **UC02 - Finalizar Venda**
- **UC03 - Consultar Produto**
- **UC04 - Verificar Estoque**
- **UC05 - Atualizar Estoque**
- **UC06 - Gerar Contas a Receber**
- **UC07 - Registrar Compra**
- **UC08 - Gerar Contas a Pagar**
- **UC09 - Receber Pagamento**
- **UC10 - Realizar Pagamento**
- **UC11 - Identificar Cliente**
- **UC12 - Emitir Comprovante**

**Includes:**

- Venda inclui:
  - Identificar Cliente
  - Consultar Produto
  - Verificar Estoque
  - Finalizar Venda

- Compra inclui:
  - Atualizar Estoque
  - Gerar Contas a Pagar

- Finalização inclui:
  - Emitir Comprovante
 
**Extends:**

- Cadastrar Cliente → só se cliente não existir
- Gerar Contas a Receber → só se venda for a prazo
- Emitir NFC-e → pode ou não ocorrer dependendo da operação

---

# 6. Documentação dos Casos de Uso
---

## **UC01 — Realizar Venda**
**Ator(es): Atendente**  
**Descrição: Permite ao atendente registrar uma venda de produtos para um cliente.**  
**Pré-condições: Sistema ativo e produtos cadastrados.**  
**Pós-condições: Venda registrada, estoque atualizado e comprovante emitido.**  

### Fluxo Principal
1. Atendente inicia uma nova venda 
2. Sistema solicita identificação do cliente
3. Atendente informa cliente
4. Sistema permite busca de produtos
5. Atendente adiciona produtos e quantidades
6. Sistema verifica disponibilidade em estoque
7. Atendente finaliza a venda
8. Sistema registra a venda e atualiza o estoque
9. Sistema emite comprovante

### Fluxos Alternativos / Exceções
- FA01 — Cliente não cadastrado
  → Sistema permite cadastro do cliente
- FA02 — Estoque insuficiente
  → Sistema informa indisponibilidade e impede a venda

### Relacionamentos
- **Include:** Identificar Cliente, Consultar Produto, Verificar Estoque, Finalizar Venda 
- **Extend:** Cadastrar Cliente  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

--- <img width="308" height="596" alt="image" src="https://github.com/user-attachments/assets/8e7044fb-a94c-4841-89a9-a2f302406d27" />

## **UC02 — Finalizar Venda**
**Ator(es): Atendente**  
**Descrição: Finaliza a venda registrando pagamento e concluindo a operação.**  
**Pré-condições: Venda em andamento com itens adicionados.**  
**Pós-condições: Venda concluída e registrada no sistema.**  

### Fluxo Principal
1. Atendente seleciona finalizar venda
2. Sistema apresenta total da venda
3. Atendente escolhe forma de pagamento
4. Sistema confirma operação
5. Sistema registra venda

### Fluxos Alternativos / Exceções
- FA01 — Venda a prazo
  → Sistema gera contas a receber
- FA02 — Emissão fiscal
  → Sistema emite NFC-e

### Relacionamentos
- **Include:** Emitir Comprovante
- **Extend:** Gerar Contas a Receber, Emitir NFC-e  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

--- <img width="200" height="599" alt="image" src="https://github.com/user-attachments/assets/624f4dce-bac3-4faa-b42f-6e7669b44291" />

## **UC03 — Consultar Produto**
**Ator(es): Usuários com Permissão**  
**Descrição: Permite consultar produtos cadastrados no sistema.**  
**Pré-condições: Produto deve estar cadastrado.**  
**Pós-condições: Produto localizado e exibido ao usuário.**  

### Fluxo Principal
1. Usuário informa nome, código ou fabricante do produto
2. Sistema realiza busca
3. Sistema exibe lista de produtos encontrados
4. Usuário seleciona produto desejado

### Fluxos Alternativos / Exceções
- FA01 — Produto não encontrado
  → Sistema informa que não há resultados
- FA02 — Erro na busca
  → Sistema exibe mensagem de erro

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

--- <img width="309" height="312" alt="image" src="https://github.com/user-attachments/assets/5d6b0f7c-becf-454f-80b8-ac838dadaf88" />

## **UC04 — Verificar Estoque**
**Ator(es): Sistema**  
**Descrição: Verifica a disponibilidade de um produto no estoque.**  
**Pré-condições: Produto deve existir.**  
**Pós-condições: Disponibilidade informada.**  

### Fluxo Principal
1. Sistema recebe produto e quantidade
2. Sistema consulta estoque
3. Sistema valida disponibilidade
4. Sistema retorna status

### Fluxos Alternativos / Exceções
- FA01 — Estoque insuficiente
  → Sistema retorna indisponibilidade
- FA02 — Produto inexistente
  → Sistema informa erro

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

--- <img width="292" height="312" alt="image" src="https://github.com/user-attachments/assets/8020bd00-20d3-4eb9-af40-141d72542be4" />

## **UC05 — Atualizar Estoque**
**Ator(es): Sistema, Almoxarifado**  
**Descrição: Atualiza o estoque com base em entradas ou saídas.**  
**Pré-condições: Produto existente.**  
**Pós-condições: Estoque atualizado.**  

### Fluxo Principal
1. Sistema identifica movimentação
2. Sistema calcula nova quantidade
3. Sistema atualiza estoque
4. Sistema registra log

### Fluxos Alternativos / Exceções
- FA01 — Erro na atualização
  → Sistema mantém valor anterior
- FA02 — Produto inexistente
  → Sistema bloqueia operação

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

--- <img width="179" height="303" alt="image" src="https://github.com/user-attachments/assets/920f2b42-1100-4f9f-b725-d135e4dfb5d8" />

## **UC06 — Gerar Contas a Receber**
**Ator(es): Sistema**  
**Descrição: Gera contas a receber a partir de vendas a prazo.**  
**Pré-condições: Venda a prazo finalizada.**  
**Pós-condições: Conta registrada no sistema.**  

### Fluxo Principal
1. Sistema identifica venda a prazo
2. Sistema calcula parcelas
3. Sistema define vencimentos
4. Sistema registra contas a receber

### Fluxos Alternativos / Exceções
- FA01 — Erro no cálculo
  → Sistema cancela geração
- FA02 — Dados inválidos
  → Sistema solicita correção

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

--- <img width="174" height="303" alt="image" src="https://github.com/user-attachments/assets/1a81dafd-52a6-4b11-afdf-a46bd72f27bf" />

## **UC07 — Registrar Compra**
**Ator(es): Gerente**  
**Descrição: Permite registrar compras de fornecedores.**  
**Pré-condições: Fornecedor cadastrado.**  
**Pós-condições: Compra registrada e estoque atualizado.**  

### Fluxo Principal
1. Gerente informa fornecedor
2. Gerente adiciona produtos
3. Sistema calcula total
4. Sistema registra compra

### Fluxos Alternativos / Exceções
- FA01 — Fornecedor inválido
  → Sistema bloqueia operação
- FA02 — Produto inexistente
  → Sistema solicita correção

### Relacionamentos
- **Include:** Atualizar Estoque, Gerar Contas a Pagar

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

--- <img width="158" height="413" alt="image" src="https://github.com/user-attachments/assets/987dfbbf-7876-409b-8e9c-16165862f4f9" />

## **UC08 — Gerar Contas a Pagar**
**Ator(es): Sistema**  
**Descrição: Gera contas a pagar a partir de compras.**  
**Pré-condições: Compra registrada.**  
**Pós-condições: Conta registrada.**  

### Fluxo Principal
1. Sistema identifica compra
2. Sistema define vencimento
3. Sistema registra conta

### Fluxos Alternativos / Exceções
- FA01 — Erro no registro
  → Sistema cancela operação
  
### Relacionamentos
- **Extend:** Registrar Compra

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

--- <img width="144" height="248" alt="image" src="https://github.com/user-attachments/assets/84b0dbcf-5d30-4b37-b55c-7a4455b63852" />

## **UC09 — Receber Pagamento**
**Ator(es): Financeiro, Atendente**  
**Descrição: Permite registrar recebimento de contas.**  
**Pré-condições: Conta a receber existente.**  
**Pós-condições: Conta atualizada para recebida.**  

### Fluxo Principal
1. Usuário consulta contas
2. Usuário seleciona conta
3. Sistema registra recebimento
4. Sistema atualiza status

### Fluxos Alternativos / Exceções
- FA01 — Conta inexistente
  → Sistema informa erro
- FA02 — Valor divergente
  → Sistema solicita confirmação

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

--- <img width="165" height="303" alt="image" src="https://github.com/user-attachments/assets/8bee058c-976c-4e33-9970-8485ac3321d9" />

## **UC10 — Realizar Pagamento**
**Ator(es): Financeiro**  
**Descrição: Permite registrar pagamento de contas a pagar.**  
**Pré-condições: Conta a pagar existente.**  
**Pós-condições: Conta atualizada para paga.**  

### Fluxo Principal
1. Usuário consulta contas
2. Usuário seleciona conta
3. Sistema registra pagamento
4. Sistema atualiza status

### Fluxos Alternativos / Exceções
- FA01 — Conta inexistente
  → Sistema informa erro
- FA02 — Pagamento inválido
  → Sistema bloqueia ação


### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

--- <img width="159" height="303" alt="image" src="https://github.com/user-attachments/assets/14d607a2-a1b6-4278-8df1-9564a00124f2" />











