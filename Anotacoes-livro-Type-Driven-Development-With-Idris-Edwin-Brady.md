### Type-driven development

#### O que são tipos

Na programação, os tipos são um meio de classificar valores. Ex: os valores 94, "coisa" e [1, 2, 3, 4]
poderiam se classificados como um número inteiro, uma string, e uma lista de números inteiros, desse modo
você não pode usar uma string em uma parte de um programa em que você precisa de um número inteiro.

##### Tipos tem várias funções importantes:

* Para uma máquina, os tipos descrevem como os padrões de bits na memória devem ser interpretados.
* Para um compilador ou interpretador, os tipos ajudam a garantir que os padrões de bits sejam interpretados consistentemente quando um programa é executado.
* Para um programador, os tipos ajudam a **nomear** e **organizar conceitos**, ajudando na **documentação** e suporte a ambientes de edição interativos  

<br>

A função dos tipos mais significativa para um programador é a terceira. Os tipos podem ajudar de diversas maneiras:

* Ao permitir a nomeação e organização de conceitos.
* Ao fornecer **documentação explícita** dos propósitos de variáveis, funções, e programas.
* Ao dirigir o auto-complete de código em ambientes de edição interativos.

<br>

#### Type-driven development
Type-driven development é um estilo de programação onde nós escrevemos os **tipos primeiro** e usamos esses tipos para guiar a
**definição de funções**. O processo geral é escrever os tipos de dados e em seguida para cada função fazer o seguinte:

* Escrever os tipos de input e output.
* Definir a função, usando a estrutura dos tipos de input e output para guiar a implementação.
* Refinar e editar os tipos e definição da função conforme necessário.

Em Type-driven development devemos pensar nos tipos como um **plano**, com o *type checker* atuando como um guia, nos
levando até um programa robusto e funcional, usando o compilador regularmente para verificar se o programa satisfaz
o tipo criado.  

Alguma linguagens de programação como Haskell e ML permitem que seja omitido a definição de tipos da função, tendo o compilardor inferir o tipo, em Type-drive development é encorajado a declaração de tipos, ajudando a documentação do programa.

<br>

#### Type, define, refine: O processo do Type-driven development

Podemos caracterizar o Type-driven development como um processo **iterativo** das seguintes etapas: **type**, **define**, **refine**, ou seja, escrever um tipo, implementar um função que satisfaça esse tipo, e refinar o tipo e a função à medida que você aprende mais sobre o problema.  
Em Type-driven development seguimos o processo ``type, define, refine``  
* ``type`` Escreva um **tipo** para iniciao o precesso de desenvolvimento ou use um tipo existente para decidir como continuar o processo;
* ``Define`` Crie a estrutura de definição de uma função, criando um esboço de uma função ou dividindo em componente menores;
* ``Refine`` Melhore a definição da função ou o tipo tornando-os mas precisos;


<br>

#### Dependent types

*Dependent type* é um tipo **calculado** a partir de outros valores, em outras palavras, **dependem** de outros valores.
Ao incluir valores em um tipo podemos tornar os tipos tão precisos quanto necessários.
Tipos dependentes são quando valores podem ser utilizados como parte de um Tipo, o Tipo depende de um valor, ex:

``function soma(tam: int, vetor: array(int, tam)) -> int``  

``array(int, tam)`` é um tipo dependente, **tam** pode ser qualquer valor, até mesmo algo fornecido pelo usuário, e ele está em um tipo.

<br>

Pensando em uma função que atualiza a idade de uma pessoa. Ela poderia ter a seguinte assinatura:

``atualizaIdade :: Pessoa -> Int -> Pessoa``   

Pensando que não seja possível uma idades < 0

``atualizaIdade :: Pessoa -> (a :: Int, a > 0) -> Pessoa``  

Agora o tipo carrega informação sobre o conteúdo. E isso é verificado em tempo de compilação.

<br>

``(n: Int) -> (m: Int) -> (p: m < n) -> Foo``

Recebe dois inteiros, osegundo deve ser manor que o primeiro e devolve um Foo.
**p** é uma prova de que **m < n**, então os parâmetros tem que obedecer a restrição.

Um conceito fundamental do Type-drive development com uma linguagem com tipos dependentes é que o **tipo** de uma variável pode ser **calculado a partir do valor de outra variável**

