## Classes Abstratas

**Classes abstratas são classes que não podem criar objetos**.

Veja o exemplo:

```java
public class Classe1{ }

public class Programa{
    public static void main (String[] args){
        Classe1 c = new Classe1();
    }
}
```

O código acima, como esperado, roda normalmente.

Vamos transformar Classe1 em uma classe abstrata adicionando *abstract* em sua declaração.

```java
public abstract class Classe1{ }

public class Programa{
    public static void main (String[] args){
        Classe1 c = new Classe1();
    }
}
```

Rode o código acima e verá que há um erro na linha `Classe1 c = new Classe1();`.

Isso se dá porque, apesar de classes abstratas até poderem ter construtores, não podemos invocar o construtor usando *new*.

Isso acontece porque elas não podem criar objetos.

Para que serve então uma classe abstrata?

Usamos a classe abstrata como superclasse quando não queremos objetos da superclasse no programa, por exemplo:

```java
public abstract class Pessoa{
    private int ID;
    private String nome;
    private int idade;

    public int getID() { return this.ID; }
    public String getNome() { return this.nome; }
    public int getIdade() { return this.idade; }

    public void setID(int id){ this.ID = id; }
    public void setNome(String nome){ this.nome = nome; }
    public void setIdade(int idade) { this.idade = idade; }
 }

 public class Cliente extends Pessoa{
    private String CPF;
        
    public String getCPF() { return this.CPF; }
    public void setCPF(String cpf){ this.CPF = cpf; }
 }

public class Usuario extends Pessoa{
    private String login;
    private String senha;
        
    public String getLogin() { return this.login; }
    public String getSenha() { return this.senha; }
    
    public void setLogin(String login){ this.login = login; }    
    public void setSenha(String senha){ this.senha = senha; }
}
```

No código acima, nosso programa precisa de duas entidades Cliente e Usuario.

Ambas tem ID, nome e idade portanto fizemos uma superclasse Pessoa com essas informações e a herdamos.

No entanto, não existe a entidade Pessoa nesse sistema (apenas Cliente e Usuario) portanto colocamos Pessoa como abstrata.

Assim asseguramos que não vamos ter nenhum objeto da Pessoa no sistema.