###### FIAP - TDS - Prof. Tiago Ferrer

## Domain Driven Design
###### Semana 3

### Objetivos

* Utilizar Scanner para ler inputs via console
* Operações de controle: Aperfeiçoaremos o uso de estruturas condicionais e de repetição para criar programas mais dinâmicos e eficientes.
* Classes, Atríbutos e Métodos
* Diagrama de classes

### Lendo inputs do console

A biblioteca `java.util.Scanner` em Java fornece uma maneira simples e eficiente de ler dados do console. Ela oferece métodos para ler diferentes tipos de dados, como strings, números inteiros e números de ponto flutuante.

**Como usar a biblioteca Scanner:**

1. Importar a biblioteca:

````java
import java.util.Scanner;
````

2. Criar um objeto Scanner:

````java
Scanner scanner = new Scanner(System.in);
````

3. Ler dados usando métodos específicos:

* `scanner.next()`: Lê a próxima string
* `scanner.nextInt()`: Lê o próximo número inteiro
* `scanner.nextDouble()`: Lê o próximo número de ponto flutuante

4. Fechar o objeto Scanner:
````
scanner.close();
````

#### Exemplo

````java
Scanner scanner = new Scanner(System.in);

System.out.println("Digite seu nome: ");
String nome = scanner.next();

System.out.println("Digite sua idade: ");
int idade = scanner.nextInt();

System.out.println("Olá, " + nome + "! Você tem " + idade + " anos de idade.");

scanner.close();

````

### Operações de Controle em Java

As operações de controle em Java permitem que você defina o fluxo de execução de um programa. Elas determinam quais partes do código serão executadas e em qual ordem.

**Existem diversos tipos de operações de controle em Java:**

* Estruturas condicionais:

    * `if`: Executa um bloco de código se uma condição for verdadeira.
    * `else`: Executa um bloco de código se uma condição for falsa.
    * `else if`: Permite verificar várias condições em sequência.
    * `switch`: Executa um bloco de código específico com base no valor de uma variável.

* Estruturas de repetição:

    * `for`: Executa um bloco de código um número determinado de vezes.
    * `while`: Executa um bloco de código enquanto uma condição for verdadeira.
    * `do-while`: Executa um bloco de código pelo menos uma vez e depois repete enquanto uma condição for verdadeira.

* Instruções de desvio:

    * `break`: Sai de um loop ou bloco de código.
    * `continue`: Pula para a próxima iteração de um loop.

#### Exemplos de uso de operações de controle:

````java
// Estruturas condicionais (if)

int idade = 17;

if (idade >= 18) {
    System.out.println("Maior de idade");
} else {
    System.out.println("Menor de idade");
}

````
````java
// Estruturas de repetição (for)

for (int i = 0; i < 10; i++) {
    System.out.println(i);
}

````
````java
// Estruturas de repetição (while)

int numero = 1;

while (numero <= 10) {
    if (numero % 2 == 0) {
        // Pula para a próxima iteração do loop se o número for par
        continue;
    }

    System.out.println("Número ímpar: " + numero);

    // Sai do loop se o número for 5
    if (numero == 5) {
        break;
    }

    numero++;
}
    
````
````java
// Estruturas de repetição (do-while)

int idade = 0;

do {
     System.out.println("Menor de idade com " + idade + " anos");
     idade ++;
     } while (numero < 18);

````
````java
// Instrução de desvio (switch)

int dia = 5;

switch (dia) {
            case 5:
                System.out.println("Dia de receber salário");
                break;
            case 10:
                System.out.println("Dia de pagar a luz");
                break;
            case 15:
                System.out.println("Dia de pagar a internet");
                break;
            default:
                System.out.println("Dia sem obrigação financeiras");
        }
````

### Classes, Atributos e Métodos


As classes são os blocos de construção fundamentais na programação baseada em Orientação a Objetos (OO). Fazendo uma analogia com a construção civil, podemos imaginar uma classe como uma planta baixa de uma casa. A planta define a estrutura da casa, incluindo o número de cômodos, portas e janelas. Analogamente, uma classe define a estrutura de um objeto, especificando suas propriedades (atributos) e comportamentos (métodos).

Por exemplo, podemos ter uma classe Carro que define as propriedades de um carro, como cor, modelo e ano. A classe também pode conter métodos que simulam o comportamento de um carro, como `acelerar()`, `frear()` e `buzinar()`.

Veja alguns pontos-chave sobre classes em Java:

