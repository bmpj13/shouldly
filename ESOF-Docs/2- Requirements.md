<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/master/ESOF-Docs/resources/images/ShouldlyLogo.png" alt="icon">
</p>
<h1 align="center">Requisitos</h1>

<h3>Âmbito e Contexto</h3>
O **Shouldly** é uma ferramente de testes, baseada em *NUnit*, e tem como objetivo simplificar a escrita de
testes, e tornar o seu *output* visualmente mais agradável.

<br>
<h3>Requisitos e Funcionalidades</h3>

Os requisitos de um *software* são um conjunto de descrições das funcionalidades que devem ser implementadas no sistema a ser desenvolvido.

Estes requisitos são formulados a partir das expectativas do utilizador, em relação ao produto - que, da perspetiva do cliente,
podem parecer óbvios e desnecessários de referir, como podem também mostrar-se como (ainda) desconhecidos.

**_Requirements Engineering_** define-se como o processo de estudo das necessidades e expectativas do cliente, para conceber a definição do sistema a implementar.
Este método divide-se em 5 partes:

<h4>1. Elicitação</h4>

  - Processo de descobrir, rever, documentar e perceber as necessidades dos **_stakeholders_**, para o sistema a implementar.
  
No que diz respeito à evolução do projeto, esta é possível pelo sistema de issues utilizada pela comunidade 
do projeto onde é feita a listagem dos erros que precisam de ser resolvidos e possibilidades de sugestões por
parte da comunidade que permitem melhorar a funcionalidade da aplicação. 

A comunicação por partes dos contribuidores e masters do Shouldly é feita pelo gitter, neste chat as respostas, dúvidas
e sugestões surgem de uma forma mais informal, sendo possível surgir novas ideias a qualquer hora e estas serem entretanto aperfeiçoadas ou , simplesmente, aprovadas tornando-se num próximo objetivo a cumprir do projeto. 
Neste projeto, qualquer pessoa pode juntar-se para ajudar a desenvolver esta framework e fazer parte deste projeto pertencendo
ao mesmo domínio.
  
<h4>2. Análise</h4>

  - Detectar e resolver conflitos entre requisitos.
  
  - Clarificar omissões de informação ou ambiguidades.
  
  - Elaborar requisitos do sistema.
  
Os requisitos de um sistema podem-se dividir em **funcionais** e **não funcionais**:

Funcionais - descrevem as capacidades do sistema/as funções que o programa deve executar.

Não funcionais - descrevem, por norma, limitações ao software, e são geralmente medidas para assegurar qualidade no programa (segurança, eficiência, portabilidade, etc).

No contexto do **Shouldly**, os requisitos são:

  - Funcionais
    1. Escolher um tipo de asserção em testes, para desenvolver.
    2. Criar uma nova função que satisfaça a asserção escolhida.
    3. A novas funções a criar devem ser baseadas em *NUnit*, ou em **Shouldly** (caso já possua as funcionalidades                  necessárias para o desenvolvimento destas).
    4. As asserções implementadas devem conseguir satisfazer tantas ou mais baterias de testes, relativamente ao *NUnit*.            Isto significa que devem ter o mesmo poder de asserção, podendo, no entanto, ser melhoradas. 
    5. Repetir o processo, até o conjunto de funcionalidades pretendidas estarem implementadas.
    
  - Não funcionais
    1. Facilitar a escrita de testes.
    3. Garantir que as mensagens de *output* são esteticamente apelativas.

A análise ao projeto é feita por qualquer contribuidor: de uma forma informal e bastante prática, são analisados os objetivos
realizados e os que ainda faltam cumprir tendo em conta o que foi feito e as limitações existentes do projeto, havendo a possibilidade de se criar um novo objetivo, caso este seja suficientemente necessário e adicione funcionalidades importantes, ou de se descartar um objetivo antigo, caso se considere de pouca importância para este projeto.  

<h4>3. Especificação</h4>

  - Produzir o documento *__SRS__ (Software Requirements Specificiation)*.
  
  - Normalmente acompanhado de outros documentos:
    + Manual de utilizador preliminar (por vezes substitui o *SRS*)
    + Glossário
    + Protótipos
    + Modelos (*Use case*, *Domain*)
    + Entre outros
    
O projeto não possui um documento formal *SRS*, mas possui [documentação](http://shouldly.readthedocs.io/en/latest/) digital que contém informação acerca do funcionamento desta framework. Neste mesmo documento, consta uma quantidade substancial de exemplos que permite aos utilizadores percecionar qual o resultado pretendido das diferentes asserções. 

<h4>4. Validação</h4>
  
   - Demonstrar que o *software* satisfaz os requisitos do cliente.
   
Apesar de não haver um controlo rigoroso sobre os avanços do projeto, todos os envolvidos no projeto e devidos utilizadores sentem-se de uma forma geral satisfeita por o projeto progredir, apesar de ser de uma forma gradual. Uma vez que o projeto ainda continua a progredir e, por vezes, os contribuidores deparam-se com certas limitações de software, assim como os utilizadores, estes últimos continuam a surgir com novas ideias ou mesmo críticas sobre o que deve ser melhorado para que esta framework se torne acessível e satisfatória para os seus clientes.

<h4>5. Gestão</h4>

  - Gestão na mudança e na evolução dos requisitos, ao longo do tempo.
  
Os requisitos do projeto podem, naturalmente, mudar ao longo do tempo. O principal factor para tal, é a introdução de ideias e novas funcionalidades por parte da comunidade. Ideias que sejam bem fundamentadas podem e devem ser implementadas, para melhorar a qualidade do *software*.

Aquando da introdução da funcionalidade, o processo de **integração contínua** vai permitir aos principais colaboradores saber se esta interfere com os outros módulos do programa, garantindo de forma constante a consistência do programa.

<br>

