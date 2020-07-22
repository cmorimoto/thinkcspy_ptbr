..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. tradução por Hitoshi: 12/2014
   
..  shortname:: Strings
..  description:: Introdução ao tipo de dados string, operadores e métodos.

Strings
=======

.. index:: tipo de dado composto, caractere, operador subscript, índice

	   
.. Strings Revisited

Revisão de strings
------------------

.. Throughout the first chapters of this book we have used strings to
   represent words or phrases that we wanted to print out.  Our
   definition was simple.  A string is simply some characters inside
   quotes.  In this chapter we explore strings in much more detail.

Ao longo dos primeiros capítulos desse livro nós usamos strings para
representar palavras ou frases que desejávamos imprimir. Nossa
definição foi simples. Um string é simplesmente um grupo de caracteres
entre aspas. Nesse capítulo vamos explorar strings com muito mais
detalhes. 


.. A Collection Data Type

Um tipo de dado composto
------------------------

.. So far we have seen built-in types like: ``int``, ``float``, 
   ``bool``, ``str`` and we've seen lists. 
   ``int``, ``float``, and
   ``bool`` are considered to be simple or primitive data types because their values are not composed
   of any smaller parts.  They cannot be broken down.
   On the other hand, strings and lists are qualitatively different from the others because they
   are made up of smaller pieces.  In the case of strings, they're made up of smaller
   strings each containing one **character**.

Até aqui vimos tipos de dados nativos como: ``int``, ``float``,
``bool``, ``str`` e vimos também listas. Os tipos ``int``, ``float`` e
``bool`` são considerados tipos simples ou primitivos pois seus
valores não são compostos por outras partes menores. Eles não podem
ser quebrados. Por outro lado, strings e listas são qualitativamente
diferentes desses tipos pois eles são construídos de pedaços
menores. No caso de strings, eles são construídos de strings menores,
cada um contendo um **caractere**. 

.. Types that are comprised of smaller pieces are called **collection
   data types**. Depending on what we are doing, we may want to treat
   a collection data type as a single entity (the whole), or we may
   want to access its parts. This ambiguity is useful. 

Tipos que são compostos de pedaços menores são chamados **tipos de
dados compostos**. Dependendo do que estamos fazendo, a gente pode
querer tratar um tipo composto como uma entidade única (o todo), ou a
gente pode querer acessar suas partes. Essa ambiguidade é útil. 

.. Strings can be defined as sequential collections of characters.
   This means that the individual characters that make up the string
   are assumed to be in a particular order from left to right.

Strings podem ser definidos como coleções de sequencias de
caracteres. Isto significa que assumimos que os caracteres individuais
que compõem a cadeia estão em uma determinada ordem, da esquerda
para a direita. 

.. A string that contains no characters, often referred to as the
   **empty string**, is still considered to be a string.  It is simply
   a sequence of zero characters and is represented by '' or "" (two
   quotes with nothing in between).

Uma cadeia que não possui nenhum caractere, muitas vezes chamada de
**string vazio**, é também considerado um string. É simplesmente uma
sequência com zero caracteres e é representado por '' ou "" (dois
apóstrofes ou aspas sem nada entre eles -- observe que o string com
um ou mais caracteres em branco como ' ' é diferente do string vazio ''). 

   
.. index:: operações com strings, concatenação

.. Operations on Strings

Operações com strings
---------------------

.. In general, you cannot perform mathematical operations on strings, even if the
.. strings look like numbers. The following are illegal (assuming that ``message``
.. has type string):

Em geral, você não pode executar operações matemáticas com strings, mesmo que os
strings se pareçam com números. As seguintes operações são ilegais (assumindo que `` message``
seja um string):

.. sourcecode:: python
    
    message - 1   
    "Hello" / 123   
    message * "Hello"   
    "15" + 2

.. Interestingly, the ``+`` operator does work with strings, but for strings, the
.. ``+`` operator represents **concatenation**, not addition.  Concatenation means
.. joining the two operands by linking them end-to-end. For example:

Curiosamente, o operador ``+`` funciona com strings. No entanto, esse
o operador ``+`` representa **concatenação** e não
adição. Concatenação significa juntar os dois operandos unindo o fim
de um com o começo do outro. Por exemplo:

.. activecode:: ch08_add
    :nocanvas:

    fruta = " banana"
    tipo  = "bolo de"
    print(tipo + fruta)

.. The output of this program is ``banana nut bread``. The space before the word
.. ``nut`` is part of the string, and is necessary to produce the space between
.. the concatenated strings.  Take out the space and run it again.

.. The ``*`` operator also works on strings; it performs repetition. For example,
.. ``'Fun'*3`` is ``'FunFunFun'``. One of the operands has to be a string; the
.. other has to be an integer.

A saída deste programa é ``bolo de banana``. O espaço antes da palavra
`` banana`` faz parte da cadeia, e é necessário para produzir o espaço entre
os strings concatenados. Retire o espaço e execute o programa novamente.

O operador ``*`` também funciona com strings; ele realiza repetição. Por exemplo,
``'Vai'*3`` é ``'VaiVaiVai'``. Um dos operadores tem que ser um string; o
outro tem de ser um número inteiro.

.. activecode:: ch08_mult
    :nocanvas:

    print("Vai "*6)

    nome = "Santos"
    print(nome * 3)

    print(nome + " Vai" * 3)

    print((nome + " Vai") * 3)

.. This interpretation of ``+`` and ``*`` makes sense by analogy with
.. addition and multiplication. Just as ``4*3`` is equivalent to ``4+4+4``, we
.. expect ``"Go"*3`` to be the same as ``"Go"+"Go"+"Go"``, and it is.  Note also in the last
.. example that the order of operations for ``*`` and ``+`` is the same as it was for arithmetic.
.. The repetition is done before the concatenation.  If you want to cause the concatenation to be
.. done first, you will need to use parenthesis.

Esta interpretação de ``+`` e ``*`` faz sentido por analogia com
adição e multiplicação. Assim como ``4*3`` é equivalente a ``4+4+4``, nós
esperamos que ``"Vai "*3`` a ser o mesmo que ``"Vai "+"Vai "+" Vai "``, e é. Note-se também no último
exemplo, que a ordem de operações para ``*`` e ``+`` é o mesmo que foi para a aritmética.
A repetição é feita antes da concatenação. Se você quer fazer com que a concatenação seja
feita primeiro, você vai precisar usar parênteses.

**Teste seu entendimento**

.. mchoice:: test_question8_1_1 
   :answer_a: python rocks
   :answer_b: python
   :answer_c: pythonrocks
   :answer_d: Error, you cannot add two strings together.
   :correct: c
   :feedback_a: A concatenação não adiciona espaços.
   :feedback_b: A expressão s+t é calculada primero, então o resultado é impresso
   :feedback_c: Sim, os dois strings são unidos.
   :feedback_d: O operador + tem significado diferente dependendo de seus operandos, nesse caso, dois strings.

   O que é impresso pelos seguintes comandos?
   <pre>
   s = "python"
   t = "rocks"
   print(s+t)

   </pre>


.. mchoice:: test_question8_1_2
   :answer_a: python!!!
   :answer_b: python!python!python!
   :answer_c: pythonpythonpython!
   :answer_d: Error, you cannot perform concatenation and repetition at the same time.
   :correct: a
   :feedback_a: Sim, repetição tem precedência sobre concatenação.
   :feedback_b: Repetição é feita primeiro.
   :feedback_c: O operador de repetição está trabalhando sobre a variável excl.
   :feedback_d: Os operadores + e * são definidos tanto para strings quanto para números.

   O que é impresso pelos seguintes comandos?
   <pre>
   s = "python"
   excl = "!"
   print(s+excl*3)

   </pre>




.. Index Operator: Working with the Characters of a String

Operador de indexação
---------------------

.. The **indexing operator** (Python uses square brackets to enclose the index) 
.. selects a single character from a string.  The characters are accessed by their position or 
.. index value.  For example, in the string shown below, the 14 characters are indexed left to right from postion 0 to position 13.  

O **operador de indexação** (o Python usa colchetes para incluir o
índice) seleciona um único caractere de um string. Os caracteres são
acessados por sua posição ou valor do índice. Por exemplo, na
sequência mostrada abaixo, os 14 caracteres são indexados da esquerda
para a direita a partir posição 0 até a posição 13.

.. image:: Figures/indexvalues.png
   :alt: index values

.. It is also the case that the positions are named from right to left
   using negative numbers where -1 is the rightmost index and so on.
.. Note that the character at index 6 (or -8) is the blank character.

As posições podem ser acessadas também da direita para a esquerda
usando números negativos, onde -1 é o índice mais à direita e assim
por diante.  Note-se que o caractere no índice 6 (ou -8) é o caractere
em branco.

.. activecode:: chp08_index1
    
    escola = "Carlos Gomes"
    m = escola[2]
    print(m)
    
    ultimo = escola[-1]
    print(ultimo)

.. The expression ``school[2]`` selects the character at index 2 from
   ``school``, and creates a new string containing just this one
   character. The variable ``m`` refers to the result.

A expressão ``escola[2]`` seleciona o caractere no índice 2 de ``escola``, e cria um novo string contendo apenas este caractere. A variável ``m`` faz referência ao resultado.

.. Remember that computer scientists often start counting from
   zero. The letter at index zero of ``"Luther College"`` is ``L``.
   So at position ``[2]`` we have the letter ``t``.

Lembre-se que os cientistas da computação muitas vezes começam a contagem
do zero. A letra no índice zero do ``"Carlos Gomes"`` é ``C``. Então,
na posição ``[2]`` temos a letra ``r``.

.. If you want the zero-eth letter of a string, you just put 0, or any expression with the value 0, in the brackets.  Give it a try.

Se você quiser a letra de índice zero de um string, simplesmente
coloque 0, ou qualquer expressão com o valor 0, dentro dos
colchetes. Experimente.

.. The expression in brackets is called an **index**. An index
   specifies a member of an ordered collection.  In this case the
   collection of characters in the string. The index *indicates* which
   character you want. It can be any integer expression so long as it
   evaluates to a valid index value.

A expressão entre parênteses é chamada de **índice**. Um índice
especifica um membro de uma coleção ordenada. Neste caso, a coleção de
caracteres na sequência. o índice *indica* qual caractere você
quer. Pode ser qualquer expressão inteira desde que ela seja avaliada
como um valor de índice válido.

.. Note that indexing returns a *string* --- Python has no special type for a single character. It is just a string of length 1.

