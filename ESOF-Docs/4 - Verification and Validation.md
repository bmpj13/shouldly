<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/master/ESOF-Docs/resources/images/ShouldlyLogo.png" alt="icon">
</p>
<h1 align="center">Verificação e Validação</h1>

Na *Engenharia de Software*, **verificação e validação (V&V)** define-se como o processo de confirmação de que a aplicação atende os requisitos e especificações do cliente, e que cumpre corretamente o seu propósito.

Este processo, tal como o nome indica, divide-se em duas componentes, apesar de serem complementares:

<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/v%26v_difference.jpg">
</p>

- **Verificação**: garantir que os produtos intermédios, e o produto final, cumprem os requisitos especificados, para a fase de desenvolvimento em questão.
  + Questão: *estamos a contruir o produto __de forma correta__?*
  + Itens para avaliação:
    - Planeamentos
    - Requisitos especificados
    - Arquitetura do sistema
    - Código
    - Casos de teste
    - Cenários
  + Atividades:
    - Revisões
    - Inspeções
    - *Walktroughs*
    
- **Validação**: garantir que as especificações eram, efetivamente, as pretendidas, e que o *software* cumpre os requisitos do cliente.
  + Questão: *estamos a contruir o produto __certo__?*
  + Itens para avaliação:
    - A aplicação propriamente dita
    - Protótipos
  + Atividades:
    - Prototipagem
    - Receber *feedback*
    - Analisar o objetivo do *software*

<br>
O processo **V&V** segue o modelo *V-Model*, no que diz respeito às atividades de desenvolvimento da aplicação, ao longo do seu ciclo de vida:
<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/develop/ESOF-Docs/resources/images/v%26v_model.png">
</p>

<br>
<h3> Testabilidade </h3>
A testabilidade de um *software* caracteriza-se pelo **grau de suporte de testes**, para um certo artefacto da aplicação, num determinado contexto. Se a testabilidade de um artefacto for elevada, então significa que encontrar *bugs* no sistema, via testes, torna-se mais simples e fácil.

Para as parágrafos seguintes, é importante referir que o **Shouldly** não usa *casos de teste*, mas sim *__cenários de teste__*. A diferença entre os dois reside no facto de um cenário ser um conjunto de casos.


A testabilidade de componentes do *software* é determinada por factores como:

- Controlabilidade
  + Possibilidade de controlar o estado de uma componente sob teste (CUT)
  
- Observalidade
  + Possibilidade de observar resultados de testes, intermédios ou finais
  
- Isolabilidade
  + Possibilidade de uma CUT ser testada isoladamente
  
  
  
- Separação de responsabilidades
  + Grau de separação de responsabilidades das CUTs - se têm uma única responsabilidade, bem definida
  
- Compreensibilidade
  + Grau de legibilidade da CUT, por clareza intrínseca ou documentação disponível
  
- Heterogeneidade
  + 
