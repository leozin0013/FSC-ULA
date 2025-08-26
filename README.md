# ULA (Unidade Lógica Aritmética) de 6 bits

## Descrição do Projeto

Este projeto implementa uma **ULA completa de 6 bits** usando o CircuitVerse, capaz de realizar operações aritméticas e lógicas básicas. A ULA é um componente fundamental em processadores, responsável por executar cálculos matemáticos e operações lógicas.

## Arquitetura do Circuito

### Componentes Principais:

- **ULA Principal**: Circuito integrador com controle de operações
- **SOMADOR6BITS**: Realiza soma binária de 6 bits com propagação de carry
- **AND6BITS**: Operação AND bit-a-bit entre dois operandos de 6 bits
- **OR6BITS**: Operação OR bit-a-bit entre dois operandos de 6 bits  
- **COMPARE6BITS**: Comparador de igualdade usando portas XNOR
- **MULTIPLEXADOR**: Seletor de operações com sinais de controle

### Entradas:
- **A1 a A6**: Primeiro operando de 6 bits (A1 = LSB, A6 = MSB)
- **B1 a B6**: Segundo operando de 6 bits (B1 = LSB, B6 = MSB)
- **Control 1 e Control 2**: Sinais de controle para seleção de operação

### Saídas:
- **6 bits de resultado**: Resultado da operação selecionada

## Tabela de Operações

| Control 1 | Control 2 | Operação | Descrição |
|-----------|-----------|----------|-----------|
| 0 | 0 | **COMPARAÇÃO** | A == B (XNOR bit a bit) |
| 0 | 1 | **SOMA** | A + B |
| 1 | 0 | **OR** | A \| B |
| 1 | 1 | **AND** | A & B |

## Cenários de Teste

### **Cenário 1: Operação de COMPARAÇÃO**
**Objetivo**: Testar comparação de igualdade (números iguais)

**Configuração das Entradas:**
```
A6=0, A5=0, A4=1, A3=0, A2=1, A1=0  → A = 001010 (decimal: 10)
B6=0, B5=0, B4=1, B3=0, B2=1, B1=0  → B = 001010 (decimal: 10)
Control 1 = 0
Control 2 = 0
```
**Resultado Esperado**: `111111` (todos os bits = 1, indicando igualdade)

**Screenshot do Teste:**
![Cenário 1 - COMPARAÇÃO Iguais](https://i.imgur.com/ohF76s3.png) 

---

### **Cenário 2: Operação de SOMA**
**Objetivo**: Testar a soma de dois números binários

**Configuração das Entradas:**
```
A6=1, A5=1, A4=1, A3=1, A2=0, A1=0  → A = 111100 (decimal: 60)
B6=1, B5=1, B4=0, B3=0, B2=1, B1=1  → B = 110011 (decimal: 51)
Control 1 = 0
Control 2 = 1
```
**Resultado Esperado**: `000011` (decimal: 3)

**Screenshot do Teste:**
![Cenário 2 - SOMA](https://i.imgur.com/7XrOjVC.png)

---

### **Cenário 3: Operação OR Lógico**
**Objetivo**: Testar a operação OR bit-a-bit

**Configuração das Entradas:**
```
A6=1, A5=0, A4=1, A3=0, A2=1, A1=0  → A = 101010 (decimal: 42)
B6=0, B5=1, B4=0, B3=1, B2=0, B1=1  → B = 010101 (decimal: 21)
Control 1 = 1
Control 2 = 0
```
**Resultado Esperado**: `111111` (decimal: 63)

**Screenshot do Teste:**
![Cenário 3 - OR Lógico](https://i.imgur.com/zYNwM2g.png)

---

### **Cenário 4: Operação AND Lógico**
**Objetivo**: Testar a operação AND bit-a-bit

**Configuração das Entradas:**
```
A6=1, A5=0, A4=0, A3=1, A2=0, A1=1  → A = 100101 (decimal: 37)
B6=1, B5=0, B4=0, B3=1, B2=0, B1=1  → B = 100101 (decimal: 37)
Control 1 = 1
Control 2 = 1
```
**Resultado Esperado**: `111101` (decimal: 61)

**Screenshot do Teste:**
![Cenário 4 - AND Lógico](https://i.imgur.com/rK0grUi.png)

---

### **Cenário 5: Comparação - Números Diferentes**
**Objetivo**: Testar comparação de igualdade (resultado = 0)

**Configuração das Entradas:**
```
A6=1, A5=1, A4=0, A3=0, A2=1, A1=0  → A = 110010 (decimal: 50)
B6=1, B5=0, B4=1, B3=1, B2=0, B1=0  → B = 101100 (decimal: 44)
Control 1 = 0
Control 2 = 0
```
**Resultado Esperado**: `100001` (decimal: 33)

**Screenshot do Teste:**
![Cenário 5 - Comparação Diferentes](https://i.imgur.com/0UID6IO.png)

## Como Executar os Testes

### No CircuitVerse:

1. **Abra o arquivo** `Projeto.cv` no CircuitVerse
2. **Configure as entradas** de acordo com cada cenário:
   - Clique em cada entrada A1-A6 e B1-B6 para definir os valores (0 ou 1)
   - Configure Control 1 e Control 2 conforme a tabela de operações
3. **Execute a simulação** e observe as saídas
4. **Verifique** se os resultados coincidem com os valores esperados

### Exemplo Prático - Cenário 1 (COMPARAÇÃO):

1. **Configure as entradas A**: A6=`0`, A5=`0`, A4=`1`, A3=`0`, A2=`1`, A1=`0`
2. **Configure as entradas B**: B6=`0`, B5=`0`, B4=`1`, B3=`0`, B2=`1`, B1=`0`
3. **Configure controles**: Control 1 = `0`, Control 2 = `0`
4. **Resultado**: A saída deve mostrar `111111` (todos os bits = 1, indicando igualdade)

## Tecnologias Utilizadas

- **CircuitVerse**: Simulador de circuitos digitais
- **Lógica Digital**: Portas AND, OR, XOR, XNOR
- **Multiplexadores**: Para seleção de operações
- **Full Adders**: Para implementação da soma binária

## Complexidade do Projeto

- **Entradas**: 14 (12 de dados + 2 de controle)
- **Saídas**: 6 bits
- **Subcircuitos**: 10 componentes modulares
- **Portas Lógicas**: 100+ componentes internos

## Limitações:
- **Capacidade máxima**: 63 (111111 em binário)
- **Overflow**: Não é detectado na soma (carry-out disponível separadamente)
- **Comparação**: Retorna apenas igualdade (não implementa maior/menor)

---

**Projeto desenvolvido como trabalho acadêmico por Leonardo Azambuja e Francisco Reis - Agosto 2025**