* **Atributos ou Campos (*Fields*)**: Representam as características de um objeto, como seus dados.

* **Métodos**: Definem o comportamento de um objeto, ditando as ações que ele pode realizar.

* **Objetos**: São instâncias criadas a partir de uma classe. Pense em um objeto como uma casa construída a partir da planta baixa. Vários objetos podem ser criados a partir da mesma classe, assim como podemos construir várias casas a partir da mesma planta.

Resumindo, classes servem como modelos para criar objetos, encapsulando suas propriedades e comportamentos. Isso promove a organização, reusabilidade e modularidade do código Java.

```java
public class Carro {

    private int velocidade;

    private String cor;

    private int portas;

    private int ano;

    private String modelo;

    public void acelerar(){
        velocidade++;
    }

    public void frear(){
        if(velocidade > 0){
            velocidade--;
        }
    }
}
```

### Classes Anêmicas: Um Problema Comum em Java e DDD

Em Java, classes anêmicas são classes que não possuem comportamento significativo. Elas servem apenas como containers de dados, armazenando atributos e *getters/setters*. Isso pode levar a diversos problemas, como:

* **Falta de coesão**: A classe não possui um único propósito claro, tornando-a difícil de entender e manter.
* **Falta de reutilização**: A classe não pode ser facilmente reutilizada em outros projetos, pois seu comportamento é específico para o contexto atual.
* **Código frágil**: Alterações nos atributos da classe podem ter um efeito cascata no código que a utiliza.

**DDD e Classes Anêmicas**:

O Domain-Driven Design (DDD) é uma metodologia de desenvolvimento de software que coloca o foco no **domínio do problema**. No DDD, as classes representam entidades do domínio e possuem um comportamento rico e significativo. Isso evita a criação de classes anêmicas.

**Exemplos de Classes Anêmicas**:

* **Classe Pessoa**: Uma classe Pessoa que apenas armazena nome, idade e sexo é anêmica. Ela não possui nenhum comportamento significativo, como calcular a idade ou verificar se a pessoa é maior de idade.
* **Classe Endereço**: Uma classe Endereço que apenas armazena logradouro, número, complemento, cidade e estado é anêmica. Ela não possui nenhum comportamento significativo, como formatar o endereço para impressão ou calcular a distância entre dois endereços.

**Como evitar Classes Anêmicas**:

Aplique os princípios do DDD: Crie classes que representam entidades do domínio e que possuem um comportamento rico e significativo.
Utilize métodos e interfaces: Utilize métodos para encapsular o comportamento da classe e interfaces para definir contratos entre classes.
Evite getters/setters triviais: Utilize getters/setters apenas quando necessário. Se um atributo não precisa ser modificado, declare-o como final.
Exemplos de Classes com Comportamento:

* **Classe Pessoa**: Uma classe Pessoa que calcula a idade, verifica se a pessoa é maior de idade e formata o nome para diferentes contextos.
* **Classe Endereço**: Uma classe Endereço que formata o endereço para impressão, calcula a distância entre dois endereços e valida o CEP.


Classes anêmicas são um problema comum em Java que pode levar a diversos problemas. Ao aplicar os princípios do DDD e evitar getters/setters triviais, você pode criar classes com comportamento rico e significativo, tornando seu código mais coeso, reutilizável e robusto.


### Enum em Java: Definição, Usos e Exemplos

Um **Enum** em Java é um tipo especial de classe que define um conjunto de valores constantes e relacionados. Pense em um Enum como um "menu" de opções pré-definidas para um determinado tipo de dado.

**Quando usar Enum:**

* Para representar um conjunto de valores finitos e relacionados, como:
    * Dias da semana (`SEGUNDA`, `TERCA`, `QUARTA`, ...)
    * Cores (`VERMELHO`, `VERDE`, `AZUL`, ...)
    * Tamanhos de roupas (`P`, `M`, `G`, ...)
* Para melhorar a legibilidade e segurança do código, evitando "strings mágicas" e valores inconsistentes.
* Para facilitar a comparação e manipulação de valores, utilizando métodos específicos de Enum.

**Como usar Enum:**

* **Declaração**: Utilize a palavra-chave enum seguida do nome do Enum e dos valores entre chaves.

**Exemplos**:

```java
enum DiaDaSemana {
    SEGUNDA, TERCA, QUARTA, QUINTA, SEXTA, SABADO, DOMINGO
}

enum Cor {
    VERMELHO, VERDE, AZUL, AMARELO, PRETO, BRANCO
}

enum TamanhoRoupa {
    P, M, G, GG, XG
}
```

