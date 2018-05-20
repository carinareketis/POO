## Chamadas à Superclasse

Vimos na lição passada que podemos alterar a forma como um método da superclasse funciona em uma classe-filha.

Resta a pergunta, a implementação original daquele método ainda pode ser usada?

Vamos retomar nosso exemplo anterior:

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

Alteramos a forma como *mover()* funciona na classe *MoverAcelerado*, mas a implementação na superclasse continua a mesma.

É possível utilizar a implementação original usando a diretiva **super**.

Observe que o método *mover()* na superclasse tem 2 linhas em comum com *mover()* da classe filha, podemos refatorar esse método para que façamos as duas linhas diferentes na classe-filha e depois invoquemos o *mover()* da superclasse.

```java
public class MovedorAcelerado extends Movedor{
    
    private float accX;
    private float accY;

    @Override
    public void mover(){

        this.velX += this.accX;
        this.velY += this.accY;
        super.mover();

    }
    
}
```

Veja que agora o método *mover()* aplica a aceleração, mas delega o restante para o *mover()* da superclasse.

Para entender como isso é possível precisamos entender como o JAVA gerencia a herança.

Para todo objeto criado a partir de classes derivadas (filhas) o JAVA cria um objeto da classe-pai.

Rode o exemplo abaixo:

```java
public class Pai{
    public Pai(){
        System.out.println("construtor pai");
    }
}

public class Filha extends Pai{
    public Filha(){
        System.out.println("construtor filha");
    }
}

public class Programa{
    public static void main(String[] args){
        Filha f = new Filha();

        /*SAÍDA:
        construtor pai
        construtor filha
        */
    }
}

```

Percebe que criamos apenas o objeto da classe-filha, mas ambos os construtores foram invocados?

O JAVA instancia a superclasse automaticamente e vincula as duas.

Existe na memória um objeto da classe-pai vinculado ao ciclo de vida de cada objeto da classe-filha.

Esse é o motivo pelo qual temos acesso aos atributos e métodos da superclasse, mesmo aqueles que sobrescrevemos na classe-filha.

Por conta disso, **construtores da superclasse e das classes-filhas devem ter o mesmo conjunto de parâmetros**, ou o código não compilará!

Por exemplo:

```java
public class Pai{
    public Pai(String x){
        System.out.println("construtor pai");
    }
}

public class Filha extends Pai{
    public Filha(){
      System.out.println("construtor filha");
    }
}
```

Esse código não compila, porque o java chama o construtor da classe-pai com os mesmos parâmetros que chamou o da classe-filha.

O construtor da filha não tem parâmetros, enquanto o da classe-pai espera uma String.

Lembra da criação do construtor? "O JAVA só cria um construtor se não criarmos um nosso".

O mesmo se dá na invocação do construtor da classe-pai. O JAVA só invoca se não invocarmos manualmente.

Para fazer isso usamos *super*,como método: **super()**. Isso é equivalente o *this()* que invocava o construtor da própria classe, mas para a classe-pai.

Podemos corrigir o código acima invocando explicitamente o construtor da superclasse:

```java
public class Pai{
    public Pai(String x){
        System.out.println("construtor pai -> " + x);
    }
}

public class Filha extends Pai{
    public Filha(){
      super("teste");
      System.out.println("construtor filha");
    }
}
```

Observe que agora passamos a String que faltava. 

Como invocamos o construtor o JAVA não precisará invocá-lo.

O código roda normalmente.

Em resumo, **para invocar um construtor da superclasse use super()**.

**Você também pode usar o super() para escolher qual construtor da superclasse rodar se houver mais de um**.
