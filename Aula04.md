# Conjunto de Instruções: Características e Funções

## Características de Instrução de Máquina
- A operação do processador é determinada pelas instruções que ele executa, referido como instruções de máquinas ou instruções de computadores.
- A coleção de instruções diferentes que o processador pode executar é **o conjunto de instruções do processador**.
- Cada instrução contém a informação necessária pelo processador para sua execução.

### Elementos de uma Instrução de Máquina
- Operation Code (opcode) (ID)
  - Especifica a operação a ser computada. A operação é especificada por um código binário, conhecido como o código da operação, ou opcode.
- Referência do Operando Fonte
  - A operação pode envolver um ou mais operandos fontes, que são operandos de entradas para a operação.
- Referência do operando resultado
  - A operação pode produzir um resultado.
- Referência da próxima instrução
  - Informa ao processador onde buscar a próxima instrução depois que a instrução corrente estiver completa.
  
### Localilazação dos Operandos Fontes e de Resultado
- Memória Principal ou memória virtual
  - Como ocorre com as referências da próxima instrução, o endereço de memória principal ou virtual deve ser fornecido.
- Dispositivo de I/O
  - A instrução deve especificar os módulos e dispositivos I/O para a operação. Se I/O mapeado em memória é usado, então é um outro endereço de memória principal ou virtual.
- Registrador do processador
  - Um processador contém um ou mais registradores que podem ser referenciados pela instruções de máquina.
  - Se mais de um registrador existir, cada registrador contém um "nome" único ou um número que é utilizado pela instrução.
- Imediato
  - O valor do operando é contido em um campo da instrução que está sendo executada.

### Representação da Instrução
- Cada instrução é representada por uma sequência de bits.
- A instrução é dividida em campos, correspondentes aos elementos que constituem a instrução.
![](./imgs/Divisão%20dos%20campos%20da%20instrução.png)
- Opcodes são representados por abreviações chamada de **mnemônicos**.
- Exemplo:
  - ADD - Adição
  - SUB - Subtração
  - MUL - Multiplicação
  - DIV - Divisão
  - LOAD - Carregar dado da memória
  - STORE - Armazenar dado na memória
- Operandos também são representados simbolicamente.
- Cada opcode simbólico tem uma representação binária fixa.
- O programador especifica a localização simbólica de cada operando.

### Tipos de Instruções
- Processamento de dados
  - Instruções aritméticas provê processamento de dados númericos.
  - Instruções lógicas (booleanas) operam de fato nos bits de uma "word", processando qualquer outro tipo de dados.
- Armazenamento de Dados
  - Movimentação de dados para dentro ou fora das localizações dos registradores ou memória.
- Movimentação de dados
  - Instruções de I/O são necessárias para transferir dados e programas da memória e os resultados das computações de volta para o usuário.
- Controle
  - Intruções de teste são usadas para testar os valores dos dados ou o status de uma computação.
  - Instruções de branch (desvio condicional) são usadas para direcionar a computação à um conjunto de instruções diferente de acordo com a decisão tomada.

### Utilização dos Endereços de instrução
![](./imgs/Utilização%20de%20endereços%20de%20instrução.png)
- AC = acumulador
- T = Topo da pilha
- (T-1) = segundo elemento da pilha
- A, B, C = Localilazação de registradores ou memória

### Projeto do Conjunto de instruções
- Muito complexo porque afeta muitos aspectos de um sistema computacional.
- Define muitas das funções executadas pelo processador.
- Meios que o programador pode controlar o processador.
- Problemas fundamentais do projeto
  - **Repertório de operações**
    - Quantas e quais operações estão disponíveis? E sua Complexidade?
  - **Tipos de dados**
    - Vários tipode de dados que as operações podem executar
- Formato da instrução
  - Comprimento da instrução em bits, # de endereços, tamanho dos campos, etc.
- Registradores
  - N de registradores que pode ser referenciados pelas instruções.
- Endereçamento
  - O modo (ou modos que o endereço de um operando é especificado)

### Tipos de Operandos
- Endereços
- númericos
- Caracteres
- Dado lógico

#### Tipos de Dados do x86
![](./imgs/type%20of%20data%20x86.png)
![](./imgs/type%20of%20data%20x86%20II.png)

#### Formato dos Dados númericos do x86
![](./imgs/Formato%20dos%20dados%20númericos%20do%20x86.png)

### Tipo de Dados Single-Instruction Multiple-DATA (SIMD)
- Introduzido na arquitetura x86 como parte das extensões do conjunto de instruções para otimizar o desempenho de aplicações multimedia.
- Essas Extensões incluem MMX (Extensões multimedia) e SSE (Extensões SIMD para streaming)
- **Tipo de dados**
  - Packed byte - 8 bytes empacotados em 64 bits
  - Packed word - 4 words empacotados em 64 bits
  - Packed double - 2 doble words empacotados em 64 bits
  - Packed quad word - 1 word de 64 bits
  - Packed single(double) - precision floating-point