Observe que a indexação retorna um *string* --- o Python não tem nenhum tipo especial para um único caractere. É apenas uma sequência de comprimento 1.
   
**Teste seu entendimento**

.. mchoice:: test_question8_2_1
   :answer_a: t
   :answer_b: h
   :answer_c: c
   :answer_d: Error, you cannot use the [ ] operator with a string.
   :correct: b
   :feedback_a: Os índices não começam de 1, eles começam de 0.
   :feedback_b: Sim, os índices começam de 0.
   :feedback_c: s[-3] retorna c, contando da direita para a esquerda.
   :feedback_d: [ ] é o operador de índice.


   O que é impresso pelos seguintes comandos?
   <pre>
   s = "python rocks"
   print(s[3])

   </pre>


.. mchoice:: test_question8_2_2
   :answer_a: tr
   :answer_b: ps
   :answer_c: nn
   :answer_d: Error, you cannot use the [ ] operator with the + operator.
   :correct: a
   :feedback_a: Sim, o operador de indexação tem precedência sobre concatenação.
   :feedback_b: p está na posição 0, não 2.
   :feedback_c: n está na posição 5, não 2.
   :feedback_d: o operador [ ] retorna um string que pode ser concatenado com outro string.


   O que é impresso pelos seguintes comandos?
   <pre>
   s = "python rocks"
   print(s[2] + s[-5])

   </pre>



.. String Methods

Métodos de string
-----------------

.. We previously saw that each turtle instance has its own attributes
   and a number of methods that can be applied to the instance.  For
   example, we wrote ``tess.right(90)`` when we wanted the turtle
   object ``tess`` to perform the ``right`` method to turn to the
   right 90 degrees.  The "dot notation" is the way we connect the
   name of an object to the name of a method it can perform.

Nós já vimos que cada instância de tartaruga tem seus próprios
atributos e um número de métodos que podem ser aplicados à
instância. Por exemplo, nós escrevemos ``tess.right(90)`` para que o
objeto tartaruga ``tess`` execute o método ``right`` para virar 90
graus para a direita. A "notação de ponto" é a forma de ligar o nome
de um objeto com o nome de um método que ele pode executar.

.. Strings are also objects.  Each string instance has its own
   attributes and methods.  The most important attribute of the string
   is the collection of characters.  There are a wide variety of
   methods.  Try the following program.

Strings também são objetos. Cada instância de string tem seus próprios atributos e métodos. O atributo mais importante do string é a coleção de caracteres. Há uma grande variedade de métodos. Rode o seguinte programa.

.. activecode:: chp08_upper

    ss = "Hello, World"
    print(ss.upper())

    tt = ss.lower()
    print(tt)


.. In this example, ``upper`` is a method that can be invoked on any
   string object to create a new string in which all the characters
   are in uppercase.  ``lower`` works in a similar fashion changing
   all characters in the string to lowercase.  (The original string
   ``ss`` remains unchanged.  A new string ``tt`` is created.)

Neste exemplo, ``upper`` é um método que pode ser chamado em qualquer
objeto string para criar um novo string no qual todos os caracteres
estão em maiúsculas. ``lower`` funciona de forma semelhante, onde
todos os caracteres do novo string estão em minúsculas. (O string
original ``ss`` permanece inalterado. Um novo string é criado e é
referenciado por ``tt``.)

.. In addition to ``upper`` and ``lower``, the following table
   provides a summary of some other useful string methods.  There are
   a few activecode examples that follow so that you can try them out.

Além de ``upper`` e ``lower``, a tabela a seguir apresenta um resumo
de alguns outros métodos úteis de string. Existem alguns exemplos em
activecode que se seguem, de modo que você pode experimentá-los.

.. ==========  ==============      ==================================================================
..  Method      Parameters          Description
.. ==========  ==============      ==================================================================
..  upper       none                Returns a string in all uppercase
..  lower       none                Returns a string in all lowercase
..  capitalize  none                Returns a string with first character capitalized, the rest lower

..  strip       none                Returns a string with the leading and trailing whitespace removed
..  lstrip      none                Returns a string with the leading whitespace removed
..  rstrip      none                Returns a string with the trailing whitespace removed
..  count       item                Returns the number of occurrences of item
..  replace     old, new            Replaces all occurrences of old substring with new
.. 
..  center      width               Returns a string centered in a field of width spaces
..  ljust       width               Returns a string left justified in a field of width spaces
..  rjust       width               Returns a string right justified in a field of width spaces
.. 
..  find        item                Returns the leftmost index where the substring item is found
..  rfind       item                Returns the rightmost index where the substring item is found
..  index       item                Like find except causes a runtime error if item is not found
..  rindex      item                Like rfind except causes a runtime error if item is not found
.. ==========  ==============      ==================================================================

==========  ==============      ================================================================================
Método      Parâmetros          Descrição
==========  ==============      ================================================================================
upper       nenhum              Retorna um string todo em maiúsculas
lower       nenhum              Retorna um string todo em minúsculas
capitalize  nenhum              Retorna um string com o primeiro caractere em maiúscula, e o resto em minúsculas

strip       nenhum              Retorna um string removendo caracteres em branco do início e do fim
lstrip      nenhum              Retorna um string removendo caracteres em brando do início
rstrip      nenhum              Retorna um string removendo caracteres em brando do fim
count       item                Retorna o número de ocorrências de item
replace     old, new            Substitui todas as ocorrências do substring old por new

center      largura             Retorna um string centrado em um campo de tamanho largura
ljust       largura             Retorna um string justificado à esquerda em um campo de tamanho largura
rjust       largura             Retorna um string justificado à direita em um campo de tamanho largura

find        item                Retorna o índice mais à esquerda onde o substring item é encontrado
rfind       item                Retorna o índice mais à direita onde o substring item é encontrado
index       item                Como find, mas causa um erro em tempo de execução caso item não seja encontrado
rindex      item                Como rfind, mas causa um erro em tempo de execução caso item não seja encontrado
==========  ==============      ================================================================================

.. You should experiment with these methods so that you understand what they do.  Note once again that the methods that return strings do not change the original.  You can also consult the `Python documentation for strings <http://docs.python.org/py3k/library/stdtypes.html#index-21>`_.

Você deve experimentar esses métodos para que você entenda o que eles fazem. Observe que os métodos que retornam um string não alteram o original. Você também pode consultar a documentação do `Python para strings <http://docs.python.org/py3k/library/stdtypes.html#index-21>`_.

.. activecode:: ch08_methods1

    ss = "    Hello, World    "

    els = ss.count("l")
    print(els)

    print("***"+ss.strip()+"***")
    print("***"+ss.lstrip()+"***")
    print("***"+ss.rstrip()+"***")

    news = ss.replace("o", "***")
    print(news)


.. activecode:: ch08_methods2


    food = "banana bread"
    print(food.capitalize())

    print("*"+food.center(25)+"*")
    print("*"+food.ljust(25)+"*")     # estrelas foram incluidas para mostrar limites
    print("*" +food.rjust(25)+"*")

    print(food.find("e"))
    print(food.find("na"))
    print(food.find("b"))

    print(food.rfind("e"))
    print(food.rfind("na"))
    print(food.rfind("b"))

    print(food.index("e"))


**Teste seu entendimento**

.. mchoice:: test_question8_3_1
   :answer_a: 0
   :answer_b: 2
   :answer_c: 3
   :correct: c
   :feedback_a: Com certeza temos alguns caracteres o e p.
   :feedback_b: Há 2 characteres o mas quantos são p?
   :feedback_c: Sim, some o número de caracteres o com o número de caracteres p.

   O que é impresso pelos seguintes comandos?
   <pre>
   s = "python rocks"
   print(s.count("o") + s.count("p"))

   </pre>



.. mchoice:: test_question8_3_2
   :answer_a: yyyyy
   :answer_b: 55555
   :answer_c: n
   :answer_d: Error, you cannot combine all those things together.
   :correct: a
   :feedback_a: Sim, s[1] é y e o índice de n é 5, portanto 5 caracteres y.
   :feedback_b: Quase. 5 não é repetido, é o número de vezes a serem repetidas.
   :feedback_c: Essa expressão usa o índice de n.
   :feedback_d: Não há erro, o operador de repetição * usou o resultado de indexação e o método index.


   O que é impresso pelos seguintes comandos?
   <pre>
   s = "python rocks"
   print(s[1]*s.index("n"))

   </pre>


.. index::
    single: função len
    single: função; len
    single: erro em tempo de execução
    single: índice negativo
    single: índice; negativo

.. Length

Comprimento
-----------

.. The ``len`` function, when applied to a string, returns the number
   of characters in a string.

A função ``len``, quando aplicada a um string, retorna o número de caracteres no string (ou seja, o seu comprimento).

.. activecode:: chp08_len1
    
    fruta = "Banana"
    print(len(fruta))
    

.. To get the last letter of a string, you might be tempted to try something like this:

Para pegar o último caractere de um string, você pode ficar tentado a experimentar algo como:

.. activecode:: chp08_len2
    
    fruta = "Banana"
    sz = len(fruta)
    last = fruta[sz]       # ERROR!
    print(last)

.. That won't work. It causes the runtime error ``IndexError: string
   index out of range``. The reason is that there is no letter at
   index position 6 in ``"Banana"``. Since we started counting at
   zero, the six indexes are numbered 0 to 5. To get the last
   character, we have to subtract 1 from ``length``.  Give it a try in
   the example above.

Isso não vai funcionar. Isso causa o erro em tempo de execução
``IndexError: string index out of range``. A razão é que não há nenhum
caractere na posição de índice 6 em ``"Banana"``. Como começamos a
contar do zero, os seis índices são numeradas de 0 a 5. Para pegar o
último caractere, temos que subtrair 1 ``comprimento``. Experimente,
tente executar o exemplo acima.

.. activecode:: ch08_len3
    
    fruta = "Banana"
    sz = len(fruta)
    lastch = fruta[sz-1]
    print(lastch)

.. Alternatively, we can use **negative indices**, which count
   backward from the end of the string. The expression ``fruit[-1]``
   yields the last letter, ``fruit[-2]`` yields the second to last,
   and so on.  Try it!  Typically, a Python programmer will access the
   last character by combining the two lines of code from above.

Normalmente, um programador Python irá acessar o último caractere 
combinando as duas linhas de código acima.

.. sourcecode:: python
    
    lastch = fruta[len(fruta)-1]

**Teste seu entendimento**

.. mchoice:: test_question8_4_1
   :answer_a: 11
   :answer_b: 12
   :correct: b
   :feedback_a: O espaço em branco conta como um caractere.
   :feedback_b: Sim, há 12 caracteres no string.


   O que é impresso pelos seguintes comandos?
   <pre>
   s = "python rocks"
   print(len(s))

   </pre>



