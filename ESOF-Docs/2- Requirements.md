<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/master/ESOF-Docs/resources/images/ShouldlyLogo.png" alt="icon">
</p>
<h1 align="center">Requisitos</h1>

<h3>Âmbito e Contexto</h3>
O **Shouldly** é uma ferramente de testes, baseada em *NUnit*, e tem como objetivo simplificar a escrita de
testes, e tornar o seu *output* visualmente mais agradável.

<h3>Elicitação</h3>

No que diz respeito à evolução do projeto, esta é possível pelo sistema de issues utilizada pela comunidade 
do projeto onde é feita a listagem dos erros que precisam de ser resolvidos e possibilidades de sugestões por
parte da comunidade que permitem melhorar a funcionalidade da aplicação.


<br>
<h3>Requisitos e Funcionalidades</h3>

Os requisitos de um *software* são um conjunto de descrições das funcionalidades que devem ser implementadas no sistema a ser desenvolvido.

Estes requisitos são formulados a partir das expectativas do utilizador, em relação ao produto - que, da perspetiva do cliente,
podem parecer óbvios e desnecessários de referir, como podem também mostrar-se como (ainda) desconhecidos.

**_Requirements Engineering_** define-se como o processo de estudo das necessidades e expectativas do cliente, para conceber a definição do sistema a implementar.
Este método divide-se em 4 partes:

<h4>1. Elicitação</h4>

  - Processo de descobrir, rever, documentar e perceber as necessidades dos **_stakeholders_**, para o sistema a implementar.
  
  Nesta fase inicial, é necessário interagir com os vários agentes que irão utilizar o *software*, para perceber quais os seus requisitos. Esta interação pode ser facilitada por entrevistas, reuniões, questionários, etc.
  
  O principal problema a enfrentar neste processo é falta de entendimento: os utilizadores não conhecem totalmente as suas necessidades e não conhecem as limitações dos computadores; o engenheiro pode não ter a inteira noção de qual o âmbito e contexto do software pedido; informação "óbvia" pode ser omitida, entre outros.
  
  
<h4>2. Análise</h4>

  - Detectar e resolver conflitos entre requisitos
  
  - Clarificar omissões de informação ou ambiguidades
  
  - Elaborar requisitos do sistema
  
  É, na sua essência, um processo para refinar o que foi pedido pelo utilizador. 
  
  Nesta fase, os requisitos são normalmente ordenados por ordem de importância. É também importante perceber se um requisito é *implementável, necessário, testável, claro, consistente, correto e completo*

<h4>2. Especificação</h4>

  - Produzir o documento *__SRS__ (Software Requirements Specificiation)*
  
  - Normalmente acompanhado de outros documentos:
    + Manual de utilizador preliminar (por vezes substitui o *SRS*)
    + Glossário
    + Protótipos
    + Modelos (*Use case*, *Domain*)
    + Entre outros
    
<h4>3. Validação</h4>

  - Demonstrar que o *software* satisfaz os requisitos do cliente
  
<h4>4. Gestão</h4>

  - Gestão na mudança e na evolução dos requisitos, ao longo do tempo

<br>
<br>
Os requisitos de um sistema podem-se dividir em **funcionais** e **não funcionais**:

Funcionais - descrevem as capacidades do sistema/as funções que o programa deve executar.

Não funcionais - descrevem, por norma, limitações ao software, e são geralmente medidas para assegurar qualidade no programa (segurança, eficiência, portabilidade, etc).

No contexto do **Shouldly**, os requisitos são:

  - Funcionais
    1. Escolher um tipo de asserção em testes, para desenvolver.
    2. Criar uma nova função que satisfaça a asserção escolhida.
    3. Repetir o processo, até o conjunto de funcionalidades pretendidas estarem implementadas.
    4. A novas funções a criar devem ser baseadas em *NUnit*, ou em **Shouldly** (caso já possua as funcionalidades necessárias para o desenvolvimento destas).
    5. As asserções implementadas devem conseguir satisfazer tantas ou mais baterias de testes, relativamente ao *NUnit*. Isto significa que devem ter o mesmo poder de asserção, podendo, no entanto, ser melhoradas. 
    
  - Não funcionais
    1. Facilitar a escrita de testes.
    3. Garantir que as mensagens de *output* são esteticamente apelativas.
