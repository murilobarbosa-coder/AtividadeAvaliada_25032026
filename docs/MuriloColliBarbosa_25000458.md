# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: *Murilo Colli Barbosa*  
RA: *25000458*  
Data: *25/03/2026*  

---

# 1. Definição do MVP

Meu MVP cobre o processo de venda, desde o cadastro ou identificação do cliente até a emissão do comprovante, incluindo consulta de produtos, verificação de estoque, registro da venda e geração de contas a receber em caso de pagamento a prazo. Ficam de fora funcionalidades como gestão de compras, contas a pagar, relatórios avançados, controle de múltiplas unidades e permissões detalhadas. Essas escolhas foram feitas para focar no fluxo principal do negócio, que é a venda, garantindo valor imediato, menor complexidade e facilidade de validação inicial do sistema.

---

# 2. Regras de Negócio

**RN01 — Venda condicionada ao estoque**

A venda de um determinado produto só pode ser realizada quando constar o suficiente do produto em questão no estoque da farmácia, caso contrário a venda será bloqueada. 

**RN02 — Atualização automática de estoque**

Toda venda realizada deve descontar o valor referente do produto no estoque da farmácia, sem a necessiadade de intervenção manual.

**RN03 — Geração automática de contas a receber**

Toda venda realizada a prazo deve gerar automaticamente um lançamento em contas a receber, com valor, vencimento e status inicial como “Aberta”.

**RN04 — Geração automática de contas a pagar**

Toda compra registrada deve gerar automaticamente uma conta a pagar, vinculada ao fornecedor e com status inicial “Aberta”.

**RN05 — Controle de acesso por perfil de usuário**

Cada usuário só pode acessar funcionalidades conforme seu cargo na farmácia, facilitando assim o contrle de acesso, integração e comunicação entre os demais setores.
Exemplos de acessibilidade por cargos:
- Atendente: vendas
- Farmacêutico: validação de receitas
- Gerente: produtos e estoque
- Financeiro: contas
- Administrador: controle total


---

# 3. Requisitos Funcionais (mínimo: 8)
Liste os requisitos funcionais do seu MVP.

**RF01 — Cadastrar clientes**

O sistema deve permitir que o atendente cadastre novos clientes, registrando informações básicas para identificação e histórico de compras.

**RF02 — Consultar produtos**  

O sistema deve permitir a pesquisa de produtos por nome, código de barras ou fabricante, exibindo preço, descrição e disponibilidade em estoque.

**RF03 — Registrar vendas**

O sistema deve permitir que o atendente registre vendas de produtos, informando itens, quantidades, forma de pagamento e cliente (quando houver).

**RF04 — Emitir comprovantes de venda**  

Após a finalização de uma venda, o sistema deve emitir automaticamente um comprovante contendo os dados da transação.

**RF05 — Controlar estoque por unidade** 

O sistema deve manter o controle de estoque individual por farmácia, atualizando as quantidades automaticamente após vendas, compras ou ajustes.

**RF06 — Registrar compras de fornecedores**

O sistema deve permitir o registro de compras, informando fornecedor, produtos, quantidades, valores e unidade que receberá o estoque.

**RF07 — Gerenciar compras a pagar e a receber**

O sistema deve permitir o registro, consulta e atualização de contas financeiras, incluindo datas de vencimento, pagamento/recebimento e status.

**RF08 — Gerar relatórios gerenciais**  

O sistema deve permitir a emissão de relatórios operacionais e financeiros, como:
- vendas por período
- estoque por unidade
- produtos mais vendidos
- contas em aberto

---

# 🛡 4. Requisitos Não Funcionais (mínimo: 4)
Liste os RNFs do sistema conforme seu MVP.

**RNF01 — Desempenho**

O sistema deve responder às operações de consulta (produtos, clientes e estoque) em até 2 segundos, mesmo com múltiplos usuários simultâneos.

**RNF02 — Segurança**

O sistema deve garantir controle de acesso por autenticação de usuário e senha, além de restringir funcionalidades conforme o perfil (atendente, gerente, financeiro etc.).

**RNF03 — Disponibilidade**

O sistema deve estar disponível 24 horas por dia, 7 dias por semana, com tolerância a falhas para não interromper as operações das farmácias.

**RNF04 — Integridade e backup de dados**  

O sistema deve garantir a integridade das informações e realizar backups automáticos diários, evitando perda de dados críticos.

---

# 6. Casos de Uso

---

## **UC01 — Realizar venda**
**Ator(es): Atendente**  
**Descrição:** Permite resgistrar a venda de produtos para um cliente.  
**Pré-condições:** Sistema ativo e produtos cadastrados  
**Pós-condições:** Venda registrada e estoque atualizado  

### Fluxo Principal
1.  Atendente inicia a venda
2.  Identifica ou cadastra cliente
3.  Consulta produtos
4.  Finaliza venda

### Fluxos Alternativos / Exceções
- FA01 —  Produto sem estoque -> sistema bloqueia
- FA02 —  Cliente não cadastrado -> direciona para cadastro

### Relacionamentos
- **Include:** UC02, UC03, UC04 e UC05
- **Extend:** UC06, UC07  

### Diagramas do caso de uso

---