.. mchoice:: test_question8_4_2
   :answer_a: o
   :answer_b: r
   :answer_c: s
   :answer_d: Error, len(s) is 12 and there is no index 12.
   :correct: b
   :feedback_a: Dê uma nova olhada no cálculo do índice, len(s)-5
   :feedback_b: Sim, len(s) é 12 e 12-5 é 7. Use 7 como índice e lembre-se de começar a contar do 0.
   :feedback_c: O s está no índice 11.
   :feedback_d: Você deve subtrair 5 antes de usar o operador índice.


   O que é impresso pelos seguintes comandos?
   <pre>
   s = "python rocks"
   print(s[len(s)-5])

   </pre>



.. The Slice Operator

Fatiamento
----------

.. A substring of a string is called a **slice**. Selecting a slice is
   similar to selecting a character:

Um substring de um string é chamado de **fatia** (do inglês slice). Selecionar uma fatia é semelhante a selecionar um caractere:
   
.. activecode:: chp08_slice1
    
    singers = "Peter, Paul, and Mary"
    print(singers[0:5])
    print(singers[7:11])
    print(singers[17:21])
    

.. The `slice` operator ``[n:m]`` returns the part of the string from
   the n'th character to the m'th character, including the first but
   excluding the last. In other words, start with the character at
   index n and go up to but do not include the character at
   index m. This behavior may seem counter-intuitive but if you recall
   the ``range`` function, it did not include its end point either.

.. If you omit the first index (before the colon), the slice starts at
   the beginning of the string. If you omit the second index, the
   slice goes to the end of the string.

O operador de `fatia` ``[n:m]`` retorna a parte do string a partir do n-ésimo caractere até o m-ésimo caractere, incluindo o primeiro mas excluindo o último. Em outras palavras, comece com o caractere no índice n e vá até, mas não inclua, o caractere no índice m. Esse comportamento pode parecer contra-intuitivo, mas se você se lembra a função ``range``, ela não inclue o seu ponto final também.

Se você omitir o primeiro índice (antes dos dois pontos), a fatia começa no início da cadeia. Se você omitir o segundo índice, a fatia vai até o fim da cadeia.

.. activecode:: chp08_slice2
    
    fruta = "banana"
    print(fruta[:3])
    print(fruta[3:])

.. What do you think ``fruta[:]`` means?

O que você acha que ``fruta[:]`` significa?

**Teste seu entendimento**

.. mchoice:: test_question8_5_1
   :answer_a: python
   :answer_b: rocks
   :answer_c: hon r
   :answer_d: Error, you cannot have two numbers inside the [ ].
   :correct: c
   :feedback_a: Isso seria s[0:6].
   :feedback_b: Isso seria s[7:].
   :feedback_c: Sim, comece com o caractere no índice 3 e vá até, mas sem incluir, o caractere de índice 8.
   :feedback_d: Isso é chamado de fatiamento, não indexação. O fatiamento requer um início e um fim.

   O que é impresso pelos seguintes comandos?
   <pre>
   s = "python rocks"
   print(s[3:8])

   </pre>



.. mchoice:: test_question8_5_2
   :answer_a: rockrockrock
   :answer_b: rock rock rock
   :answer_c: rocksrocksrocks
   :answer_d: Error, you cannot use repetition with slicing.
   :correct: a
   :feedback_a: Sim, rock começa em 7 e vai até 10. Repita 3 vezes.
   :feedback_b: Repetição não insere um espaço.
   :feedback_c: Fatiamento não inclui o caractere de índice 11, apenas até o caractere anterior (10 nesse caso). 
   :feedback_d: O fatiamento ocorre primeiro e depois a repetição. Assim não há erro.

   O que é impresso pelos seguintes comandos?
   <pre>
   s = "python rocks"
   print(s[7:11]*3)

   </pre>


   
.. l index  string comparison, comparison of strings

index:: comparação de strings

.. String Comparison

Comparação de strings
---------------------

.. The comparison operators also work on strings. To see if two
   strings are equal you simply write a boolean expression using the
   equality operator.
   
Os operadores de comparação também funcionam com strings. Para ver se dois strings são iguais, basta escrever uma expressão booleana usando o operador de igualdade.

.. activecode:: ch08_comp1
    
    word = "banana"
    if word == "banana":
        print("Yes, we have bananas!")
    else:
        print("Yes, we have NO bananas!")

.. Other comparison operations are useful for putting words in
   `lexicographical order
   <http://en.wikipedia.org/wiki/Lexicographic_order>`__. This is
   similar to the alphabetical order you would use with a dictionary,
   except that all the uppercase letters come before all the lowercase
   letters.

Outras operações de comparação são úteis para colocar palavras em
`ordem lexicográfica <http://en.wikipedia.org/wiki/Lexicographic_order>` __. Isto é semelhante à ordem alfabética usada em um dicionário,
exceto que todas as letras maiúsculas vêm antes de todas as letras minúsculas.

.. activecode:: ch08_comp2

    word = "zebra"
    
    if word < "banana":
        print("Your word, " + word + ", comes before banana.")
    elif word > "banana":
        print("Your word, " + word + ", comes after banana.")
    else:
        print("Yes, we have no bananas!")


.. It is probably clear to you that the word `apple` would be less
   than (come before) the word ``banana``. After all, `a` is before
   `b` in the alphabet.  But what if we consider the words ``apple``
   and ``Apple``? Are they the same?

Deve ser evidente para você que a palavra `apple` seria inferior a
(deve vir antes) palavra` `banana``. Afinal, `a` vem antes de `b` no
alfabeto. Mas e se considerarmos as palavras ``apple`` e ``Apple``?
Eles são iguais?

.. activecode:: chp08_ord1

    print("apple" < "banana")

    print("apple" == "Apple")
    print("apple" < "Apple")

.. It turns out, as you recall from our discussion of variable names,
   that uppercase and lowercase letters are considered to be different
   from one another.  The way the computer knows they are different is
   that each character is assigned a unique integer value.  "A" is 65,
   "B" is 66, and "5" is 53.  The way you can find out the so called
   **ordinal value** for a given character is to use a character
   function called ``ord``.

Acontece que, como você deve se lembrar da nossa discussão sobre nomes
de variáveis, que letras maiúsculas e minúsculas são consideradas
diferentes umas das outras. A forma como o computador sabe que eles
são diferentes é que cada caractere corresponde a um valor inteiro
único. Por exemplo, "A" é de 65, "B" é de 66, e "5" é 53. Você pode
descobrir o chamado **valor ordinal** de um caractere utilizando a
função ``ord``.

.. activecode:: ch08_ord2

    print(ord("A"))
    print(ord("B"))
    print(ord("5"))

    print(ord("a"))
    print("apple" > "Apple")

.. When you compare characters or strings to one another, Python
   converts the characters into their equivalent ordinal values and
   compares the integers from left to right.  As you can see from the
   example above, "a" is greater than "A" so "apple" is greater than
   "Apple".

Quando você compara caracteres ou strings, o Python converte os
caracteres para seus valores ordinais e compara os inteiros da
esquerda para a direita. Como você pode ver no exemplo acima, "a" é
maior que "A" de forma que "apple" é maior do que "Apple".

.. Humans commonly ignore capitalization when comparing two words.
   However, computers do not.  A common way to address this issue is
   to convert strings to a standard format, such as all lowercase,
   before performing the comparison.

Nós geralmente ignoramos a capitalização ao comparar duas palavras. No entanto, os computadores não. Uma maneira comum de resolver este problema é converter as strings para um formato padrão, tal como todas as letras minúsculas, antes de realizar a comparação.

.. There is also a similar function called ``chr`` that converts
   integers into their character equivalent.

Há também uma função semelhante chamada ``chr`` que converte inteiros para o seu caractere equivalente.

.. activecode:: ch08_ord3

    print(chr(65))
    print(chr(66))

    print(chr(49))
    print(chr(53))

    print("O caractere correspondente a 32 e",chr(32),"!!!")
    print(ord(" "))

.. One thing to note in the last two examples is the fact that the
   space character has an ordinal value (32).  Even though you don't
   see it, it is an actual character.  We sometimes call it a
   *nonprinting* character.

Uma coisa a notar nos dois últimos exemplos é o fato de que o
caractere de espaço tem um valor ordinal (32). Mesmo que você não
o veja, ele é um caractere real.
Às vezes chamamos esses caracteres de *não impressos*.
   
**Teste seu entendimento**

.. mchoice:: test_question8_6_1
   :answer_a: True
   :answer_b: False
   :correct: a
   :feedback_a: Ambos os strings são idênticos até o l mas como mel é mais curto que melhor então ele vem primeiro no dicionário.
   :feedback_b: Strings são comparados caractere a caractere.
   
   Qual o resultado da seguinte comparação:
   <pre>
   "mel" < "melhor"

   </pre>

   
   
.. mchoice:: test_question8_6_2
   :answer_a: True
   :answer_b: False
   :answer_c: Eles são a mesma palavra
   :correct: b
   :feedback_a: m é maior que M de acordo com a função ord (77 versus 109).
   :feedback_b: Sim, um caractere maiúsculo é menor que seu correspondente minúsculo de acordo com os seus valores ordinais.
   :feedback_c: Em Python, letras maiúsculas e minúsculas são diferentes.
   
   Qual o resultado da seguinte comparação:
   <pre>
   "mel" < "Mel"

   </pre>

   

.. mchoice:: test_question8_6_3
   :answer_a: True
   :answer_b: False
   :correct: b
   :feedback_a: m é maior que M.
   :feedback_b: O comprimento não é importante.

   Qual o resultado da seguinte comparação:
   <pre>
   "mel" < "Melhor"

   </pre>

   

.. mutable, immutable, runtime error

.. index:: mutável, imutável, erro de execução

.. Strings are Immutable
   
Strings são imutáveis
---------------------

.. One final thing that makes strings different from some other Python collection types is that you are not allowed to modify the individual characters in the collection.  It is tempting to use the ``[]`` operator on the left side of an assignment, with the intention of changing a character in a string.  For example, in the following code, we would like to change the first letter of ``greeting``.

Uma última coisa que faz que strings sejam diferentes de alguns outros tipos coletivos de Python é que você não tem permissão para modificar os caracteres individuais na coleção. É tentador usar o operador ``[]`` no lado esquerdo de uma atribuição com a intenção de mudar um caractere em um string. Por exemplo, no código a seguir, gostaríamos de mudar a primeira letra de ``conversa``.


