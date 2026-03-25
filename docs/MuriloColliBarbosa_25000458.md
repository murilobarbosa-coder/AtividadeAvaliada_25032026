# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: *Murilo Colli Barbosa*  
RA: *25000458*  
Data: *25/03/2026*  

---

# 1. Definição do MVP
Descreva aqui **qual parte do sistema** foi incluída no seu MVP.  
Explique claramente:

- O que está **dentro** do MVP  
- O que está **fora** do MVP  
- Por que você fez essas escolhas  

Exemplo de início:  
> “Meu MVP cobre o processo de venda desde a identificação/cadastro do cliente até a emissão do comprovante, incluindo tratamento de estoque insuficiente.”

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

# 5. Casos de Uso (mínimo: 10)
### Inserir **diagrama de casos de uso geral**, demonstrando claramente:
- os 10 casos
- relação entre eles e atores
- pelo menos 3 includes
- pelo menos 3 extends

---

# 6. Documentação dos Casos de Uso
Para **cada caso de uso**, utilize o template abaixo:
---

## **UCXX — Nome do Caso de Uso**
**Ator(es):**  
**Descrição:**  
**Pré-condições:**  
**Pós-condições:**  

### Fluxo Principal
1.  
2.  
3.  
4.  

### Fluxos Alternativos / Exceções
- FA01 —  
- FA02 —  

### Relacionamentos
- **Include:** (listar quando aplicável)  
- **Extend:** (listar quando aplicável)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

> Repita essa estrutura para **todos os seus casos de uso** (mínimo 10).
