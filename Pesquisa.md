#Comparação: XHR, Fetch, Promises e Async/Await

##1. Descrição das Diferenças
Existem formas distintas de realizar comunicações assíncronas no JavaScript. O XMLHttpRequest (XHR) é a tecnologia mais antiga e baseia-se em um sistema complexo de eventos e estados que exige controle manual de variáveis. Já a Fetch API foi introduzida como uma alternativa moderna e nativa, construída sobre o conceito de Promises, que são objetos que representam a eventual conclusão ou falha de uma operação assíncrona. Enquanto as Promises permitem o encadeamento linear de passos através do método .then(), o Async/Await oferece uma camada sintática que torna o código assíncrono visualmente idêntico ao código síncrono. Esta última opção simplifica o tratamento de erros, permitindo o uso da estrutura tradicional try/catch em vez de múltiplos blocos de captura.

##2. Desempenho (Velocidade)
A diferença de performance entre os métodos de comunicação assíncrona é mínima na maioria dos casos.

Embora existam diferenças técnicas em como cada um é processado pelo motor do navegador, o impacto no tempo final de resposta para o usuário é desprezível. O tempo de execução de qualquer uma dessas funções é medido em microssegundos, enquanto o tempo gasto com a rede e o processamento do servidor representa a vasta maioria do atraso percebido. Portanto, para o desenvolvimento de aplicações web, a escolha do método não altera significativamente a performance da aplicação.

##3. Facilidade de Uso e Legibilidade
A diferença real entre as abordagens está na manutenção e na clareza do código escrito.

###XMLHttpRequest
Apresenta baixa legibilidade. Exige a escrita de muitas linhas de código para operações simples, além da necessidade de monitorar manualmente os códigos de estado (readyState == 4 e status == 200). Quando há requisições dependentes em sequência, o código tende a se tornar confuso rapidamente (Callback Hell).

###Promises
Corrigiram os problemas de aninhamento do XHR ao introduzir o encadeamento com o método .then(). O fluxo de execução passa a ser lido de forma estritamente vertical. Caso ocorra uma falha em qualquer etapa do processo, a execução é desviada diretamente para o bloco .catch() no final.

###Fetch API
Tornou o consumo de dados mais intuitivo, pois o navegador fornece a função fetch() de forma nativa, criando as Promises automaticamente. O único ponto de atenção é que o fetch não rejeita a Promise em caso de erros HTTP do servidor (como 404 ou 500); o desenvolvedor precisa validar isso manualmente via if (!response.ok).

###Async/Await
É o padrão mais utilizado no desenvolvimento moderno. Em vez de encadear métodos .then(), utiliza-se a palavra-chave await antes da requisição, fazendo com que o JavaScript aguarde a resolução da linha antes de prosseguir. O código se torna mais limpo e o tratamento de erros utiliza a estrutura try/catch, comum em diversas linguagens de programação.