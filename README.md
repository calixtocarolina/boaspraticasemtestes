# Boas práticas e Estratégias de Testes :robot:

### A pirâmide de Testagem

Quando pensamos em uma estratégia para testar, existem três aspectos principais a se considerar, sendo eles:

1. **Escopo:** Qual é o alcance do teste em seu código? Testes podem executar apenas um método, percorrendo toda a aplicação, ou o escopo pode definir o quanto o método pode percorrer em seu código.
2. **Velocidade:** Em qual velocidade o seu teste executa? A velocidade dos testes varia de milissegundos até alguns minutos.
3. **Fidelidade:** Quão próximo da realidade está o teste? Por exemplo, se a parte do código em que seu teste cobre precisa realizar uma requisição de network, o teste de código realmente faz essa requisição ou ele mascara o resultado? Se a resposta for que o teste faz a comunicação com a network, isso significa que ele precisa de uma maior fidelidade. Essa é uma “troca” que se deve considerar ao escrever um teste pois muitas variáveis estão em jogo, como o custo, o tempo de execução da tarefa e questões externas (caso, nesse exemplo, a network esteja indisponível).

Algumas “trocas” são inerentes ao pensar estrategicamente em criar testes - quanto mais veloz for a execução de seu código, menor a sua fidelidade, e vice-versa. Uma forma comum de dividir os testes é nessas três categorias:

1. **Testes unitários:** Esse tipo de teste é altamente focado em executar uma única classe, geralmente invocando apenas um método nessa classe. Se o teste unitário falha, é então possível saber exatamente onde está o erro em seu código. Porém, os testes unitários não possuem alta fidelidade, uma vez que no “mundo real” uma aplicação envolve muito mais do que a execução de um único método ou classe. Eles são velozes para executar toda vez que há mudanças em seu código e estão localizados no <code>test</code> source.
2. **Testes de integração:** Testam a interação entre diversas classes para se certificar que se comportem como o esperado quando utilizadas em conjunto. Uma forma de estruturar os testes de integração é testar uma única funcionalidade, testando um escopo maior que os testes unitários mas ainda assim otimizados para executar rapidamente. Podem ser localizados tanto localmente quanto ou como em testes de instrumentação, dependendo do tipo de situação.
3. **Testes End-to-end (E2e):** Estes testes são usados para testar uma combinação de funcionalidades trabalhando juntas. Testam uma grande porção da aplicação, simulando o real uso e, portanto, geralmente são lentos. Possuem alta fidelidade e mostram como a aplicação funciona como um todo. Estes testes podem ser encontrados nos testes de instrumentação (no <code>androidTest</code> source).

É uma recomendação que a maior parte de seus testes sejam unitários, como o ilustrado abaixo:
![imagem com uma pirâmide com E2e no topo, testes de integração em seu meio e testes unitários na base](https://talented-exception-f09.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F25d5612b-305e-45a3-b15f-6a567588f13e%2FUntitled.png?id=78d3718f-2e41-4047-b371-54507dc8b729&table=block&spaceId=e9121651-b6f3-42e8-b52c-beb687ad4949&width=2000&userId=&cache=v2)

É também importante dizer que a pirâmide de testagem funciona bem se a sua própria aplicação seguir uma arquitetura, pois ambos os conceitos estão inerentemente ligados. Caso sua aplicação siga um bom padrão de arquitetura, ficará mais fácil e lógico fazer testes unitários e de integração, uma vez que pode-se testar uma única unidade ou funcionalidade dentro do código.
Um padrão simples e seguindo boas práticas de arquitetura de aplicação está ilustrado abaixo:
![imagem contendo uma arquitetura padrão de aplicação, com activity, fragments, view model, repository e camadas de data (network e database)](https://talented-exception-f09.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2cde8fbb-156a-4966-9c87-d9d3037e0f5e%2FUntitled.png?id=51463918-37a0-4ab3-ab1b-f50f79dd2b94&table=block&spaceId=e9121651-b6f3-42e8-b52c-beb687ad4949&width=2000&userId=&cache=v2)

Fonte das imagens: [Google Codelabs](https://codelabs.developers.google.com/)

Esse conteúdo foi adaptado e traduzido para o português por Carolina Alexandre Calixto e está disponível em inglês no treinamento da Google Codelabs para Testes Unitários. Espero que tenham gostado! :heart:
