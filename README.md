# Trabalhando-com-Spark
Neste repositório trabalharemos com processamento de dados usando Spark.

Primeiro iremos entrar com uma base teórica, depois vamos para implementação de um projeto.

## Tabela de Conteúdo

- [Processamento em Batch](#Processamento-em-Batch)
- [Processamento em Streaming](#Processamento-em-Streaming)
- [Arquiteturas de Processamento de Dados em Larga Escala](#Arquiteturas-de-Processamento-de-Dados-em-Larga-Escala)
- [Introdução ao Apache Spark](#Introdução-ao-Apache-Spark)
- [DataBricks](#DataBricks)


## Processamento em Batch

O processamento em Batch envolve a execução de operações em um conjunto fixo de dados, coletados ao longo de um período de tempo. Ao contrário do processamento em streaming, em que os dados são processados em tempo real, o processamento em lote lida com volumes de dados maiores, geralmente em intervalos programados.

### Exemplo Prático

Suponha que esteja analisando dados de vendas de uma loja online. Com o processamento em batch, poderíamos executar análises diárias ou semanais, processando todas as transações acumuladas nesse período. Isso é útil para relatórios periódiocos, geração de insights hitóricos e otimização de recusos.

### Características Principais:

- **Eficiência:** Adequado para grandes volumes de dados que podem ser processados de uma vez

- **Planejamento:** As operações são programadas para serem executadas em intervalos específicos.

### Conclusão

O processamento em Batch é eficaz para tarefas que não exigem resposta em tempo real e permite o processamento eficiente de grandes conjuntos de dados em momentos específicos. É comumente utilizado em cenários que demandam análises retrospectivas e relatórios periódicos.


## Processamento em Streaming

O processamento em streaming é uma abordagem dinâmica para lidar com dados em tempo real. Ao contrário do processamento em lote, onde os dados são processados em grupos, o streaming permite a análise contínua à medida que os dados são gerados.

### Exemplo Prático

Imagine um app de análise de redes sociais que atualiza em tempo real a contagem de likes ou retweets. Com o processamento em streaming, cada interação do usuário é processada assim que ocorre, permitindo uma exibição em tempo real das métricas de engajamento.

### Características Principais:

- **Latência Baixa:** Respostas quase instantâneas às mudanças nos dados.

- **Monitoramento Contínuo:** Ideal para sistemas que exigem atualizações constantes.

- **Detecção de Padrões em Tempo Real:** Permite identificar tendências e eventos imediatamente. 

### Conclusão

O processamento em streaming é essencial para cenários onde a análise em tempo real é crucial, como monitoramento de Iot, análise de dados de tráfego na web ou detecção de froudes em transações financeiras.


## Arquiteturas de Processamento de Dados em Larga Escala.

As arquiteturas Lambda e Kappa são duas abordagens distintas para projetar sistemas de processamento de dados em larga escala, especialmente em ambientes onde há necessidade de lidar com grandes volumes de dados. Vamos explorar cada uma delas e destacar as diferenças.

### Arquitetura Kappa

A arquitetura Kappa é um modelo de arquitetura para sistemas de processamento de dados em tempo real. Ela foi proposta como uma alternativa à arquitetura Lambda, simplificando o design e mantendo a capacidade de lidar com fluxos contínuos de dados.

#### Características Principais da Arquitetura Kappa

- **Unified Stream Processing:** Diferentemente da arquitetura Lambda, que separa o processamento em lote e em tempo real, a arquitetura Kappa unifica ambos sob um único sitema de processamento de stream.

- **Simplicidade:** A principal ideia por trás da arquitetura Kappa é simplificar a infraestrutura, removendo a necessidade de ter sistemas distintos para processamento em lote e em tempo real.

- **Processamento de Eventos:** O processamento de eventos é o foco principal. Todos os dados, incluindo dados históricos, são tratados como eventos de streaming contínuo.

- **Imutababilidade:** Os dados são considerados imutáveis. Em vez de atualizar registros existentes, novos ecentos são adicionados ao stram, facilitando a escalabilidade e a consistência.

#### Para que serve a Arquitetura Kappa.

Essa arquitetura é especialmente útil em casos em que:

- **Baixa Latência é Crucial:** Situações em que a necessidade de resposta em tempo real é fundamental, como em sistemas de monitoramento, análise de tráfego em tempo real ou detecção de fraudes.

- **Simplicidade é Prioridade:** Projetos que buscam uma arquitetura mais simples e menos complexa, evitando a necessidade de gerenciar sistemas separados para processamento em lote e em tempo real.

- **Escalabilidade é Necessaria:** Aplicações que precisam escalar facilmente para lidar com volumes crescentes de dados, aproveitando a natureza distribuída do processamento de streaming.

#### Exemplo:

![Arquitetura Kappa](prints/1.png)

#### Conclusão:

A arquitetura Kappa, ao focar em processamento de eventos em tempo real e simplificar a infraestrutura, é adequada para casos de uso que demandam agilidade, baixa latência e capacidade de expansão em ambientes dinâmicos de dados.

### Arquitetura Lambda

A arquitetura Lambda foi proposta para lidar com as limitações encontradas em sistemas de processamento em tempo real, reconhecendo a importância de ter uma camada de processamento em lote para tarefas como ETL (extração, transformação e carga) e processamento histórico.

#### Características Principais da Arquitetura Kappa

- **Camadas Distintas:** Divide o processamento de dados em duas camadas principais: a camada de batch (em lote) e a camada de stream (em tempo real).

- **Processamento em Lote::** Utiliza sistemas de processamento em lote para análises históricas e ETL, garantindo a consistência e confiabilidade dos dados.

- **Processamento em Tempo Real:** Incorpora um sistema de processamento de stream para lidar com dados em tempo real, permitindo análises em tempo real e respostas a eventos instantâneas.

#### Para que serve a Arquitetura Lambda.

- **Necessidade de Análises Históricas::** Quando é necessário analisar grandes volumes de dados históricos.

- **Garantia de Consistência::** Em cenários em que a consistência entre dados históricos e em tempo real é crítica.

- **Suporte a ETL Complexo::** Para processar dados brutos e transformá-los em formatos mais úteis.

#### Exemplo:

![Arquitetura Lambda](prints/2.png)

#### Conclusão:

A escolha entre arquitetura Lambda e Kappa dependerá das necessidades específicas do projeto, priorizando fatores como latência, consistência, complexidade e tipo de análise de dados realizada.


## Introdução ao Apache Spark.

O Apache Spark é um poderoso framework open source para processamento de dados distribuído e escalável. Projetado para oferecer alto desempenho e facilidade de uso, o Spark é amplamente utilizado em diversas aplicações de processamento de dados em larga escala. Aqui estão algumas características e conceitos-chave relacionados ao Apache Spark:

- **Processamento em Memória:** O Spark é conhecido por seu modelo de processamento em memória, que permite armazenar dados na RAM, proporcionando um processamento significativamente mais rápido em comparação com sistemas que dependem principalmente de disco.

- **APIs Abertas:** Oferece APIs em várias linguagens, incluindo Scala, Java, Python e R, o que facilita a integração com diferentes ecossistemas e permite que os desenvolvedores escolham a linguagem de programação de sua preferência.

- **Resiliente e Tolerante a Falhas:** O Spark é projetado para ser tolerante a falhas e resiliente. Se ocorrerem falhas em um nó, o Spark pode recuperar os dados perdidos automaticamente, garantindo a continuidade do processamento.

- **DAG (Directed Acyclic Graph):** O Spark executa operações em um grafo acíclico direcionado (DAG), permitindo a otimização das operações. As transformações são planejadas e otimizadas antes da execução real.

- **Módulos e Bibliotecas:** Além do processamento de dados em lote (Batch Processing), o Spark oferece módulos para processamento de stream em tempo real (Structured Streaming), aprendizado de máquina (MLlib), processamento de gráficos (GraphX) e consultas SQL (Spark SQL).

- **Suporte a Diversas Fontes de Dados:** O Spark suporta várias fontes de dados, incluindo Hadoop Distributed File System (HDFS), Apache Cassandra, Apache HBase, Amazon S3, entre outras, tornando-o flexível para integração com diversos sistemas de armazenamento.

- **Cluster Manager:** Pode ser executado em diversos gerenciadores de cluster, como Apache Mesos, Hadoop YARN e o gerenciador de cluster próprio chamado Spark Standalone.


## DataBricks.

Databricks é uma plataforma de análise de dados baseada em nuvem, centrada no suporte ao Apache Spark. Oferece um ambiente colaborativo de notebook interativo para cientistas de dados e engenheiros trabalharem juntos. Além do processamento em lote, suporta processamento de stream em tempo real. Integra-se a ecossistemas de dados, como Delta Lake e serviços de nuvem. Fornece automação, segurança avançada, escalabilidade na nuvem e recursos integrados de machine learning. É agnóstico de nuvem, oferecendo suporte a AWS, Azure e Google Cloud. Databricks é amplamente utilizado para análise de dados e desenvolvimento de big data na nuvem.

### Criando uma conta no DataBricks.

Crie uma conta no dataBricks utilizando a opção community cloud. 

### Criando cluster no DataBricks

Crie um cluster na plataforma, acessando na barra lateral a opção `+` logo em seguida `Cluster` como no print:

![Cluster DataBricks](prints/3.png)

Compute name: `cluster_spark_1`
Databricks runtime version: `Runtime: 13.1 ML`

Clique em create cluste e aguarde alguns minutos.







