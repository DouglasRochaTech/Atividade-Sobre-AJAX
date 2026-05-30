# Comparação: XHR, Fetch, Promises e Async/Await

## 1. Conceitos Fundamentais

### XMLHttpRequest
A XMLHttpRequest, frequentemente abreviada como XHR, é uma API fundamental que permite a comunicação assíncrona entre o cliente e o servidor na web [^1]. Essa tecnologia é amplamente utilizada para criar aplicações web dinâmicas, permitindo que os desenvolvedores carreguem dados em segundo plano sem a necessidade de recarregar a página inteira [^1]. Isso resulta em uma experiência de usuário mais fluida e interativa, essencial para aplicações modernas que exigem atualizações em tempo real, como redes sociais, plataformas de e-commerce e serviços de streaming [^1].

### Fetch API
A API Fetch fornece uma interface JavaScript para acessar e manipular partes do pipeline HTTP, tais como os pedidos e respostas [^2]. Ela fornece o método global `fetch()` que oferece uma maneira fácil e lógica para buscar recursos de forma assíncrona através da rede [^2]. Este tipo de funcionalidade era obtida anteriormente utilizando o XMLHttpRequest [^2]. O Fetch fornece uma alternativa melhor que pode ser facilmente utilizada por outras tecnologias como Service Workers, e provê um lugar lógico único para definir outros conceitos relacionados ao protocolo HTTP, como CORS e extensões [^2].

### Promises
Uma Promise é um objeto que representa a eventual conclusão ou falha de uma operação assíncrona [^3]. Essencialmente, uma promise é um objeto retornado para o qual você adiciona callbacks, em vez de passar callbacks para uma função [^3]. Ao contrário dos callbacks com retornos de funções antigas, uma promise vem com algumas garantias [^3]:
* Callbacks nunca serão chamados antes da conclusão da execução atual do loop de eventos do JavaScript.
* Callbacks adicionados com `.then()` serão chamados mesmo depois do sucesso ou falha da operação.
* Múltiplos callbacks podem ser adicionados chamando-se `.then()` várias vezes, para serem executados independentemente da ordem de inserção.

### Async/Await
Async e Await são as duas palavras-chave que ajudam a programar de forma assíncrona [^4]. Usamos a palavra-chave `async` com uma função para representar que a função é assíncrona [^4]. A palavra-chave `await` é usada dentro da função `async` para aguardar a operação assíncrona ser concluída [^4]. O `await` significa suspender a execução do método assíncrono em que está sendo executado até que a tarefa seja concluída [^4]. Após a suspensão, o controle volta para o método invocador da função [^4].

## 2. Descrição das Diferenças
Existem formas distintas de realizar comunicações assíncronas no JavaScript. O XMLHttpRequest (XHR) é a tecnologia mais antiga e baseia-se em um sistema complexo de eventos e estados que exige controle manual de variáveis. Já a Fetch API foi introduzida como uma alternativa moderna e nativa, construída sobre o conceito de Promises, que são objetos que representam a eventual conclusão ou falha de uma operação assíncrona. Enquanto as Promises permitem o encadeamento linear de passos através do método .then(), o Async/Await oferece uma camada sintática que torna o código assíncrono visualmente idêntico ao código síncrono. Esta última opção simplifica o tratamento de erros, permitindo o uso da estrutura tradicional try/catch em vez de múltiplos blocos de captura.

## 3. Desempenho (Velocidade)
A diferença de performance entre os métodos de comunicação assíncrona é mínima na maioria dos casos.

Embora existam diferenças técnicas em como cada um é processado pelo motor do navegador, o impacto no tempo final de resposta para o usuário é desprezível. O tempo de execução de qualquer uma dessas funções é medido em microssegundos, enquanto o tempo gasto com a rede e o processamento do servidor representa a vasta maioria do atraso percebido. Portanto, para o desenvolvimento de aplicações web, a escolha do método não altera significativamente a performance da aplicação.

## 4. Facilidade de Uso e Legibilidade
A diferença real entre as abordagens está na manutenção e na clareza do código.

### XMLHttpRequest
Apresenta baixa legibilidade. Exige a escrita de muitas linhas de código para operações simples, além da necessidade de monitorar manualmente os códigos de estado (readyState == 4 e status == 200). Quando há requisições dependentes em sequência, o código tende a se tornar confuso rapidamente (Callback Hell).

### Promises
Corrigiram os problemas de aninhamento do XHR ao introduzir o encadeamento com o método .then(). O fluxo de execução passa a ser lido de forma estritamente vertical. Caso ocorra uma falha em qualquer etapa do processo, a execução é desviada diretamente para o bloco .catch() no final.

### Fetch API
Tornou o consumo de dados mais intuitivo, pois o navegador fornece a função fetch() de forma nativa, criando as Promises automaticamente. O único ponto de atenção é que o fetch não rejeita a Promise em caso de erros HTTP do servidor (como 404 ou 500); o desenvolvedor precisa validar isso manualmente via if (!response.ok).

### Async/Await
É o padrão mais utilizado no desenvolvimento moderno. Em vez de encadear métodos .then(), utiliza-se a palavra-chave await antes da requisição, fazendo com que o JavaScript aguarde a resolução da linha antes de prosseguir. O código se torna mais limpo e o tratamento de erros utiliza a estrutura try/catch, comum em diversas linguagens de programação.

### Alunos:
- Pedro Henrique Coelho Lima;
- Douglas Rocha Vasco; 
- Raphael Alves Mendes; 
- Jonas Santos Barbosa; 
- Calebe Bezerra Feitosa;  
- Tiago de Andrade Lima;

## Referências
[^1]: [Mina Criativa. O que é: XMLHttpRequest (Requisição XMLHttp).](https://minacriativa.com.br/glossario/o-que-e-xmlhttprequest-requisicao-xmlhttp/)
[^2]: [MDN Web Docs. Usando Fetch - APIs da Web.](https://developer.mozilla.org/pt-BR/docs/Web/API/Fetch_API/Using_Fetch)
[^3]: [MDN Web Docs. Usando promises - JavaScript.](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Using_promises)
[^4]: [Baradel, L. Async/await: funções assíncronas no Javascript! Medium.](https://lucasbaradel.medium.com/async-await-fun%C3%A7%C3%B5es-ass%C3%ADncronas-no-javascript-85768f3460fa)
