<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/master/ESOF-Docs/resources/images/ShouldlyLogo.png" alt="icon">
</p>
<h1 align="center">Processo de Desenvolvimento</h1>

<h3>Desenvolvimento do projeto</h3>
A contribuição para este projeto não é dependente de uma vertente de desenvolvimento, isto é, os contribuidores
são livres de melhorar e optimizar o programa de forma autónoma, não havendo atribuição de papéis ou cargos aos diferentes *developers*, distruibuindo-os por várias equipas.

A maneira mais sugerida e convidativa para contribuir é pelo sistema de [issues](https://github.com/shouldly/shouldly/issues)
que a comunidade do projeto utiliza, sempre que algum erro é encontrado, ou se quer apresentar alguma sugestão.

Este sistema permite que os problemas sejam do conhecimento de todos os contribuidores, possibilitando o desenvolvimento de 
várias soluções. Permite também que os proprietários do repositório saibam de forma rápida qual o objetivo do *pull request*.

Para além disso, são atribuídas tags aos problemas encontrados, como **_Enhancement_** ou **_Jump-In_**, 
para facilitar a escolha de problemas a ser resolvidos, permitindo ao contribuidor filtrar as questões 
que estejam fora do seu âmbito.

É também aconselhado utilizar o [gitter](https://gitter.im/shouldly/shouldly?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) do repositório, para obter rapidamente informações e para trabalhar conjuntamente.

<br>

<h3>Contribuição</h3>
Para contribuir para o **Shoudly** é somente necessário

1. Fazer um *fork* do repositório
2. Alterar o projeto de forma a satisfazer o problema a resolver
3. Enviar um *pull request*

Os principais colaboradores vão verificar a viabilidade das mudanças, e, 
possivelmente, aceitar o que foi feito.

Mais informações podem ser encontradas no [readme](https://github.com/shouldly/shouldly#contributing) do projeto.

<br>

<h3>Processo de Software</h3>
Consideramos que o processo utilizado é **Iterative and incremental development** (a base para os métodos de desenvolvimento *agile*), visto que, regularmente, são lançadas novas [versões](https://github.com/shouldly/shouldly/releases) do projeto, complementadoras das versões que as precedem. 
 
Este método consiste em aumentar a funcionalidade do código à medida que vai sendo desenvolvido, de forma gradual e por ordem de prioridade, sem alterar substancialmente o anterior. Este processo é repetido de forma cíclica até que se chegue ao resultado pretendido.

<br>
<br>

<h1 align="center">Análise crítica</h1>
<h3>Processos</h3>
O modelo de desenvolvimento de software do **Shoudly** é adequado ao âmbito do projeto, pelas seguintes razões:

+ Iterative and incremental development
  - Permite criar software rapidamente.
  - Flexível.
  - Permite satisfazer facilmente os requirimentos essenciais.
  - Facilita o desenvolvimento de funções adicionais e complementares.
  
 É um bom processo para o projeto a ter em conta, pois permite utilizar a prática de **integração contínua (CI)**, possibilitando o aparecimento de novas funcionalidades estáveis, sempre que possível.
Desta forma, a interação com o cliente é mais frequente, o que permite receber mais vezes *feedback* de 
como a aplicação deve evoluir.

Quando posto em perspetiva com métodos *non-agile (__Waterfall__, __V-model__, ...)*, que:
 - Dividem estrita e sequencialmente as fases de desenvolvimento de um projeto.
 - Avançam para uma fase seguinte, quando a fase atual estiver totalmente concluída.
 - Produzem software apenas numa fase final de desenvolvimento, *i.e*, demora mais a distribuir a aplicação.
 - Custosos se é necessário fazer modificações em etapas de desenvolvimento posteriores.

Este processo mostra-se como ideal para desenvolvimento de *software*, especialmente em *open-source*, pois possibilita a distribuição (de uma versão) do programa mais cedo. Consequentemente, há uma maior probabilidade de o projeto ser visto por mais desenvolvedores, que podem ficar interessados em contribuir: este efeito pode resultar num crescimento abrupto da aplicação, em termos de visibilidade, qualidade e velocidade de construção.

Além disso, o uso de um método *non-agile* dificultaria bastante a chegada de novos contribuidores, visto que estes teriam
que dedicar grande porção do tempo a estudar as etapas iniciais (Requirimentos e análise/Arquitetura do sistema), para ter as
ideias bem definidas e sedimentadas, aquando da codificação propriamente dita.

<br>

Quando posto em perspetiva com métodos *agile*, é da nossa opinião que outros processos seriam igualmente válidos, dependendo
da estrutura do projeto:

**Scrum** pode ser utilizado quando há uma separação dos programadores em equipas (em que os vários intervenientes são os *Product Owner*, *Scrum Master* e *Development Team*). As equipas também devem fazer, em reuniões, *reviews* do trabalho feito, com uma frequência pré-estabelecida (p.ex. de 2 em 2 semanas), podendo também fazer uso de [milestones](https://github.com/shouldly/shouldly/milestones). <br>
Tal como referido anteriormente, não existe esse tipo de estrutura neste repositório: as contribuições são individuais e nem sequer é usado o sistema de *milestones* do Github. Além disso, como o **Shoudly** é um projeto *open-source*, a garantia que as equipas se disponibilizariam a fazer reuniões em certos intervalos de tempo é, geralmente, baixa. <br>
Finalmente, o envolvimento do *Product Owner* não é simples, visto que, neste caso, este é a comunidade, pelo que, muito dificilmente, é exequível ter este elemento a liderar o projeto.

Deste modo, este método não seria apropriado, tendo em conta a estruturação do repositório - note-se, no entanto, que seria perfeitamente viável, caso a organização das equipas fosse outra.

 
<br>

<h3>Estrutura e Contribuição</h3>

Tendo em conta a finalidade e complexidade do projeto, a estrutura do repositório é aceitável. Porém, é de notar que o projeto
beneficiaria de uma agrupação de contribuidores em cargos (por exemplo: *Developers*, *Testers*, *Designers* e *Translators*).
Isto permitiria uma maior compreensão do código entre as unidades, focando-se nos aspetos chave que lhes compete.

O processo de contribuição é simples e intuitivo, usando um sistema de *issues* para ajudar o contribuidor a ter noção daquilo que pode e deve fazer. Além disso, são atribuídas tags aos problemas encontrados para ajudar o programador a escolher problemas
dentro do seu nível de conhecimento.

======

<h3>Contribuição do grupo</h3>

João Barbosa - 25% <br>
Lázaro Costa - 25% <br> 
Miguel Lira - 25% <br>
Miriam Gonçalves - 25%