<br>

```idris
f : Bool -> Type
f x = case x of
	True => Int
	False => String
```

```idris
fn : (x : Bool) -> f x -> String
fn x val = case x of
	True => cast val
	False => val
```

<br>

##### Linguagem funcional

Não existe um concenso sobre uma definição do que é uma linguagem funcional, mas tomamos os seguintes pontos:

* Os programas são compostos de funções.
* A execução do programa consiste na avaliação de funções.
* Funções são uma construção first-class da linguagem.

Programação funcional se difere do paradigma imperativo por se preocupar com a avaliação de funções e não com a execução de instruções.

Em uma linguagem de programação funcional pura existem dois pontos:

* As funções não têm **efeitos colaterais**, como modificar variáveis globais, lançar exceções ou mostras algo do console.
* Como resultado, para **quaisquer entradas** específicas, uma função sempre fornecerá o **mesmo resultado**.

<br>

#### Pureza e transparência referêncial  

O conceito chave de uma **função pura** é que as mesmas entradas sempre devem produzir as mesmas saídas, essa propriedade se chama ``transparência referencial``.
Uma expressão em uma função é **referêncialmente transparente** se puder ser substituída pelo resultado sem alterar o comportamento da função, se a função não produz efeitos colaterais essa propriedade é verdadeira.

<br>

##### First-class types

Uma linguagem que tem **first-class** types significa que  uma expressão é tratada como um valor, sem restrição sintática, sendo assim ela pode ser passada como parâmetro pra um função, retornada como resultado de uma função e atribuída a uma variável.  
Na maioria das linguagens estaticamente tipadas existem restrições de onde os tipos podem ser usados, e também há uma separação sintática entre tipos e valores. As espressões como first-class podem ser utilizadas da mesma forma como qualquer valor e também como parte de um tipo.  

<br>

* Tipos são um **meio para classificar valores**. Linguagens de programação usam tipos para organizar os dados na memória;
* Podemos ver um **Tipo** como uma especificação para que uma implementação de linguagem (Type Checker) possa verificar se um programa está em conformidade com essa especificação;
* Type-driven development é um **processo iterativo** de criar um tipo para modelar um sistema, definir funções para esse tipo e refinar ambos a medida que se aprende mais sobre o problema a ser resolvido;
* Em Type-driven development um tipo é visto mais como um **plano**;
* Dependent Types permite criarmos **tipos mais precisos** e descritivos para os nosso programas;
* Em uma linguagem de programação funcional a execução de um programa consiste na **avaliação de funções**;
* Em uma linguagem funcional as funções não tem **efeitos colaterais**;
* Ao invez de escrever programas com efeitos colateriais, pode-se escrever **programas que descrevam** efeitos colateriais explicitamente nos tipos;
* Uma *total function* é garantida que **produzirá um resultado** para qualquer entrada em tempo finito;

<br>

##### Partial application
Quando temos uma função que possui mais de um parâmetro, podemos criar uma versão mais especializada dessa função passando apenas alguns dos argumentos e omitindo o restante, essa técnica é chamada de **Partial application**
Imaginamos uma função ``add``

```idris
add : Int -> int -> Int
add x y = x + y
```

Se aplicarmos essa função apenas com o primeiro parâmetro é retornado uma outra função com a definição ``Int -> Int``, assim criamos uma função especializada que adiciona 2 a qualquer valor inteiro passado.
```
addTwo = add 2

addTwo 5 // 7

addTwo 20 // 22
```

<br>

##### Higher-order function types
Não há restrição ao argumento ou tipo de retorno de uma função, dessa forma, funções podem ser passadas como argumento de outra função, essas funções são chamdas de **Higher-order function**.  
Higher-order function podem ser utilizadas para criar abstrações para padrões de desenvolvimento.

<br>

##### Composite types  
Composite types são tipos compostos por outros tipos
``Tuple`` é uma collection de tamanho fixo onde cada valor **pode ser de tipos diferentes**.
```
(Integer, String)
(49, "pages")
```

``List`` é uma collection de valores, pode ter tamanho variados, todos os elementos de uma List **devem ser do mesmo tipo**.
```
List Integer
[1, 2, 3, 4, 5]
```