## **UC02 — Identificar clientes**
**Ator(es):** Atendente   
**Descrição:** Permite localizar clientes já cadastrado. 
**Pré-condições:** Cliente previamente cadastrado. 
**Pós-condições:** Cliente vinculado a venda 

### Fluxo Principal
1.  Informar dados do cliente
2.  Sistema busca cadastro
3.  exibe informações

### Fluxos Alternativos / Exceções
- FA01 — Cliente não encontrado 
- FA02 — Dados inválidos 

### Relacionamentos
- **Include:** nenhum
- **Extend:** UC03

### Diagramas do caso de uso

---
## **UC03 — cadastrar clientes**
**Ator(es):** Atendente.
**Descrição:** Permite registrar novo cliente no sistema. 
**Pré-condições:** Cliente não existente. 
**Pós-condições:** Cliente cadastrado 

### Fluxo Principal
1. Inserir dados  
2. validar informações 
3. Salvar cadastro 

### Fluxos Alternativos / Exceções
- FA01 —  Dados incompletos
- FA02 —  Erro ao salvar

### Relacionamentos
- **Include:** nenhum
- **Extend:** UC01

### Diagramas do caso de uso

---
## **UC04 — Consultar produto**
**Ator(es):** Atendente  
**Descrição:**  Permite buscar produtos no sistema.
**Pré-condições:**  produtos cadastrados
**Pós-condições:**  Produtos exibido.

### Fluxo Principal
1. Inserir nome/código 
2.  Sistema realiza busca
3.  exibe resultado

### Fluxos Alternativos / Exceções
- FA01 —  Produto não encontrado
- FA02 —  Falha na busca

### Relacionamentos
- **Include:** UC05
- **Extend:** nenhum 

### Diagramas do caso de uso

---
## **UC05 — Verificar estoque**
**Ator(es):** Sistema 
**Descrição:**  Verificar disponibilidade de produto no estoque
**Pré-condições:** Produto Selecionado 
**Pós-condições:**  Quantidade exibida

### Fluxo Principal
1.  Recebar produto
2.  Consultar estoque
3.  retornar quantidade

### Fluxos Alternativos / Exceções
- FA01 —  estoque zerado
- FA02 —  erro no sistema

### Relacionamentos
- **Include:** nenhum 
- **Extend:** UC04

### Diagramas do caso de uso

---
## **UC06 — registrar venda a prazo**
**Ator(es):** Atendente 
**Descrição:**  Registra venda com pagamento futuro.
**Pré-condições:**  Venda em andamento
**Pós-condições:**  Conta a receber gerada

### Fluxo Principal
1.  Selecionar pagamento a prazo
2.  Definir vencimento
3.  Confirmar operação

### Fluxos Alternativos / Exceções
- FA01 — Cliente não autorizado 
- FA02 —  Erro financwiro

### Relacionamentos
- **Include:** UC08 
- **Extend:** UC01

### Diagramas do caso de uso

---
## **UC07 — Emitir comprovantes**
**Ator(es):** Sistema  
**Descrição:** Gera comprovantes de venda 
**Pré-condições:** Venda finalizada. 
**Pós-condições:** Comprovante emitido 

### Fluxo Principal
1. Gera dados 
2.  Montar comprovantes
3.  exibir/imprimir

### Fluxos Alternativos / Exceções
- FA01 — Falha na impressão 
- FA02 —  Dados inconsistentes

### Relacionamentos
- **Include:** nenhum  
- **Extend:** UC01

### Diagramas do caso de uso

---
## **UC08 — Gerar Conta a receber**
**Ator(es):** Sistema  
**Descrição:** Cria registro financeiro de venda a prazo 
**Pré-condições:** Venda a prazo confirmada 
**Pós-condições:**  contra registrada

### Fluxo Principal
1. receber dados da venda 
2.  definir vencimento
3.  salvar conta

### Fluxos Alternativos / Exceções
- FA01 — Erro no registro  
- FA02 — dados inválidos 

### Relacionamentos
- **Include:** UC10
- **Extend:** nenhum  

### Diagramas do caso de uso

---
## **UC09 — registrar compra**
**Ator(es):** Gerente 
**Descrição:** registra compra de produtos 
**Pré-condições:** fornecedor cadastrado 
**Pós-condições:**  Estoque atualizado

### Fluxo Principal
1. Selecionar fornecedor 
2. Inserir produtos 
3. confirmar compras 

### Fluxos Alternativos / Exceções
- FA01 —  Fornecedor inválido
- FA02 —  erro no cadastro

### Relacionamentos
- **Include:** UC10
- **Extend:** nenhum

### Diagramas do caso de uso

---
## **UC10 — Atualizar estoque**
**Ator(es):** Sistema 
**Descrição:** Atualiza quantidade de produtos no estoque 
**Pré-condições:** movimnetação realizada 
**Pós-condições:**  Estoque atualizado

### Fluxo Principal
1. Receber movimentação 
2.  Atualizar quantidade
3. Salvar alterção 

### Fluxos Alternativos / Exceções
- FA01 — erro de atualização 
- FA02 — Dados inconsistentes

### Relacionamentos
- **Include:** nenhum
- **Extend:** UC01, UC09

### Diagramas do caso de uso

---




