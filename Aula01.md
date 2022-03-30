# Apresentação da Disciplina

- Professor: Leandro Santiago
- Email: leandro@ic.uff.br

Geralmente as atividades vão ser a cada 3 semanas.

- relembrar sistemas de memória.
- Modelos de implementação.
- é importante conhecer o desenvolvimento de processadores, para podermos ter conhecimentos em IOT...
- Vamos ver Assembly novamente.
- é meio que uma revisão de FAC, só que mais aprofundada.
- Computer Organization and Arhitecture é a literatura complementar.

## Motivação e conceitos básicos

### Lei de Moore
"A densidade de transitores nos circuitos integrados dobra a cada dois anos"

Mais transistores igua a:
- Maior conectividade
  - Número de conexões cresce quadraticamente com o número de unidades funcionais
- Dissipação de calor
  - gerência do uso de energia
- Sincronização (Clock)
- Variabilidade do substrato (silício)
  
### Multicores
- Fim da era de ILP (paralelismo a nível de instruções)
- Só nos resta o TLP (thread level parelism)
- Muitos núcleos afim de aproveitar a maior densidade de transistores
- Programador responsável por obter desempenho (antes era só trocar de hardware):
  - Mudança de paradigma
  - Parelelização automática ou assistida?
  - Paralelismo em nível de instrução (ILP)
    - memória Transacional
  - Data-flow

### Cores mais simples
- Graphics Processing Units (GPUs)
  - Aceleradores gráficos
  - NVIDIA, AMD/ATI

- General Purpose GPUs (GPGPUs)
  - Programáveis em subconjunto do C
  - CUDA (NIVIDIA)
  - OpenCL (NVIDIA e ATI)


### Clusters
- Agregado de máquinas off-the-shelf realizando processamento paralelo
  - Beowulf (NASA, 1994)
  
### Grids
- Grade Computacional (Grid computing)
  - Analogia com a malha elétrica:
    - Usuários podem ceder ou consumir "energia" computacional
- União Voluntária
  - SETI@home (Search for ET intelligence)
  - PS3grid/GPUgrid
- Tarifação: cloud  computing
  - Amazon Elastic Compute Cloud (Amazon EC2)
  - Microsoft Azure
  - Google Cloud Platform
  - Não somente infraestrutura (IaaS), como também software (SaaS) e plataformas (PaaS)

## Definições

### Processo:
  - "Um programa em execução" - A.S. Tanembaum
  - "A entidade que pode ter sua execução atribuída a um processador" - W. Stallings
  - Dentro de processo, temos 3 pricipais conceitos: **Contexto de software, Contexto de Hardware e Espaço de Endereçamento**
  - Para criar um novo processo temos o "fork" no linux

### Threads
  - Linhas de execução, também chamadas de lightweight processes
  - Processos leves que compartilham espaço de endereçamento de memória

### Paralelismo
  - Situação em que as coisas acontecem ao mesmo tempo

### Concorrência
 - Situação onde há competição por recursos, indicando potencial paralelismo
 - Havendo recursos suficientes, haverá paralelismo

### Distribuição (vs Centralização)
- Não centralização do controle (da administração dos recursos por parte dos processos)

### Distribuição (Geográfica)
- Pode existir sob controle hierarquizado ou mesmo centralizado.

### Multiprocessamento
- Vários processos (threads) executando em paralelo.
- Pressupõe a disponibilidade de mais de um processador (núcleo)
  
### Multiprogramação
- Vários programas compartilhando a mesma máquinas
- Conceitos ligado aos de compartilhamento de tempo (time-sharing), suspensão de execução e concorrência
  
### Algoritmo distribuído
- Envolve elementos cooperando através de troca de informações, sem uma orquestração centralizada.
- O código de cada elemento pode ser o mesmo, ou podem existir diferenças

### Sistema distribuído
- "Uma coleção de computadores independentes que aparece para os usuários do sistema que os rege com um único computador (entidade)" - A.S. Tanembaum
  
## Dualidades
- Na computação
  - O bit: 0 ou 1
  - Hardware - Software
  - Real - Virtual
  - Sequencial - Paralelo
  - Centralizado - Distribuído
  - Memória - Processador
  - Dado - Processamento
  - Mono - Multi
  - Mensagem - Passo (na rede)
  - Comunicação - Execução
  - Síncrono - Assíncrono