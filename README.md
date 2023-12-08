# Trabalhando-com-Spark
Neste repositório trabalharemos com processamento de dados usando Spark.

Primeiro iremos entrar com uma base teórica, depois vamos para implementação de um projeto.

## Tabela de Conteúdo

- [Processamento em Batch](#Processamento em Batch)
- [Processamento em Streaming](#Processamento em Streaming)


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

