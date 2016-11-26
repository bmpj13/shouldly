<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/master/ESOF-Docs/resources/images/ShouldlyLogo.png" alt="icon">
</p>
<h1 align="center">Verificação e Validação</h1>

Na *Engenharia de Software*, **verificação e validação (V&V)** define-se como o processo de confirmação de que a aplicação atende os requisitos e especificações do cliente, e que cumpre corretamente o seu propósito.

Este processo, tal como o nome indica, divide-se em duas componentes, apesar de serem complementares:

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/v%26v_difference.jpg">
</p>

- **Verificação**: garantir que os produtos intermédios, e o produto final, cumprem os requisitos especificados, para a fase de desenvolvimento em questão.
  + Questão: *estamos a construir o produto __de forma correta__?*
  + Itens para avaliação:
    - Planeamentos
    - Requisitos especificados
    - Arquitetura do sistema
    - Código
    - Casos de teste
    - Cenários
  + Atividades:
    - Revisões
    - Inspeções
    - *Walktroughs*
    
- **Validação**: garantir que as especificações eram, efetivamente, as pretendidas, e que o *software* cumpre os requisitos do cliente.
  + Questão: *estamos a construir o produto __certo__?*
  + Itens para avaliação:
    - A aplicação propriamente dita
    - Protótipos
  + Atividades:
    - Prototipagem
    - Receber *feedback*
    - Analisar o objetivo do *software*

<br>
O processo **V&V** segue o modelo *V-Model*, no que diz respeito às atividades de desenvolvimento da aplicação, ao longo do seu ciclo de vida:
<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/v%26v_model.png">
</p>

<br>
<h3> Testabilidade </h3>
A testabilidade de um *software* caracteriza-se pelo **grau de suporte de testes**, para um certo artefacto da aplicação, num determinado contexto. Se a testabilidade de um artefacto for elevada, então significa que encontrar *bugs* no sistema, via testes, torna-se mais simples e fácil, para além disso, de fácil correção.

Os diferentes testes são usados para descobrir *bugs*, e não garantir a sua ausência; os testes de defeito são testes mais específicos e, deste modo, têm maior probabilidade de encontrar erros; também podem ser usados testes de estatística para verificar o desempenho e a eficiência do programa.

Para as parágrafos seguintes, é importante referir que o **Shouldly** não usa *casos de teste*, mas sim *__cenários de teste__*. A diferença entre os dois reside no facto de um cenário ser um conjunto de casos.

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/test_scenario.png" width=50%>
  <br>
  <sub>Source: blog.testlodge.com</sub>
</p>

Nesta aplicação, os cenários de teste passam por, não só verificar se a asserção passa ou falha, mas também qual a mensagem que será retornada - com e sem *source code* do utilizador.

Por este motivo, nem tudo descrito será diretamente visível nos testes da aplicação. No entanto, é da nossa opinião que as características ilustradas estão presentes.

<br>
A testabilidade de componentes do *software* é determinada por factores como:

