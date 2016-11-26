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
A testabilidade de um *software* caracteriza-se pelo **grau de suporte de testes**, para um certo artefacto da aplicação, num determinado contexto. Se a testabilidade de um artefacto for elevada, então significa que encontrar *bugs* no sistema, via testes, torna-se mais simples e fácil.

Para as parágrafos seguintes, é importante referir que o **Shouldly** não usa *casos de teste*, mas sim *__cenários de teste__*. A diferença entre os dois reside no facto de um cenário ser um conjunto de casos.

  Os diferentes testes são usados para descobrir bugs, mas nao a sua ausência; os testes de defeito são testes mais específicos e deste modo tem maior probabilidade de encontrar erros; também podem ser usados testes de estatistica para verificar o desempenho e a eficiência do programa.

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/test_scenario.png" width=50%>
  <br>
  <sub>Source: blog.testlodge.com</sub>
</p>

Por este motivo, nem tudo descrito será diretamente visível nos testes da aplicação. No entanto, é da nossa opinião que as características ilustradas estão presentes.

<br>
A testabilidade de componentes do *software* é determinada por factores como:

- **Controlabilidade**
  + Possibilidade de controlar o estado de uma componente sob teste (CUT)
  
- **Observalidade**
  + Possibilidade de observar resultados de testes, intermédios ou finais.
  Pelo facto de testar os testes fornecidos ao sistema é possivel encontrar e descobrir os diferentes desvios das espectactivas das funcionalidades do programa.   
  
- **Isolabilidade**
  + Possibilidade de uma CUT ser testada isoladamente
  
  A isolabilidade das CUTs no **Shouldly** decresce com o grau de dependência de outras componentes.
  
  Por exemplo, a componente *Assertion* utiliza a componente *Exception* (caso a asserção falhe). Para garantir que a asserção está a funcionar como pretendido, deve ser assegurado que a exceção é chamada corretamente, e que retorna os valores esperados. 
  
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
