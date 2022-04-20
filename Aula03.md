# Entendendo Desempenho!

## Desempenho
- Desempenho é a chave para entender a motivação implicita para o hardware e sua organização.
- Medir, relatar e resumir o desempenho permite que os usuários façam:
  - escolhas inteligentes
  - vejam além do hype do marketing
- Nossas métricas de desempenho vão sempre variar dependendo das questões que estão sendo analisadas.

### Entendendo Desempenho
- O **algoritmo** determina o número de instruções do código fonte e o número de operações de I/O executadas.
- A **linguagem de programação, o compilador e a arquitetura** determinam o número de instruções de máquinas executadas por cada instrução do código fonte.
- O **processador e o sistema de memória** determinam a rapidez com que as instruções são executadas.
- O **sistema de I/O (hardware e sistema operacional)** determinam a rapidez com que as operações de I/O são executadas.

## Métricas de Desempenho
- **Métricas de desempenho para processadores:** avalia o desempenho de uma unidade de processamento, normalmente feito medindo a velocidade ou o número de operações que ela faz em um determinado período de tempo.
- **Métricas de desempenho para aplicativos paralelos**: avalia o desempenho de um aplicativo paralelo, normalmente feito comparando o tempo de execução com várias unidades de processamento em relação ao tempo de execução com apenas uma unidade.

### Medidas de Desempenho para Processadores
- **MIPS**: Milhões de instruções por segundo.
- **FLOPS**: Operações de ponto flutuante por segundo.
- **SPECint**: Benchmarks SPEC (Standart Performance Evaluation Corporation) que avaliam o desempenho do processador em aritmética de inteiros (primeiro lançamento em 1992).
- **SPECfp**: Benchmarks SPEC que avaliam o desempenho do processador em operações do ponto flutuante (primeiro lançamento em 1989).
- **Whetstone**: Benchmarks sintéticos para avaliar o desempenho do processador em operações de ponto flutuante (primeiro lançamento em 1972).
- **Dhrystone**: Benchmarks sintéticos para avaliar o desempenho do processador em aritmética de inteiros (primeiro lançamento em 1984).
  
## Desempenho Computacional

### Tempo de resposta (tempo decorrido, latência)
- Quanto tempo leva para o meu job rodar?
- Quanto tempo para executar (iniciar e terminar) meu job?
- Quanto tempo devo esperar por uma query no banco de dados?
  
### Vazão (Throughput)
- Quantos jobs a máquina pode rodar de uma vez?
- Qual é a taxa de execução média?
- Quanto trabalho está sendo feito?

### Tempo de execução
#### Tempo decorrido
- Conta tudo do ínicio até o fim (acesso no disco e memória, I/O).
- É uma medida útil, mas não é muito boa para fins de comparação.
$$
  Tempo\space decorrido = tempo\space CPU + tempo\space de\space espera(I/O, outros\space programas)
$$

#### Tempo de CPU
- Não conta espera por I/O ou tempo gasto rodando outros programas.
- Pode ser dividido em tempo de CPU do usuário e tempo de CPU do sistema (chamada de SO).
$$
  Tempo\space CPU = tempo\space CPU\space usuário + tempo\space CPU\space sistema.
$$

- **Nosso foco**: tempo de CPU do usuário (tempo de execução da CPU, ou simplesmente, tempo de execução)
  - tempo gasto executando as linhas de código que estão no nosso programa.

## Definição de Desempenho
- Para um programa que roda na máquina X:
$$
  Desempenho_x = \frac{1}{tempo\space de\space execução_x}
$$

- X é n vezes mais rápido que Y:
$$
  \frac{Desempenho_x}{Desempenho_y} = \frac{tempo\space de\space execução_y}{tempo\space de\space execução_x} = n
$$

## Ciclos de Clock
- Frequentemente usamos **ciclos** para calcular o tempo de execução.
- Quase todos os computadores usam um **clock** que determina quando os eventos ocorrem no hardware. Esses intervalos de tempo discretos são chamados de ciclos de clock (ou ticks, clocks, ciclos).
![](imgs/Cilclos%20de%20Clock.png)

