<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/master/ESOF-Docs/resources/images/ShouldlyLogo.png" alt="icon">
</p>
<h1 align="center">Evolução e Manutenção do Software</h1>

Em engenharia de *software*, manutenção ou evolução de *software* é descrito como o processo de otimização e melhoria de um software já desenvolvido. Esta fase, que ocorre durante o desenvolvimento de um *software*, envolve a melhoria de funcionalidades, correção e prevenção de erros, adaptação a diferentes mudanças do sistema e o requerimento de novas funcionalidades por parte dos utilizadores.

Durante esta alteração feita ao software com o objetivo de melhorá-lo, é necessário ter em conta as partes deste que serão alteradas. Deve ser garantido que as alterações são feitas de forma correta, i.e. as mudanças ou funcionalidades implementadas no código não mudam o comportamento expectável do *software*.

Estas mudanças, dependendo do tipo de projeto, podem requerer custos. No entanto, sendo o **Shouldly** um projeto *open source*, aberto à comunidade para o seu desenvolvimento, este não é um fator considerável. Por outro lado, o facto de haver mudança na equipa de desenvolvimento do *software* é obrigatório que haja diálogo entre os *developers*, se as mudanças a aplicar ao projeto são necessárias, úteis ou mesmo possíveis de concretizar, tendo em conta a características e estrutura do projeto em desenvolvimento.   

<h3> Métricas SIG </h3>

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
