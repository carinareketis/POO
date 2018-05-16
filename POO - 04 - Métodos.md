### Métodos

Podemos olhar métodos por dois ângulos em POO.

O primeiro, computacional, é que métodos são o equivalente em POO de funções. E, portanto, obedecem as mesmas regras:

Precisam ter um nome, um conjunto de parâmetros (que pode ser vazio) e um tipo de retorno (que pode ser nenhum).

Para criar um método em JAVA usamos o padrão: <tipo_de_retorno> \<nome> (\<parametros>) { \<corpo>}

Veja alguns exemplos:
```java
public void imprimir(String texto){
    System.out.println(texto);
}

public int somar(int a, int b){
    return a + b;
} 
```

Observer que em métodos com retorno void (ou seja, sem retorno) a palavra return não pode aparecer, enquanto em métodos com qualquer tipo de retorno que não seja void é obrigatório que ela apareça para indicar o resultado da excecução do método.

A segunda forma de ver métodos em POO, e que se combina com a forma anterior, é como comportamentos de uma entidade.

Métodos só existem dentro de classes, portanto, devem ser algum comportamento que a entidade que a classe representa tem na vida real, ou algum comportamento sistêmico da classe. Isso restringe o que vimos anteriormente, funções são globais, portanto podem manipular quaisquer valores no código, já métodos estão reservados ao escopos de suas classes então devem manipular apenas o que estiver diretamente relacionado à sua classe.

Por exemplo se precisarmos de um método que faz somas, o que faria mais sentido:

```java
//COLOCA-LO EM PESSOA
public class Pessoa{
    public int somar (int a, int b){ return a+b; }
}
``` 

ou

```java
//COLOCA-LO EM MATEMATICA
public class Matematica{
    public int somar (int a, int b){ return a+b; }
}
``` 
Lembre-se que para invocar o método teremos que construir um objeto da classe. 
Imagine toda vez que quiser fazer uma soma ter que construir uma Pessoa, isso não faz sentido...

Vejamos o que faria sentido em pessoa:
```java
public class Pessoa{
    
    public String nome;
    public int idade;

    public void salvar(DB db){
        db.salvar(this);
    }

    public Pessoa carregar(DB db, int id){
        return db.obterPessoaPorId(id);
    }

    public validar(){
        boolean ok = true;

        if(this.nome.equals("")) ok = false;
        if(this.nome == null) ok = false;
        if(this.idade <= 0) ok = false;

        return ok;
    }
}
```

Para finalizar, vejamos como representar métodos em UML:

![UML - Carro - Atributos](https://github.com/profgabrielmilitello/POO/blob/master/imagens/cap4-uml-matematica.png "UML matemática + métodos")

Quando fizemos o UML com atributos eles eram escritos invertido *\<nome> : \<tipo>*. Os métodos também ficam invertidos:

*\<encapsulamento> \<nome>(\<nome_parametro> : \<tipo_parametro>) : \<retorno>*

Observer que o tipo dos parâmetros e seus nomes também aparecem na posição inversa que fazemos em código.

Por fim, lembre-se que podemos ter quantos métodos quisermos em um classe.
Até mesmo métodos de mesmo nome, isso se chama **sobrecarga de operadores**, no entanto, é obrigatório que eles tenham assinaturas diferentes!
**Assinatura é o nome do método + seu conjunto de parâmetros.**
