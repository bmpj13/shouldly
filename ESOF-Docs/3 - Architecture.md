<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/master/ESOF-Docs/resources/images/ShouldlyLogo.png" alt="icon">
</p>
<h1 align="center">Arquitetura</h1>

A arquitetura de *software* define-se como a organização fundamental de um sistema, incorporado em diversas componentes, estipulando as suas relações, e também os princípios de *design* da aplicação. Permitindo, desta forma, uma análise à evolução e desenvolvimento do projeto. Esta arquitetura centra-se na ideia da redução da complexida através da abstração e separação de interesses. 

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

No caso do shoudly um dos padrões de arquitetura usado é **Engenharia de software baseada em componentes** (**CBSE**), é uma abordagem baseada em reutilização de definição, implementação e composição de componente independentes.

<h5>Caraterísticas</h5>
  + Maior organização do sistema.
  + Os diferentes processos dos sistema são colocados em componentes, de modo a que as funções e dados de cada componente se relacionem entre si, idêntico a uma classe.
  + Cada componente do sistema comunica entre sí através de interfaces  disponibilizadas pelo sistema.
  + O cliente nao tem acesso ao funcionamente interno de cada componente.
  + A utilização de componentes permite ao fabricante do projeto uma melhor manipulação dos mesmos, podem ser alterados ou substituidos, sem comprometer o normal funcionamento do sistema devido a intepêndencia dos componetes.


<br>
<h3> Vista Lógica </h3>
Mostra as abstrações chave no sistema. No caso do **Shouldly**, as principais abstrações manifestam-se nos diferentes *namespaces* que são definidos e utilizados na aplicação.

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/logical_view.jpg" alt="logical view">
</p>

O **Shouldly** é uma ferramenta de testes baseada em [NUnit](https://www.nunit.org/), que tem como principal objetivo simplificar a escrita de testes e tornar o seu output mais agradável. Para que isto seja possível, recorre-se a todos os pacotes referidos no diagrama acima.

Os diferentes namespaces têm a sua função no projeto:

- Shouldly
  + Definir asserções da API.
  + Definir exceções (de interação com o utilizador).
  + Definir contexto da aplicação.
  
- Shouldly.MessageGenerators
  + Gerar de mensagens de erro, dependendo do contexto da aplicação.
  
- Shouldly.DifferenceHighlighting
  + Diferenciar, de forma mais clara, o resultado esperado *vs* resultado devolvido.
  
- Shouldly.Configuration
  + Configura e verifica as definições do computador, onde o programa está a ser corrido.
  
- Shouldly.Internals
  + Definir *templates* a serem utilizados pelas outras componentes da aplicação (mensagens, operadores, etc).
  
- NUnit
  + Framework externa ao programa.
  + Suporte para construír as asserções base do **Shouldly**.


<br>
<h3> Vista de Implementação </h3>
Define como o *software* é decomposto, em várias componentes para desenvolvimento.

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/implementation_view.png" alt="implementation view">
</p>
<sub> Nota: a vermelho encontram-se as componentes externas, utilizadas pelo **Shouldly**. </sub>

Pelo diagrama apresentado, é visível que a componente *Assertion* funciona de interface com o utilizador, mas, na realidade, a componente *Exception* vai ser a componente principal, pois vai garantir que uma mensagem chega ao utilizador, caso o resultado da asserção seja inesperado.

Além disso, vai servir de intermediário entre a função de asserção utilizada e a mensagem a apresentar ao cliente: sempre que a componente *Exception* é necessária, esta vai transmitir a informação suficiente ao *Message Generator* - para que este último possa criar uma mensagem de erro de acordo com os objetivos do **Shouldly**.

A componente *Message Generator* vai converter a informação recebida da *Exception*, e alterar o contexto da aplicação. Dependendo do contexto, o *Differences Highlighter* poderá ser utilizado. Seguidamente, é retornada a mensagem a mostrar ao utilizador, à componente *Exception*.

A arquitetura estruturada e simbiótica destas componentes permite, com facilidade, atingir os objetivos do **Shouldly**: criar uma ferramenta de testes de fácil escrita, e de visualização agradável. 

<br>
<h3> Vista de Distribuição </h3>
Mostra o *hardware* do sistema, e como as componentes de *software* são distribuídas.

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/deployment_view.png" alt="deployment view">
</p>
Para utilizar esta framework, desenvolvida em [C#](https://msdn.microsoft.com/en-us/library/kx37x362.aspx) e [.NET](https://www.microsoft.com/net), é necessário usar o Visual Studio ou o MonoDevelop. Se o *plug-in* NuGet Package Manager não vier instalado com o IDE, então deve também ser instalado.

Após a instalação, deve seguir-se as seguintes instruções: Tools > NuGet Package Manager > Package Manager Console, e escrever na consola do Package Manager o comando: Install-Package Shouldly.

<br>
<h3> Vista de Processo </h3>
Define as diferentes interações dos processos do sistema, em *run-time*. Tendo em conta que o **Shouldly** é uma *framework*, não existe um ponto de início do programa, e portanto esta vista define-se em várias partes. Para as componentes principais da aplicação, apresenta as seguintes modelações:

- Processo da asserção
<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/activity_assercao.png" alt="process_assertion">
</p>
Quando o utilizador chama uma função da API do **Shouldly**, é verificada a validade da operação. Se o resultado estiver incorreto é lançada uma exceção, em resultado contrário nada é feito.

- Processo da exceção
<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/activity_excecao.png" alt="process_exception">
</p>
Após o lançamento da exceção é invocado o gerador de mensagens e ,de seguida, é feita a conversão desta para string.

- Processo do gerador de mensagens
<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/activity_gerador_de_mensagens.png" alt="process_exception">
</p>

Dependendo da asserção invocada pelo utilizador, o contexto do programa é atualizado. Tendo em conta este contexto, o **Shouldly** verifica se é necessário para esta asserção sublinhar as suas diferenças. Após esta verificação, é gerada e retornada a mensagem. 
