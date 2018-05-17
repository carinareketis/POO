## Métodos de Acesso

Antes de mais nada rode os códigos abaixo:

```java
public class Pessoa{
    public String nome;
    public int idade;
}

public class Programa{
    public static void main(String[] args){
        Pessoa p = new Pessoa();
        p.nome = "Teste";
        p.idade = 20;

        System.out.println("Sou " + p.nome + " e tenho " + p.idade + " anos.");
    }
}
```

Agora mude o encapsulamento de *nome* e *idade* para *private*:

```java
public class Pessoa{
    private String nome;
    private int idade;
}
```

Nosso método main passou a apresentar dois erros. Esses erros foram introduzidos pelo *private*: *nome* e *idade* não são mais **visíveis** fora de *Pessoa*.

Esse é o padrão JAVA, todos os atributos *private* mas como acessá-los uma vez que estão privados?

Lembre-se do conceito de *private*: visibilidade apenas dentro da classe.

Isso quer dizer que qualquer membro da classe continua sendo capaz de ler e escrever nesses atributos.

Se analisarmos o programa dentro do método main, o que ele realmente faz é incializar Pessoa e imprimir na tela.

Portanto, podemos criar um construtor e um método print para testar a manipulação dos atributos por métodos da classe:

```java
public class Pessoa{
    public String nome;
    public int idade;

    public Pessoa (String nome, int idade){
        p.nome = nome;
        p.idade = idade;
    }

    public void print(){
        System.out.println("Sou " + this.nome + " e tenho " + this.idade + " anos.");
    }
}

public class Programa{
    public static void main(String[] args){
        Pessoa p = new Pessoa("Teste", 20);
        p.print();
    }
}
```

Agora nosso programa funciona novamente, setamos o *nome* e a *idade* ao criar o objeto e o método *print* consegue ler os atributos e mostrar seus valores na tela.
Ainda temos o benefício de nosso método *main* ter ficado mais enxuto.
No entanto, ainda não podemos escrever nem ler os atributos de fora da classe.
A única coisa que podemos fazer é imprimir os valores na tela depois de criar o objeto com eles.
Sendo assim, do ponto de vista do programa nossa classe é bem inútil.

É aí que entram os **métodos de acesso**. Podemos fazer dois métodos para cada atributo, uma para retornar o valor e outro para setar um novo valor.
Assim poderemos voltar a manipular nossos atributos de fora da classe, mas com maior controle (o que veremos mais à frente).

Para começar segue a estrutura dos métodos de acesso:

GET:

public \<tipo_do_atributo> get\<nome_do_atributo>( ) { return this.<nome_do_atributo>; }

SET:

public void set<nome_do_atributo>(<tipo_do_atributo> <nome_do_parametro>) { this.<nome_do_atributo> = <nome_do_parametro>; }

Vamos criar métodos de acesso na classe *Pessoa*:

Começando com a classe Pessoa com todos os atributos privados:

```java
public class Pessoa{
    private String nome;
    private int idade;
}
```

Adicionamos os métodos GET para ambos atributos:

```java
public class Pessoa{
    private String nome;
    private int idade;

    public String getNome() { return this.nome; }
    public int getIdade(){ return this.idade; }
}
```

Então adicionamos os métodos SET para ambos atributos:

```java
public class Pessoa{
    private String nome;
    private int idade;

    public String getNome() { return this.nome; }
    public int getIdade(){ return this.idade; }

    public void setNome(String nome){ this.nome = nome; }
    public void setIdade(int idade){ this.idade = idade; }
}
```

Vamos testar os métodos de acesso usando a classe Programa que escrevemos originalmente com algumas alterações:

Nosso código era assim:

```java
public class Programa{
    public static void main(String[] args){
        Pessoa p = new Pessoa();
        p.nome = "Teste";
        p.idade = 20;

        System.out.println("Sou " + p.nome + " e tenho " + p.idade + " anos.");
    }
}
```

Para usar os métodos de acesso será assim:

```java
public class Programa{
    public static void main(String[] args){
        Pessoa p = new Pessoa();
        p.setNome("Teste");
        p.setIdade(20);

        System.out.println("Sou " + p.getNome() + " e tenho " + p.getIdade() + " anos.");
    }
}
```

Veja que a mudança é exclusivamente sintática, e não semântica. 

O código faz as mesmas coisas, nas mesmas linhas, mas chamando métodos em vez de usar os atributos diretamente.

Usamos o *private* para restringir a manipulação direta dos atributos.

Mas você pode dizer, os métodos de acesso permitem a manipulação, então qual a vantagem? Ainda tive que escrever mais código!

Tem uma vantagem enorme! Quando usamos atributos públicos não temos nenhum controle sobre os atributos, se uma mudança de valor é feita nem sabemos.

