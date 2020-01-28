
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

Type-driven development é um estilo de programação onde nós escrevemos os **tipos primeiro** e usamos esses tipos para guiar a
**definição de funções**. O processo geral é escrever os tipos de dados e em seguida para cada função fazer o seguinte:

* Escrever os tipos de input e output.
* Definir a função, usando a estrutura dos tipos de input e output para guiar a implementação.
* Refinar e editar os tipos e definição da função conforme necessário.

Em Type-driven development devemos pensar nos tipos como um **plano**, com o *type checker* atuando como um guia, nos
levando até um programa robusto e funcional, usando o compilador regularmente para verificar se o programa satisfaz
o tipo criado.

<br>

#### Type, define, refine: O processo do Type-driven development

Podemos caracterizar o Type-driven development como um processo **iterativo** das seguintes etapas: **type**, **define**, **refine**, ou seja, escrever um tipo, implementar um função que satisfaça esse tipo, e refinar o tipo e a função à medida que você aprende mais sobre o problema.

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








