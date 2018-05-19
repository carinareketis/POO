## Herança

Em POO, falando em termos computacionais, o conceito de heranças tem dois aspectos fundamentais:

1. Reaproveitar o código de uma classe (classe-pai/super-classe) em diversas outras classes (classes-filhas).
2. Adicionar o tipo da classe-pai aos tipos das classes-filhas.

Imagine que estamos codificando um jogo e temos as seguintes classes:

```java
public class Personagem{
    private float vida;
    private float ataque;
    private int velocidade;
    private int posX;
    private int posY;

    public void mover(){
        posX += velocidade;
        posY += velocidade;
    }

    public float getVida() { return this.vida; }

    public void tomarDano(int qtd){ this.vida -= qtd; }

    public void atacar(Monstro m){ m.tomarDano(this.ataque); }

    public void regenerar(){ this.vida++; }
}
```

```java
public class Monstro{
    private float vida;
    private float ataque;
    private int velocidade;
    private int posX;
    private int posY;

    public void mover(){
        posX += velocidade;
        posY += velocidade;
    }

    public float getVida() { return this.vida; }

    public void tomarDano(int qtd){ this.vida -= qtd; }

    public void atacar(Personagem p){ p.tomarDano(this.ataque); }

    public void atacarEspecial(Personagem p) { p.tomarDano(this.ataque * 2); }
}
```

Observe como as classes acima são praticamente idênticas.

Vamos listar as diferenças:

1. *Personagem* tem o método *regenerar*, o *Monstro* não.
2. *Monstro* tem o método *ataqueEspecial*, o *Personagem* não.
3. O método *atacar* de *Personagem* tem *Monstro* como parâmetro e de *Monstro* tem *Personagem*.

Vamos reescrever essas classes com herança.
Por enquanto só vamos aplicar o primeiro aspecto listado, ou seja, agrupar códigos idênticos em uma super-classe e herdá-la. Depois aplicaremos o segundo.

```java
public class Ator{
    private float vida;
    private float ataque;
    private int velocidade;
    private int posX;
    private int posY;

    public void mover(){
        posX += velocidade;
        posY += velocidade;
    }

    public float getVida() { return this.vida; }

    public void tomarDano(int qtd){ this.vida -= qtd; }
}
```

```java
public class Personagem extends Ator{

    public void atacar(Monstro m){ m.tomarDano(this.ataque); }

    public void regenerar(){ this.vida++; }
}
```

```java
public class Monstro extends Ator{
    
    public void atacar(Personagem p){ p.tomarDano(this.ataque); }

    public void atacarEspecial(Personagem p) { p.tomarDano(this.ataque * 2); }
}
```

A palavra **extends** nas classes-filhas indica herança. 

Fazemos herança seguindo a forma: `<encapsulamento> class <nome_da_classe> extends <nome_da_superclasse>{ }`

Mas cuidado: **No JAVA só é permitido herdar UMA super-classe**

A dica é: Filhos só tem 1 pai. Pai tem n filhos.

Observe que tudo que era comum entre as duas classes foi passado para a super-classe Ator.

O que era diferente nas duas classes foi mantido nas classes-filhas.

Assim escrevemos menos código, não temos duplicações, e se desejarmos fazer outra classe parecida (Boss (chefão), por exemplo) basta herdar a mesma super-classe;

Nossa implementação está reaproveitando o código, nosso primeiro aspecto foi cumprido.

Mas podemos fazer ainda melhor se usarmos o segundo aspecto: Por conta da herança tanto *Mostro* quanto *Jogador* agora compartilham o tipo *Ator*.

Sendo assim, podemos tomar o *Jogador* como *Ator*, assim como o *Monstro* como *Ator*, portanto, se observarmos o método atacar de *Jogador*, que tem *Monstro* como parâmetro e o de *Monstro* que tem *Jogador* como parâmetro, podemos generalizá-los para usar *Ator* como parâmetro. Veja o código abaixo:

```java
public class Personagem extends Ator{

    public void atacar(Ator a){ a.tomarDano(this.ataque); }

    public void regenerar(){ this.vida++; }
}
```

```java
public class Monstro extends Ator{
    
    public void atacar(Ator a){ a.tomarDano(this.ataque); }

    public void atacarEspecial(Personagem p) { p.tomarDano(this.ataque * 2); }
}
```

Podemos fazer isso porque o método *tomarDano*, que é usado no método *ataque*, está na classe Ator.

Veja que agora que a implementação de ataque ficou idêntica nas duas classes, podemos aplicar o primeiro aspecto novamente e colocar esse método na super-classe.

```java
public class Ator{
    private float vida;
    private float ataque;
    private int velocidade;
    private int posX;
    private int posY;

    public void mover(){
        posX += velocidade;
        posY += velocidade;
    }

    public float getVida() { return this.vida; }

    public void tomarDano(int qtd){ this.vida -= qtd; }

    public void atacar(Ator a){ a.tomarDano(this.ataque); }
}
```

```java
public class Personagem extends Ator{
    public void regenerar(){ this.vida++; }
}
```

```java
public class Monstro extends Ator{
    public void atacarEspecial(Personagem p) { p.tomarDano(this.ataque * 2); }
}
```

Ainda ganhamos o benefício de *atacar* ter ficado mais genérico, agora qualquer classe que herde *Ator*, pode atacar qualquer outra classe que também herde *Ator*.

Imagine que nosso personagem tem um lobo que o acompanha na sua jornada.

O lobo é criado com a classe *Mostro*, no código original ele não poderia atacar outros monstros, apenas personagens, agora ele pode.

Assim como nosso *Personagem* pode atacar outros personagens e *Monstro* pode atacar monstros.

**Usar a super-classe para representar qualquer tipo filho é um conceito-chave de POO chamado POLIMORFISMO.**

Abaixo temos um UML simplificado representando a Herança e um UML completo:

![UML - Herança Simplificado](https://github.com/profgabrielmilitello/POO/blob/master/imagens/cap11-uml-heranca-simples.png "UML Herança Simplificado")

![UML - Herança](https://github.com/profgabrielmilitello/POO/blob/master/imagens/cap11-uml-heranca-completo.png?raw=true "UML Herança")

Observe que não repetimos os atributos e métodos herdados nos diagramas das classes-filhas. O diagrama reflete exatamente o que será codificado!