* **Utilização**: Crie variáveis do tipo Enum e utilize os valores como constantes.

* **Exemplos**:

```java
DiaDaSemana hoje = DiaDaSemana.QUARTA;
Cor carro = Cor.VERMELHO;
TamanhoRoupa camisa = TamanhoRoupa.M;

if (hoje == DiaDaSemana.SEXTA) {
    System.out.println("Ufa, fim de semana!");
}

switch (carro) {
    case VERMELHO:
        System.out.println("Carro vermelho é paixão!");
        break;
    case VERDE:
        System.out.println("Carro verde é esperança!");
        break;
    default:
        System.out.println("Carro de outra cor!");
}
```

**Vantagens de usar Enum**:

* **Segurança**: Evita erros de digitação e valores inconsistentes.
* **Legibilidade**: Torna o código mais fácil de entender e manter.
* **Reutilização**: Permite a criação de tipos de dados customizados e reutilizáveis.
* **Facilidade de uso**: Oferece métodos para comparação, ordenação e outras operações.

Enum é um recurso poderoso em Java que permite definir conjuntos de valores constantes e relacionados,
melhorando a legibilidade, segurança e reutilização de código. Explore os recursos avançados para
criar tipos de dados customizados e ainda mais eficientes

### UML (Unified Modeling Language)

UML (Linguagem de Modelagem Unificada) é uma linguagem de modelagem padrão usada para descrever, visualizar, especificar, construir e documentar os artefatos de sistemas de software. Ela é amplamente utilizada no desenvolvimento de software orientado a objetos, oferecendo uma maneira compreensível de representar tanto o design quanto a estrutura de sistemas complexos.

#### Representação de Classes no UML

No UML, as classes são representadas por um retângulo dividido em três seções:
* **Nome da Classe**: Localizado na parte superior do retângulo, contém o nome da classe.
* **Atributos**: Localizados no meio do retângulo, contêm os atributos da classe.
* **Métodos**: Localizados na parte inferior do retângulo, contêm os métodos da classe.
* **Símbolos de Visibilidade**: Podem ser usados para indicar a visibilidade dos atributos e métodos (público, privado, protegido, pacote).
* **Símbolos de Estereótipo**: Podem ser usados para indicar o papel da classe (por exemplo, interface, classe abstrata).

<div style="text-align: center;">
  <img src="imgs/img_class_basics.png" alt="Representação básica de classes no UML">
</div>

#### Representações de Visibilidade no UML

No UML (Unified Modeling Language), as visibilidades são utilizadas para controlar o acesso a atributos e métodos dentro de uma classe. Elas determinam se um membro de uma classe é acessível fora dela ou apenas dentro do próprio contexto. As representações de visibilidade são indicadas por modificadores de acesso, que são símbolos colocados antes do nome do atributo ou método.

As principais representações de visibilidade no UML são:

- **Público (`+`)**: O membro é acessível de qualquer lugar, ou seja, fora da classe e até mesmo de outras classes. Representado pelo símbolo `+`.

- **Privado (`-`)**: O membro é acessível apenas dentro da própria classe. Não pode ser acessado diretamente de fora. Representado pelo símbolo `-`.

- **Protegido (`#`)**: O membro é acessível dentro da classe e suas subclasses (herança). Representado pelo símbolo `#`.

- **Pacote (`~`)**: O membro é acessível apenas dentro do mesmo pacote (ou namespace). Representado pelo símbolo `~`.

*Observação: Vamos estudar visibilidade mais a fundo nas próximas semanas.*

#### Relacionamentos em UML

No contexto do UML, os **relacionamentos** são essenciais para ilustrar como os diferentes elementos de um sistema interagem entre si. Alguns dos principais tipos de relacionamentos em UML são:

<div style="text-align: center;">
  <img src="imgs/uml_relacoes.gif" alt="Tipos de Relacionamentos em UML">
</div>

##### 1. Associação
Representa uma ligação entre duas classes ou objetos. A associação pode ter um nome, uma direção e, muitas vezes, é associada a uma multiplicidade que especifica quantas instâncias de uma classe podem estar relacionadas a uma instância de outra classe. É representada por uma linha simples entre as classes.

##### 2. Agregação
Um tipo especial de associação, onde uma classe representa uma parte de outra classe. A agregação implica que a parte pode existir independentemente do todo. A relação é mostrada com uma linha que termina em um losango vazio na classe "todo". Um exemplo seria uma "Escola" agregando "Professor" ou "Aluno", pois essas entidades podem existir fora do contexto da escola.

