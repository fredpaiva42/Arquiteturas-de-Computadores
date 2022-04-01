# Arquitetura e Organização de Computadores

## Arquitetura vs Organização

### Arquitetura
- Atributos do sistema visíveis ao programador
- Tem impacto direto na execução lógica de um programa
- Atributos arquiteturais
  - Instruction Set Architecture (**ISA**) define o formato das instruções, opcodes, registradores, instruções, memória de dados
  - Conjunto de instrução do processador
  - n bits usados para representar os tipos de dados
  - mecanismos de I/O
  - Técnicas para endereçamento de memória

### Organização
- Forma pela qual as unidades operacionais se interligam para cumprir aquilo que é exigido pela arquitetura
- Atributos organizacionais
  - Detalhes de hardware transparente para o programador, sinais de controle, interfaces entre computador e periféricos, tecnologia de memória usada.

## Estrutura e Função

### Estrutura
- Modo que os componentes se relacionam entre si

### Função
- Operação de componentes individuais que são parte da estrutura
  
- Natureza hierárquica dos sistemas complexos é essencial descrição e o projeto
- Projetista só precisam lidar com um nível particular do sistema por vez
  - Responsável com a estrutura e função de cada nível

## Função
- O computador executa 4 tipos de funções básicas

### Processamento de dados
- Dados possuem varías formas e requisitos de processamento

### Armazenamento de Dados
- Short-term: Memória RAM, Cache
- Long-term: HD, SSD

### Movimentação de dados
- I/O: Quando os dados são recebidos de um ou entregue para um dispositivo (periférico) que é diretamente conectado aos computadores
- Comunicações de dados - Quando os dados são movidos para longas distâncias, de ou para um dispositivo remoto

### Controle
- Uma unidade de controle gerencia os recursos computacionais e orquestra o desempenho de suas partes funcionais em resposta para instruções
  
## Estrutura
- Os 4 Principais Componentes Estruturais

- CPU: controla a operação do computador e execução das funções de processamento de dados
- Memória Principal: Armazena dados
- I/O: Move os dados entre o computador e seu ambiente externo
- Interconexão de Sistema: mecanismos que são usados para comunicação entre CPU, memória principal e I/O

### Componentes estruturais da CPU
- Unidade de controle
  - Controla a operação da CPU e portanto do computador
- Unidade Lógica e Aritmética (ALU)
  - Executa a função de processamento de dados do computador
- Registradores
  - Armazenamento interno da CPU
- Interconexão da CPU
  - Mecanismos de comunicação entre as unidades de controle, ALU e registradores

### Estrutura de Computador Multicore
- Central Processing Unit (CPU)
  - Porção do computador que busca e executa instruções
  - consiste basicamente na ALU, uma unidade de controle e registradores
  - É chamado de processador em sistema com uma unidade de processamento (single core)
- Core
    - Uma unidade de processamento num chip de processador
    - Equivalente em funcionalidade de uma CPU em sistema single core
    - Unidades de processamento especializadas também são chamadas de cores
- Processador
  - Pedaço físico de silício contendo um ou mais cores
  - Componente do computador que interpreta e excecuta as instruções
  - Chamado de processador multicore se contém múltiplos cores
  
### Memória Cache
- Múltiplas camadas de memória entre o processador e memória principal
- Menor e mais rápida que a memória principal
- Usada para acelerar o acesso da memória, movendo os dados da memória principal para cache que provavelmente serão usadas no futuro
- Maior melhoria de desempenho pode ser obtida usando múltiplos níveis de cache:
  - Level 1 (L1) mais próximo dos cores
  - L2, L3, etc. se distancia progressivamente de um core
  
## Conceitos

### Computador Digital
- Máquina que resolve problemas executando uma série de instruções
- Máquina programável

### Programa
- Sequência de instruções que descrevem como executar uma tarefa

### Linguagem de Máquina
- Conjunto de instruções básicas executadas por circuitos eletrônicos
- Linguagem binária

## Instruction Set Architecture (ISA)
- Importante abstração do Computador Digital
- Interface entre hardware e o nível mais do software
- Instruções padronizadas, padrão de bits para linguagem de máquina
- **Vantagem:** Permite diferentes implementações da mesma arquitetura
- **Desvantagem:** As vezes dificultam adicionar inovações
- ISA modernas
  - 80x86/86x64, PowerPC, DEC Alpha, MIPS, SPARC, HP, ARM

### Arquitetura de Computador
- ISA + Organização de Máquina
  
## Máquinas Multi-Níveis
- diferentes camadas ou níveis de abstração
- **Nível ou Camada:** uma máquina (computador real ou virtual) e sua linguagem correspondente, sobre a qual uma nova camada pode ser acrescentada
- Nível (linguagem) mais baixo é o mais simples e o nível mais alto é mais sofisticado

![](./imgs/Máquinas%20multiniveis.png)

- Cada máquina virtual tem associada a si uma linguagem, composta por todas as instruções que ela pode executar
- **Máquina define uma linguagem. Uma linguagem define uma máquina**
- Vantagens
  - Computador com n níveis pode ser visto com n máquinas virtuais distintas
  - Programador que desenvolve programas para máquina virtual de nível k, não precisa conhecer os detalhes dos níveis inferiores
  - Estrutura hierárquica possibilita flexibilidade e independência ao usuário

