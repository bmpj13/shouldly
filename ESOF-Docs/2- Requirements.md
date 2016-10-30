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

Nesta fase inicial, é necessário interagir com os vários agentes que irão utilizar o *software*, para perceber quais os seus requisitos. Esta interação pode ser facilitada por entrevistas, reuniões, questionários, etc.

O principal problema a enfrentar neste processo é falta de entendimento: os utilizadores não conhecem totalmente as suas necessidades e não conhecem as limitações dos computadores; o engenheiro pode não ter a inteira noção de qual o âmbito e contexto do software pedido; informação "óbvia" pode ser omitida, entre outros.

É também possível fazê-lo com recurso a *gitter*: dúvidas, sugestões e discussões surgem de uma forma mais informal, sendo possível aparecerem novas ideias a qualquer hora. Estas podem ser, entretanto, aprovadas e, eventualmente, aperfeiçoadas para satisfazer melhor as necessidades do *software*. Nesta altura, é, por norma, aconselhado a mover a dita sugestão para o sistema de *issues* acima referido, podendo mais facilmente ser acedido por todos os participantes.

<br>
No que diz respeito ao levantamento de novos requisitos no projeto, este é possível pelo sistema de issues utilizada pela comunidade, onde não só é feita a listagem dos erros que precisam de ser resolvidos, como também são dadas sugestões que permitem melhorar a funcionalidade da aplicação (normalmente rotuladas com as tags *Enchancement* ou *Discussion*).

Posteriormente, qualquer pessoa pode juntar-se para ajudar a desenvolver esta funcionalidade, e fazer parte deste projeto.

<br>
<h4>2. Análise</h4>

  - Detectar e resolver conflitos entre requisitos.
  
  - Clarificar omissões de informação ou ambiguidades.
  
  - Elaborar requisitos do sistema.
  
É, na sua essência, um processo para refinar o que foi pedido pelo utilizador. 

Nesta fase, os requisitos são, normalmente, ordenados por ordem de importância. É também importante perceber se um requisito é *implementável, necessário, testável, claro, consistente, correto e completo*
  
Os requisitos de um sistema podem-se dividir em **funcionais** e **não funcionais**:

Funcionais - descrevem as capacidades do sistema/as funções que o programa deve executar.

Não funcionais - descrevem, por norma, limitações ao software, e são geralmente medidas para assegurar qualidade no programa (segurança, eficiência, portabilidade, etc).

<br>
No contexto do **Shouldly**, os requisitos são:

  - Funcionais
    1. Escolher um tipo de asserção em testes, para desenvolver.
    2. Criar uma nova função que satisfaça a asserção escolhida.
    3. A novas funções a criar devem ser baseadas em *NUnit*, ou em **Shouldly** (caso já possua as funcionalidades                  necessárias para o desenvolvimento destas).
    4. As asserções implementadas devem conseguir satisfazer tantas ou mais baterias de testes, relativamente ao *NUnit*.            Isto significa que devem ter o mesmo poder de asserção, podendo, no entanto, ser melhoradas. 
    5. Repetir o processo, até o conjunto de funcionalidades pretendidas estarem implementadas.
    
  - Não funcionais
    1. Facilidade na escrita de testes.
    2. Mensagens de *output* esteticamente apelativas.
    3. Open source
    4. Documentação
    5. Integração contínua
    6. Compatível com C#

A análise ao projeto é feita por qualquer contribuidor: de uma forma informal e bastante prática, são analisados os objetivos já realizados, e os que ainda faltam cumprir. Tendo em conta o que foi feito e as limitações existentes do projeto, há a possibilidade de se criar um novo requisito, caso este seja suficientemente necessário e/ou adicione funcionalidades importantes.

Note-se, também, que não existe uma ordenação direta da importância dos requisitos: qualquer contribuidor pode desenvolver qualquer *feature*, dentro das *issues*.

