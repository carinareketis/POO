## Sobrecarga de Operadores (overload)

Métodos de mesmo nome com assinaturas diferentes em uma mesma classe configuram sobrecarga de operadores.

Por exemplo:

```java
public class Matematica{
    public byte somar (byte a, byte b){ return a + b; }         //Assinatura: somar(byte,byte)
    public short somar (short a, short b){ return a + b; }      //Assinatura: somar(short,short)
    public int somar (int a, int b){ return a + b; }            //Assinatura: somar(int,int)
    public long somar (long a, long b){ return a + b; }         //Assinatura: somar(long,long)
    public float somar (float a, float b){ return a + b; }      //Assinatura: somar(float,float)
    public double somar (double a, double b){ return a + b; }   //Assinatura: somar(double,double)
}
```

Nesse exemplo a sobrecarga se dá pela mudança dos tipos dos dois parâmetros que os métodos "soma" recebem.

Podemos também mudar a assinatura dos métodos mudando a quantidade de parâmetros.

```java
public class conexao{
    private String host = "localhost";
    private int port = 8080;

    //Assinatura: conectar()
    
    public void conectar(){ 
        /*...lógica da conexão...*/ 
    }

    //Assinatura: conectar(String)
    
    public void conectar(String host){
        this.host = host;
        /*...lógica da conexão...*/
    }

    //Assinatura: conectar(String, int)
    
    public void conectar(String host, int port){
        this.host = host;
        this.port = port;
        /*...lógica da conexão...*/
    }
}
```

Nesse exemplo, o método conectar pode ser invocado sem parâmetros, e usará os valores pré-definidos.
Pode ser chamado com uma String e altera o valor de host antes de rodar.
Pode ser chamado com uma String e um int e altera host e port antes de rodar.

Quando uma sobrecarga apenas aumenta a quantidade de parâmetros e executa a lógica geralmente chamamos um método dentro do outro.
Assim a manutenção é mais simples por não existirem cópias dos métodos:

```java
public class conexao{
    private String host = "localhost";
    private int port = 8080;

    //Assinatura: conectar()
    
    public void conectar(){ 
        /*...lógica da conexão...*/ 
    }

    //Assinatura: conectar(String)
    
    public void conectar(String host){
        this.host = host;
        conectar();
    }

    //Assinatura: conectar(String, int)
    
    public void conectar(String host, int port){
        this.port = port;
        conectar(host);
    }
}
```

No exemplo acima, apenas o método com assinatura *conectar()* possui a lógica de conexão.
Assim evitamos duplicações e qualquer alteração será feita apenas nele, e não em todos os três.