- A duração de um ciclo completo do clock é o período do clock e o número de ciclos por segundo é a taxa do clock (ou frequência do clock), que é o inverso do período do clock.
$$
 Frequencia\space clock_{(Hz)} = \frac{1}{Periodo\space de\space clock(s)}
$$

- **Período de clock (tempo)** = duração do ciclo do clock (segundo).

Ex:
$$
  250ps (picossegundos) = 0.25 ns (nanossegundos) = 250 * 10^{-12}
$$ 

- **Velocidade de clock (frequência)** = ciclos por segundo

Ex: Um clock com 200 Mhz tem:
$$
  Tempo\space de\space ciclo = \frac{1}{200 * 10^6} * 10^9 = 5ns
$$

## Equação de Desempenho I

$$
  \frac{segundos}{programa} = \frac{ciclos}{programa} * \frac{segundos}{ciclo}
$$

- equivalente (Programa P):

$$
  Tempo\space de\space execução\space CPU_p = Ciclos\space de\space Clock\space CPU_p * Tempo\space de\space ciclo\space clock
$$

- equivalente: 

$$
  Tempo\space de\space execução\space CPU_p = \frac{Ciclos\space de\space Clock\space CPU_p}{Velocidade\space clock} 
$$

- Então para melhorar o desempenho temos que:
  - Reduzir o **número de ciclos** do programa, ou
  - Reduzir o **tempo do ciclo de clock**, ou 
  - Aumentar a **velocidade de clock**

### Quantos ciclos são necessários para um programa?
- Não se pode dizer que o **# de ciclos = # de instruções**. Porque intruções diferentes levam quantidade de tempo (ciclos) diferentes.
- Multiplicação leva mais tempo do que adição de ciclos.
- Operações de ponto flutuante demoram mais que de inteiros
- Acesso de memória leva mais tempo que acesso nos registradores.
- **Ponto importante:** trocar o tempo de ciclo geralmente troca o número de ciclos necessários por várias instruções porque isso significa que o projeto do hardware foi alterado.

#### Exemplo
- Nosso programa favorito roda em 10 segundos no computador A, que tem um clock de 400 Mhz
- Estamos ajudando um Projetista de computador a construir um novo computador B, que vai rodar este programa em 6 segundos. O projetista pode usar novas tecnologias para aumentar a frequência de clock, mas ele nos informou que esse aumento afetará o resto do projeto da CPU, fazendo com que o computador B, precise de 1.2 vezes mais ciclos de clock que o computador A para o mesmo programa.
- Qual velocidade devemos sugerir ao projetista?
  
$$
Dados:TE_A = 10s, Vel_A = 400MHz = 400 * 10^6 Hz\\ TE_B = 6s, Ciclos_B = 1.2 * Ciclos_A
$$

$$
TE_A = \frac{Ciclos_A}{Vel_A} \to 10 = \frac{Ciclos_A}{400 * 10^6} \to Ciclos_A = 4000 * 10^6 \\
$$

$$
Ciclos_B = 1,2 * 4000 * 10 ^ 6\\
Vel_B = \frac{Ciclos_B}{TE_B} \to Vel_B = \frac{4800 * 10^6}{6} = 800 MHz
$$

## Terminologia
- Um dado programa precisa:
  - algum número de instruções.
  - algum número de ciclos.
  - algum número de segundos.

- Termos referentes a esses valores:
  - tempo de ciclo (segundo por ciclo)
  - velocidade de clock (frequência, ciclos por segundos)
  - (média) CPI (ciclos de clock por instrução)
    - aplicações com ponto flutuante possui maior média de CPI
  - MIPS (milhões de instruções por segundo)
    - É maior para programas usando instruções simples

## Medida de desempenho
- Desempenho é determinado pelo **tempo de execução**.
- Alguma dessas outras medidas medem desempenho?
  - n de ciclos para executar um programa? Não
  - n de instruções no programa? Não
  - n de ciclos por segundo? Sim, é a velocidade de clock
  - média n de ciclos por instrução? Não
  - média n de instruções por segundo? Não
- **Armadilha**: achar que uma variável é indicativo de desempenho quando de fato ela não é.

## Equação de desempenho II

$$
Tempo\space CPU_P = Contagem\space instrução * média\space CPI * Tempo\space ciclo\space clock
$$
- Equivalente: 

