### POO - Classes

Em POO uma classe é um constructo capaz de descrever computacionalmente uma entidade do mundo real. Classes são tipos, ou seja, descrevem um tipo específico de entidade de forma genérica. Por exemplo, uma classe **Carro** não descreve um carro específico, mas sim qualquer carro.

Portanto, ao criar uma classe lembre-se de procurar quais são as características e comportamentos comuns a **todos** os objetos daquele tipo. No caso do **Carro** a linha de raciocínio será: O que todos os carros têm em comum e o que é específico de cada carro?

Dessa forma, uma carcterística "*partida elétrica*", por exemplo, fará menos sentido do que uma característica "*tipo de partida*", afinal uma só se aplica aos carros com partida elétrica e a outra se aplica a qualquer carro.

Para criar uma classe em JAVA basta utilizar a palavra class seguida do nome da classe (com primeira letra maiúscula) e chaves:

```java
class Carro{
    
}
```
Tudo que pertencer à classe Carro deverá estar entre as chaves. 
Na grande maioria das vezes, queremos que nossas classes possam ser vistas e utilizadas pelo restante do programa. Para isso convencionamos utilizar a palavra public, que veremos o que é mais adiante, na frente da declaração de uma classe. 

```java
public class Carro{
    
}
```

Também podemos expressar uma classe usando a "*Unified Modeling Language*" ou **UML**, que contém um diagrama intuitivamente chamado *Diagrama de classe* para representar classes em uma forma visual.

O UML abaixo representa a classe **Carro**, como ela não possui nada dentro das chaves ela pode ser representada apenas como uma "caixinha" com o nome da classe dentro. 

![UML - Carro](https://github.com/profgabrielmilitello/POO/blob/master/imagens/cap1-uml-carro.png "UML Carro")

Veremos como o UML fica mais complexo quando adicionarmos mais componentes à nossa classe.