Já com métodos de acesso rodamos um trecho de código toda vez que o atributo é lido ou escrito, e nele podemos fazer o que quisermos.

Vejamos alguns exemplos com seus casos de uso:

**Cenário**: Objeto apresenta valores indevidos no final de um processamento

**Abordagem**: Fazer um log no console toda vez que um atributo é modificado para entender o que está acontecendo.

**Solução**: Adicionar um print() nos métodos SET. 

```java
public class Pessoa{
    private String nome;
    private int idade;

    public String getNome() { return this.nome; }
    public int getIdade(){ return this.idade; }

    public void setNome(String nome){ 
        System.out.println("Atributo nome alterado para: " + nome + " Valor anterior: " + this.nome);
        this.nome = nome; 
    }
    
    public void setIdade(int idade){ 
        System.out.println("Atributo idade alterado para: " + idade + " Valor anterior: " + this.idade);
        this.idade = idade; 
    }
}

public class Programa{
    public static void main(String[] args){
        Pessoa p = new Pessoa();
        p.setNome("Teste");
        p.setIdade(20);

        p.setNome("Teste2");
        p.setIdade(21);

        System.out.println("Sou " + p.getNome() + " e tenho " + p.getIdade() + " anos.");
    }
}
```

**Cenário**: Objeto apresenta valores indevidos (nulos) no final de um processamento

**Abordagem**: Fazer um restrição para evitar que valor indevidos sejam atribuídos aos atributos.

**Solução**: Adicionar uma validação nos métodos SET. 

```java
public class Pessoa{
    private String nome;
    private int idade;

    public String getNome() { return this.nome; }
    public int getIdade(){ return this.idade; }

    public void setNome(String nome){ 
        if(nome != null && !nome.equals("")) this.nome = nome; 
    }
    
    public void setIdade(int idade){ 
        if(idade > 0 && idade < 150) this.idade = idade; 
    }
}

public class Programa{
    public static void main(String[] args){
        Pessoa p = new Pessoa();
        p.setNome("Teste");
        p.setIdade(20);

        p.setNome("Teste2");
        p.setIdade(21);

        System.out.println("Sou " + p.getNome() + " e tenho " + p.getIdade() + " anos.");
    }
}
```
**Cenário**: O time de front-end não validou o tamanho dos campos, aconteceram várias tentativas de inserir nomes maiores do que o tamanho do VARCHAR no banco.

**Abordagem**: Fazer um restrição para evitar que valor maiores que 127 sejam atribuídos ao nome, enquanto arrumam o front-end.

**Solução**: Adicionar uma validação no método SET de nome. 

```java
public class Pessoa{
    private String nome;
    private int idade;

    public String getNome() { return this.nome; }
    public int getIdade(){ return this.idade; }

    public void setNome(String nome){ 
        if(nome != null){
            if(nome.length() < 127) this.nome = nome;
            else this.nome = nome.substring(0,126);
        } 
    }
    
    public void setIdade(int idade){ 
        if(idade > 0 && idade < 150) this.idade = idade; 
    }
}

public class Programa{
    public static void main(String[] args){
        Pessoa p = new Pessoa();
        p.setNome("Teste");
        p.setIdade(20);

        p.setNome("Teste2");
        p.setIdade(21);

        System.out.println("Sou " + p.getNome() + " e tenho " + p.getIdade() + " anos.");
    }
}
```

**Cenário**: O DBA pediu para os nomes serem gravados em minúsculas para facilitar buscas textuais. Já o time de front quer todas maiúsculas (sabe deus o porquê)...

**Abordagem**: Alterar para minúsculas para gravar, alterar para maiúsculas para mostrar.

**Solução**: Adicionar toLowerCase no SET e toUpperCase no GET.

```java
public class Pessoa{
    private String nome;
    private int idade;

    public String getNome() { return this.nome.toUpperCase(); }
    
    public int getIdade(){ return this.idade; }

    public void setNome(String nome){ this.nome = nome.toLowerCase(); }
    
    public void setIdade(int idade){ this.idade = idade; }
}

public class Programa{
    public static void main(String[] args){
        Pessoa p = new Pessoa();
        p.setNome("Teste");
        p.setIdade(20);

        p.setNome("Teste2");
        p.setIdade(21);

        System.out.println("Sou " + p.getNome() + " e tenho " + p.getIdade() + " anos.");
    }
}
```

Em suma, os métodos de acesso podem ter implementações muito diferentes, mas sua estrutura é sempre a mesma.

A estrutura é tão previsível que um programa poderia escrever métodos de acesso... Está aí um bom exercício...

Por fim, abaixo vemos um UML representando métodos de acesso e construtores:

![UML - Pessoa - Métodos de Acesso](https://github.com/profgabrielmilitello/POO/blob/master/imagens/cap9-uml-pessoa.png "UML Pessoa + construtores + métodos de acesso")