$$
Tempo\space CPU\space Programa = \frac{Contagem\space instrução * média\space CPI}{Velocidade\space clock}
$$

- Derivada da **Equação de Desempenho I**

#### Exemplo I de CPI
- Suponha que temos duas implementações do mesmo ISA. Para um determinado programa:
  - o computador A tem um tempo de ciclo de clock de 10ns e um CPI de 2,0
  - o computador B tem um tempo de ciclo de clock de 20ns e um CPI de 1,20
- Qual computador é mais rápido para esse programa e o quanto mais rápido?
  - **Portanto, a máquina A é a mais rápida. é 1,2 vezes mais rápida que a máquina B.**
$$
Dados: TC_A = 10ns, CPI_A = 2\\
TC_B = 20ns, CPI_B = 1,2
$$
$$
  N = QtdIstruções; \\
  TE = N * CPI * TC
$$
$$
TE_A = N * 2 * 10 \to TE_A = 20N\\
TE_B = N * 1,2 * 20 \to TE_B = 24N
$$
$$
\frac{TE_B}{TE_A} = \frac{24N}{20N} = 1,2 \space vezes \space mais \space rápida.
$$
- Se os dois computadores tem o mesmo ISA, quais de nossas métricas permanecerão (frequência, CPI, tempo de execução, MIPS) idênticas?
  - **Apenas CPI permanece idêntica.**

#### Exemplo II de CPI
- Um projetista de compilador está tentando decidir entre duas sequências de código para uma máquina em particular.
- Baseado na implementação do hardware, há 3 classes diferentes de instruções: Classe A, Classe B e Classe C, requerendo 1, 2 e 3 ciclos (respectivamente).
- A primeira sequência de código tem 5 instruções:
  - 2 de A,  1 de B e 2 de C.
- A segunda sequência tem 6 instruções:
  - 4 de A, 1 de B e 1 de C.
- Qual sequência vai ser mais rápida? quanto mais rápida? Qual é a CPI de cada sequência?
  - **A segunda sequência é a mais rápida, 1,11... mais rápida. A CPI da primeira sequência é 2 e a CPI da segunda sequência é 1,5**
$$
Seq_1 = 5\space instruções \\
Ciclos_1 = 2 * 1 + 1 * 2 + 2 * 3 = 10 \space ciclos \\
TE_1 = 10 * TC \\
CPI = \frac{N Ciclos}{N instruções} = CPI_2 = \frac{10}{5} = 2
$$
$$
Seq_2 = 6\space instruções \\
Ciclos_2 = 4 * 1 + 1 * 2 + 1 * 3 = 9 \space ciclos \\
TE_2 = 9 * TC \\
CPI = \frac{N Ciclos}{N instruções} = CPI_2 = \frac{9}{6} = 1,5
$$
$$
\frac{TE_1}{TE_2} = \frac{10}{9} = 1,11... \space vezes \space mais\space rápida
$$
## MIPS
- **MIPS**: Million Instructions Per Second.

$$
MIPS = \frac{contagem\space intrução}{TE * 10^6}
$$

- Máquinas mais rápidas possuem MIPS maiores.
- Problemas:
  - Máquinas com conjuto de instruções diferentes não podem ser comparadas porque o número de instruções vai diferir entre elas.
  - Não se pode considerar uma medida única, pois cada programa executado apresenta uma medida diferente
  - Pode variar inversamente ao desempenho

#### Exemplo MIPS
- Dois compiladores diferentes estão sendo testados para um computador de 500 MHz com 3 classes de instruções diferentes: Classe A, Classe B e Classe C, que requerem 1, 2 e 3 ciclos (respectivamente). Ambos compiladores estão sendo usados para produzir código oara um grande pedaço de software.
- Compilador 1 gera código com 5 bilhões de instruções da Classe A, 1 bilhão da Classe B e 1 bilhão da Classe C.
- Compilador 2 gera código com 10 bilhões de instruções da Classe A, 1 bilhão da Classe B e 1 bilhão da Classe C
$$
Comp_1 = 5 * 10^9 + 1 * 10^9 + 1 * 10^9 = 7 * 10^9 \\
Ciclos_1 = 5 *10^9 + (1*10^9 * 2) + (3 * 1 * 10^9) = 10 * 10^9 \\
TE_1 = \frac{10 * 10^9}{500 * 10 ^ 6} = 20 \\
MIPS_1 = \frac{7 * 10^9}{20 * 10^6} = 350
$$
$$
Comp_2 = 10 * 10^9 + 1 * 10^9 + 1 * 10^9 = 12 * 10^9 \\
Ciclos_2 = 10 *10^9 + (1*10^9 * 2) + (3 * 1 * 10^9) = 15 * 10^9 \\
TE_2 = \frac{15 * 10^9}{500 * 10 ^ 6} = 30 \\
MIPS_2 =  \frac{12 * 10^9}{30 * 10^6} = 400
$$
- Qual sequência será mais rápida de acordo com o MIPS?
  - **Compilador 2**
