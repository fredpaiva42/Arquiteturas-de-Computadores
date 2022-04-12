# Conjunto de instruções: Modos de Endereçamento e Formatos

## Modos de Endereçamento
- Imediato
- Direto
- Indireto
- Registrador
- Registrador Indireto
- Deslocamento
- Pilha
  
![](./imgs/Modos%20de%20Endereçamento.png)

#### Modos de Endereçamento Básicos
![](./imgs/Modos%20de%20Endereçamento%20Básico.png)

## Endereçamento Imediato
- Endereçamento mais simples
- Operando = A
- Pode ser usado para definir e usar constantes ou para definir os valores iniciais da varáveis
  - Tipicamente, o número é armazenado na forma de complemento a 2
  - O bit mais à esquerda do campo do operando é usado como bit de sinal
- **Vantagem**
  - Não precisa de referência de memória para obter o operando
  - O ciclo da instrução é reduzido, pois não precisa ter acesso a memória
- **Desvantagem**
  - O tamanho do número é restrito ao tamanho do campo de endereço, que em geral é menor que o comprimento de uma word (16 bits)

## Endereçamento Direto 
- Endereçamento mais simples
- Endereço efetivo (EA) = campo de endereço (A)
- Mais comum nas primeiras gerações de computadores
- Necessita somente de uma referência de memória sem cálculo especial 
- Limitação: possui somente um espaço de endereçamento

## Enderaçamento Indireto
- Referência para o endereço de uma word na memória que contém o endereço do operando (full-length)
- EA = (A)
- **Vantagem**
  - Para uma word de comprimento N é possível endereçar até 2^N operandos
- **Desvantagem**
  - A execução da instrução requer duas referências de memória para buscar o operando (endereço e valor)
  - EA = (...(A)...): 3 ou mais referências de memória

## Endereçamento de Registrador
- Campo de endereço indica o registrador ao invés do endereço de memória
- EA = R
- **Vantagem**
  - Só precisa de um pequeno campo de endereço na instrução
  - Não consome tempo de acesso à referência de memória
- **Desvantagem**
  - O espaço de endereço é muito limitado

## Endereçamento Indireto por Registrador 
- Igual o endereçamento indireto, onde o campo de endereço indica um registrador
- EA = (R)
- A limitação do espaço de endereço do campo de endereço é superada
- Usa uma referência de memória a menos que o endereçamento indireto

## Endereçamento por Deslocamento
- Combinação do endereçamento direto e o endereçamento indireto por registrador
- EA = A + (R)
- Dois campos de endereço
  - Valor de A é usado diretamente
  - Valor de Referêcnia de R
- Uso mais comum
  - Endereçamento relativo
  - Endereçamento por registrador base
  - Indexação

## Endereámento Relativo ou PC-Relativo
- registrador referenciado implicitamente é o **contador do programa (PC)**
  - EA = A + (PC)
- Explora o conceito de localidade
- Salva bits de endereço na instrução se a maioria das referências de memória estiverem relativamente próximas da instrução sendo executada
  
## Endereçamento por Registrador Base
- O **registrador** referenciado contém um endereço de memória principal e o **campo de endereço** contém um deslocamento desse endereço
- A referência de registrador pode ser explícita ou implícita
- Explora a localidade de referências de memória
- A = deslocamento // Campo de endereço
- R = endereço base
- EA = A + R
  
## Indexação
- A = endereço base // Campo de endereço
- R = Deslocamento
- EA = A + R
- **Autoindexação**: Aumenta ou diminui automaticamente o registrador de índice após cada referência a ele
  - EA = A + (R)
  - (R) <- (R) + 1
- **Pós-indexação**: A indexação é realizada após a indireção
  - EA = (A) + (R)
- **Pré-indexação**: A indexaçãp é realizada antes da indireção
  - EA = (A + (R))

## Enderaçamento de Pilha
- Itens são acrescentados no topo da pilha
- Ponteiro de pilha contém o endereço do topo da pilha
- Forma de endereçamento implícito
  - As instruções não incluem a referência de memória e as operações são executadas implicitamente no topo da pilha

#### Modos de endereçamento do x86
![](./imgs/Modo%20de%20enderaçamento%20do%20x86.png)
![](./imgs/Modo%20de%20enderaçamento%20do%20x86%20II.png)
![](,/../imgs/Modo%20de%20enderaçamento%20do%20x86%20III.png)

#### Modos de Indexação do ARM
![](./imgs/Modos%20de%20Indexação%20do%20ARM.png)

## Formatos de Instruções
- Define o layout dos bits de uma instrução em termos de campo
- Inclui opcode e indica o modo de endereçamento de cada operando de forma explícita ou implícita
- Mais de um formato de instrução é usado

### Tamanho da Instrução
- Problema básico do projeto
- Afeta e é afetado por:
  - Tamanho da memória
  - Organização da memória
  - Estrutura de Barramento
  - Complexidade do Processador
  - Velocidade do processador
  - Deve ser igual ou múltiplo ao tamanho de uma word de memória
  - Deve ser um múltiplo de tamanho de um caracter (o bits) e de números inteiros

### Alocação de bits
- Número de modos de endereçamento
- Número de operandos
- Registrador vs Memória
- Número de conjuntos de registradores
- intervalo de endereços
- Granularidade do endereço

### Instruções de Tamanho Variável
- Variações no opcode e referências de registrador e memória podem ser mais eficientes e compactas
- Aumenta a complexidade do processador
- Não acaba com a necessidade de relacionar integralmente todos os tamanhos das instruções com o tamanho da word
  - Processador não conhece o tamanho da próxima instrução
  - Às vezes, múltiplas instruções são buscadas

#### Formato de instrução do x86
![](./imgs/Formato%20de%20Instrução%20do%20x86.png)

#### Formato de instrução do ARM
![](./imgs/Formato%20de%20Instrução%20do%20ARM.png)
