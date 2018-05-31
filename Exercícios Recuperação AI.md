## Instruções

Abaixo estão os exercícios de recuperação para a prova AI.

Faça todos os UMLs solicitados em papel, lembre-se de por nome em todas as folhas!

Todos os códigos JAVA solicitados, bem como demais respostas devem ser entregues no formulário abaixo:

[https://goo.gl/forms/NKUQMHhucpHD2uTk2](https://goo.gl/forms/NKUQMHhucpHD2uTk2)

Nesse formulário também há uma cópia da avaliação A.I. para refacção.

## DATAS

### O formulário deverá ser entregue sem possibilidade de adiamento/prorrogação até **3 de Junho (domingo) às 23:59:59**.

### Os UMLs em papel devem ser entregues na aula de **4 de junho**.

## Exercícios

### Classes / Atributos / Métodos

1. Crie uma classe(UML e JAVA) Gato com nome, raça, cor e idade públicos.

2. Crie uma classe(UML e JAVA) Boletim com nome do aluno, um vetor de notas e um vetor de boolean para presenças, todos públicos;

3. Crie uma classe(UML e JAVA) Motor com fabricante, modelo, preco públicos.

4. Crie uma classe(UML e JAVA) Carro com fabricante, nome, modelo, e Motor (do exercício 3) públicos.

5. Crie uma classe(UML e JAVA) PeixeOrnamental com PH ideal, temperatura ideal, dureza da Agua ideal, nome e nome científico públicos.

### Encapsulamento / Construtor

6. Crie uma classe(UML e JAVA) Contato com nome e telefone privados e com métodos de acesso.

    Faça também um construtor que receba um nome e telefone: ele deve invocar o set de cada atributo passando o valor recebido.

7. Crie uma classe (UML e JAVA) chamada Lampada, com um boolean privado chamado aceso.
 
    Adicone dois métodos, acender e apagar, que alteram aceso para true e false respectivamente. 
 
    Faça também um método print() que imprime na tela “aceso” ou “apagado” dependendo do valor em aceso.

8. Crie uma classe (UML e JAVA) Pessoa com nome, altura e peso. 
 
    Os atributos devem ser privados. 
 
    Crie um construtor que receba o nome, a altura e o peso e atribua aos atributos. 
 
    Crie um método que imprime na tela o IMC da pessoa. IMC = peso / (altura * altura). 
 
    Faça apenas os métodos de acesso GET.

9. Faça o código JAVA para a classe abaixo:
    
    Os métodos aumentar e diminuir devem modificar a resistenciaAtual para cima ou para baixo em 0.1.
    
    Também devem garantir que o valor de resitenciaAtual não se torne maior que resistenciaMaxima e nem menor que resistenciaMinima.

    ![UML - Potenciometro](https://github.com/profgabrielmilitello/POO/blob/master/imagens/RecAI-uml-Potenciometro.png "UML Potenciometro")

10. Aproveite a classe Motor criada no exercício 3.
    
    Faça uma classe Carro com fabricante, nome, modelo, e Motor como no exercício 4.
    
    Faça um construtor que inicialize o Motor (`this.motor = new Motor();`).
    
    Faça os métodos de acesso para os atributos de Carro.
    
    Faça os métodos de acesso para os atributos do motor em Carro (para cada atributo do motor faça get e set no carro).

## Sobrecarga

11. Faça uma classe Conexao com ip, porta, login e senha.
    
    Faça um construtor que recebe ip e porta e seta os atributos.
    
    Faça um construtor que recebe ip e seta o ip e a porta para 3306 usando o outro construtor.

    Faça um método `conectar` que recebe login e senha e seta ambos.

    Faça um método `conectar` que recebe ip, porta, login e senha e seta todos os atributos.

## Herança

12. Faça uma classe (UML e JAVA) Pessoa com nome e sobrenome. (encapsulado c/ metodos de acesso).
    
    Faça uma classe (UML e JAVA) Cliente com RG, CPF e codigo de cliente. (encapsulado c/ metodos de acesso).
    
    Faça uma classe (UML e JAVA) Usuario com login e senha. (encapsulado c/ metodos de acesso).

    Usuário deverá herdar Cliente, que deverá herdar Pessoa.

    Em seguida responda:

    a) Quais são os atributos **VISÍVEIS** na classe Usuario?
    
    b) Quais são os atributos **NÃO VISÍVEIS** da classe Usuario?

    c) Quais os métodos visíveis na classe Usuário?

13. Quais das linhas abaixo estão corretas levando em conta o Polimorfismo nas classe abaixo?

    ```java
    public class A { }
    public class B extends A { }
    public class C extends B { }
    ```

    a) `A a = new A();`
    
    b) `A a = new B();`
    
    c) `A a = new C();`

    
    d) `B b = new A();`
    
    e) `B b = new B();`
    
    f) `B b = new C();`


    g) `C c = new A();`

    h) `C c = new B();`

    i) `C c = new C();` 

    
    j) `Object o = new A();`

    k) `Object o = new B();`

    l) `Object o = new C();`


    14. Quais das linhas abaixo estão corretas levando em conta o Polimorfismo, e o conceito de classes abstratas, nas classe abaixo?

    ```java
    public abstract class A { }
    public abstract class B extends A { }
    public class C extends B { }
    ```

    a) `A a = new A();`
    
    b) `A a = new B();`
    
    c) `A a = new C();`

    
    d) `B b = new A();`
    
    e) `B b = new B();`
    
    f) `B b = new C();`


    g) `C c = new A();`

    h) `C c = new B();`

    i) `C c = new C();` 

    
    j) `Object o = new A();`

    k) `Object o = new B();`

    l) `Object o = new C();`
