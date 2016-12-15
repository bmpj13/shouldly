<p align="center">
  <img src="https://github.com/bmpj13/shouldly/blob/master/ESOF-Docs/resources/images/ShouldlyLogo.png" alt="icon">
</p>
<h1 align="center">Evolução e Manutenção do Software</h1>


Em engenharia de *software*, manutenção ou evolução de *software* é descrito como o processo de otimização e melhoria de um software já desenvolvido. Esta fase que ocorre durante o desenvolvimento de um *software* envolve a melhoria de funcionalidades, correção e prevenção de erros, adaptação a diferentes mudanças do sistema e o requerimento de novas funcionalidades por parte dos utilizadores.

Durante esta alteração feita ao software com o objetivo de melhorá-lo é necessário ter em conta as partes deste que serão alteradas, se as alterações são feitas de forma correta, de maneira a que as mudanças ou funcionalidades implementadas no código não mudam o comportamento expectável do *software*, sendo esta última parte facilmente verificada através de testes.

Estas mudanças, dependendo do tipo de projeto, podem requerer custos. No entanto, sendo o **Shouldly** um projeto *open source* aberto à comunidade para o seu desenvolvimento a parte dos custos não é aplicável a esta *framework*. Por outro lado, o facto de haver mudança na equipa de desenvolvimento do *software* é obrigatório que haja diálogo entre os *developers* se as mudanças a aplicar ao projeto são necessárias, úteis ou mesmo possíveis de concretizar tendo em conta a características e estrutura do projeto em desenvolvimento.   

<h3> Métricas SIG <h3>

Tendo em conta o *software* em estudo, **Shouldly**, foi proposto o uso de uma ferramenta para verificar se é possível a sua manutenção e, de certa forma, avaliar a qualidade do projeto desenvolvido até então.

Para que um projeto seja de possível manutenção é necessário que, segundo esta framework obdeça aos seguintes pontos:
   -	Escrever pequenas unidade de código
   - 	Escrever unidades simples de código
   -  Evitar a repetição de código
   -  Manter as unidades de interface pequenas
   -  Separar funcionalidades em módulos
   -  Arquitetura com componentes independentes
   -  Manter as componentes arquiteturais equilibradas
   -  Manter a base de código pequena
   -  Testes automatizados
   -  Desenvolvimento de código estruturado e otimizado
   
   
Após correr esta ferramenta no projeto em estudo o resultado final foi de 7/10. Tendo este software passado com sucesso em quase todos os pontos anteriores. No final, foi possível verificar que segundo esta ferramenta o projeto não mantém as unidades de interface pequenas, as componentes arquiteturais equilibradas e os testes automatizados.
