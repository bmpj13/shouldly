<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/master/ESOF-Docs/resources/images/ShouldlyLogo.png" alt="icon">
</p>
<h1 align="center">Arquitetura</h1>

A arquitetura de *software* define-se como a organização fundamental de um sistema, incoporado em diversas componentes, estipulando as suas relações, e também os princípios de *design* da aplicação. Permitindo, desta forma, uma análise à evolução e desenvolvimento do projeto. Esta arquitetura centra-se na ideia da redução da complexida através da abstração e separação de interesses. 

Resumidamente, estabelece e responde às principais questões de desenho da aplicação.

<br>
Neste contexto, vai ser estudado o **modelo de arquitetura 4+1**:

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/4%2B1architecture.jpg" alt="4+1 architecture">
</p>

para o **Shouldly**, ou seja, vão ser apresentados os diferentes modelos arquiteturais presentes na aplicação, excetuando 
o *Use Case View*. Além disso, serão também exibidos os diferentes padrões de arquitetura encontrados.

<br>
<h3>Padrões de Arquitetura</h3>
Um padrão arquitetural é uma solução, geral e reusável, para um problema comum na arquitetura de *software*, dentro de um contexto.


<br>
<h3> Vista Lógica </h3>
Mostra as abstrações chave no sistema. No caso do **Shouldly**, as principais abstrações manifestam-se nos diferentes *namespaces* que são definidos e utilizados na aplicação.

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/logical_view.jpg" alt="logical view">
</p>

O shouldly como se pode ver pela vista lógica é uma ferramenta de testes baseada em NUnit, que tem como principal objetivo simplificar a escrita de testes e tornar o seu output mais agradável. Para que isto seja possível, recorre-se a todos os pacotes referidos no diagrama acima, sendo que este projeto usa o NUnit para permitir o output melhorado dos testes.

<br>
<h3> Vista de Implementação </h3>
Define como o *software* é decomposto, em várias componentes para desenvolvimento.

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/implementation_view.png" alt="implementation view">
</p>
<sub> Nota: a vermelho encontram-se as componentes externas, utilizadas pelo **Shouldly** </sub>


<br>
<h3> Vista de Distribuição </h3>
Mostra o *hardware* do sistema, e como as componentes de *software* são distribuídas.

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/deployment_view.png" alt="deployment view">
</p>
Para utilizar esta framework que utiliza a linguagem c# é necessário usar o Visual Studio e, após a instalação, deve seguir-se as seguintes instruções: Tools > NuGet Package Manager > Package Manager Console e escrever na consola do Package Manager o comando: Install-Package Shouldly.


<br>
<h3> Vista de Processo </h3>
Define as diferentes interações dos processos do sistema, em *run-time*. Tendo em conta que o **Shouldly** é uma *framework*, não existe um ponto de início do programa, e portanto esta vista define-se em várias partes. Para as componentes principais da aplicação, as modelações são:

- Processo da asserção
<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/activity_assercao.png" alt="process_assertion">
</p>

- Processo da exceção
<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/activity_excecao.png" alt="process_exception">
</p>

- Processo do gerador de mensagens
<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/activity_gerador_de_mensagens.png" alt="process_exception">
</p>
