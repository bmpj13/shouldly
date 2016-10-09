<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/master/ESOF/resources/images/ShouldlyLogo.png" alt="icon">
</p>
<h1 align="center">Shoudly</h1>

<p align="right">
  <img src="https://github.com/bmpj13/shouldly/blob/master/ESOF/resources/images/FEUPlogo.png" alt="FEUP logo">
</p>
<h3>Faculdade de Engenharia da Universidade do Porto</h3> 
<h5>Rua Roberto Frias, sn, 4200-465, Porto, Portugal</h5>
======

<h5 align="center"> Mestrado Integrado em Engenharia Informática e Computação</h5>
<h5 align="center"> 2016/2017</h5>
<h6 align="center">Turma COMP_1049 Grupo - 1</h6>
<h6>Lázaro Gabriel Barros da Costa - up201405342 - @lazarocosta</h6>
<h6>João Paulo Moreira Barbosa – up201406241 - @bmpj13</h6>
<h6>Miguel Barbeitos Lira Luís - up201405324 - @mitchLira</h6>
<h6>Miriam Cristiana Meireles Campos Gonçalves – up201403441 - @miriamcmcg</h6>
======

<h3>Descrição:</h3>
Shoudly é uma framework de testes para desenvolvimento de software em [.NET](https://www.microsoft.com/net).

É baseado em asserções e tem como objetivo simplificar a maneira como os testes são feitos, assim como 
apresentar mensagens de erro mais claras e simpáticas:


*Asserção* normal

    Assert.That(map.IndexOfValue("boo"), Is.EqualTo(2));
    > Expected 2 but was 1
    
*Asserção* com Shoudly

    map.IndexOfValue("boo").ShouldBe(2);
    > map.IndexOfValue("boo") should be 2 but was 1

<br>
<h3>História:</h3>
O projeto começou a 24 de janeiro de 2010 e continua ativo atualmente, sendo desenvolvido por 57 contribuidores.
Dos seus criadores Dave Newman, Xerxes Battiwala, Anthony Egerton, Peter van der Woude e Jake Ginnivan, 
apenas o primeiro referido continua a contribuir no código juntamente com Joseph Woodward.

Desde o início da criação desta estrutura que foram feitos mais de 800 commits, o último commit foi feito a 19 de agosto de 2016.

<h3>Licença:</h3>
Protegido pela licença [BSD-3-Clause](https://opensource.org/licenses/BSD-3-Clause).
