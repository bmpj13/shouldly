<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/master/ESOF-Docs/resources/images/ShouldlyLogo.png" alt="icon">
</p>
<h1 align="center">Evolução e Manutenção do Software </h1> 

[![BCH compliance](https://bettercodehub.com/edge/badge/bmpj13/shouldly)](https://bettercodehub.com)

Em engenharia de *software*, manutenção ou evolução de *software* é descrito como o processo de otimização e melhoria de um software já desenvolvido. Esta fase, que ocorre durante o desenvolvimento de um *software*, envolve a melhoria de funcionalidades, correção e prevenção de erros, adaptação a diferentes mudanças do sistema e o requerimento de novas funcionalidades por parte dos utilizadores.

Durante esta alteração feita ao software com o objetivo de melhorá-lo, é necessário ter em conta as partes deste que serão alteradas. Deve ser garantido que as alterações são feitas de forma correta, i.e. as mudanças ou funcionalidades implementadas no código não mudam o comportamento expectável do *software*.

Estas mudanças, dependendo do tipo de projeto, podem requerer custos. No entanto, sendo o **Shouldly** um projeto *open source*, aberto à comunidade para o seu desenvolvimento, este não é um fator considerável. Por outro lado, o facto de haver mudança na equipa de desenvolvimento do *software* é obrigatório que haja diálogo entre os *developers*, se as mudanças a aplicar ao projeto são necessárias, úteis ou mesmo possíveis de concretizar, tendo em conta a características e estrutura do projeto em desenvolvimento.   

<h3> Evolução e Manutenção </h3>

Para avaliar a qualidade do **Shouldly**, foi utilizada a ferramenta [Better Code Hub](https://bettercodehub.com/). Esta ferramenta avalia a aplicação e determina fatores como legibilidade, manutenibilidade e capacidade de evolução. Para tal, os seguintes são calculados os seguintes pontos:

 -	Escrever pequenas unidade de código
 - 	Escrever unidades simples de código
 -  Evitar a repetição de código
 -  Manter as unidades de interface pequenas
 -  Separar funcionalidades em módulos
 -  Arquitetura com componentes independentes
 -  Manter as componentes arquiteturais equilibradas
 -  Manter a base de código pequena
 -  Automação de testes
 -  Desenvolvimento de código estruturado e otimizado

<br>
Após execução da ferramenta no nosso projeto, verificámos que nem todos as métricas de avaliação obtiveram aprovação. O **Shouldly** obteve aprovação em 8 e reprovação em 2 métricas, num total de 10.

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/bch_score.png" alt="icon">
</p>

É de notar que, para obter uma avaliação positiva em *Keep Architecture Componentes Balanced*, foi preciso criar um ficheiro de configuração designado [.bettercodehubyml](https://github.com/bmpj13/shouldly/blob/master/.bettercodehub.yml), alterando o nível de profundidade das componentes.

<br>
De facto o **Shouldly** é um projeto que possui, em geral, pequenos e simples pedaços de código, que o tornam mais legível e de mais fácil compreensão. Além disso, é um projeto que não possui código repetido, isto é, existe apenas uma função para cada ação.

Duas das métricas que fazem com que o **Shouldly** possa ser considerado um projeto extremamente estruturado, é o facto de estar dividido em módulos, tendo cada módulo a ver apenas com uma certa secção do projeto, e além disso, tem um grande grau de independência entre cada um dos módulos. Mostra, também, que tem uma arquitetura sólida.

Outro fator crucial, para permitir uma melhor manutenção e evolução da aplicação, está relacionado com o tamanho do *source code* do projeto. O *BetterCode* avalia o projeto em 12 *man-month*, afirmando ainda que o limite ideal máximo é de 20 *man-year*. Isto é um resultado notável, tendo em conta que o projeto é uma ferramenta de asserções, e, por essa razão, tem uma API extensa.

<br>
Uma das métricas em que o projeto não passou com sucesso, foi em manter as interfaces pequenas.

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/bch_interfaces_small.png" alt="icon">
</p>

O **Shouldly** tem diversos métodos que necessitam de muitos argumentos (como é visível na imagem), pelo que esta avaliação é correta. A quantidade de argumentos devia ser reduzida, para tornar a utilização das funções mais intituiva, e também para facilitar a manutenção destas componentes. Uma solução passaria por agrupar a informação em estruturas apropriadas, para tornar o código mais organizado e legível.

<br>
Outro dos pontos em que o **Shouldly** não obteve aprovação, foi na métrica de testes automatizados:

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/bch_automate_tests.png" alt="icon">
</p>

O *BetterCode* rotula o **Shouldly** como um projeto de dimensão média (menos de 10.000 linhas de código), pelo que indica que a aplicação deve ter metade das linhas de código para linhas de teste. Além disso, deve ter 1% de asserções. Note-se que este projeto tem mais linhas de testes do que linhas de código - pelo que, provavelmente, esta métrica falha devido à falta de asserções, visto que nenhuma é usada nos testes.

Tendo em conta que o **Shouldly** possui um rácio de 170% na cobertura, é possível admitir que está bem testado, e que cobre grande parte dos pontos cruciais da aplicação. Por isso, é da nossa opinião que este ponto de avaliação, provavelmente, deveria ter passado, podendo o *BetterCode* ser mais flexível.

Em geral, é possível afirmar que o **Shouldly** é um projeto bem construído, pelo que a pontuação atribuída é merecida - devendo até, provavelmente, ser superior.

<br>
<h3> Implementação da feature </h3>

Foram implementadas duas novas funcionalidades para adicionar à aplicação: as funções [ShouldBeginWith](https://github.com/shouldly/shouldly/issues/281) e [ShouldEndWith](https://github.com/shouldly/shouldly/issues/282) foram discutidas no sistema de *issues* do **Shouldly**, e, sendo métodos úteis, foi decidido que seriam desenvolvidas.

É de notar que a função *ShouldBeginWith* foi inicialmente proposta para se chamar *ShouldStartWith*. No entanto, como estas funções já exisitiam para *strings* e usavam a notação __Begin__ e __End__, decidimos que seria melhor manter os mesmos nomes, pois torna mais intuitiva a sua utilização.

As funcionalidades são similares ao método [ShouldContain](http://docs.shouldly-lib.net/docs/shouldcontain), no sentido em que processam o conteúdo de [IEnumerables](https://msdn.microsoft.com/en-us/library/system.collections.ienumerable(v=vs.110).aspx).
Ao contrário do *ShouldContain* que verifica se um certo elemento pertence ao enumerável, as funções *ShouldBeginWith* e *ShouldEndWith* verificam se esse elemento se encontra exatamente no início ou no fim do enumerável, respetivamente. 

Estes métodos são bastante úteis quando é necessário ter mais especifidade nas unidades de teste, utilizando o **Shouldly**. Estas funcionalidades são implementadas noutras ferramentas variadas de teste, pelo que o desenvolvimento destas pretendem preencher uma lacuna na aplicação. São funções genéricas pois funcionam com qualquer tipo de enumerável.

A facilidade na implementação destas *features* comprova que a aplicação tem, na realidade, uma estrutura ótima para poder evoluir as suas funcionalidades: nenhum código já feito teve que ser alterado, pois o **Shouldly** tem algum tratamento semi-automático para as suas funções. Nomedamente, existe um processamento no nome do método, que posteriormente é utilizado para gerar mensagens de erro. Desta forma, o gerador de mensagens do projeto consegue criar grande parte da mensagem, somente acedendo às ao nome e aos argumentos da função.

Este tratamento é __semi__-automático, porque, na realidade, é necessário identificar o tipo de mensagem que queremos criar, pelo que o nome do método deve ser identificado no [ficheiro apropriado](https://github.com/shouldly/shouldly/blob/cb58830180c1c3f87db9b0eb74ef9d7c446ec71e/src/Shouldly/MessageGenerators/ShouldBeginEndWithMessageGenerator.cs). Deve também ser construído o *template* da mensagem a ser gerada - mas, seguindo os padrões do **Shouldly**, isto torna-se relativamente simples. 

Note-se que não foi necessário alterar código já criado na aplicação, pois os métodos *ShouldBeginWith* e *ShouldEndWith* já exisitiam para processar *strings*, como referido anteriormente. Assim, a associação ao gerador de mensagens já tinha sido implementada, não sendo necessários esforços adicionais.

Tendo em conta todos estes fatores, não foi necessário uma grande análise sobre o impacto das mudanças: visto que nenhum código foi alterado, dificilmente a criação de novas asserções vão afetar o bom funcionamento das restantes, visto que são independentes entre si. Para chegar a estas conclusões, foram analisadas a sequências de chamadas a partir da asserção *ShouldContain*, e é facilmente perceptível que os maiores cuidados a ter residem no gerador de mensagens.

A criação de novas asserções passa, então, por:
  1. Implementar a funcionalidade.
  2. Associar a funcionalidade ao gerador de mensagens apropriado.
  
A facilidade em implementar novas *features* torna o **Shouldly** um projeto bastante convidativo para novos participantes. Além disso, é simplificada a manutenção e evolução do programa.

<br>
_<h3> Pull Request </h3>_

A solução foi implementada com sucesso, mostrando-se simples e fiável. Foram também adicionados testes, para garantir o seu bom funcionamento.

Por estes motivos, foi enviado um [_pull request_](https://github.com/shouldly/shouldly/pull/417) para o repositório principal. Note-se, no entanto, que provavelmente não será aceite, tendo em conta que as *issues* referentes às funções implementadas na nossa solução foram abertas em 2015, e não houve posteriormente uma grande discussão sobre o tópico. Isto porque o **Shouldly** é uma aplicação com alguns anos, e, portanto, a maioria das *features* principais já foram implementadas. Portanto, a maioria dos *pull requests* aceites passam por resolução de *bugs*, ou pela implementação de funcionalidades especialmente pedidas pelos coordenadores do projeto.