- Qual sequência será mais rápida de acordo com o tempo de execução?
  - **Compilador 1**
  
## Benchmarks
- Melhor desempenho determinado pela execução de um aplicativo real
  - Usar programas típicos da carga de trabalho esperada
  - Ou, típica da classe de aplicativos esperada. Ex: compiladores/editores, aplicativos científicos, gráficos etc.
- Benchmarks pequenos
  - Agradável para arquitetos e designers
  - fácil de padronizar
  - pode ser abusado
- Suítes de Benchmark
  - SPEC: combinação de código de organização da indústria
  - Linpack: pacote de álgebra linear

## Lei de Amdahl

$$
 Tempo\space execução \space melhoria = Tempo\space não\space afetado\space melhoria + \frac{Tempo\space afetado\space melhoria}{QtdMelhoria}
$$

![](./imgs/Lei%20de%20Amdahl.png)
- **Princípio de design**: torne o caso comum rápido.
  
#### Exemplos
- Suponha um programa executado em 100 segundos com operações de multiplicação responsáveis por 80 segundos desse tempo.
$$
TE_M = TE_S + \frac{TE_M}{M} \to TE_M = \frac{100}{4} \to 25 = 20 + \frac{80}{M} \to M = 16 \\
  \frac{100}{5} = 20 \to 20 = 20 + \frac{80}{M} \to M = 0
$$
  - Em quanto tempo preciso melhorar a velocidade da multiplicação para rodar 4 vezes mais rápido? e 5 vezes mais rápido?
    - **Em 4x, vamos precisar melhorar 16 vezes. Em 5x, não vamos conseguir fazer melhoria nas instruções de multiplicação**
  

- Suponha que melhoramos um computador para realizar todas as operações de ponto flutuante 5 vezes mais rápidas. O tempo de execução de um benchmark antes da melhoria é de 10 segundos.
$$
TE = 10s, TE_m = 5s, TE_s = 5s, M = 5\\
TE_F = 5 + \frac{5}{5} = 6 \\
SpeedUP = \frac{TE}{TE_F} \to SPeedUP = \frac{10}{6} = 1,6667
$$
  - Qual será a aceleração (speedup) se a metade de 10 segundos é gasta executando operações de ponto flutuante?
    - **1,6667 vezes mais rápido que a máquina antiga**

- Estamos procurando um benchmark para mostrar a nova unidade de ponto flutuante descrita acima e queremos um benchmark que mostre um speedup de 3. Estamos considerando que roda em 100 segundos com o hardware antigo.
$$
TE = 100, TE_F = \frac{100}{3}\\
\frac{100}{3} = 100 - x + \frac{x}{5} \to x = 83,33
$$
  - Quanto tempo de execução as instruções de ponto flutuante teriam que levar em conta neste programa para gerar a aceleração desejada nesse benchmark?
    - **83,33 segundos deveriam ser somente para executar instruções de ponto flutuante para conseguirmos o tempo de execução 3x mais rápido.**

## Resumo
- Desempenho é específico à um programa
  - Tempo de execução total é um resumo consistente de desempenho
- Um dado aumento de desempenho da arquitetura ocorre:
  - Aumento na velocidade de clock
  - Melhorias na organização do processador que reduz o CPI
  - Melhorias no compilador que reduz o CPI e/ou a quantidade de instrução
- **Armadilha**: esperar que a melhoria em um aspecto do desempenho da máquina afete o desempenho total.