.. activecode:: cg08_imm1
    
    conversa = "Ola, mundo!"
    conversa[0] = 'B'            # ERROR!
    print(conversa)

.. Instead of producing the output ``Jello, world!``, this code produces the runtime error ``TypeError: 'str' object does not support item assignment``.

Em vez de produzir a saída ``Bla, mundo``, este código produz o erro de execução ``TypeError: 'str' object does not support item assignment``.

.. Strings are **immutable**, which means you cannot change an existing string. The best you can do is create a new string that is a variation on the original.

Strings são **imutáveis**, o que significa que você não pode mudar um string existente. O melhor que você pode fazer é criar um novo string que é uma variação do original.
   
.. activecode:: ch08_imm2
    
    conversa = "Ola, mundo!"
    nova_conversa = 'B' + conversa[1:]
    print(nova_conversa)
    print(conversa)            # mesmo que antes

.. The solution here is to concatenate a new first letter onto a slice of ``greeting``. This operation `has no effect on the original string.

A solução aqui é concatenar uma nova primeira letra com uma fatia de ``conversa``. Esta operação não tem efeito sobre o string original.

**Teste seu entendimento**

.. mchoice:: test_question8_7_1
   :answer_a: Ball
   :answer_b: Call
   :answer_c: Error
   :correct: c
   :feedback_a: Atribuição não é permitida com strings.
   :feedback_b: Atribuição não é permitida com strings. 
   :feedback_c: Sim, strings são imutáveis.

   O que é impresso pelos seguintes comandos?
   <pre>
   s = "Ball"
   s[0] = "C"
   print(s)

   </pre>



.. traversal, for loop, concatenation, abecedarian series
   
.. index:: percurso, comando for, concatenação, séries alfabéticas

.. index::
    single: McCloskey, Robert
    single: Make Way for Ducklings    

.. Traversal and the ``for`` Loop: By Item
   
Varredura com ``for`` por item
------------------------------

.. A lot of computations involve processing a collection one item at a
   time.  For strings this means that we would like to process one
   character at a time.
.. Often we start at the beginning, select each character in turn, do
   something to it, and continue until the end. This pattern of
   processing is called a **traversal**.

Um grande número de computações envolvem o processamento de item de um
conjunto de cada vez. Para strings, isto significa que nós gostaríamos
de processar um caractere de cada vez.  Muitas vezes, nós começamos no
início, selecionamos um caractere de cada vez, fazemos alguma coisa
com ele, e continuamos até o final. Este padrão de processamento é
chamado um **percurso**.

.. We have previously seen that the ``for`` statement can iterate over
   the items of a sequence (a list of names in the case below).

Anteriormente, vimos que o comando ``for`` pode iterar sobre os itens
de uma sequência (uma lista de nomes no caso abaixo).

.. activecode:: ch08_4
    :nocanvas:

    for um_nome in ["Joe", "Amy", "Brad", "Angelina", "Zuki", "Thandi", "Paris"]:
        convite = "Oi " + um_nome + ".  Venha para a festa nesse sabado!"
        print(convite) 
      
.. Recall that the loop variable takes on each value in the sequence
   of names.  The body is performed once for each name.  The same was
   true for the sequence of integers created by the ``range``
   function.

Lembre-se que a variável do laço assume cada valor da sequência de
nomes. O corpo é executado uma vez para cada nome. O mesmo era verdade
para a sequência de números inteiros criada pela função ``range``.

.. activecode:: ch08_5
    :nocanvas:

    for um_valor in range(10):
        print(um_valor)


.. Since a string is simply a sequence of characters, the ``for`` loop
   iterates over each character automatically.

Como um string é simplesmente uma sequência de caracteres, o laço
``for`` itera sobre cada caractere automaticamente.
   
.. activecode:: ch08_6
    :nocanvas:

    for um_char in "Venha para a festa":
        print(um_char)

.. The loop variable ``achar`` is automatically reassigned each character in the string "Go Spot Go".
.. We will refer to this type of sequence iteration as **iteration by item**.  
.. Note that it is only possible to process the characters one at a time from left to right.

A variável ``um_char`` do laço recebe automaticamente cada caractere
da sequência "Venha para a festa".  Vamos nos referir a esse tipo de
iteração de sequência como **iteração por item**.  Note que só é
possível processar os caracteres um de cada vez, da esquerda para a
direita.

**Teste seu entendimento**

.. mchoice:: test_question8_8_1
   :answer_a: 11
   :answer_b: 12
   :answer_c: 13
   :answer_d: Erro, o comando for precisa ser usado com a função range.
   :correct: c
   :feedback_a: Iteração por item processará cada item da sequência uma vez.
   :feedback_b: Os espaços fazem parte da sequência.
   :feedback_c: Sim, há 13 caracteres, incluindo os espaços.
   :feedback_d: O comando for pode iterar sobre uma sequência item por item.

   Quantas vezes a palavra OLA é impressa pelos seguintes comandos?
   <pre>
   s = "viva o python"
   for ch in s:
      print("OLA")

   </pre>


   
.. mchoice:: test_question8_8_2
   :answer_a: 4
   :answer_b: 5
   :answer_c: 6
   :answer_d: Erro, o comando for não pode usar fatias.
   :correct: b
   :feedback_a: A fatia retorna uma sequência que pode ser percorrida. Os espaços fazem parte da sequência.
   :feedback_b: Sim, os espaços fazem parte da sequência retornada pela fatia.
   :feedback_c: Verifique o resultado de s[3:8]. Ele não inclui o item de índice 8.
   :feedback_d: A fatia s[3:8] retorna uma sequência.

   Quantas vezes a palavra OLA é impressa pelos seguintes comandos?
   <pre>
   s = "viva o python"
   for ch in s[3:8]:
      print("OLA")

   </pre>


.. Traversal and the ``for`` Loop: By Index
   
Varredura com ``for`` por índice
--------------------------------

.. It is also possible to use the ``range`` function to systematically generate the indices of the characters.  The for loop can then be used to iterate over these positions. 
.. These positions can be used together with the indexing operator to access the individual characters in the string.

Também é possível utilizar a função ``range`` para gerar sistematicamente os índices dos caracteres. O laço for pode então ser usado para iterar sobre essas posições.
Estas posições podem ser utilizados em conjunto com o operador de indexação para acessar os caracteres individuais na sequência.


.. Consider the following codelens example.
   
Considere o seguinte exemplo no codelens.

.. codelens:: ch08_7

    fruta = "apple"
    for idx in range(5):
        currentChar = fruta[idx]
        print(currentChar)

.. The index positions in "apple" are 0,1,2,3 and 4.  This is exactly the same sequence of integers returned by ``range(5)``.  The first time through the for loop, ``idx`` will be 0 and the "a" will be printed.  Then, ``idx`` will be reassigned to 1 and "p" will be displayed.  This will repeat for all the range values up to but not including 5.  Since "e" has index 4, this will be exactly right to show all of the characters.

As posições de índice de "apple" são 0,1,2,3 e 4. Esta é exatamente a mesma sequência de números inteiros retornado por ``range(5)``. Na primeira vez dentro do laço for, ``idx`` será 0 e o "a" será impresso. Em seguida, ``idx`` receberá 1 e "p" será exibido. Isso vai se repetir para todos os valores do intervalo até, mas não incluindo, o 5. Como "e" tem índice 4, este programa vai mostrar todos
os caracteres de "apple".

.. In order to make the iteration more general, we can use the ``len`` function to provide the bound for ``range``.  This is a very common pattern for traversing any sequence by position.	Make sure you understand why the range function behaves correctly when using ``len`` of the string as its parameter value.

A fim de tornar a iteração mais genérica, podemos usar a função ``len`` para fornecer o limite para ``range``. Este é um padrão muito comum para percorrer qualquer sequência por posição. Certifique-se de entender por que a função range se comporta
corretamente ao usar ``len`` de um string como parâmetro.

.. activecode:: ch08_7b
    :nocanvas:


    fruta = "apple"
    for idx in range(len(fruta)):
        print(fruta[idx])


.. You may also note that iteration by position allows the programmer to control the direction of the traversal by changing the sequence of index values.  Recall that we can create ranges that count down as well as up so the following code will print the characters from right to left.

Você também pode notar que a iteração por posição permite que o programador controle a direção da travessia, alterando a sequência de valores dos índices. Lembre-se que nós podemos criar tanto intervalos que contam para baixo quanto para cima. Assim o código a seguir irá imprimir os caracteres da direita para a esquerda.

.. codelens:: ch08_8

    fruta = "apple"
    for idx in range(len(fruta)-1, -1, -1):
        print(fruta[idx])

.. Trace the values of ``idx`` and satisfy yourself that they are correct.  In particular, note the start and end of the range.

Simule os valores de ``idx`` e verifique que eles estão corretos. Em particular, note o início e o fim do intervalo.

**Teste seu entendimento**

.. mchoice:: test_question8_9_1
   :answer_a: 0
   :answer_b: 1
   :answer_c: 2
   :answer_d: Erro, o comando for não pode conter um comando if.
   :correct: c
   :feedback_a: O laço for visita todos os índices mas a seleção somente imprime alguns.
   :feedback_b: o está nas posições 4 e 8.
   :feedback_c: Sim, todos os caracteres nas posições pares serão impressos.
   :feedback_d: O comando for pode conter qualquer outro comando, incluindo if e outros comandos for. 

   Quantas vezes a letra o é impressa pelos seguintes comandos?
   <pre>
   s = "python rocks"
   for idx in range(len(s)):
      if idx % 2 == 0:
         print(s[idx])

   </pre>



.. Traversal and the ``while`` Loop
   
Varredura com ``while``
-----------------------

.. The ``while`` loop can also control the generation of the index
   values.  Remember that the programmer is responsible for setting up
   the initial condition, making sure that the condition is correct,
   and making sure that something changes inside the body to guarantee
   that the condition will eventually fail.

O laço ``while`` também pode controlar a geração dos valores de
índices. Lembre-se que o programador é responsável por configurar a
condição inicial, certificando-se que a condição é correta e
certificando-se de que algo muda dentro do corpo para garantir que a
condição se tornará falsa.

.. activecode:: ch08_7c
    :nocanvas:


    fruta = "apple"

    position = 0
    while position < len(fruta):
        print(fruta[position])
        position = position + 1


.. The loop condition is ``position < len(fruit)``, so when
   ``position`` is equal to the length of the string, the condition is
   false, and the body of the loop is not executed. The last character
   accessed is the one with the index ``len(fruit)-1``, which is the
   last character in the string.

A condição do loop é ``position < len(fruta)``, por isso, quando
``position`` é igual ao comprimento do string, a condição é falsa, e o
corpo do laço não é executado. O último caractere acessado é aquele
com o índice ``len(fruta)-1``, que é o último caractere no string.

.. Here is the same example in codelens so that you can trace the
   values of the variables.

Aqui está o mesmo exemplo em codelens para que você possa verificar os
valores das variáveis.

.. codelens:: ch08_7c1
    
    fruta = "apple"

    position = 0
    while position < len(fruta):
        print(fruta[position])
        position = position + 1

**Teste seu entendimento**

.. mchoice:: test_question8_10_1
   :answer_a: 0
   :answer_b: 1
   :answer_c: 2
   :correct: a
   :feedback_a: Sim, idx varre os números ímpares a partir do 1 e a letra o está nas posições 4 e 8.
   :feedback_b: a letra o está nas posições 4 e 8, e o idx começa em 1, não 0.
   :feedback_c: Há duas letras o mas idx não recebe os valores de índice corretos.

   Quantas vezes a letra o é impressa pelos seguintes comandos?
   <pre>
   s = "python rocks"
   idx = 1
   while idx < len(s):
      print(s[idx])
      idx = idx + 2

   </pre>


.. index::
    single: operador in
    single: operador; in

.. The ``in`` and ``not in`` operators
   
Operadores ``in`` e ``not in``
------------------------------

.. The ``in`` operator tests if one string is a substring of another:
   
O operador ``in`` testa se um string é um substring de outro: 

.. activecode:: chp8_in1
    
    print('p' in 'apple')
    print('i' in 'apple')
    print('ap' in 'apple')
    print('pa' in 'apple')

.. Note that a string is a substring of itself, and the empty string is a substring of any other string. (Also note that computer scientists like to think about these edge cases quite carefully!) 

Note que um string é um substring de si mesmo, e o string vazio é um substring de qualquer outro string. (Note também que os cientistas da computação gostam de pensar sobre estes casos particulares com muito cuidado!)

.. activecode:: chp8_in2
    
    print('a' in 'a')
    print('apple' in 'apple')
    print('' in 'a')
    print('' in 'apple')
    
.. The ``not in`` operator returns the logical opposite result of ``in``.
   
O operador ``not in`` retorna o resultado lógico oposto de ``in``.

.. activecode:: chp8_in3

    print('x' not in 'apple')

.. The Accumulator Pattern with Strings
   
Padrão de acumulação com strings
--------------------------------


.. Combining the ``in`` operator with string concatenation using ``+``
   and the accumulator pattern, we can write a function that removes
   all the vowels from a string.  The idea is to start with a string
   and iterate over each character, checking to see if the character
   is a vowel.  As we process the characters, we will build up a new
   string consisting of only the nonvowel characters.  To do this, we
   use the accumulator pattern.

Combinando o operador ``in`` com concatenação de strings usando ``+``
e o padrão de acumulação, podemos escrever uma função que remove todas
as vogais de um string. A idéia é começar com um string e iterar sobre
cada caractere, verificando se o caractere é uma vogal. À medida que
processamos os caracteres, vamos construindo uma nova cadeia contendo
apenas os caracteres não vogais. Para fazer isso, usamos o padrão de
acumulação.

.. Remember that the accumulator pattern allows us to keep a "running
   total".  With strings, we are not accumulating a numeric total.
   Instead we are accumulating characters onto a string.

Lembre-se que o padrão de acumulação nos permite manter uma "total em execução". Com strings, não estamos acumulando um total numérico. Em vez disso, estamos acumulando caracteres em um string.

.. activecode:: ch08_acc1
    
    def removeVowels(s):
        vowels = "aeiouAEIOU"
        sWithoutVowels = ""
        for eachChar in s:
            if eachChar not in vowels:
                sWithoutVowels = sWithoutVowels + eachChar
        return sWithoutVowels 
       
    print(removeVowels("compsci"))
    print(removeVowels("aAbEefIijOopUus"))

.. Line 5 uses the ``not in`` operator to check whether the current
   character is not in the string ``vowels``. The alternative to using
   this operator would be to write a very large ``if`` statement that
   checks each of the individual vowel characters.  Note we would need
   to use logical ``and`` to be sure that the character is not any of
   the vowels.

A linha 5 usa o operador ``not in`` para verificar se o caractere
atual não se encontra no string ``vowels``. A alternativa para o uso
deste operador seria escrever uma grande declaração ``if`` que
verifica cada vogal individualmente. Note que precisaríamos usar
operadores lógicos ``and`` para ter certeza de que o caractere não é
uma vogal.

.. sourcecode:: python

    if eachChar != 'a'  and eachChar != 'e'  and eachChar != 'i'  and
       eachChar != 'o'  and eachChar != 'u'  and eachChar != 'A'  and
       eachChar != 'E'  and eachChar != 'I'  and eachChar != 'O'  and
       eachChar != 'U':      
       
         sWithoutVowels = sWithoutVowels + eachChar

                  
      

.. Look carefully at line 6 in the above program (``sWithoutVowels =
   sWithoutVowels + eachChar``).  We will do this for every character
   that is not a vowel.  This should look very familiar.  As we were
   describing earlier, it is an example of the accumulator pattern,
   this time using a string to "accumulate" the final result.
.. In words it says that the new value of ``sWithoutVowels`` will be
   the old value of ``sWithoutVowels`` concatenated with the value of
   ``eachChar``.  We are building the result string character by
   character.

Olhe atentamente para a linha 6 no programa acima (``sWithoutVowels =
sWithoutVowels + eachChar``). Vamos fazer isso para cada caractere que
não é uma vogal. Isso deve parecer muito familiar. Como descremos
anteriormente, este é um exemplo do padrão de acumulação, desta vez
usando um string para "acumular" o resultado final.  Em palavras, ele
diz que o novo valor de ``sWithoutVowels`` será o valor antigo de
``sWithoutVowels`` concatenado com o valor de ``eachChar``. Estamos
construindo o string resultante caractere por caractere.

.. Take a close look also at the initialization of ``sWithoutVowels``.
   We start with an empty string and then begin adding new characters
   to the end.

Dê uma olhada também na inicialização de ``sWithoutVowels``. Começamos
com um string vazio e, em seguida, adicionamos novos caracteres até o
fim.

.. Step thru the function using codelens to see the accumulator variable grow.

Simule a execução da função usando codelens para ver a variável
acumuladora crescer.

.. codelens:: ch08_acc2
    
    def removeVowels(s):
        vowels = "aeiouAEIOU"
        sWithoutVowels = ""
        for eachChar in s:
            if eachChar not in vowels:
                sWithoutVowels = sWithoutVowels + eachChar
        return sWithoutVowels 
       
    print(removeVowels("compsci"))


**Teste seu entendimento**

.. mchoice:: test_question8_11_1
   :answer_a: Ball
   :answer_b: BALL
   :answer_c: LLAB
   :correct: c
   :feedback_a: Cada item é convertido para maiúscula antes da concatenação.
   :feedback_b: Cada caractere é convertido para maiúscula mas a ordem está errada.
   :feedback_c: Sim, a ordem é reversa devido a ordem da concatenação.

   O que é impresso pelos seguintes comandos:
   <pre>
   s = "ball"
   r = ""
   for item in s:
      r = item.upper() + r
   print(r)

   </pre>


.. Turtles and Strings and L-Systems
   
Tartarugas, strings e Sistemas-L
--------------------------------

.. This section describes a much more interested example of string
   iteration and the accumulator pattern.  Even though it seems like
   we are doing something that is much more complex, the basic
   processing is the same as was shown in the previous sections.

Esta seção descreve um exemplo muito mais interessante de iteração de
strings e o padrão de acumulação. Mesmo que pareça que estamos fazendo
algo que é muito mais complexo, o processamento básico é o mesmo que
foi mostrado nas seções anteriores.

.. In 1968 Astrid Lindenmayer, a biologist, invented a formal system
   that provides a mathematical description of plant growth known as
   an **L-system**.  L-systems were designed to model the growth of
   biological systems.  You can think of L-systems as containing the
   instructions for how a single cell can grow into a complex
   organism.  L-systems can be used to specify the **rules** for all
   kinds of interesting patterns.  In our case, we are going to use
   them to specify the rules for drawing pictures.

Em 1968 Astrid Lindenmayer, uma bióloga, inventou um sistema formal
que fornece uma descrição matemática do crescimento de plantas
conhecido como um **sistema-L**. O sistema-L foi concebido para
modelar o crescimento de sistemas biológicos. Você pode considerar que
um sistema-L contem as instruções de como uma única célula pode se
transformar em um organismo complexo. Sistemas-L podem ser utilizados
para especificar as **regras** para todos os tipos de padrões
interessantes. No nosso caso, vamos usá-los para especificar as regras
para desenhar figuras.

.. The rules of an L-system are really a set of instructions for
   transforming one string into a new string.  After a number of these
   string transformations are complete, the string contains a set of
   instructions.  Our plan is to let these instructions direct a
   turtle as it draws a picture.

As regras de um sistema-L são na verdade um conjunto de instruções
para transformar um string em um novo string. Depois de uma série de
tais transformações de strings se completar, o string contém um
conjunto de instruções. Nosso plano é deixar estas instruções
dirigirem uma tartaruga para desenhar uma figura.

.. To begin, we will look at an example set of rules:

Para começar, vamos ver um exemplo de conjunto de regras:

.. ========  =====================
.. A         Axiom
.. A -> B    Rule 1 Change A to B
.. B -> AB   Rule 2 Change B to AB
.. ========  =====================
   
========  =====================
A         Axioma               
A -> B    Regra 1 Mude A para B
B -> AB   Regra 2 Mude B to AB 
========  =====================

.. Each rule set contains an axiom which represents the starting point
   in the transformations that will follow.  The rules are of the
   form : :
   
Cada conjunto de regras contém um axioma que representa o estado
inicial do processo de transformação. As regras são da forma::

        lado esquerdo -> lado direito
        
.. where the left and side is a single symbol and the right had side
   is a sequence of symbols.  You can think of both sides as being
   simple strings.
.. The way the rules are used is to replace occurrences of the left
   hand side with the corresponding right hand side.

Onde o lado esquerdo é um único símbolo e o lado direito é uma
sequência de símbolos. Você pode considerar ambos os lados como
strings.  A forma de usar as regras é substituir as ocorrências do
lado esquerdo pelos correspondentes lados direitos.

.. Now lets look at these simple rules in action, starting with the string A : :
   
Agora vamos dar uma olhada nessas regras simples em ação, começando a
partir do string A::

    A
    B      Aplique a Regra 1  (A é substituido por B)
    AB     Aplique a Regra 2  (B é substituido por AB)
    BAB    Aplique a Regra 1 para A e então a Regra 2 para B
    ABBAB  Aplique a Regra 2 para B, Regra 1 para A, e Regra 2 para B

.. Notice that each line represents a new transformation for entire string.  Each character that matches a left-hand side of a rule in the original has been replaced by the corresponding right-hand side of that same rule.  After doing the replacement for each character in the original, we have one transformation.
   
Observe que cada linha representa uma nova transformação para todo o
string. Cada caractere do string original que corresponda a um do lado
esquerdo de uma regra foi substituído pelo lado direito correspondente
da mesma regra. Depois de fazer a substituição para cada caractere no
string original, obtemos o string transformado.

.. So how would we encode these rules in a Python program?  There are a couple of very important things to note here:

Então como podemos codificar essas regras em um programa Python? Há
algumas coisas muito importantes a serem observadas aqui:

.. #. Rules are very much like if statements.
.. #. We are going to start with a string and iterate over each of its characters.
.. #. As we apply the rules to one string we leave that string alone and create
   a brand new string using the accumulator pattern.  When we are all done with the original we replace it with the new string.

#. As regras são muito parecidas com comandos if.
#. Vamos começar com um string e iterar sobre cada um de seus caracteres.
#. À medida que aplicamos as regras para um string vamos criando um string novo usando o padrão de acumulação. Quando todos os caracteres do string original forem processados, nós o substituímos pelo novo string transformado.
   
.. Lets look at a simple Python program that implements the example set of rules described above.

Vamos dar uma olhada em um programa simples em Python que implementa o exemplo de conjunto de regras descrito acima.

.. activecode::  string_lsys1

    def applyRules(ch):
        newstr = ""
        if ch == 'A':
            newstr = 'B'   # Rule 1
        elif ch == 'B':
            newstr = 'AB'  # Rule 2
        else:
            newstr = ch    # no rules apply so keep the character

        return newstr


    def processString(oldStr):
        newstr = ""
        for ch in oldStr:
            newstr = newstr + applyRules(ch)

        return newstr


    def createLSystem(numIters,axiom):
        startString = axiom
        endString = ""
        for i in range(numIters):
            endString = processString(startString)
            startString = endString

        return endString

    print(createLSystem(4,"A"))

.. Try running the example above with different values for the
   ``numIters`` parameter.  You should see that for values 1, 2, 3,
   and 4, the strings generated follow the example above exactly.

Tente executar o exemplo acima, com valores diferentes para o
parâmetro ``numIters``. Você verá que, para os valores 1, 2, 3 e 4, os
strings gerados são idênticos aos do exemplo acima.
 
.. One of the nice things about the program above is that if you want
   to implement a different set of rules, you don't need to re-write
   the entire program. All you need to do is re-write the applyRules
   function.

Uma das coisas legais sobre o programa acima é que se você quiser
implementar um conjunto diferente de regras, você não precisa
re-escrever o programa inteiro. Tudo que você precisa fazer é
re-escrever a função applyRules.

.. Suppose you had the following rules:

Suponha que você tenha as seguintes regras:

========  =======================
A         Axioma
A -> BAB  Regra 1 Mude A para BAB
========  =======================

.. What kind of a string would these rules create?  Modify the program
   above to implement the rule.
   
Que tipo de string seria criado por essa regra? Modifique o programa
acima para implementar essa regra.

.. Now lets look at a real L-system that implements a famous drawing.
   This L-system has just two rules:
   
Agora vamos dar uma olhada em um sistema-L real que implementa um
desenho famoso. Esse sistema-L possui apenas duas regras:

=============  =====================
F              Axioma
F -> F-F++F-F  Regra 1
=============  =====================

.. This L-system uses symbols that will have special meaning when we use them later with the turtle to draw a picture.
   
Esse sistema-L usa símbolos que terão significado especial quando usados para a tartaruga desenhar uma figura.

.. ====  ===================================
.. F     Go forward by some number of units
.. B     Go backward by some number of units
.. \-    Turn left by some degrees
.. \+    Turn right by some degrees
.. ====  ===================================
   
====  ==============================
F     Dê alguns passos para a frente
B     Dê alguns passos para trás
\-    Vire alguns graus à esquerda
\+    Vire alguns graus à direita
====  ==============================

.. Here is the ``applyRules`` function for this L-system.
   
Essa é a função ``applyRules`` para esse sistema-L.

.. sourcecode:: python

    def applyRules(ch):
        newstr = ""
        if ch == 'F':
            newstr = 'F-F++F-F'   # Rule 1
        else:
            newstr = ch    # no rules apply so keep the character

        return newstr

.. Pretty simple so far.  As you can imagine this string will get
   pretty long with a few applications of the rules.  You might try to
   expand the string a couple of times on your own just to see.
   
Muito simples até agora. Como você pode imaginar esse string vai ficar muito longo
com algumas aplicações das regras. Você pode tentar expandir a cadeia algumas vezes
no papel só para ver.

.. The last step is to take the final string and turn it into a
   picture.  Lets assume that we are always going to go forward or
   backward by 5 units.  In addition we will also assume that when the
   turtle turns left or right we'll turn by 60 degrees.  Now look at
   the string ``F-F++F-F``.  You might try to us the explanation above
   to show the resulting picture that this simple string represents.
   At this point its not a very exciting drawing, but once we expand
   it a few times it will get a lot more interesting.
   
O último passo é pegar o string final e transformá-lo em uma
figura. Vamos assumir que a tartaruga sempre dá 5 passos para frente
ou para trás.  Além disso, vamos assumir que a tartaruga sempre gira
60 graus ao virar para a direita ou esquerda. Observe agora o string
``F-F++F-F``. Você pode tentar seguir a explicação acima para ver a
figura que este string simples representa. Neste ponto a figura não é
grande coisa, mas depois de expandir o string algumas vezes ele vai
ficar muito mais interessante.

.. To create a Python function to draw a string we will write a
   function called ``drawLsystem`` The function will take four
   parameters:
   
Para criar uma função em Python para desenhar um string vamos escrever
uma função chamada ``drawLsystem``. A função terá quatro parâmetros:

.. * A turtle to do the drawing
.. * An expanded string that contains the results of expanding the rules above.
.. * An angle to turn
.. * A distance to move forward or backward

* Uma tartaruga para fazer o desenho
* Um string expandido que contém o resultados da expansão usando as regras acima.
* Um ângulo para virar
* Uma distância para avançar ou retroceder

  .. sourcecode:: python

    def drawLsystem(aTurtle,instructions,angle,distance):
        for cmd in instructions:
            if cmd == 'F':
                aTurtle.forward(distance)
            elif cmd == 'B':
                aTurtle.backward(distance)
            elif cmd == '+':
                aTurtle.right(angle)
            elif cmd == '-':
                aTurtle.left(angle)
            else:
                print('Error:', cmd, 'is an unknown command')

.. Here is the complete program in activecode.  The ``main`` function
   first creates the L-system string and then it creates a turtle and
   passes it and the string to the drawing function.
   
Esse é o programa completo em activecode. A função ``main`` primeiro
cria o string do sistema-L e então cria a tartaruga e passa a
tartaruga e o string para a função de desenho.

.. activecode:: strings_lys2

    import turtle
    
    def createLSystem(numIters,axiom):
        startString = axiom
        endString = ""
        for i in range(numIters):
            endString = processString(startString)
            startString = endString

        return endString

    def processString(oldStr):
        newstr = ""
        for ch in oldStr:
            newstr = newstr + applyRules(ch)

        return newstr

    def applyRules(ch):
        newstr = ""
        if ch == 'F':
            newstr = 'F-F++F-F'   # Rule 1
        else:
            newstr = ch    # no rules apply so keep the character

        return newstr

    def drawLsystem(aTurtle,instructions,angle,distance):
        for cmd in instructions:
            if cmd == 'F':
                aTurtle.forward(distance)
            elif cmd == 'B':
                aTurtle.backward(distance)
            elif cmd == '+':
                aTurtle.right(angle)
            elif cmd == '-':
                aTurtle.left(angle)
            else:
                print('Error:', cmd, 'is an unknown command')

    def main():
        inst = createLSystem(4,"F")   #create the string
        print(inst)
        t = turtle.Turtle()           #create the turtle
        wn = turtle.Screen()
        
        t.up()
        t.back(200)
        t.down()
        t.speed(9)
        drawLsystem(t,inst,60,5)      #draw the picture
                                      #angle 60, segment length 5
        wn.exitonclick()

    main()

.. Feel free to try some different angles and segment lengths to see
   how the drawing changes.
   
Sinta-se a vontade para tentar alguns ângulos e distâncias diferentes
para ver como a figura se modifica.

.. index : : counting pattern
   
.. index:: padrão de contagem

.. Looping and counting
   
Repetições e contagens
----------------------

.. We will finish this chapter with a few more examples that show
   variations on the theme of iteration through the characters of the
   string.  We will implement a few of the methods that we described
   earlier to show how they can be come.
   
Vamos terminar este capítulo com mais alguns exemplos que mostram
variações sobre o tema da iteração pelos dos caracteres de um
string. Vamos implementar alguns dos métodos que descrevemos
anteriormente para mostrar como eles podem vir a ser.

.. The following program counts the number of times a particular
   letter, `` aChar``, appears in a string.  It is another example of
   the accumulator pattern that we have seen in previous chapters.
   
O programa a seguir conta o número de vezes que uma letra em
particular, ``aChar``, aparece em um string. É mais um exemplo do
padrão de acumulação que vimos nos capítulos anteriores.


.. activecode:: chp08_fun2

    def count(text, aChar): 
        lettercount = 0
        for c in text:
            if c == aChar:
                lettercount = lettercount + 1
        return lettercount

    print(count("banana","a"))    

.. The function ``count`` takes a string as its parameter.  The
   ``for`` statement iterates through each character in the string and
   checks to see if the character is equal to the value of ``aChar``.
   If so, the counting variable, ``lettercount``, is incremented by
   one. When all characters have been processed, the ``lettercount``
   is returned.

A função ``count`` recebe um string como parâmetro. O comando ``for``
itera por cada caractere do string e verifica se o caractere é igual
ao valor de ``aChar``. Se igual, a variável de contagem,
``lettercount``, é incrementada. Quando todos os caracteres forem
processados, ``lettercount`` é retornada.

.. index : : traversal, eureka traversal, pattern of computation,
           computation pattern
	   
.. index:: percurso, percurso eureka, padrão de computação, padrão computacional.
	   
.. A ``find`` function
   
Função ``find``
---------------

.. Here is an implementation for the ``find`` method.
   
Essa é uma implementação da função ``find``, que procura um caractere em um string. 

.. activecode:: ch08_run3
    
    def find(astring, achar):
        """
          Find and return the index of achar in astring.  
          Return -1 if achar does not occur in astring.
        """
        ix = 0
        found = False
        while ix < len(astring) and not found:
            if astring[ix] == achar:
                found = True
            else:
                ix = ix + 1
        if found:
            return ix
        else:
            return -1
        
    print(find("Compsci", "p"))
    print(find("Compsci", "C"))
    print(find("Compsci", "i"))
    print(find("Compsci", "x"))
    

.. In a sense, ``find`` is the opposite of the indexing
   operator. Instead of taking an index and extracting the
   corresponding character, it takes a character and finds the index
   where that character appears for the first time. If the character
   is not found, the function returns ``-1``.
   
Num certo sentido, ``find`` é o oposto do operador de indexação. Em
vez de receber um índice e extrair o caractere correspondente, ela
pega um caractere e encontra o índice onde esse caractere aparece pela
primeira vez. Se o caractere não for encontrado, a função retorna
``-1``.

.. The ``while`` loop in this example uses a slightly more complex
   condition than we have seen in previous programs.  Here there are
   two parts to the condition.  We want to keep going if there are
   more characters to look through and we want to keep going if we
   have not found what we are looking for.  The variable ``found`` is
   a boolean variable that keeps track of whether we have found the
   character we are searching for.  It is initialized to *False*.  If
   we find the character, we reassign ``found`` to *True*.
   
O laço ``while`` neste exemplo usa uma condição um pouco mais complexa
do que temos visto em programas anteriores. Aqui há duas partes para a
condição. Queremos continuar se houver mais caracteres para serem
olhados e queremos continuar caso ainda não tenhamos encontrado o que
estamos procurando. A variável ``found`` é uma variável booleana que
controla se já encontramos o caractere que estamos procurando. Ele é
inicializado com *False*. Se encontrarmos o caractere, ``found``
recebe *True*.

.. The other part of the condition is the same as we used previously
   to traverse the characters of the string.  Since we have now
   combined these two parts with a logical ``and``, it is necessary
   for them both to be *True* to continue iterating.  If one part
   fails, the condition fails and the iteration stops.
   
A outra parte da condição é a mesma que foi utilizada anteriormente
para percorrer os caracteres do string. Como combinamos essas duas
partes com um operador lógico ``and``, é necessário que ambas as
partes sejam *True* para continuar a iteração. Se uma parte falhar, a
condição falha e a iteração pára.

.. When the iteration stops, we simply ask a question to find out why
   and then return the proper value.
   
Quando a iteração pára, nós simplesmente fazemos uma pergunta para
descobrir o porquê e, em seguida, retornamos o valor adequado.

.. note::

	.. This pattern of computation is sometimes called a eureka
           traversal because as soon as we find what we are looking
           for, we can cry Eureka!  and stop looking.  The way we stop
           looking is by setting ``found`` to True which causes the
           condition to fail.
	   
	Esse padrão de computação é chamado às vezes de percurso
	eureka pois assim que encontramos o que estamos procurando
	podemos gritar Eureka! e parar de procurar. A forma de parar
	de procurar é alterando o valor de ``found`` para True, que
	causa a falha na condição.


.. index: : optional parameter, default value, parameter; optional
   
.. index:: parâmetro opcional, valor default, parâmetro; opcional

.. optional_parameters:
   
.. _parâmetros_opcionais:

.. Optional parameters
   
Parâmetros opcionais
--------------------

.. To find the locations of the second or third occurrence of a
   character in a string, we can modify the ``find`` function, adding
   a third parameter for the starting position in the search string:
   
Para encontrar a posição da segunda ou terceira ocorrência de um
caractere em um string nós podemos modificar a função ``find``,
adicionando um terceiro parâmetro para a posição inicial no string de
busca:

.. activecode:: ch08_fun4
    
    def find2(astring, achar, start):
        """
          Find and return the index of achar in astring.  
          Return -1 if achar does not occur in astring.
        """
        ix = start
        found = False
        while ix < len(astring) and not found:
            if astring[ix] == achar:
                found = True
            else:
                ix = ix + 1
        if found:
            return ix
        else:
            return -1
        
    print(find2('banana', 'a', 2))


.. The call ``find2('banana', 'a', 2)`` now returns ``3``, the index
   of the first occurrence of 'a' in 'banana' after index 2. What does
   ``find2('banana', 'n', 3)`` return? If you said, 4, there is a good
   chance you understand how ``find2`` works.  Try it.
   
A chamada ``find2('banana', 'a', 2)`` agora retorna ``3``, o índice da
primeira ocorrência de 'a' em 'banana' depois do índice 2. O que é
retornado pela chamada ``find2('banana', 'n', 3)``? Se você respondeu
4, há uma boa chance que você tenha entendido como ``find2``
funciona. Experimente.

.. Better still, we can combine ``find`` and ``find2`` using an
   **optional parameter**.
   
Melhor ainda, podemos combinar ``find`` e ``find2`` usando um
**parâmetro opcional**.

.. activecode:: chp08_fun5
    
	def find3(astring, achar, start=0):
	    """
	      Find and return the index of achar in astring.  
	      Return -1 if achar does not occur in astring.
	    """
	    ix = start
	    found = False
	    while ix < len(astring) and not found:
	        if astring[ix] == achar:
	            found = True
	        else:
	            ix = ix + 1
	    if found:
	        return ix
	    else:
	        return -1
	
	print(find3('banana', 'a', 2))

.. The call ``find3('banana', 'a', 2)`` to this version of ``find``
   behaves just like ``find2``, while in the call ``find3('banana',
   'a')``, ``start`` will be set to the **default value** of ``0``.
   
A chamada ``find3('banana', 'a', 2)`` para essa versão de ``find`` se
comporta da mesma forma que ``find2``, enquanto na chamada
``find3('banana', 'a')``, ``start`` receberá o **valor default** de
``0``.

.. Adding another optional parameter to ``find`` makes it search from
   a starting position, up to but not including the end position.
   
Adicionando um outro parâmetro opcional em ``find`` permite que a
busca seja feita a partir de uma posição inicial (start), até mas não
incluindo a posição final (end).
   

.. activecode:: chp08_fun6
    
    def find4(astring, achar, start=0, end=None):
	    """
	      Find and return the index of achar in astring.  
	      Return -1 if achar does not occur in astring.
	    """
	    ix = start
	    if end == None:
	       end = len(astring)

	    found = False
	    while ix < end and not found:
	        if astring[ix] == achar:
	            found = True
	        else:
	            ix = ix + 1
	    if found:
	        return ix
	    else:
	        return -1

    ss = "Python strings have some interesting methods."
 
    print(find4(ss, 's'))
    print(find4(ss, 's', 7))
    print(find4(ss, 's', 8))
    print(find4(ss, 's', 8, 13))
    print(find4(ss, '.'))


.. The optional value for ``end`` is interesting.  We give it a
   default value ``None`` if the caller does not supply any argument.
   In the body of the function we test what ``end`` is and if the
   caller did not supply any argument, we reassign ``end`` to be the
   length of the string.
.. If the caller has supplied an argument for ``end``, however, the caller's value will be used in the loop.

O valor opcional para ``end`` é interessante. Nós damos um valor
default ``None`` se o chamador não fornecer esse argumento. No corpo
da função testamos o valor de ``end`` e, caso seja None, vamos
atribuir o comprimento do string para ``end``.  No entanto, se o
chamador tiver fornecido um argumento para ``end``, o valor do
chamador será utilizado no laço.

.. The semantics of ``start`` and ``end`` in this function are
   precisely the same as they are in the ``range`` function.

A semântica de ``start`` e ``end`` nessa função é precisamente a mesma
usada na função ``range``.

.. index : : module, string module, dir function, dot notation, function type,
           docstring
	   
.. index:: módulo, modulo string, função dir, notação ponto, tipo de função, docstring


.. Character classification
   
Classificação de caracteres
---------------------------

.. It is often helpful to examine a character and test whether it is
   upper- or lowercase, or whether it is a character or a digit. The
   ``string`` module provides several constants that are useful for
   these purposes. One of these, ``string.digits`` is equivalent to
   "0123456789".  It can be used to check if a character is a digit
   using the ``in`` operator.
   
Muitas vezes, é útil examinar um caractere e testar se ele é maiúsculo
ou minúsculo, ou se é uma letra ou um dígito. O módulo ``string``
fornece várias constantes que são úteis para esses fins. Uma delas,
``string.digits`` é equivalente a "0123456789". Ela pode ser usada
para verificar se um caractere é um dígito usando o operador ``in``.

.. The string ``string.ascii_lowercase`` contains all of the ascii
   letters that the system considers to be lowercase. Similarly,
   ``string.ascii_uppercase`` contains all of the uppercase
   letters. ``string.punctuation`` comprises all the characters
   considered to be punctuation. Try the following and see what you
   get.
   
O string ``string.ascii_lowercase`` contém todas as letras ASCII que o
sistema considera serem minúsculas. Da mesma forma,
``string.ascii_uppercase`` contém todas as letras
maiúsculas. ``string.punctuation`` contem todos os caracteres
considerados símbolos de pontuação. Experimente o seguinte e veja o
que acontece.

.. sourcecode:: python
    
    print(string.ascii_lowercase)
    print(string.ascii_uppercase)
    print(string.digits)
    print(string.punctuation)

    

.. For more information consult the ``string`` module documentaiton
   (see `Global Module Index
   <http://docs.python.org/py3k/py-modindex.html>`_).
   
