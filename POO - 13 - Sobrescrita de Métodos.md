## Sobrescrita de Métodos

Usamos a técnica de sobrescrita de métodos para fazer em uma classe-filha uma implementação diferente para um método da super-classe.

```java
public class Movedor{
    
    private float posX;
    private float posY;
    private float velX;
    private float velY;

    public void mover(){

        this.posX += this.velX;
        this.posY += this.velY;

    }

}
```

```java
public class MovedorAcelerado extends Movedor{
    
    private float accX;
    private float accY;
    
}
```

No código acima, temos uma classe *Movedor* que se mover invocando o método *mover()* e uma classe *MovedorAcelerado* que herda *Movedor*.

*MovedorAcelerado* deve implementar *Movimento Uniformemente Variado* (com aceleração), mas *Movedor*, que tem a implementação do método *mover()* usa Movimento Uniforme (sem aceleração).

Esse é um caso em que a classe-filha precisa modificar o funcionamento de um método da classe-pai. Não podemos alterar a super-classe porque ela também é usada no programa para simular o movimento uniforme. Também não seria ideal fazer outro método *mover* na classe-filha com outra assinatura usando sobrecarga.

Nesses casos usamos sobrescrita (override), não confunda com sobrecarga (overload) que vimos anteriormente...

Veja, no código abaixo, como fica o exemplo acima se usarmos sobrescrita:

```java
public class Movedor{
    
    protected float posX;
    protected float posY;
    protected float velX;
    protected float velY;

    public void mover(){

        this.posX += this.velX;
        this.posY += this.velY;

    }

}
```

```java
public class MovedorAcelerado extends Movedor{
    
    private float accX;
    private float accY;

    @Override
    public void mover(){

        this.velX += this.accX;
        this.velY += this.accY;
        this.posX += this.velX;
        this.posY += this.velY;

    }
    
}
```

No código acima criamos um método *mover()* com **a mesma assinatura** do método *mover()* da classe-pai.

Acima dele, colocamos a diretiva @Override, indicando para o JAVA que não estamos criando um método novo, estamos sobrescrevendo o que já existe.

Como estamos na classe-filha os atributos privados da super-classe (velX, velY, posX e posY) não estavam visíveis, por isso alteramos o encapsulamento desses atributos para protected, na super-classe, que permite a visibilidade de dentro de classes derivadas (classes-filhas).

Em suma, para sobrescrever a implementação de um método da super-classe em uma classe-filha crie um método na classe-filha com **a mesma assinatura do método da classe-pai e na linha anterior utilize o comando @Override**.