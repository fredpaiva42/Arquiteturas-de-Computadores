# Entendendo Desempenho

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