Para mais informações consulte a documentação do módulo ``string``
(veja `Global Module Index
<http://docs.python.org/py3k/py-modindex.html>`_).


.. Summary
   
Resumo
------ 

.. This chapter introduced a lot of new ideas.  The following summary
   may prove helpful in remembering what you learned.
   
Esse capítulo introduziu várias novas ideias. O seguinte resumo pode
ser-lhe útil para lembrar o que você aprendeu.

.. glossary::

    indexação (``[]``)
        Acessa um único caractere em um string usando sua posição (com início em 0). Exemplo: ``'Isso'[2]`` resulta em ``'s'``.

    função len (comprimento)
        Retorna o número de caracteres em um string. Exemplo:
	``len('happy')`` resulta em ``5``.

    percurso do laço for (``for``)
        *Percorrer* um string significa acessar cada caractere no string, um de
	cada vez. Por exemplo, o seguinte laço for: 

        .. sourcecode:: python

            for ix in 'Exemplo':
                ...

        executa o corpo do laço 7 vezes com diferentes valores de `ix` a cada vez. 

    fatiamento (``[:]``)
        Uma *fatia* (slice) é um substring de um string. Exemplo: ``'sorvete de banana'[3:6]`` resulta em ``vet``. 

    comparação de strings (``>, <, >=, <=, ==, !=``)
        Os seis operadores relacionais (de comparação) comuns funcionam com
	strings e são avaliados de acordo com a `ordem lexicográfica
        <http://en.wikipedia.org/wiki/Lexicographic_order>`__.  Exemplos:
        ``'apple' < 'banana'`` resulta em ``True``.  ``'Zeta' < 'Appricot'``
        resulta em ``False``.  ``'Zebra' <= 'aardvark'`` resulta em 
        ``True`` pois todas as letras maiúsculas precedem as minúsculas.

    operadores in e not in (``in``, ``not in``)
        O operador ``in`` testa se um string está contido em outro. Exemplos:
	``'curar' in "Eu vou procurar voce."`` resulta em ``True``.
	``'curdado' in "Eu vou procurar voce."`` resulta em ``False``. 


