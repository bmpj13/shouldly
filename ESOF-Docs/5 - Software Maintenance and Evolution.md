<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/master/ESOF-Docs/resources/images/ShouldlyLogo.png" alt="icon">
</p>
<h1 align="center">Evolução e Manutenção do Software</h1>

Em engenharia de *software*, manutenção ou evolução de *software* é descrito como o processo de otimização e melhoria de um software já desenvolvido. Esta fase, que ocorre durante o desenvolvimento de um *software*, envolve a melhoria de funcionalidades, correção e prevenção de erros, adaptação a diferentes mudanças do sistema e o requerimento de novas funcionalidades por parte dos utilizadores.

Durante esta alteração feita ao software com o objetivo de melhorá-lo, é necessário ter em conta as partes deste que serão alteradas. Deve ser garantido que as alterações são feitas de forma correta, i.e. as mudanças ou funcionalidades implementadas no código não mudam o comportamento expectável do *software*.

Estas mudanças, dependendo do tipo de projeto, podem requerer custos. No entanto, sendo o **Shouldly** um projeto *open source*, aberto à comunidade para o seu desenvolvimento, este não é um fator considerável. Por outro lado, o facto de haver mudança na equipa de desenvolvimento do *software* é obrigatório que haja diálogo entre os *developers*, se as mudanças a aplicar ao projeto são necessárias, úteis ou mesmo possíveis de concretizar, tendo em conta a características e estrutura do projeto em desenvolvimento.   

<h3> Métricas SIG </h3>

Para avaliar a qualidade do **Shouldly**, foi utilizada a ferramenta [Better Code Hub](https://bettercodehub.com/). Esta ferramenta avalia a aplicação e determina fatores como legibilidade, manutenibilidade e capacidade de evolução.

Após execução da ferramenta no nosso projeto, verificámos que nem todos as métricas de avaliação obtiveram aprovação. O **Shouldly** obteve aprovação em 8 e reprovação em 2 métricas, num total de 10.

Dedicamo-nos, de uma maneira mais específica, a perceber cada uma das métricas, e como estavam ou não presentes no projeto. Com uma análise mais detalhada, percebemos que o **Shouldly**, sendo um projeto *open source*, e que permite constantemente adicionar colaboradores, terá de ser um projeto bem organizado.

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/bch_score.png" alt="icon">
</p>

 -	__Escrever pequenas unidade de código__
    
    
 - 	Escrever unidades simples de código
 -  Evitar a repetição de código
 -  Manter as unidades de interface pequenas
 -  Separar funcionalidades em módulos
 -  Arquitetura com componentes independentes
 -  Manter as componentes arquiteturais equilibradas
 -  Manter a base de código pequena
 -  Testes automatizados
 -  Desenvolvimento de código estruturado e otimizado

De facto o **Shouldly** é um projeto que possui, em geral, pequenos e simples pedaços de código que o tornam mais legível e de mais fácil compreensão. Além disso, é um projeto que não possui código repetido, isto é, existe apenas uma função para cada ação.

Duas das métricas que fazem com que o **Shouldly** possa ser considerado um projeto extremamente estruturado, é o facto de estar dividido em módulos, tendo cada módulo a ver apenas com uma certa secção do projeto, e além disso, tem um grande grau de independência entre cada um dos módulos. Mostra, também, que tem uma arquitetura sólida.

Outros fatores importantes residem no facto de 

É de salientar que o **Shouldly** não tem aprovação na métrica de testes automatizados, porque as metas do *BetterCode* são de um certo número de lindas de testes unitários e um certo número de linhas de asserções, sendo neste último que falha, pois o **Shouldly** não possui asserções de nenhum tipo. 

(nao disse nada sobre o ponto oito porque nao entendi muito bem)
(nao disse nada sobre o ponto dez porque acho que seria repetir me ainda mais pois acho que em termos práticos tudo é diferente, mas em termos teoricos todos nos levam a um codigo muito bem organizado e estruturado e limpo)
(falta o primeiro e o segundo ponto que falha)

