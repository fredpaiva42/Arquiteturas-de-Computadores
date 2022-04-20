### 1. Qual é, em termos gerais, a distinção entre a organização e a arquitetura do computador?

**Arquitetura descreve o que o computador faz, e a organização descreve como ele faz isso.**

**Arquitetura**: São os atributos do sistema que são visíveis ao programador, e tem impacto direto na execução lógica de um programa.

Alguns exemplos de atributos que fazem parte da arquitetura:
- ISA
- mecanismos de I/O

**Organização**: Forma na qual as unidades operacionais se interligam para cumprir aquilo que é exigido pela arquitetura. São os detalhes do hardware, como tecnologia de memória usada.


### 2. Qual é, em termos gerais, a distinção entre estrutura e a função do computador?

A **estrutura** de um computador é o modo como seus componentes se relacionam entre si, está mais interligado ao conceito de organização. Já a **função**, diz respeito a operação de cada componente indivual que faz parte da estrutura.

### 3. Quais são as quatro funções principais de um computador?
- Processamento de dados
- Armazenamento de Dados
- Movimentação
- Controle

### 4.Liste e defina resumidamente os principais componentes estruturais de um computador.

- **CPU**: controla a operação do computador e a execução das funções de processamento de dados.
- **Memória Principal**: Armazena informações para acesso imediato da CPU.
- **I/O**: Proporciona uma interface entre o computador e o usuário.
- **Interconexão de Sistema (Barramentos)**: Mecanismo que é usado para fazer a conexão entre os componentes estruturais do computador.

### 5. Liste e defina resumidamente os principais componentes estruturais de um processador.

- **Unidade de Controle**: Controla a operação da CPU e portanto do computador.
- **Unidade Lógica Aritmética**: Executa a função de processamento de dados do computador.
- **Registradores**: Armazenamento interno do Processador.
- **Interconexão da CPU**: Mecanismos de comunicação entre a UC, ULA e registradores.

### 6. Que Categorias gerais de funções são especificadas pelas instruções do computador?

- **Processador - Memória**: dados podem ser transferidos do processador para a memória e da memória para o processador.
- **Processador - I/O**: Dados podem ser transferidos para ou de periféricos tranferindo entre o processador e o módulo de I/O.
- **Processamento de dados**: O processador pode executar operações aritméticas ou lógicas com os dados.
- **Controle**: Uma instrução pode especificar qual a sequência de instruções a serem alteradas.

### 7. Liste e defina resumidamente os estados possíveis que defienm a execução de uma instrução.
**Tranferências de valores entre o processador e a memória ou I/O**
- Cálculo de endereço da instrução: o endereço da próxima instrução a ser executada é determinado.
- Busca de instrução: Uma instrução é lida na memória e armazenada no processador.
- Decodificação de instrução: O código da instrução a ser executada é analisado, para determinar qual é a operação a ser realizada e os operandos a serem usados.

**Operações internas no processador**:
- Cálculo de endereço de operando: Se a operação envolver a referência a um  na memória ou estiver disponível via I/O, o endereço do operando será determinado.
- Busca de operando: o operando é localizado na memória ou é lido do dispositivo de I/O.
- Execução da Operação: A operação indicada na instrução é executada.
- Armazenamento de resultados: o resultado é escrito na memória ou no dispositivo de I/O.

### 8. Explique a Lei de Moore.
A Lei de Moore refere-se à percepção de Gordon Moore de que o número de transistores em um microchip dobra a cada dois anos, embora o custo dos computadores seja reduzido pela metade. A Lei de Moore diz que podemos esperar que a velocidade e a capacidade de nossos computadores aumentem a cada dois anos, e pagaremos menos por eles.

### 9. Explique cada um dos termos seguintes com suas próprias palavras: Tradutor, Interpretador e Máquina Virtual

**Tradutor**: O tradutor ou compilador, é o programa que recebe codígo fonte em linguagem de alto nível e faz a tradução para a linguagem de montagem (arquivo objeto).

**Interpretador**: O interpretador faz a execução e analise do código linha a linha em tempo de execução.

**Máquina Virtual**:Na ciência da computação, máquina virtual consiste em um software de ambiente computacional, que executa programas como um computador real, também chamado de processo de virtualização. Uma máquina virtual pode ser definida como “uma duplicata eficiente e isolada de uma máquina real”.