Glossário
---------

.. glossary::

    branco (whitespace)
        Qualquer caractere que move o cursor sem imprimir caracteres visíveis.
	A constante ``string.whitespace`` contém todos os caracteres "brancos".
	
    fatia
        Uma parte de um string (substring) especificado por um intervalo de índices.
	De forma mais genérica, uma subsequência de qualquer tipo de sequência
	em Python pode ser criada usando o operador de fatia
	(``sequencia[inicio:fim]``).

    imutável
        Um tipo de dado composto cujos elementos não podem receber novos valores.
	
    índice
        Uma variável ou valor usado para selecionar um membro de uma coleção
	ordenada, como um caractere em um string, ou um elemento de uma lista.

    notação ponto
        Uso do **operador ponto**, ``.``, para acessar funções dentro de um
	módulo, ou acessar métodos e atributos de um objeto.

    parâmetro opcional
        Um parâmetro definido no cabeçalho de uma função com a atribuição
	de um valor default que ele receberá caso nenhum argumento correspondente
	seja fornecido na chamada da função.

    percurso
        Para iterar pelos elementos de uma coleção, realizando uma operação similar
	para cada elemento.

    tipo de dado coletivo
        Um tipo de dado no qual os valores são constituidos por componentes, ou
	elementos, que são valores. 

    valor default
        O valor dado para um parâmetro opcional caso nenhum argumento seja fornecido
	na chamada.



