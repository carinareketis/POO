# Encapsulamento

Até agora vimos atributos e métodos públicos.
Também vimos, na lição de objetos que temos que ter uma classe Programa, com um método main, para podermos criar nossos objetos.
Na POO, o cenário mais comum é usar objetos fora da sua própria classe, salvo raras exceções.
Quando usamos atributos e métodos públicos dizemos que eles tem visibilidade fora de sua classe. Ou seja, qualquer outra classe do programa pode usá-los.
Podemos querer restringir esse comportamento. Pode haver partes de nossa classe que não queremos expor para outras classes.
Para isso usamos o encapsulamento.

Os modificadores de encapsulamento são os descritos na tabela abaixo:

|Modificador                        |Classe|Pacote|Subclasse|Programa|
|-----------------------------------|:----:|:----:|:-------:|:------:|
|public                             |V     |V     |V        |V       |
|protected                          |V     |V     |V        |F       |
|sem modificador (package-private)  |V     |V     |F        |F       |
|private                            |V     |F     |F        |F       |

Vamos relembrar, no JAVA toda a classe fica dentro de um **pacote** (package), que são equivalentes a módulos do sistema.

O que a tabela nos conta é que:
*public* - Torna o membro (atributo ou método) visível para qualquer classe no programa.
*protected* - Torna o membro visível apenas às classes do próprio pacote e classes-filhas (que podem estar em outro pacote).
*package-private* - Quando não colocamos **nenhum modificador** o membro é visíveis apenas às classes do pacote (padrão).
*private* - Torna o membro visível apenas de dentro da própria classe.

Teste os códigos abaixo:

```java
package teste;
public class Programa{
    public static void main (String[] args){
        Exemplo ex = new Exemplo();
        System.out.print(ex.campo1);
        System.out.print(ex.campo2);
        System.out.print(ex.campo3);
        System.out.print(ex.campo4);
    }
}
```

```java
package teste;
public class Exemplo{
    public String campo1;
    public String campo2;
    public String campo3;
    public String campo4;
}
```

A classe Programa vai funcionar normalmente, afinal todos os campos são públicos e visíveis por qualquer classe.

Agora vamos alterar a classe Exemplo.

```java
package teste;
public class Exemplo{
    public    String campo1;
              String campo2;
    protected String campo3;
    private   String campo4;
}
```

Agora a classe Programa apresenta erro. O erro é no campo4, que por estar private não é visível à nenhuma outra classe.

Crie um novo pacote, e troque a classe programa de pacote. Lembre-se de trocar a primeira linha da classe também.

Agora ela tem mais erros!

Apenas o campo1 tem visibilidade para fora do pacote, por ser public e continua funcionando.

Todos os outros modificadores não permitem visibilidade para fora do pacote, então a classe programa não os enxerga.

Utilizamos muito esse tipo de encapsulamento para restringir o quando um módulo poderá acessar de outro.

Já o encapsulamento *private* é mais usado para restringir a forma como outra classe fará acesso aos atributos, o que veremos a seguir.