- **Controlabilidade**
  + Possibilidade de controlar o estado de uma componente sob teste (CUT)
  
  A controlabilidade do **Shouldly** possui duas facetas. As asserções propriamente ditas são faceis de controlar: controlar o seu estado, i.e. saber quais os passos que executa e qual o resultado que deve devolver, é claro e natural.
  
  Tomando como exemplo o seguinte teste:
  
      [Fact]
      public void ShouldPass()
      {
          new[] { 1, 2, 3 }.ShouldAllBe(x => x < 4);
      }
  
  é constatável a facilidade em criar os *inputs* necessários para a asserção funcionar. A criação de um array com valores inteiros, e a criação de uma condição que se verifica em cada um deles são variáveis da CUT facilmente controláveis.
  
  O problema da controlabilidade torna-se mais claro, no entanto, quando se quer verificar se a asserção falha. Tomando o mesmo contexto do exemplo anterior:
  
      [Fact]
      public void IntegerArrayScenarioShouldFail()
      {
          Verify.ShouldFail(() =>
            new[] { 1, 2, 3 }.ShouldAllBe(x => x < 2, "Some additional context"),

            errorWithSource:
            @"new[] { 1, 2, 3 }
                should satisfy the condition
            (x < 2)
                but
            [2, 3]
                do not
            Additional Info:
                Some additional context",

            errorWithoutSource:
            @"[1, 2, 3]
                should satisfy the condition
            (x < 2)
                but
            [2, 3]
                do not
            Additional Info:
                Some additional context");
      }
  
  Controlar o desfecho da asserção continua a ter o mesmo nível de complexidade. A dificuldade encontra-se na geração da mensagem de erro: na utilização normal do **Shouldly**, a informação que irá substituir a frase *"Some additional context"*. Esta informação adicional depende muitos factores, nomeadamente se está a ser utilizado *source code* para melhorar as mensagens, e também dos argumentos da chamada à função.
  
  Esta geração dinâmica de mensagens torna-se difícil de testar, e dificulta também a previsão do estado da aplicação. 
  
- **Observalidade**
  + Possibilidade de observar resultados de testes, intermédios ou finais.
  
  Para uma CUT do **Shouldly**, determinar se um teste deve falhar ou não, é uma tarefa relativamente fácil, devido à simplicidade do funcionamento da API. Além disso, a recriação de situações específicas, para testar certos estados do programa, também é bastante acessível e descomplicada. 
  
  Por exemplo, é fácil de perceber que
  
      [Fact]
      public void ShouldPass()
      {
         (-7).ShouldBeNegative();
      }
      
  deve ser um teste que passa com sucesso. Seria, também, igualmente fácil criar um teste em que esta mesma asserção falhasse - usando um número positivo.
  
  O facto do **Shouldly** usar cenários de teste, aumenta o grau de dificuldade de recriação de certas situações, nomeadamente asserções que falham - pois é necessário também prevêr a mensagem que deve ser recebida pelo utilizador. Nestes casos, a [documentação](http://docs.shouldly-lib.net/v2.4.0/docs) da aplicação ajuda a prevêr a mensagem que deve ser recebida.
  
- **Isolabilidade**
  + Possibilidade de uma CUT ser testada isoladamente
  
  A isolabilidade das CUTs no **Shouldly** decresce com o grau de dependência de outras componentes.
  
  Por exemplo, a componente *Assertion* utiliza a componente *Exception* (caso a asserção falhe). Para garantir que a asserção está a funcionar como pretendido, deve ser assegurado que a exceção é chamada corretamente, e que retorna os valores esperados. É, portanto, importante que as duas sejam testadas em simultâneo.
  
  Por sua vez, a componente *Exception* recorre à componente *MessageGenerator* para obter as mensagens para o utilizador, pelo que testar o seu correto funcionamento implica recorrer sempre a essa componente. 
  
  A *MessageGenerator*, no entanto, já tem menos grau de dependência, pelo que poderia ser testada isoladamente. Note-se que esta componente tem dependências, mas são de mais baixo nível, facilmente controláveis e têm um relacionamento direto com a componente (*Context* e *DifferencesHighlighter*).
  
  Para simplificar a escrita dos testes, a melhor maneira de implementá-los é usar os cenários de teste, tal como o **Shouldly** utiliza, pois permite que todos os pontos essenciais sejam verificados, para cenários específicos. É necessário, no entanto, garantir que há uma grande cobertura dos diferentes cenários de utilização da aplicação.
  
- **Separação de responsabilidades**
  + Grau de separação de responsabilidades das CUTs - se têm uma única responsabilidade, bem definida
  
  Apesar de haver pouca isolabilidade das componentes (ou, pelo menos, em parte delas), isto não implica que não há uma boa separação de responsabilidades. No **Shouldly**, as componentes possuem um propósito bem definido - em termos gerais, cada componente tem garantia que a informação recebida a partir de outra componente é estável, bem construída e correta. Desta forma, não é preciso haver um processamento adicional sob os dados.
  
  As várias responsabilidades das componentes são:
  - *Assertion*
    1. Verificar a validade dos valores recebidos.
  - *Exception*
    1. Invocar a *MessageGenerator*
    2. Apresentar o *output*
  - *MessageGenerator*
    1. Invocar a *Context*
    2. Invocar a *DifferencesHighlighter*
    3. Contruir a mensagem a ser apresentada ao cliente
  - *Context*
    1. Atualizar o contexto da aplicação
  - *DifferencesHighlighter*
    1. Realçar as diferenças em *valor esperado vs. valor recebido*
    
- **Compreensibilidade**
  + Grau de legibilidade da CUT, por clareza intrínseca ou documentação disponível
  
  Ao contrário da isolabilidade, o grau de compreensibilidade cresce com o grau de dependência das componentes. Concretamente, as componentes *Assertion* e *Exception* são mais simples de compreender. Isto deve-se ao facto de as responsabilidades destas componentes serem mais leves, no sentido em que não existe um grande processamento de informação. Exemplos ilustrativos podem ser encontrados [aqui](https://github.com/bmpj13/shouldly/tree/develop/src/Shouldly/ShouldlyExtensionMethods) para a *Assertion*, e [aqui](https://github.com/bmpj13/shouldly/blob/develop/src/Shouldly/ShouldAssertException.cs) para a *Exception*.
  
  As restantes componentes, intrinsecamente relacionadas, fazem um processamento extensivo sob *Strings*, para gerar as mensagens que serão apresentadas ao cliente. A legibilidade dessas operações é reduzida, e há pouca ajuda disponível para aumentar a compreensão do código. Por exemplo, o código relativo ao [processamento do *source code*](https://github.com/bmpj13/shouldly/blob/develop/src/Shouldly/Internals/SourceCodeTextGetter.cs) do utilizador é uma das componentes fundamentais, na construção de mensagens, e encontra-se pouco documentada. O mesmo acontece para o [principal construtor de mensagens](https://github.com/bmpj13/shouldly/blob/develop/src/Shouldly/Internals/StringHelpers.cs).
  
- **Heterogeneidade**
  + Dificuldade de obter um software confiável que é flexível o suficiente para lidar com dificuldades futuras
  
  No caso do **Shoudly**, isto é visivel no facto de os testes poderem ser usados para diferentes situações e existir um vasto leque de testes disponivéis, que foram implementados, tendo por base necessidades futuras por parte dos utilizadores. 
