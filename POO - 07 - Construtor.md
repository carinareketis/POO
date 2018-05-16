## Método Construtor

Observe o código abaixo:

```java
public class Programa{
    public static void main(String[] args){

        Pessoa p = new Pessoa();

    }
}
```

Dissemos que para construir qualquer objeto precisamos dizer *new* + *nomedaclasse* + *()*;

Já vimos em métodos que para invocar um método usamos *nome()*.

Então quando criamos um objeto estamos invocando um método de mesmo nome que a classe. Mas onde está esse método?

```java
public class Pessoa{
    public String nome;
}
```

A classe pessoa não tem um método com assinatura *Pessoa()* então de onde ele vem?

O JAVA assume por padrão que, se você escreveu uma classe, você quer construir objetos a partir daquela classe.

Por isso, o compilador adiciona um **método construtor** em todas as classes que **não tiverem construtores**.

Vamos rescrever a classe Pessoa, dessa vez faremos explicitamente o que o JAVA fez:

 ```java
public class Pessoa{
    public String nome;

    public Pessoa() { }
}
```

Observe algumas peculiaridades sobre esse método.

A mais importante é que ele não tem *tipo de retorno* (nem void) isso se dá porque ele sempre retornará a instância da classe (objeto), portanto, ele não pode retornar outros valores ou deixar de retornar.

Outra peculiaridade é que, apesar de não marcarmos os construtores como estáticos, eles estão sempre disponíveis na memória, podendo ser invocados a partir de qualquer classe onde a classe a ser instânciada esteja visível. Diferente dos demais métodos de uma classe que, ou são dependentes de um objeto e só estão disponíveis enquanto o objeto estiver na memória, ou são estáticos e estão disponíveis por meio da classe.

Você pode aplicar sobrecarga nos construtores também da mesma forma que os métodos comuns, lembre-se apenas que o construtor padrão, vazio, só é crido pelo JAVA se não houver mais nenhum construtor na classe. Então se você fizer um construtor com parâmetros, aquele construtor sem parâmetros "automático" deixa de existir, então você precisará escrevê-lo também se quiser usá-lo.

Veja os exemplos:

```java
public class Pessoa{
    public String nome;
}
```

Pessoa possui um construtor de assinatura *Pessoa()* criado pelo compilador.

```java
public class Pessoa{
    public String nome;

    public Pessoa(String nome) {this.nome = nome;}
}
```

Pessoa, acima, possui um construtor de assinatura *Pessoa(String)* apenas. O automático não será criado.
Observer que agora Pessoa só pode ser instanciada se passarmos um nome.

```java
public class Pessoa{
    public String nome;

    public Pessoa(){}
    public Pessoa(String nome) {this.nome = nome;}
}
```

Pessoa acima tem um construtor de assinatura Pessoa(String) e um de assinatura Pessoa(). 

Um não faz nada de especial além de criar o objeto, o outro espera uma String para atribuir em *nome*;

Uma última consideração, de dentro da própria classe podemos invocar um construtor em outro método.

Para isso não usamos o *new*, porque não queremos criar um objeto, e não chamamos o construtor pelo nome da classe, mas por **this()**.

Quando fazemos isso o construtor se comportará como um método comum de retorno void, rodará sua lógica normalmente sem criar um novo objeto.

Podemos também usar um construtor para invocar outro dessa forma.

Veja os exemplos:

```java
public class Pessoa{
    
    public String nome;

    public Pessoa()
    {
        this("anônimo");
    }
    
    public Pessoa(String nome) {
        this.nome = nome;
    }
}
```

No caso acima, o construtor que o pogramador espera que seja usado é o de assinatura Pessoa(String), que cria uma pessoa com um nome. 

No entanto exite um construtor que permite não passar um nome de assinatura Pessoa(). 

Se ele for invocado, ele invocará o outro construtor (Pessoa(String)), passando como nome o valor padrão "anônimo".

Ele é capaz de invocar o outro construtor usando **this()**.