### Tipos de Dados do ARM
- Processadores ARM suportam os tipos de dados de:
  - 8 (byte)
  - 16 (half word)
  - 32 (word) bits de comprimento
- Verificação de alinhamento
  - Quando o bit de controle apropriado é ativo, o sinal dado abortado indica uma falha no alinhamentos para uma tentativa de acesso desalinhado.
- Acesso desalinhado
  - Quando ativo, o processador usa um ou mais acessos de memória para gerar tranferência dos bytes adjacentes necessárias de forma transparente ao programador.
- Os 3 tipos de dados possuem uma versão **usigned**.
- Todos os 3 tipos de dados também podem ser usados por inteiros **signed** com complemento a 2.

### Organização de Memória: Ordenação de Byte Little e Big Endian
- **Big Endian**: byte 0 mais à esquerda (mais significante) para o byte 3 mais à direita (menos significante).
- **Byte little**: byte 3 mais à esquerda (mais significante) para o byte 0 mais à direita (menos significante).
![](./imgs/big%20endian%20and%20little%20endian.png)

#### Suport of ARM for Endianess
![](./imgs/support%20of%20ARM%20for%20Endianess.png)

#### Operações comuns do Conjunto de instruções
![](./imgs/Operações%20comuns%20I.png)
![](./imgs/Operações%20comuns%20II.png)
![](./imgs/Operações%20comuns%20III.png)
![](./imgs/Operações%20comuns%20IV.png)
![](./imgs/Operações%20comuns%20V.png)

#### Açoes para os vários tipos de Operações
![](./imgs/Açoes%20para%20vários%20tipos%20de%20operações.png)

### Tranferência de Dados (Data Transfer)
- O tipo de instrução de máquina mais fundamental
- Deve-se especificar:
  - Localização dos operandos fontes e destino.
  - Comprimento de dado para ser transferido.
  - Modo de Endereçamento para cada operando.

### Aritmética
- Maioria das máquinas fornecem as operações aritméticas básicas: adição, subtração, multiplicação e divisão.
- São fornecidas para número signed integer
- Geralmente são fornecidas também para números de ponto flutuante e os tipos packed.
- Outras possíveis:
  - Absoluto
  - Negar
  - Incrementa
  - Decrementa

### Conversão
- Instruções que alteram o formato ou operam no formato dos dados
- Um exemplo é a conversão de decimal para binário.

### Input / Output
- Variedade de abordagens:
  - I/O programado isolado
  - I/O programado com mapeamento de memória
  - DMA
  - Uso de um processador de I/O
  - Muitas implementaçÕes fornecem poucas instruções de I/O, com ações especificadas por parâmetros, códigos ou words de comando.

### Controle de Sistema
- Instruções que podem ser executadas somente enquanto o processador está em um estado de acesso privilegiado ou está executando o programa em área privilegiada especial da memória.
- Tipicamente são instruções reservadas para o uso do Sistema Operacional.
- Exemplos de Operações de controle de sistema:
  - Uma instrução que pode ler ou alterar o registrador de controle.
  - Uma instrução para ler ou modificar uma chave de proteção do armazenamento.
  - Acesso para controlar os blocos de controle em um sistema de multiprogramação.

### Tranferência de Controle
- Por que são instruções necessárias?
  - Essencial para execuatar uma instrução mais de uma vez.
  - Virtualmente todos os programas envolvem uma tomada de decisão.
  - Ajuda em mecanismos que dividem uma tarefa em pequenas partes que podem trabalhar simultaneamente.
- As operações de transferência de controle mais comuns:
  - Branch
  - Skip
  - Chamada de procedimento

#### intruções Branch
![](./imgs/Instruções%20Branch.png)

#### Instruções Skip
- Inclui um endereço implícito
- Tipicamente uma instrução é pulada. O endereço implícito é igual o endereço da próxima instrução mais um comprimento de instrução
- Como essa instrução não precisa do campo de endereço destino, ela pode ser usada para outras coisas
- Exemplo:
  - Intrução **increment-and-skip-if-zero(ISZ)**

#### Instruções de Chamada de Procedimentos
- Por que são instruções necessárias?
  - **Economia**: Parte do código é reutilizada várias vezes
  - **Modularidade**
- Duas instruções básicas:
  - Uma instrução **call** que redireciona do local atual para o procedimento.
  - Intrução **return** que retorna de um procedimento para o lugar de onde foi chamado.

#### Procedimento Aninhados
![](./imgs/Procedimento%20Aninhados.png)

#### Pilha usando Procedimentos P e Q
![](./imgs/Pilha%20usando%20o%20procedimento%20P%20e%20Q.png)