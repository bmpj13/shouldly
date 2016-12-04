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

Nesta aplicação, os cenários de teste passam por, não só verificar se a asserção passa ou falha, mas também qual a mensagem que será retornada - com e sem *source code* do utilizador. Por isso, pode-se considerar que o tipo de teste utilizado é *teste de integração*.

Por este motivo, nem tudo descrito será diretamente visível nos testes da aplicação. No entanto, é da nossa opinião que as características ilustradas estão presentes.

<br>
A testabilidade de componentes do *software* é determinada por factores como:

<a name="controllability"/>
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
  
  Outra dificuldade está relacionada com o facto do **Shouldly** utilizar informações do sistema, em certas partes da construção da mensagem. No cenário [*ActionDelegateScenario*](https://github.com/bmpj13/shouldly/blob/develop/src/Shouldly.Tests/ShouldNotThrow/ActionDelegateScenario.cs), no teste da asserção *ShouldNotThrow*, é esperado que a mensagem retorne
      
      (...)
      System.InvalidOperationException
      with message
      ""Operation is not valid due to the current state of the object.""
      
  mas, quando corrido nos nosso computadores, a mensagem retornada foi
  
      (...)
      System.InvalidOperationException
      with message
      ""A operação não é válida devido ao estado atual do objeto.""
  
  e, consequentemente, o teste falha.
  
  O teste não está mal formulado, nem a função retorna valores inesperados. Aliás, a [integração contínua](https://ci.appveyor.com/project/shouldly/shouldly/build/2.8.3+29.build.308/tests) do **Shouldly** aprova o teste. A adversidade está na utilização de informações do sistema, de que esta aplicação tira partido: certas mensagens são automaticamente traduzidas, pelo que o teste falhará quando as definições não estão em inglês.
  
  Além do supramencionado, mensagens que retornem números não inteiros também irão falhar, como o caso do [DoubleScenario](https://github.com/bmpj13/shouldly/blob/develop/src/Shouldly.Tests/ShouldBePositive/DoubleScenario.cs), pois o teste espera que o separador decimal seja um ponto ('.'), quando, na realidade, também pode ser uma vírgula (',').
  
  Esta geração dinâmica de mensagens torna-se difícil de testar, e dificulta também a previsão do estado da aplicação. 

<br>  
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

<br>
- **Isolabilidade**
  + Possibilidade de uma CUT ser testada isoladamente
  
  A isolabilidade das CUTs no **Shouldly** decresce com o grau de dependência de outras componentes.
  
  Por exemplo, a componente *Assertion* utiliza a componente *Exception* (caso a asserção falhe). Para garantir que a asserção está a funcionar como pretendido, deve ser assegurado que a exceção é chamada corretamente, e que retorna os valores esperados. É, portanto, importante que as duas sejam testadas em simultâneo.
  
  Por sua vez, a componente *Exception* recorre à componente *MessageGenerator* para obter as mensagens para o utilizador, pelo que testar o seu correto funcionamento implica recorrer sempre a essa componente. 
  
  A *MessageGenerator*, no entanto, já tem menos grau de dependência, pelo que poderia ser testada isoladamente. Note-se que esta componente tem dependências, mas são de mais baixo nível, facilmente controláveis e têm um relacionamento direto com a componente (*Context* e *DifferencesHighlighter*).
  
  Para simplificar a escrita dos testes, a melhor maneira de implementá-los é usar os cenários de teste, tal como o **Shouldly** utiliza, pois permite que todos os pontos essenciais sejam verificados, para cenários específicos. É necessário, no entanto, garantir que há uma grande cobertura dos diferentes cenários de utilização da aplicação.

<br>
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

<br>
- **Compreensibilidade**
  + Grau de legibilidade da CUT, por clareza intrínseca ou documentação disponível
  
  Ao contrário da isolabilidade, o grau de compreensibilidade cresce com o grau de dependência das componentes. Concretamente, as componentes *Assertion* e *Exception* são mais simples de compreender. Isto deve-se ao facto de as responsabilidades destas componentes serem mais leves, no sentido em que não existe um grande processamento de informação. Exemplos ilustrativos podem ser encontrados [aqui](https://github.com/bmpj13/shouldly/tree/develop/src/Shouldly/ShouldlyExtensionMethods) para a *Assertion*, e [aqui](https://github.com/bmpj13/shouldly/blob/develop/src/Shouldly/ShouldAssertException.cs) para a *Exception*.
  
  As restantes componentes, intrinsecamente relacionadas, fazem um processamento extensivo sob *Strings*, para gerar as mensagens que serão apresentadas ao cliente. A legibilidade dessas operações é reduzida, e há pouca ajuda disponível para aumentar a compreensão do código. Por exemplo, o código relativo ao [processamento do *source code*](https://github.com/bmpj13/shouldly/blob/develop/src/Shouldly/Internals/SourceCodeTextGetter.cs) do utilizador é uma das componentes fundamentais, na construção de mensagens, e encontra-se pouco documentada. O mesmo acontece para o [principal construtor de mensagens](https://github.com/bmpj13/shouldly/blob/develop/src/Shouldly/Internals/StringHelpers.cs).

<br>
- **Heterogeneidade**
  + Determina o grau em que o uso de diversas tecnologias requer diversos casos de teste
  
  O **Shouldly** tem pouca heterogeneidade, no sentido em que só usa testes de integração. Os testes dos módulos têm sempre a mesma receita:
  
  1. Criar um cenário de teste que deve passar.
  2. Criar um cenário de teste que deve falhar, verificando a mensagem retornada.
  3. Podem ser criados mais testes - por exemplo, quando são encontrados *bugs*.
  
  Note-se, no entanto, que, apesar da pouca heterogeneidade nos testes, os uso de cenários como testes de integração são suficientes para garantir uma boa consistência da aplicação.

<br>
<h3>Estatísticas e Análises de Testes</h3>
  
  Os testes são um processo realizado pelo testador de software. Estes fornecem informações importantes sobre a qualidade, fiabilidade e eficiência do código desenvolvido e têm como principais objetivos descobrir possíveis erros, e encontrar inconsistências no código. No entanto, para se ter confiança no código desenvolvido, é também necessário que os testes tenham qualidade, para que os seus resultados permitam detetar defeitos no sistema. 

  No total de 626 testes desenvolvidos, o resultado total foi de 21 testes falhados e 605 concluidos com sucesso. Isto mostra uma inconsistência com os resultados indicados pela integração contínua **Shouldly**, em que a taxa de sucesso nestes é de 100%. Estas incoerências devem-se ao facto do **Shouldly** utilizar definições do sistema, como é explicado anteriormente.
  
  <p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/TestsResult.png">
  <br>
  <sub> Resultado dos testes</sub>
</p>

**Cobertura de Código**
  
  Com o uso da ferramenta [ReSharper](https://www.jetbrains.com/resharper/), desenvolvida pela JetBrains, obteu-se o seguinte resultado na cobertura de código:
  
  <p align="center">
    <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/Coverage.png" width=50%>
    <br>
    <sub> Resultado da cobertura de código dos testes</sub>
  </p>
  
  Como se pode ver, os testes cobrem 72% do código. Acredita-se que, atualmente, esta *framework* tem um boa cobertura de código, porque , na maior parte das funcionalidades, os módulos principais têm todos 100% ou perto de cobertura. Os módulos *JetBrains.Annotations* e *NUnit.Framework.Constraints*, por exemplo, são ficheiros auxiliares que não fazem integralmente parte do programa e não desempenham uma função vital - por isso, é aceitável que tenham pouca cobertura.

<br>
**_HotSpots_**

  Foi também possível obter os sítios no código onde há mais risco de haver erros, chamados de [HotSpots](https://www.jetbrains.com/help/dotcover/10.0/dotCover__Detecting_Hot_Spots.html).  
 
  <p align="center">
    <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/HotSpots.png">
    <br>
    <sub> Sitíos potenciais de risco </sub>
  </p>
  
  Os HotSpots são calculados a partir da seguinte fórmula:
  
    Risk(m) = comp(m)^2 * (1 – cov(m)/100)^3 + comp(m)
    m - método;
    comp(m) - complexidade ciclomática do método;
    cov(m) - cobertura de código do método obtida pelos testes.
   
  As expressões de maior tamanho representam as zonas de código onde há mais vulnerabilidade a erros. Pode-se confirmar, então, que os módulos *JetBrains.Annotations* e *NUnit.Framework.Constraints* estão bem controlados, e não precisam de mais cobertura.
  
  Das potenciais áreas de risco, a que aparece mais destacada é a [ExpressionStringBuilder](https://github.com/bmpj13/shouldly/blob/develop/src/Shouldly/App_Packages/ExpressionStringBuilder.0.10.0/ExpressionStringBuilder.cs). Após estudar-se o código existente neste ficheiro, verifica-se que aqui é feita a construção de uma asserção ("string") através de uma expressão recebida como argumento. Uma vez que o **Shouldly** trabalha substancialmente com asserções, considera-se que esta parte em específico, sendo de conversão, pode ser considerada um potencial risco. Durante as conversões muita informação recebida pode ser perdida, e com as traduções a possibilidade de a conversão ser mal feita é maior ainda.
  
  Estes aspetos vêm a confirmar a análise feita acerca da testabilidade do programa.

<br>
**Dependências**
  
  Após seguir as instruções do **Shouldly** para proceder corretamente à sua instalação, constatou-se que esta framework tem bastantes dependências, interação entre diversos módulos/sistemas de um projeto de software, que são essenciais para o seu correto funcionamento.   
  
  <p align="center">
    <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/Dependencies.png">
    <br>
    <sub> Lista de dependências </sub>
  </p>
  
  De todas a mais significativa para todo o projeto é a ["NETStandard.Library"](https://docs.microsoft.com/en-us/dotnet/articles/standard/library), esta biblioteca tem um conjunto de .NET runtimes que melhoram esta biblioteca, tais como .NET Standard, .Net Core, .NET Framework e outras importantes. Trazendo vantagens como a possibilidade dos developers criarem bibliotecas portáteis, reduz e , em alguns casos, elimina compilação condicional source partilhada e outras vantagens. 
 
  O uso desta biblioteca, tornou-se um obstáculo na parte de obter a cobertura de código, uma vez que é incompatível com uma grande parte das aplicações existentes para correr e calcular a cobertura de código para a linguagem C#. 
  
  Como o **Shouldly** é um projeto de grande complexidade, o uso de tantas dependências permite a sua modularização, ou seja, a sua divisão em partes distintas, melhorando a sua legibilidade e a sua manutenção. Esta divisão em módulos permite melhorar a programação e os testes ao programa, a criação de bibliotecas que podem ser usadas noutros projetos ou por outros programadores, economizar memória do computador e entre outras vantagens. No entanto, a necessidade de modularizar um programa aumenta o tempo de execução de código, devido ao tratamento adicional de ativação dos diferentes módulos.  
  
<br>    
<h3>Identificação e correção de um bug</h3>
  
  Na página de *issues* do **Shouldly**, pode ser encontrado o [bug](https://github.com/shouldly/shouldly/issues/363) que aqui será discutido.
  
<h4> Informação </h4>

  Para reproduzir o problema, o seguinte código de teste poderia ser corrido:
  
      [Test]
      public void ShouldHandleTimeoutException()
      {
          Func<Task> func = async () => { throw new TimeoutException(); };

          Should.Throw<TimeoutException>(func);
      }
      
   O teste criado deveria correr com sucesso, já que a *Task* lança a exceção *TimeoutException* da [.NET Framework](https://msdn.microsoft.com/en-us/library/system.timeoutexception(v=vs.110).aspx), e a chamada a asserção do **Shouldly** espera que ele faça isso mesmo. No entanto, o teste falha com a seguinte mensagem:
   
        Shouldly.ShouldCompleteInException : 
        Task
            should complete in
        00:00:10
            but did not
        ----> System.TimeoutException : The operation has timed out.
        
  É importante notar que a asserção *Should.Throw* pode lançar a mensagem acima, quando a *Task* criada não corre no tempo estabelecido (alterável pelo utilizador). Porém, no excerto de código apresentado tal não devia acontecer, pois o lançamento da exceção não demoraria 10 segundos.
  
 Quando a *Task* demora demasiado tempo a acabar de correr, o **Shouldly**, internamente, lançaria a mesma exceção *TimeoutException* utilizada no exemplo. No código de teste, esta exceção é lançada diretamente, e a aplicação não estava preparada para receber este tipo de *input*.
  
<h4>Estratégia de resolução</h4>
   
   A origem do *bug* não se encontra num erro de codificação, mas sim num erro de concepção - devido à grande agilidade e diversidade dos *inputs* que o **Shouldly** pode receber, este devia-se abster de usar ferramentas acessíveis a qualquer utilizador, para ditar o comportamento do programa - pois vai fragilizar a sua segurança, aumentando a probabilidade de ser "atacado" (note-se que esta estratégia devia ser adotada para qualquer código que altere o estado do programa, e não só para corrigir este *bug* em específico).
   
   A estratégia de resolução passa, então, por alterar o *handling* das *Tasks*, quando estas demoram muito a correr. Em vez de ser usada a exceção *System.TimeoutException*, foi criada uma nova exceção, denominada de *ShouldlyTimeoutException*, que será lançada nas condições referidas. Como a exceção *ShouldlyTimeoutException* é usada somente dentro do **Shouldly**, não podendo ser chamada por utilizadores, o programa correrá conforme esperado.
   
   As alterações feitas podem ser vistas com mais detalhe [aqui](https://github.com/bmpj13/shouldly/commit/50a46607fa196bbece867ce22efd812c2b3abb85). Foram também criados [novos testes](https://github.com/bmpj13/shouldly/commit/b9aef0062940f9756dcda30329a1724da0316707), para garantir que o *bug* estava a ser corrigido.
   
*<h4> Pull Request </h4>*
  
  É da nossa opinião que a resolução criada segue os *coding standards* do **Shouldly**, tem qualidade, é escalável, e resolve de forma simples o *bug* pretendido. Por essas mesmas razões, um [*pull request*](https://github.com/shouldly/shouldly/pull/414) foi enviado para o repositório principal. Note-se, também, que as alterações efetuadas não mudam os *outcomes* dos [testes de integração contínua](https://ci.appveyor.com/project/shouldly/shouldly/build/tests).
  
  O *pull request* foi revisto e aceite pelos dois coordenadores do projeto :+1:.
  
<br>
------
<h3>Contribuição do grupo</h3>
João Barbosa - 25% <br>
Lázaro Costa - 25% <br> 
Miguel Lira - 25% <br>
Miriam Gonçalves - 25% 