Exercícios
----------


#. Qual o resultado de cada um dos seguintes:

    a. 'Python'[1]
    #. "Strings são sequências de caracteres."[5]
    #. len("maravilhoso")
    #. 'Mistério'[:4]
    #. 'p' in 'Pineapple'
    #. 'apple' in 'Pineapple'
    #. "pear" not in 'Pineapple'
    #. 'apple'> 'pineapple'
    #. 'pineapple'<'Peach'
       
#. 	No livro *Make Way for Ducklings* de Robert McCloskey, os patinhos são
	chamados de Jack, Kack, Lack, 
	Mack, Nack, Ouack, Pack, e Quack.
	Esse laço tenta imprimir esses nomes ordenadamente.

	.. sourcecode:: python

	    prefixes = "JKLMNOPQ"
	    suffix = "ack"

	    for p in prefixes:
	        print(p + suffix)




	é claro que esse programa tem problemas pois Ouack e Quack não são
	escritos corretamente. Você consegue consertar o programa?
   
    .. actex:: ex_8_2
   
#. Atribua a uma variável em seu programa um string entre aspas triplas contendo
   seu parágrafo favorito de um poema, discurso, receita de bolo, etc.

   Escreva uma função que remove toda a pontuação de um string e conta o
   número de palavras no string que contém a letra 'e'. Seu programa deve imprimir
   uma análise desse texto da seguinte forma::

         Seu texto contém 243 palavras, das quais 109 (44.8%) contém um 'e'.

   .. actex:: ex_8_3

