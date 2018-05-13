### POO - Atributos

Quando modelamos um cenário do mundo real para uma linguagem computacional fazemos um exercício de abstação: 

Primeiro definimos quais das entidades que observamos são parte essencial do nosso problema. Isso definirá quais classes teremos no programa.

A seguir, definiremos quais são as **características** dessa entidade que precisam ser incluídas em nosso modelo. Para isso, precisamos nos referir a um *domínio*. A palavra *domínio* nesse contexto será o problema a ser resolvido. Então, usamos a abstração para elencar quais características são essenciais para o problema e quais podem ser ignoradas.

O domínio é essencial porque a mesma entidade terá características importantes diferentes em cada domínio.

Por exemplo, uma entidade *Pessoa* pode aparecer em diversos domínios, quase todo sistema tem alguma entidade representando seres humanos. No entanto, a *Pessoa* muda de domínio para domínio. Em uma escola, podemos descrever uma pessoa pelo seu nome, idade e matrícula por exemplo. Já em uma academia precisamos de peso e altura. Em uma agência de modelos talvez a cor dos olhos, a cor do cabelo e a cor da pele da pessoa seja importante.

Seria muito estranho uma escola querer registrar a cor de pele dos alunos, assim como seria estranho uma academia querer saber a cor dos olhos. O importante é perceber que domínios diferentes representam sua entidades com características diferentes. Quais características colocar? Apenas as relevantes ao problema!

Assim como chamamos as *Entidades* de **Classes**, na POO, também temos uma palavra especial para *Características*: **Atributos**.

Formalmente um atributo é composto por 3 coisas: Nome, Tipo e Encapsulamento.

**Nome:** Deve descrever com precisão que característica ele representa, mas deve obedecer as convenções de cada linguagem.
**Tipo:** Deve ser um *tipo primitivo*, uma *classe* ou uma *interface*.
**Encapsulamento:** Define a visibilidade do atributo para fora da classe. Veremos mais a frente como usar.

Definir o nome de um atributo é o mais fácil, obedeça às regras de nomes de variáveis da liguagem de programação que você vai utilizar, no geral não coloque acentos, espaços, caracteres especiais ou inicie com números (varia de linguagem para linguagem). No JAVA, temos a convenção de usar letras minúsculas, execeto ao juntar palavras quando a letra inicial de cada palavra (a partir da segunda) deverá ser maiúscula, por exemplo, **nomeCompleto**. Lembre-se de usar nomes bons para descrever as características! 

**A350** é um nome válido em JAVA, mas quebra a convenção de usar minúsculas e seria terrível em um atributo que representa a característica idade de uma pessoa! Por que não usar **idade**?? 
Hoje em dia, temos um limite grande para o nome do atributo utilize o mais claro possível, mesmo que mais longo...

Quanto ao **tipo**: 
Você pode escolher qualquer um dos tipos primitivos do JAVA:

|Tipo     | Valor padrão|Representa                                                                     |
|---------|:-----------:|-------------------------------------------------------------------------------|
|byte     |0            | Número inteiro de -128 até 127                                                |
|short	  |0            | Número inteiro de -32.768 até 32.767                                          |
|int      |0            | Número inteiro de -2.147.483.648 até 2.147.483.647                            |
|long	  |0L           | Número inteiro de -9.223.372.036.854.775.808 até 9.223.372.036.854.775.80     |
|float	  |0.0f         |Número decimal de 4 bytes com 7 dígitos decimais                               |
|double	  |0.0d         |Número decimal de 8 bytes com 16 dígitos decimais                              |
|char	  |'\u0000'     | Uma letra, deve-se usar apóstrofe ex. 'a'                                     |
|boolean  |false        | Valores true ou false                                                         |

Você pode escolher qualquer **classe**: 
Usamos a classe **String** para representar textos de múltiplos caracteres.
O tipo de um atributo pode ser uma classe que você mesmo criou.

Interfaces: Veremos mais adiante...

Para escrever um atributo em JAVA basta seguir a sintaxe "<encapsulamento> <tipo> <nome>;". 

Vamos padronizar o encapsulamento como *public* por enquanto:

```java
public class Carro{
    public String marca;
    public String modelo;
    public int ano;
    public float preco;
}
```

Já em UML, representamos os atributos em sua própria divisão, public é representado pelo símbolo + e o padrão se inverte escrevemos <nome> : <tipo>.

![UML - Carro - Atributos](https://github.com/profgabrielmilitello/POO/blob/master/imagens/cap2-uml-carro.png "UML Carro + atributos")

É muito importante saber traduzir UML em código e vice-versa.

Veja que não colocamos valores nos atributos, isso se dá porque a classe é uma estrutura genérica para representar qualquer objeto de seu tipo. Não faz sentido dizer que todo carro é Fiat ou do ano 2018!

Nos raros casos em que queremos um valor padrão aplicado a todos os objetos do tipo da classe, podemos inicializar o atributo com um valor:

```java
public class Conexao{
    public String protocolo = "http";
}
```