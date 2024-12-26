# Projeto de Desenvolvimento de Sistema Bancário com Paradigma Orientado a Aspectos

## Índice
- [Introdução](#introdução)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Detalhes das Classes](#detalhes-das-classes)
- [Implementação do Aspecto](#implementação-do-aspecto)
- [Manipulação de Exceções](#manipulação-de-exceções)
- [Testes e Classe Principal](#testes-e-classe-principal)
- [Considerações Finais](#considerações-finais)

---

## Introdução
Este projeto visa implementar um sistema bancário utilizando os paradigmas de **Programação Orientada a Objetos (POO)** e **Programação Orientada a Aspectos (POA)**. 

O objetivo principal é aplicar uma preocupação transversal, que é a verificação de saldo antes de qualquer operação de saque, em diferentes tipos de contas (**corrente**, **poupança**, **investimento**).

---

## Estrutura do Projeto
O projeto é estruturado em várias classes e aspectos:

- **Classes de Conta**: `Conta`, `ContaPoupanca`, `ContaInvestimento`
- **Aspecto**: `BalanceCheckAspect`
- **Exceção Personalizada**: `InsufficientBalanceException`
- **Classe Principal**: `Main`

---

## Detalhes das Classes

### Classe Base: `Conta`
#### Atributos:
- `tipoConta`
- `tipoCliente`
- `dataAbertura`
- `saldo`

#### Métodos:
- **`sacar(double valor)`**: 
  - Realiza um saque.
  - Lança a exceção `InsufficientBalanceException` se o saldo for insuficiente.

- **`depositar(double valor)`**:
  - Realiza um depósito.

- **`calculaValorRefinanciamento()`**:
  - Implementa a lógica de cálculo de refinanciamento.

- **`anutencao()`**:
  - Implementa a lógica de manutenção.

- **`getSaldo()`**:
  - Retorna o saldo da conta.

---

### Subclasses
#### `ContaPoupanca`
- Estende `Conta` e implementa lógica específica para conta de poupança.

#### `ContaInvestimento`
- Estende `Conta` e implementa lógica específica para conta de investimento.

---

## Implementação do Aspecto
### `BalanceCheckAspect`
- Utiliza `@Around` para interceptar chamadas ao método `sacar()`.
- Verifica se o saldo é suficiente antes de permitir a operação.
- Registra erros usando **SLF4J**.

---

## Manipulação de Exceções
### `InsufficientBalanceException`
- Lançada quando o saldo é insuficiente para realizar um saque.
- A mensagem de erro descreve o problema e a conta afetada.

---

## Testes e Classe Principal

### `Main`
- Contém testes para demonstrar a funcionalidade do sistema.
- Cria instâncias de diferentes tipos de contas e executa operações de saque.
- Utiliza logging para registrar erros e informações.

---

## Considerações Finais
- **Encapsulamento e Segurança de Concorrência**: 
  - Os métodos `sacar()` são sincronizados para evitar problemas de concorrência.
- **Logging**:
  - O aspecto utiliza **SLF4J** para registrar erros, facilitando a monitoração e debugging.
- **Extensibilidade**:
  - A estrutura POO permite a fácil adição de novos tipos de contas e funcionalidades específicas.
- **Aspectos Transversais**:
  - A POA permite a separação de preocupações transversais, como a verificação de saldo, mantendo o código principal limpo e focado na lógica de negócios.

Este projeto demonstra uma abordagem eficaz para a integração de **POO** e **POA**, proporcionando um sistema modular, mantível e escalável.