*"Maioria dos computadores modernos possui dois ou mais níveis, sendo que máquinas com seis ou mais níveis são cada vez mais comuns."*
### Nível dos dispositivos (-1)
- Situado abaixo do nível 0
- Microeltrônica
- Características físicas
- Malha de transistores
- Tecnologias de fabricação de circuitos integrados

### Nível da lógica digital (0)
- Composto pelo hardware da máquina
- Executa diretamente as instruções (ou micro-instruções) submetidas pelo nível 1
- Portas lógicas
  - Dispositivos digitais cosntuídos a partir de componentes analógicos
- Combinação de portas lógicas
  - Funções aritméticas
  - Memórias (registradores)
  - Processadores

### Nível da Microarquitetura (1)
- Conceito de programa como uma sequência de instruções a serem executadas diretamente pelos circuitos eletrônicos
- Enxerga-se os componentes da CPU: ALU, Unidade de controle e registradores
- Algumas arquiteturas, possuem microprogramas
  - Controla a operação do caminho de Dados
  - Interpreta as instruções de nível 2, executando-as em seguida
  - Controle por software ou hardware
  - **Vantagens**
    - Facilita o projeto e construção dos circuitos digitais
    - Possibilita o desenvolvimento de instruções mais potentes

### Nível ISA (2)
- Nível convencional da máquina
- Define o conjunto das instruções executáveis por uma máquina (processador) -  Linguagem de Máquina
- Pode ser vista como verdadeira interface entre o software e hardware
- Discute-se
  - Tipo de Dados
  - Modelos de Memória e de Endereçamento
  - Formato e Tipos de Instruções

### Nível do Sistema Operacional (3)
- Suporta um conjunto de novas instruções, uma Organização diferente da memória, capacidade de rodar dois ou mais programas de forma simultânea, entre outros
- Fornece serviços básicos para os níveis acima: interface (gráfica ou linha de comando), gerenciamento de memória, etc.
- **Níveis abaixo:** dirigidos aos programadores de sistema
  - Programadores que projetam máquinas virtuais / interpretadores/ tradutores
- **Níveis acima:** dirigidos aos programadores de aplicações
  - Programadores com problemas a serem solucionados
  - Linguagens contendo palavras e abreviações

### Nível de Linguagem de Montagem (Assembly) (4)
- Forma simbólica de representação das linguagens dos níveis mais baixos
- Provê métodos para pessoas escreverem programas para os níveis 1, 2 e 3 de maneira mais "confortável".
- Programas escritos em linguagem de montagem são primeiramente traduzidos para a linguagem dos níveis 1, 2 ou 3, e depois interpretados
- **Montador (assembler):** programa que traduz programas em linguagem de montagem para uma linguagem do nível 1, 2 e 3

### Nível de linguagens de alto nível (5)
- Linguagens projetadas para serem utilizadas por programadores de aplicação com problemas a serem resolvidos
- Programas escritos nessas linguagens são geralmente traduzidos para o nível 3 ou 4 por tradutores conhecidos como compiladores, embora às vezes sejam interpretados (como no caso de Java)

### Acima do nível 5
- Encontram-se coleções de programas projetados para criar máquinas especialmente adequadas para certas aplicações (ou domínios), contendo grandes quantidades de informação acerca da aplicação
- Máquinas virtuais voltadas às aplicações
  - Administração, Educação, realidade virtual, emulador de consoles, etc.
- Níveis variam dependendo do projeto de arquitetura
  
## Hardware
- Composto por objetos tangíveis: circuitos integrados, placas de circuito impresso, cabos, fonte de alimentação, etc.

## Software
- Composto de instruções, algoritmos e por suas representações computacionais: os programas

## Firmware
- Software embarcado (embutido no dispositivo durante a fabricação)
- Controla o hardware diretamente. Ex: BIOS (Basico Input/Output System)
  
![](imgs/Hierarquia%20Hardware%20Software%20e%20Firmware.png)

## Execução de um Programa

### Compilador
- Programa que recebe como entrada arquivos de texto escritos contendo **módulos** escritos em **linguagem de alto nível** e geram como saída um programa em **linguagem de montagem** (ou arquivo objeto) correspondente a cada módulo
- Recebe bibliotecas e módulos, gerando um programa executável
  
### Montador (Assembler)
- Gera um programa em linguagem de máquina a partir de sua versão em linguagem de montagem
- Gera um **arquivo objeto**. Em geral, não pode ser executado diretamente pela máquina por conter referências a sub-rotinas e dados especificados de outros arquivos (bibliotecas)
  
### Ligador (Linker)
- Programas que recebem como entrada arquivos objetos e geram como saída o programa final em linguagem de Montagem
- Gera um programa executável a partir de um ou mais arquivos objetos

### Carregador (Loaders)
- Utilizado para executar um programa
- Parte do sistema operacional - escalonador de médio prazo

## Interpretador
- Recebe como entrada arquivos texto contendo programas em linguagem assembly, linguagem de alto nível ou arquivos binários com instruções de máquina, e os executam diretamente
- Percorrem os programas linha a linha a partir de seu ponto de entrada, executando cada comando
- Processadores são interpretadores implementados em hardware