## Heranças Múltiplas

Dissemos que no JAVA em qualquer classe só é permitido fazer herança de 1 classe.

No entanto, existem situações em que gostaríamos de fazer herança de mais de uma super-classe, nesses casos temos que encadear as heranças.

Ou seja, podemos fazer a super-classe herdar outra super-classe em vez da classe filha fazer herança múltipla.

O que é mostrado no diagrama abaixo:

![UML - Herança Múltipla](https://github.com/profgabrielmilitello/POO/blob/master/imagens/cap12-uml-heranca.png "UML Herança Múltipla")

**Em outras palavras, podemos fazer apenas 1 herança direta em cada classe, mas podemos herdar indiretamente qualquer número de classes.**

O motivo para esse tipo de arquitetura é que no JAVA, assim como em outras liguagens, todas as classes tem uma super-classe em comum.

No JAVA todas as classes herdam a classe Object, portanto, qualquer classe tem o tipo Object.

Essa herança é implícita, mesmo sem o comando extends todas as classes herdam Object.

Mas porque a herança de Object faz com que mais de uma herança direta seja ilegal, mas heranças indiretas sejam permitidas?

Primeiro, tenha em mente que apenas as classes que não tem o comando *extends* em sua declaração herdarão diretamente Object.

Em outras palavras, se você tem uma classe Pessoa declarada:

`public class Pessoa{ //... }` 

Na verdade o JAVA a declarará:

 `public class Pessoa extends Object{ //... }`.

 Veja o diagrama abaixo que representa como seria uma classe herdar duas super-classes:

![UML - Herança Múltipla](https://github.com/profgabrielmilitello/POO/blob/master/imagens/cap12-uml-heranca-object-incorreta.png "UML Herança Múltipla")

No final das contas a Classe3 acabará herdando a classe Object duas vezes.

Isso quer dizer que se o compilador não restringisse, acabaríamos com duas cópias de todos os atributos e métodos de Object na Classe3. E classes não podem ter atributos com mesmo nome ou métodos com a mesma assinatura, portanto, teríamos um monte de erros.

Já na forma encadeada isso não acontece:

![UML - Herança Múltipla](https://github.com/profgabrielmilitello/POO/blob/master/imagens/cap12-uml-heranca-object-correta.png "UML Herança Múltipla")

Observe que Object aparece apenas uma vez no diagrama. Porque apenas a Classe1 não tem *extends* em sua declaração e portanto herda Object implicitamente.