<br>
<h4>3. Especificação</h4>

  - Produzir o documento *__SRS__ (Software Requirements Specificiation)*.
  
  - Normalmente acompanhado de outros documentos:
    + Manual de utilizador preliminar (por vezes substitui o *SRS*)
    + Glossário
    + Protótipos
    + Modelos (*Use case*, *Domain*)
    + Entre outros

<br>
O projeto não possui um documento formal *SRS*, mas possui [documentação](http://shouldly.readthedocs.io/en/latest/) digital, que contém informação acerca do funcionamento desta framework. Neste mesmo documento, consta uma quantidade substancial de exemplos que permitem aos utilizadores percecionar qual o resultado pretendido das diferentes asserções. 

<br>
<h4>4. Validação</h4>
  
   - Demonstrar que o *software* satisfaz os requisitos do cliente.

<br>
O **Shouldly** possui uma vasta bateria de testes, que permite testar com rigor a qualidade do código produzido. Isto permite trazer mais segurança ao cliente, quando utiliza o *software* - não obstante que existirão sempre *bugs*.

No entanto, isto não significa que o **Shouldly** satisfaz as necessidades do utilizador: esta evidência aparece nas críticas escritas por várias entidades de alta fiabilidade - p.ex. nos artigos da [VisualStudio Magazine](https://visualstudiomagazine.com/articles/2015/08/01/improve-test-asserts-with-shouldly.aspx) ou [NuGet Must Haves](http://nugetmusthaves.com/Package/Shouldly).

É quase imediato perceber que este *software* preenche uma necessidade dos clientes, que eles próprios desconheciam que a tinham até encontrarem o **Shouldly**. Isto porque a aplicação faz um trabalho notável em facilitar toda a escrita de testes, possuindo ferramentas poderosas, mas ao mesmo tempo simples, coisa que nem sempre se verifica nas *frameworks* de teste *standard*.

Uma vez que o projeto ainda continua a progredir, os contribuidores, assim como os utilizadores, deparam-se, por vezes, com certas limitações no *software*. Neste contexto, devem ser introduzidas continuamente novas ideias, ou mesmo críticas, acerca do que deve ser melhorado para que esta *framework* se torne ainda mais completa, satisfatória e válida na perspetiva do cliente.

<br>

<h4>5. Gestão</h4>

  - Gestão na mudança e na evolução dos requisitos, ao longo do tempo.

<br>
Os requisitos do projeto podem, naturalmente, mudar ao longo do tempo. O principal factor para tal, é a introdução de ideias e novas funcionalidades por parte da comunidade. Ideias que sejam bem fundamentadas podem e devem ser implementadas, para melhorar a qualidade do *software*.

Aquando da introdução da funcionalidade, o processo de **integração contínua** vai permitir aos principais colaboradores saber se esta interfere com os outros módulos do programa, garantindo de forma constante a consistência do programa.

<br>
<h1 align="center">Análise crítica</h1>
<h3>Requisitos e Funcionalidades</h3>
<br>
<h4>Elicitação</h4>
Por vezes, a criação do projeto pedido pelo utilizador pode tornar-se difícil de implementar por falta de esclarecimento por parte do utilizador e por falta de conhecimento do utilizador das capacidades e funcionalidades do software.

Por outro lado, o constante surgimento de novas ideias e funcionalidades para o software pode complicar a tentativa de corresponder a todos os requisitos, impostos pelos utilizadores.
Alguns desses requisitos não são possíveis de implementar ou, por vezes, para os implementar seria necessário alterar a estrutura do projeto em si e por este motivo não são implementados devido aos custos associados.

O uso do sistema de *issues*, tal como o **Shouldly** utiliza, mostra-se como uma boa prática para a introdução de novas ideias 
e sugestões, pois pode ser facilmente acedido, visto que se encontra diretamente no repositório do projeto. É portanto, em geral,
um método suficientemente bom para o levantamento de novos requisitos. No entanto, no nosso caso, não existe uma grande 
distinção entre a listagem de problemas no *software*, e a listagem de novos requisitos propriamente ditos: as tags utilizadas,
*Discussion* e *Enhancement*, podem ser referidas em ambos os contextos. Consequentemente, não é possível filtrar de forma clara as duas 
vertentes.

Soluções para tal passariam por criar uma nova *label*, como *feature-request* ou *idea*, para utilizar exclusivamente nas 
novas ideias para o projeto; ou então, criar um fórum exclusivo só para a introdução das mesmas. Desta forma, seria possível, de forma fácil, introduzir a aceder aos requisitos da aplicação.

<br>
<h4>Análise</h4>
Tendo em conta que o **Shouldly** tem um contexto restrito (asserções em testes), a análise de requisitos é bastante simples e concisa:  o desenvolvimento de uma funcionalidade passa sempre pelas etapas anteriormente referidas.

Como não existe uma ordenação da importância dos vários requisitos, existe a possibilidade de requisitos menos importantes serem implementados primeiro, podendo adiar de forma considerável o desenvolvimento de funcionalidades mais urgentes. Seria aconselhável, portanto, haver uma estruturação mais clara, neste contexto, para garantir mais qualidade e menos custos no *software*. 

<br>
<h4>Especificação</h4>
Embora o **Shoudly** possua uma documentação informal, a documentação existente sobre esta *framework* é bastante completa. É visível o manual de utilizador, com a descrição de cada função de testes disponíveis, bem como protótipos de chamadas às funções e a respetiva visualização dos outputs obtidos. Logo, do ponto de vista do utilizador é uma documentação suficiente e completa.

Já do ponto de vista dos contribuidores não se verifica isso. Para alguém que queira tornar-se contribuidor do **Shoudly** a documentação existente é pouco clara em alguns aspetos. Exemplos disso seria, na documentação, incluir modelos de *Use Case* e *Domain* como os construídos acima, visto serem modelos que ajudam a perceber como a *framework* funciona internamente.

<br>
<h4>Validação</h4>
Esta *framework* de testes mostra-se ser bastante simples e útil no que diz respeito à escrita de testes por partes dos utilizadores.
Estes fatores, por si só, permitem satisfazer as necessidades dos clientes em relação às frameworks *standard*.

Como este projeto continua em desenvolvimento, existe sempre espaço para melhorar as suas funcionalidades e a sua segurança, tendo em conta as críticas ou sugestões apresentadas tanto por parte dos developers, como dos seus utilizadores. A diversidade de opiniões permite, com alguma segurança, garantir que as necessidades dos clientes são satisfeitas.

É de notar que, por norma, não existe uma “validação intermédia” no desenvolvimento das funcionalidades do **Shouldly** 
(p.ex. via prototipagem), o que se torna perigoso, visto poder vir a refletir-se em custos acrescidos. No entanto, é da 
nossa opinião que há razões para tal:

  - As principais funcionalidades do **Shouldly** são independentes umas das outras: dificilmente a introdução de uma 
  nova funcionalidade danifica a aplicação.

  - São também, em geral, pequenas, o que facilita a correção de erros, sem introduzir grandes custos.
  
  - O projeto é *open source*: obrigar os *developers* a usar técnicas mais formais de validação pode restringir o número de 
  contribuidores (por falta de conhecimento).

<br>
<h4>Gestão</h4>
<br>
A gestão e evolução do projeto é feita maioritariamente com recurso ao sistema de *issues* (onde são colocados os problemas a resolver, e onde são introduzidas novas ideias). Este método mostra-se suficientemente adequado e simples, tendo em conta as características do projeto, pois permite ao contribuidor aceder, de forma acessível e rápida, aos vários tópicos em aberto.

Além disso, a utilização de integração contínua garante a consistência e bom funcionamento do *software*, sempre que uma nova funcionalidade é adicionada. 


<h3>Contribuição do grupo</h3>

João Barbosa - 25% <br>
Lázaro Costa - 25% <br> 
Miguel Lira - 25% <br>
Miriam Gonçalves - 25% 