#. Imprima de forma organizada e formatada uma tabela de multiplicação, até 12 x 12.

   .. actex:: ex_8_4


#. Escreva uma função que retorna o número de dígitos de um inteiro.

    .. actex:: ex_7_10


#. Escreva uma função ``reverse`` que recebe um string e o retorna invertido.

   .. actex:: ex_8_5

      from test import testEqual

      def reverse(astring):
          # your code here

      testEqual(reverse("happy"), "yppah")
      testEqual(reverse("Python"), "nohtyP")
      testEqual(reverse(""),"")

#. Escreva uma função que recebe um string e retorna o string espelhado.

   .. actex:: ex_8_6

      from test import testEqual

      def mirror(mystr):
          # your code here

      testEqual(mirror('good'),'gooddoog')
      testEqual(mirror('Python'),'PythonnohtyP')
      testEqual(mirror(''), '')
      testEqual(mirror('a'),'aa')



#. Escreva uma função que remove todas as ocorrências de uma letra de um string.

   .. actex:: ex_8_7

      from test import testEqual

      def remove_letter(theLetter, theString):
          # your code here

      testEqual(remove_letter('a', 'apple'),'pple')
      testEqual(remove_letter('a', 'banana'),'bnn')
      testEqual(remove_letter('z', 'banana'),'banana')



#. Escreva uma função que reconhece palíndromes.
   (Dica: use a sua função ``reverse``). 

   .. actex:: ex_8_8

      from test import testEqual

      def is_palindrome(myStr):
          # your code here

      testEqual(is_palindrome('abba'),True)
      testEqual(is_palindrome('abab'),False)
      testEqual(is_palindrome('straw warts'),True)
      testEqual(is_palindrome('a'), True)
      testEqual(is_palindrome(''),True)


#. Escreva uma função que conta o número de vezes que um substring ocorre em um string.

   .. actex:: ex_8_9

      from test import testEqual

      def count(substr,theStr):
          # your code here

      testEqual(count('is', 'Mississippi'), 2)
      testEqual(count('an', 'banana'), 2)
      testEqual(count('ana', 'banana'), 2)
      testEqual(count('nana', 'banana'),  1)
      testEqual(count('nanan', 'banana'),  0)
      testEqual(count('aaa', 'aaaaaa'),  4)


#. Escreva uma função que remove a primeira ocorrência de um string de outro string.

   .. actex:: ex_8_10

      from test import testEqual

      def remove(substr,theStr):
          # your code here

      testEqual(remove('an', 'banana'),'bana')
      testEqual(remove('cyc', 'bicycle'), 'bile')
      testEqual(remove('iss', 'Mississippi'), 'Missippi')
      testEqual(remove('egg', 'bicycle'), 'bicycle')



#. Escreva uma função que remove todas as ocorrências de um string de outro string.
 
   .. actex:: ex_8_11

      from test import testEqual

      def remove_all(substr,theStr):
          # your code here

      testEqual(remove_all('an', 'banana'), 'ba')
      testEqual(remove_all('cyc', 'bicycle'), 'bile')
      testEqual(remove_all('iss', 'Mississippi'), 'Mippi')
      testEqual(remove_all('eggs', 'bicycle'), 'bicycle')


#. Esse é um outro sistema-L interessante chamado de curva de Hilbert. Use 90 graus.::

       L
       L -> +RF-LFL-FR+
       R -> -LF+RFR+FL-

   .. actex:: ex_8_12

#. Essa é uma curva dragão. Use 90 graus.::

       FX
       X -> X+YF+
       Y -> -FX-Y

   .. actex:: ex_8_13

#. Essa é uma curva chamada de cabeça de flecha (arrowhead). Use 60 graus.::

       YF
       X -> YF+XF+Y
       Y -> XF-YF-X

   .. actex:: ex_8_14

#. Experimente a curva de Peano-Gosper. Use 60 graus.::

       FX
       X -> X+YF++YF-FX--FXFX-YF+
       Y -> -FX+YFYF++YF+FX--FX-Y

   .. actex:: ex_8_15

#. Triângulo de Sierpinski. Use 60 graus.::

       FXF--FF--FF
       F -> FF
       X -> --FXF++FXF++FXF--

   .. actex:: ex_8_16

#. Escreva uma função que implementa uma cifra de substituição. Em uma cifra de
   substituição uma letra é substituída por outra para codificar a mensagem.
   Por exemplo A -> Q, B -> T, C -> G etc. Sua função deve receber dois parâmetros,
   a mensagem que você deseja codificar e um string que representa o mapeamento
   das 26 letras no alfabeto. Sua função deve retornar um string que é a versão
   codificada da mensagem. 

   .. actex:: ex_8_17

#. Escreva uma função que decodifica a mensagem do exercício anterior.
   A função também deve receber dois parâmetros. A mensagem codificada, e o
   alfabeto para decodificação. A função deve retornar um string que corresponde
   à mensagem original antes de ser codificada.

   .. actex:: ex_8_18

#. Escreva uma função ``desembaralha`` que recebe uma mensagem que foi embaralhada
   usando o algoritmo ``picket fence``. Experimente trocar mensagens
   secretas com amigos e a mensagem abaixo (em inglês):

   .. actex:: ex_8_19

      def descramble(secret):
          # your code here

      testmess = "ogauain o aescesul erpe hssce esg ueyyudsrea  o hsasgmncnrtltosyuhv ucsflydcytdti ertmsaesrl o eev nafrti sinet"
      print(descramble(testmess))


#. Escreva uma função chamada ``rot13`` que usa a cifra de César para
   codificar uma mensagem. A cifra de César funciona como uma cifra de
   substituição mas cada caractere é substituído pelo caractere a uma certa
   distância de sua posição. Por exemplo, se a distância for 4, então o alfabeto
   seria codificado da seguinte maneira: A->E, B->F, C->G, ..., Z->D, etc.
   Observe que caracteres no final do alfabeto são transformados para caracteres
   no início, como uma lista circular. 
   *Dica:* sempre que trabalhar com coisas circulares, é sempre bom
   considerar o operador módulo (``%``). 
   
   .. actex:: ex_8_20

      def rot13(mess):
          # Your code here

      print(rot13('abcde'))
      print(rot13('nopqr'))
      print(rot13(rot13('Since rot13 is symmetric you should see this message')))


   

