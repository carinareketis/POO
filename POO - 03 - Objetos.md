# POO - Objetos

Fazer classes é a maior parte da rotina de um programador POO, no entanto, a programação chama-se orientada a **objetos** não orientada a classes.

Quando falamos em classes dissemos que a classe representa uma entidade de forma genérica, ou seja, que uma classe é um tipo e que ela pode representar qualquer objeto daquele tipo.

Falamos que os atributos são as características de um tipo (entidade), portanto, na classe eles raramente apresentam valores.

Os **objetos** são o outro lado da equação, também chamados de instâncias de uma classe, eles representam os objetos de um tipo de forma particular e não genérica.

É nos objetos que armazenamos os valores para os atributos que fizemos nas classes. Por enquanto, podemos pensar nas classes como a declaração de uma estrutura de dados e nos objetos como as estruturas de dados preenchidas com os valores. Também podemos fazer a analogia da classe como um formulário em branco contendo os campos e o objeto como as respostas preenchidas nesses campos de um formulário.

Linguagens orientadas a objetos só rodam aqueles códigos que aprendemos em lógica de programação ou algoritmos dentro de métodos. Seu programa roda a partir de um método especial chamado main. Ele marca onde seu programa começa a executar. Quando fazemos classes elas ficam em arquivos diferentes e apenas uma deve ter o método main. Abaixo mostramos como criar objetos, mas só podemos criá-los dentro de métodos, portanto precisamos de uma classe com o método main.

Para criar um objeto precisamos fazer duas coisas:

1. Declarar uma variável do mesmo tipo do objeto. Isso é fácil, lembre-se que o tipo do objeto é o mesmo tipo da classe e que o tipo da classe é seu nome.
2. Atribuir à variável (=) o comando *new* seguido do nome da classe + ( );

Portanto, para construir um obejto da classe Carro:

```java
public class Programa{
    public static void main(String[] args){
        
        Carro c = new Carro();

    }
}
```
Nosso objeto foi criado pelo comando new seguido de um método especial chamado construtor (falaremos dele em breve).

O objeto está guardado na variável de tipo *Carro* e nome **c**.

Assim, podemos acessar nosso objeto usando **c** e usando o **"."** acessamos os atributos. 

Observe que todos os atributos públicos que criamos podem ser acessados por "c.<nome_do_atributo>".

O código abaixo mostra como ler e atribuir valores em atributos: 

```java
System.out.println(c.marca); //imprime o valor de marca na tela
c.marca = "Fiat"; // altera o valor de marca 
System.out.println(c.marca); //agora imprime o valor Fiat na tela
```

Observe que você pode criar quantos carros quiser usando a classe Carro:

```java
public class Programa{
    public static void main(String[] args){
        
        Carro c = new Carro();
        Carro c1 = new Carro();
        Carro c2 = new Carro();
        Carro c3 = new Carro();
        Carro c4 = new Carro();
        Carro c5 = new Carro();

    }
}
```

Quando criamos um objeto, todos os valores dos atributos estarão setados para o valor padrão:

Se o atributo é de um dos tipos primitivos consulte a tabela da lição anterior.

Se o tipo do atributo for uma classes o valor é sempre null (nulo).

