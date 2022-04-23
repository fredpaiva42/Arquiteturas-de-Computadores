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

### 10. É concebível um compilador gerar saída para o nível de microarquitetura em vez de para o nível ISA? Discuta prós e contras dessa proposta.
É possível, mas é problemático, o primeiro problema é a quantidade de código que será produzido, pois como a ISA é um conjunto de micro instruções e tem uma complexidade menor, ela vai precisar de mais linha de códigos para fazer o mesmo serviço que um código em linguagem de maior nível. Outro problema é que o compilador vai ter que lidar com uma linguagem mais primitiva, o que vai acabar tornado ela mesma mais complexa. Já o lado positivo é que o programa final pode ser muito mais rápido já que vai pular a etapa de interpretação.

### 11. Você pode imaginar qualquer computador multiníveis no qual o nível de dispositivo e os níveis lógicos digitais não estivessem nos níveis mais baixos? Explique

?

### 12. Considere um computador multinível no qual todos os níveis são diferentes. Cada nível tem instruções que são m vezes mais poderosas que as do nível abaixo dele; isto é, uma intrução no nível r pode fazer o trabalho de m instruções de nível r-1. Se um programa de nível 1 requer k segundos para executar, quanto tempo levariam programas equivalentes nos níveis 2, 3 e 4 admitindo que são necessárias n intruções de nível r para interpretar uma única instrução de nível r + 1?
Cada nível de interpretação retarda à máquina em fator de:
$$
\frac{n}{m}
$$

Assim os tempos para os níveis de execução 2, 3 e 4 são respectivamente:
$$
2: \frac{k * n}{m};\space3:\frac{k * n^2}{m};\space 4: \frac{k * n^3}{m}
$$

### 13. Algumas instruções no nível do sistema operacional da máquina são idênticas a instruções em linguagem ISA. Elas são executadas diretamente pelo microprograma ou pelo hardware, e não pelo sistema operacional. À luz de sua resposta ao problema anterior, por que você acha que isso acontece?
?

### 14. Considere um computador com interpretadores idênticos aos níveis 1, 2 e 3. Um interpretador precisa de n instruções para buscas, examinr e executar um instrução. Uma instrução de nível 1 demora k nanossegundos para executar. Quanto tempo demora para executar uma instrução nos níves 2, 3 e 4?

### 15. Em que sentido hardware e software são equivalentes? E não equivalentes?

Hardware e software são logicamente equivalentes, isto é, qualquer operação efetuada pelo software pode também ser implementada pelo hardware e qualquer instrução executada pelo hardware pode também ser simulada pelo software.

Não são equivalentes pois Hardware está em forma física e o software em forma digital ou seja, impossível de se tocar ou modificar ou até mesmo fazer overclocking.

Princípio de Equivalência de Hardware e Software: Qualquer coisa que 
possa ser feita com software pode ser feita com hardware, e qualquer coisa 
que possa ser feita com hardware também pode ser feita com software.