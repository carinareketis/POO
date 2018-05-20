## Interfaces

Interfaces são tipos em JAVA cuja declaração é semelhante a de uma classe:

```java 
public interface Teste{ }

```
Na declaração apenas usamos a palavra *interface* no lugar de *class*.

No entanto, as semelhanças com classe acabam por aqui.

Interfaces só podem conter uma coisa: **declaração de métodos sem implementação**.

Em um método temos duas partes:

1. Declaração `<encapsulamento> <tipo_de_retorno> <nome>(<parametros>)`
2. Implementação `{ /*lógica do método*/ }`

Em outras palavras, a declaração define a estrutura de um método, seu nome, o que ele precisa de informação para executar e o que ele retornará (se é que retorna).

Já a implementação é o algoritmo que ele executa quando invocado (o que vai dentro das chaves).

Vamos criar um método de exemplo e ver como ele seria escrito em uma interface:

```java 
public void fazerLog(String texto){
    System.out.println("["LocalDateTime.now()+ "] " + texto);
}
```
Para representar esse método em uma interface basta usar apenas a declaração:

```java 
public interface Logavel{
    public void fazerLog(String texto);
}
```
Para usar uma interface, ou melhor, para usar a terminologia correta, para implementar uma interface em uma classe usamos **implements**.

Genéricamente a declaração será: `<encapsulamento> class <nome_da_classe> implements <nome_da_interface>{ }`.

```java 
public interface Logavel{
    public void fazerLog(String texto);
}

public class MinhaClasse implements Logavel{
    @Override
    public void fazerLog(String text){
        System.out.println("["LocalDateTime.now()+ "] " + texto);
    }
}
```
Vamos a alguns detalhes importantes do uso das interfaces:
1. **Na mesma classe você pode implementar quantas interfaces desejar basta separar os nomes por vírgula**.
2. **TODOS os métodos presentes na interface devem ser implementados na classe e devem ter a diretiva (@Override)**.
3. **Assim como vimos em herança, a classe que implementa uma interface adiciona aos seus tipos o tipo da interface**.

Veja que o nome da interface é logável e existe um método fazerLog nela.

Normalmente o nome de uma interface indica uma capacidade que as classes que a implementam têm.

No caso, toda classe que implementa *Logavel* tem a capacidade de escrever um log no console.

Para garatir essa capacidade o JAVA **obriga** que a classe implemente os métodos descritos na interface.

Toda classe que implementar *Logavel* terá o tipo *Logavel* e o método *fazerLog*.