##### 3. Composição
É uma forma mais forte de agregação. Quando uma classe contém outra em uma relação de composição, a parte não pode existir sem o todo. A composição é representada com uma linha que termina em um losango sólido. Um exemplo seria uma "Casa" e "Quarto", onde o quarto não faz sentido sem a casa.

##### 4. Generalização
Indica uma relação entre uma classe mais geral (superclasse) e uma classe mais específica (subclasse). A classe filha herda as propriedades e comportamentos da classe mãe. Este relacionamento é indicado por uma linha com um triângulo na extremidade apontando para a superclasse.

##### 5. Realização
Refere-se à implementação de uma interface por uma classe. Uma classe que implementa uma interface "realiza" essa interface. Esse relacionamento é indicado por uma linha pontilhada com um triângulo na extremidade.

##### 6. Dependência
Mostra que uma classe depende de outra para funcionar. Isso indica que qualquer mudança na classe dependente pode afetar a classe que a utiliza. Representado por uma linha pontilhada com uma seta.

#### Multiplicidade em UML

A **multiplicidade** em UML define quantas instâncias de uma classe podem estar associadas a uma instância de outra classe. Essa característica é usada principalmente nas associações e pode ser especificada ao longo das linhas de associação entre os elementos do diagrama.

A multiplicidade é indicada com números ou intervalos nas extremidades das linhas de associação. Alguns exemplos de multiplicidade são:

* **n**: Indica que deve haver exatamente uma instância da classe associada. Por exemplo, uma pessoa pode ter apenas um RG, nesse caso `n` seria igual a 1.

* **0..1** (opcional): Indica que pode haver zero ou uma instância associada. Por exemplo, um cliente pode não ter um pedido, mas se tiver, será apenas um.

* **1..* ou * (asterisco)**: Indica que pode haver uma ou mais instâncias associadas. Por exemplo, uma "Biblioteca" pode ter muitos "Livros", mas cada livro deve pertencer a apenas uma biblioteca.

* **0..* ou * (asterisco)**: Indica que pode haver zero ou muitas instâncias associadas. Por exemplo, uma "Pessoa" pode ter nenhum ou muitos "Filhos".

Essas anotações de multiplicidade são fundamentais para compreender as restrições e limitações no relacionamento entre os elementos do sistema, ajudando a modelar e entender melhor o comportamento do sistema.


### Exercícios

1. Escreva um programa para ler 2 valores (considere que não serão informados valores iguais) e escrever o maior deles.
2. Escreva um programa para ler o ano de nascimento de uma pessoa e escrever uma mensagem que diga se ela poderá ou não votar este ano
   (não é necessário considerar o mês em que ela nasceu). 
3. Escreva um programa que verifique a validade de uma senha fornecida pelo usuário. A senha válida é o número 1234. Devem ser impressas as seguintes mensagens:
   ACESSO PERMITIDO caso a senha seja válida.
   ACESSO NEGADO caso a senha seja inválida.
4. As maçãs custam `R$ 0,30` cada se forem compradas menos do que uma dúzia, e R$ 0,25 se forem compradas pelo menos doze. Escreva um  
   programa que leia o número de maçãs compradas, calcule e escreva o valor total da compra.
5. Escreva um programa que leia as medidas dos lados de um triângulo e escreva se ele é Equilátero, Isósceles ou Escaleno. Sendo que:
      − Triângulo Equilátero: possui os 3 lados iguais.
      − Triângulo Isóscele: possui 2 lados iguais.
      − Triângulo Escaleno: possui 3 lados diferentes.
6. Leia o código de um determinado produto e mostre sua classificação. Utilize a seguinte tabela como referência:

| Código | Classificação | 
| :------: | :-------------: |
| 1 	 | Alimento não-perecível |
| 2 | Alimento perecível |
| 3 | Vestuário |
| 4 | Higiene Pessoal |
| 8 até 15 |  Limpeza e Utensílios Domésticos |
| Qualquer outro código | Código  inválido |

7. Faça um programa que receba duas notas, calcule e mostre a média aritmética e mensagem que está na tabela a seguir:

| Média Aritmética | Mensagem | 
| :------: | :-------------: |
|0,0 – 4,0 |Reprovado |
|4,1 – 7,0 |Exame |
|7,1 – 10,0| Aprovado |