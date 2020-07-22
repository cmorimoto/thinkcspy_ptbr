..  Copyright (C)  Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. Debugging
.. =========

Depuração (*Debugging*)
=======================

..
   Different kinds of errors can occur in a program, and it is useful to
   distinguish among them in order to track them down more quickly:

Diferentes tipos de erros pode ocorrer em um programa. É importante
diferenciarmos os diferentes tipos de erro para corrigi-los mais
rapidamente.

..
   #. Syntax errors are produced by Python when it is translating the source code
      into byte code. They usually indicate that there is something wrong with the
      syntax of the program. Example: Omitting the colon at the end of a ``def``
      statement yields the somewhat redundant message ``SyntaxError: invalid
      syntax``.
   #. Runtime errors are produced by the runtime system if something goes wrong
      while the program is running. Most runtime error messages include
      information about where the error occurred and what functions were
      executing. Example: An infinite recursion eventually causes a runtime error
      of maximum recursion depth exceeded.
   #. Semantic errors are problems with a program that compiles and runs but
      doesn't do the right thing. Example: An expression may not be evaluated in
      the order you expect, yielding an unexpected result.

#. Erros de sintaxe (*syntax errors*) ocorrem quando o Python está
   traduzindo o código fonte do seu programa em código executável
   (*byte code*).  Eles usualmente indicam que você escreveu algo
   sintaticamente errado no seu programa.  Por exemplo, não escrever
   ``:`` no final da linha linha com um ``def`` produz uma mensagem de
   certa forma redundante ``SyntaxError: invalid syntax``.
#. Erros de execução (*runtime erros*) ocorrem durante a execução do
   programa.  Eles usualmente indicam que o você cometeu um erro de
   lógica no seu programa.  A maioria das mensagens que relatam um
   erro de execução indicam o ponto do programa em que o erro ocorreu
   e quais funções estavam sendo executadas.  Por exemplo, recursão
   infinita causa o erro de execução ``maximum recursion depth
   exceeded``.  É importante observar que apesar do erro ter se
   manifestado em um certo ponto durante a execução do programa o erro
   de lógica responsável pelo erro pode estar em um trecho de código
   bem distante desse ponto.
#. Erros de semântica (*semantic errors*) ocorrem quando o programa não
   apresenta erro de sintaxe e não ocorre um erro durante a
   execução. O programa é executado do começo ao fim, mas ele não
   produz o resultado desejado.  Isto indica que você cometeu um erro
   de lógica no seu programa.  Por exemplo, uma expressão pode não ser
   avaliada na ordem que você deseja e isso produz o resultado
   errado. Por exemplo, desejamos calcular o valor da expressão ``a /
   (b * c)`` mas escrevemos no programa ``a / b * c`` que devido a
   precedência dos operadores é avaliada como ``(a / b) * c``.


..
   The first step in debugging is to figure out which kind of error you are
   dealing with. Although the following sections are organized by error type, some
   techniques are applicable in more than one situation.

O primeiro passo em **depurar** (*debugging*), ou seja eliminar erros
de programação, é identificar que tipo de erro você cometeu. Apesar
das próximas seções estarem organizadas de acordo com o tipo do erro,
alguma técnicas são aplicáveis em mai do que uma situação.


.. Syntax errors
.. -------------

Erros de sintaxe (*Syntax errors*)
----------------------------------

..
   Syntax errors are usually easy to fix once you figure out what they are.
   Unfortunately, the error messages are often not helpful. The most common
   messages are ``SyntaxError: invalid syntax`` and ``SyntaxError: invalid
   token``, neither of which is very informative.

Erros de sintaxe são comumente fáceis de serem corrigidos, uma vez que
você entenda o qual é o problema.  Infelizmente, as mensagens de erro
frequentemente não ajudam muito, em particular, os iniciantes.  A
mensagem mais comum é ``SyntaxError: invalid syntax`` e ``SyntaxError:
invalid token``, e nenhuma delas é muito informativa.

..
   On the other hand, the message does tell you where in the program the problem
   occurred. Actually, it tells you where Python noticed a problem, which is not
   necessarily where the error is. Sometimes the error is prior to the location of
   the error message, often on the preceding line.

Por outro lado, as mensagens indicam onde no programa o erro ocorreu.
Na verdade, ele diz a você onde o Python notou o problema, que não
é necessariamente onde está o erro. Algumas vezes o erro está localizado 
em um ponto anterior ao indicado pela mensagem de erro, frequentemente
na linha anterior.

..
   If you are building the program incrementally, you should have a good idea
   about where the error is. It will be in the last line you added.

Se você está construindo o programa incrementalmente, pouco a pouco, você
deveria ter um boa ideia sobre onde está localizado o erro.
Estará na última linha que você adicionou.

..
   If you are copying code from a book, start by comparing your code to the book's
   code very carefully. Check every character. At the same time, remember that the
   book might be wrong, so if you see something that looks like a syntax error, it
   might be.

Se você está copiando o código de um livro. comece comparando o seu
código com o código original cuidadosamente. Verifique caractere por caractere.
Ao mesmo tempo, o código original pode estar errado, assim se você vir algo 
que se parece com um erro de sintaxe, ele pode ser um erro mesmo.
 

.. Here are some ways to avoid the most common syntax errors:

Aqui estão alguma maneiras de se evitar os erros de sintaxe mais comuns.

.. #. Make sure you are not using a Python keyword for a variable name.
.. #. Check that you have a colon at the end of the header of every compound
      statement, including ``for``, ``while``, ``if``, and ``def`` statements.
.. #. Check that indentation is consistent. You may indent with either spaces or
      tabs but it's best not to mix them. Each level should be nested the same
      amount.
.. #. Make sure that any strings in the code have matching quotation marks.
.. #. If you have multiline strings with triple quotes (single or double), make
      sure you have terminated the string properly. An unterminated string may
      cause an ``invalid token`` error at the end of your program, or it may treat
      the following part of the program as a string until it comes to the next
      string. In the second case, it might not produce an error message at all!
.. #. An unclosed bracket -- (, {, or [ -- makes Python continue with the next
      line as part of the current statement. Generally, an error occurs almost
      immediately in the next line.
.. #. Check for the classic ``=`` instead of ``==`` inside a conditional.

#. Certifique-se que você não está usando uma palavra reservada do Python 
   (*Python keyword*) como nome de variável.
#. Verifique que você colocou um dois-pontos (``:``) no final do cabeçalho 
   de cada comando composto (*compound statement*), incluindo laço ``for``,
   laço ``while``, comandos de seleção ``if``, ``elif`` e ``else`` e 
   declaração de funções ``def``. 
#. Verifique se a tabulação é consistente. Você pode tabular com espaços ou 
   tabs mas não é aconselhável misturá-los, Cada nível deve ter a mesma 
   quantidade de espaços ou tabs.
#. Certifique de que as aspas ou apóstrofos de qualquer string no código
   estão emparelhados.  
#. Se você tem strings que se estendem por várias linhas delimitados por
   citação tripla (com ``'``  ou ``"``), certifique-se que você terminou o 
   strings de maneira apropriada. Um string não terminado pode causar 
   o erro ``invalid token`` no final do seu programa ou pode tratar 
   o trecho seguinte de código como um string até encontrar o próximo 
   string. No segundo caso pode até não produzir uma mensagem de erro!
#. Uma falta de fecha parêntese, chave ou colchete -- ``(``, ``{`` ou ``[`` -- 
   faz o Python continuar com a próxima linha como parte da expressão corrente.
   Geralmente, um erro ocorre quase que imediatamente na próxima linha.
#. Verifique pelo clássico ``=`` em vez de ``==`` em uma condição.

.. If nothing works, move on to the next section...

Se nada funcionar, vá para a próxima seção...


.. I can't get my program to run no matter what I do.
.. --------------------------------------------------

Não consigo fazer o meu programa rodar
--------------------------------------

..
   If the compiler says there is an error and you don't see it, that might be
   because you and the compiler are not looking at the same code. Check your
   programming environment to make sure that the program you are editing is the
   one Python is trying to run. If you are not sure, try putting an obvious and
   deliberate syntax error at the beginning of the program. Now run (or import) it
   again. If the compiler doesn't find the new error, there is probably something
   wrong with the way your environment is set up.

Se o compilador diz que existe um erro e você não consegue vê-lo, isto
pode ser porque você e o compilador não estão olhando para o mesmo
código.  Verifique o seu ambiente de programação para ter certeza que
o programa que você está editando é o mesmo que o Python está tentando
executar. Se você não tem certeza tente colocar deliberadamente um
erro de sintaxe óbvio no início do programa. Agora execute-o ou
importe-o novamente. Se o compilador não encontrar o novo erro, há
provavelmente algo errado com a maneira que o seu ambiente está
configurado.
  
..
   If this happens, one approach is to start again with a new program like Hello,
   World!, and make sure you can get a known program to run.  Then gradually add
   the pieces of the new program to the working one.

Se isso ocorrer, uma estratégia é começar novamente um novo programa
como "Olá, Mundo!", e se certificar que você consegue far um programa
conhecido ser executado.  Então, gradualmente, adicione pedaços do seu
programa original ao novo programa fazendo funcionar depois de cada
alteração.


.. Runtime errors
.. --------------

Erros de execução (*Runtime errors*)
------------------------------------

..
   Once your program is syntactically correct, Python can import it and at least
   start running it. What could possibly go wrong?

Uma vez que seu programa esteja sintaticamente correto, Python pode 
importá-lo e pelo menos começar a executá-lo. 
O que pode dar errado agora?


.. My program does absolutely nothing.
.. -----------------------------------

Meu programa não faz nada
-------------------------

..
   This problem is most common when your file consists of functions and classes
   but does not actually invoke anything to start execution. This may be
   intentional if you only plan to import this module to supply classes and
   functions.

   If it is not intentional, make sure that you are invoking a function to start
   execution, or execute one from the interactive prompt. Also see the Flow of
   Execution section below.

Este problema é muito comum quando o seu arquivo consiste apenas de funções
ou classe mas na realidade não há invocação de alguma função para se começar 
a execução. Isto pode ser intencional se você somente planeja importar esse
módulo para suprir classes e funções.

Se isso não é intecional, certifique-se que você está invocando uma função
para iniciar a execução, ou execute uma função a partir do Python shell. 
Também leia a seção *Fluxo de execução* mais abaixo.


.. My program hangs.
.. -----------------

Meu programa trava
------------------

..
   If a program stops and seems to be doing nothing, we say it is hanging. Often
   that means that it is caught in an infinite loop or an infinite recursion.

   #. If there is a particular loop that you suspect is the problem, add a
      ``print`` statement immediately before the loop that says entering the loop
      and another immediately after that says exiting the loop.
   #. Run the program. If you get the first message and not the second, you've got
      an infinite loop. Go to the Infinite Loop section below.
   #. Most of the time, an infinite recursion will cause the program to run for a
      while and then produce a RuntimeError: Maximum recursion depth exceeded
      error. If that happens, go to the Infinite Recursion
      section below.
   #. If you are not getting this error but you suspect there is a problem with a
      recursive method or function, you can still use the techniques in the
      Infinite Recursion section.
   #. If neither of those steps works, start testing other loops and other
      recursive functions and methods.
   #. If that doesn't work, then it is possible that you don't understand the flow
      of execution in your program. Go to the Flow of Execution section below.

Se um programa para e parece que não está fazendo nada, dizemos que ele 
está travado (*hanging*). Frequentemente isso significa que você cometeu
algum erro de lógica e que ele está em um laço infinito (*infinite loop*)
ou uma recursão infinita.

#. Se existe um laço particular que você suspeita é o problema, acrescente
   um comando ``print`` imediatamente antes do laço que diz ``entrando no laço`` e
   um outro imediatamente depois que diz ``sai do laço``. 
#. Execute o programa. Se o programa exibe a primeira mensagem e não exibe a 
   segunda, você encontrou um laço infinito. Vá para a seção *Laço infinito* 
   mais adiante.
#. Na maioria da vezes, um recursão infinita fará com que o programa seja executado
   até que um erro ``RuntimeError: Maximum recursion depth exceeded error`` seja
   produzido. Se isso ocorre, vá para a seção *Recursão infinita* mais abaixo.
#. Se você não está recebendo a mensagem anterior e suspeita que existe um
   problema com o método da recursão ou função, você ainda pode usar a técnica na
   seção *Recursão infinita*.
#. Se nenhum desses passos funcionar, começa a testar outros laços e outras
   funções recursivas e métodos.
#. Se isto não funcionar, então é possível que você não esteja entendo o 
   fluxo de execução do seu programa. Vá para a seção *Fluxo de execução* mais
   adiante.    

.. Infinite Loop
.. -------------

Laço infinito
-------------

..
   If you think you have an infinite loop and you think you know what loop is
   causing the problem, add a ``print`` statement at the end of the loop that
   prints the values of the variables in the condition and the value of the
   condition.

Se você encontrou um laço infinito e você acredita que sabe qual laço 
está causando o problema, acrescente um ``print`` no final do laço que 
exibe o valor de cada variável na condição e o valor da condição do laço. 

Por exemplo:

.. sourcecode:: python
    
    while x > 0 and y < 0:
        # faz algo com x
        # faz algo com y
       
        print("x: ", x)
        print("y: ", y)
        print("condicao: ", (x > 0 and y < 0))

..
   Now when you run the program, you will see three lines of output for each time
   through the loop. The last time through the loop, the condition should be
   ``false``. If the loop keeps going, you will be able to see the values of ``x``
   and ``y``, and you might figure out why they are not being updated correctly.

Agora, quando você executa o programa, você verá três linha na saída para
cada vez que o laço é executado. Na última vez que o laço é executado a condição
deveria ser ``False``. Se o laço não para você será capaz de ver os valores de
``x``e ``y``, e você pode ser capaz de perceber porque os valores não estão
sendo atualizados corretamente.

..
   In a development environment like PyScripter, one can also set a breakpoint
   at the start of the loop, and single-step through the loop.  While you do
   this, inspect the values of ``x`` and ``y`` by hovering your cursor over 
   them. 

Em um ambiente de desenvolvimento como PyScripter, podemos também 
colocar um ponto de pausa (*breakpoint*) no início do laço e para
a execução do programa cada vez que no fluxo de execução esse ponto 
é atingido. Nesse momento é possível inspecionar o valores de ``x`` 
e ``y`` movendo seu curso sobre essas variáveis.

..
   Of course, all programming and debugging require that you have a good mental 
   model of what the algorithm ought to be doing: if you don't understand what 
   ought to happen to ``x`` and ``y``, printing or inspecting its value is
   of little use. Probably the best place to debug the code is away from 
   your computer, working on your understanding of what should be happening. 

É evidente que todo processo de programação e depuração exige que você tenha
um bom modelo mental do que o algoritmo deve estar fazendo: se você não 
entende o que deve acontecer com ``x`` e ``y``, imprimir e inspecionar os valores 
dessas variáveis será de *pouquíssima valia*. Provavelmente o melhor para depurar 
o código é *longe* do seu computador, trabalhando a sua compreensão do que
deveria estar acontecendo.


.. Infinite Recursion
.. ------------------

Recursão infinita
-----------------

..
   Most of the time, an infinite recursion will cause the program to run for a
   while and then produce a ``Maximum recursion depth exceeded`` error.

Na maioria das vezes, um recursão infinita causará que o programa seja
executado até que a mensagem de erro ``Maximum recursion depth exceeded``
seja exibida pelo Python.

..
   If you suspect that a function or method is causing an infinite recursion,
   start by checking to make sure that there is a base case.  In other words,
   there should be some condition that will cause the function or method to return
   without making a recursive invocation. If not, then you need to rethink the
   algorithm and identify a base case.

Se você suspeita que uma função ou método está causando uma recursão 
infinita, comece certificando-se que a recursão tem uma base. Em outras
palavras, deve existir alguma condição que causa a função ou método 
a retornar sem fazer mais chamadas recursivas. Se não há uma base você 
precisa repensar o algoritmo e identificar um caso base.


..
   If there is a base case but the program doesn't seem to be reaching it, add a
   ``print`` statement at the beginning of the function or method that prints the
   parameters. Now when you run the program, you will see a few lines of output
   every time the function or method is invoked, and you will see the parameters.
   If the parameters are not moving toward the base case, you will get some ideas
   about why not.

Se existe um caso base mas  programa parece não chegar nesse caso, 
acrescente um ``print`` no início da função ou método para exibir os
valores dos parâmetros. Agora quando executar o programa, você verá na saída 
algumas linhas cada vez que a função ou método for invocado e você verá os valores
dos parâmetros. Se os parâmetros não estão se aproximando do caso base, você
começará  ater ideias sobre a razão disso estar acontecendo.  
 
..
   Once again, if you have an environment that supports easy single-stepping,
   breakpoints, and inspection, learn to use them well. It is our opinion that
   walking through code step-by-step builds the best and most accurate mental
   model of how computation happens. Use it if you have it!

Mais uma vez, se você tem um ambiente que permite pontos de pausa e
um passo-a-passo da execução do programa, aprenda como usar esses
recursos apropriadamente.  É nossa opinião que andar pelo o código
passo-a-passo cria o melhor e mais preciso modelo de como a computação
acontece, Use isso se você tiver.


.. Flow of Execution
.. -----------------

Fluxo de execução
-----------------

..
   If you are not sure how the flow of execution is moving through your program,
   add ``print`` statements to the beginning of each function with a message like
   entering function ``foo``, where ``foo`` is the name of the function.

   Now when you run the program, it will print a trace of each function as it is
   invoked.

   If you're not sure, step through the program with your debugger.

Se você não está seguro sobre como o fluxo de execução (*flow of execution*) esta
se movimento através do seu programa, acrescente alguns comandos ``print``
no inícios de cada função com uma mensagem como ``entrei na função blá``
onde ``blá`` é o nome da função. No final de cada função, antes que o fluxo de
execução volte a função que fez a chamada desta, acrescente um comandos
``print`` com a mensagem ``sai da função blá``.
 

.. When I run the program I get an exception.
.. ------------------------------------------

Quando executo o programa ocorre uma excessão
---------------------------------------------

..
   If something goes wrong during runtime, Python prints a message that includes
   the name of the exception, the line of the program where the problem occurred,
   and a traceback.

Se algo errado ocorre durante a execução do programa, Python imprime uma
mensagem que inclui o nome da exceção (*exception*), a linha do programa
onde o problema ocorreu e um rastro (*traceback*) dos passos que levaram
até aquele ponto do programa.

.. Put a breakpoint on the line causing the exception, and look around!

Coloque pontos de pausa na linha que está causando a exceção, e olhe
no código a sua volta.

..  
   The traceback identifies the function that is currently running,
   and then the function that invoked it, and then the function that
   invoked *that*, and so on.  In other words, it traces the path of
   function invocations that got you to where you are. It also
   includes the line number in your file where each of these calls
   occurs.

O rastro (*traceback*) identifica a função que está sendo executada,
e a função que a invocou, a então a função que invocou a função
que a invocou, e assim sucessivamente até chegar na função inicial do 
programa. Em outras palavras, o Python exibe os rastro das chamadas
de função que fez com que o fluxo de execução chegasse aquela determinada
linha. Ele também inclui o número da linha no programa de onde essas
chamadas foram feitas.

..  
   The first step is to examine the place in the program where the
   error occurred and see if you can figure out what happened. These
   are some of the most common runtime errors:

O primeiro passo  examinar o lugar do programa onde o erro
ocorreu e ver se você consegue perceber o que ocorreu.
A seguir estão alguns do erros de execução mais comuns:

NameError 
    Você está tentando usar uma variável que não existe no
    ambiente corrente. Lembre-se que variáveis locais são locais.
    Você não pode fazer referência a elas fora da função onde foram
    definidas.

    ..
       You are trying to use a variable that doesn't exist in the current
       environment. Remember that local variables are local. You cannot refer to
       them from outside the function where they are defined.

TypeError
    Existem várias causa possíveis:

    #. Você esta tentando usar um valor inapropriado. Por exemplo, 
       índices de strings, listas e tuplas devem ser valores inteiros 
       (tipo ``int``).
    #. Existe uma incompatibilidade entre itens em um formato de um string 
       e os valores passados para conversão. Isto ocorre quando o 
       número de itens não é o esperado ou uma conversão inválida é 
       executada.
    #. Você está passando o numero errado de argumentos para uma função ou 
       método. Para métodos, olhe a definição do método e verifique
       se o primeiro parâmetros é ``self``. Depois olhe a invocação 
       do método; certifique-se de que a chamada do método sobre um
       objeto do tipo certo e fornecendo os argumento corretamente.

..
       There are several possible causes:

       #. You are trying to use a value improperly. Example: indexing a
          string, list, or tuple with something other than an integer.
       #. There is a mismatch between the items in a format string and the
          items passed for conversion. This can happen if either the number of
          items does not match or an invalid conversion is called for.
       #. You are passing the wrong number of arguments to a function or
          method. For methods, look at the method definition and check that the
          first parameter is ``self``. Then look at the method invocation; make
          sure you are invoking the method on an object with the right type and
          providing the other arguments correctly.

KeyError
    Você esta tentando acessar um elemento de um dicionário usando 
    um valor de uma chave que o dicionário não contém.

..    You are trying to access an element of a dictionary using a key value that
..    the dictionary does not contain.

AttributeError
    Você esta tentando acessar um atributo ou método que não 
    existe

..    You are trying to access an attribute or method that does not exist.

IndexError
    O índice que você está usando para acessar uma lista, string, ou 
    tupla é maior que o seu comprimento menos um. Imediatamente antes
    da linha desse erro acrescente um comando ``print`` para exibir
    o valor do índice e o comprimento da lista, string ou tupla. 
    O objetos tem o tamanho certo? O índice é um valor correto?
 

..    The index you are using to access a list, string, or tuple is
      greater than its length minus one. Immediately before the site
      of the error, add a ``print`` statement to display the value of
      the index and the length of the array. Is the array the right
      size? Is the index the right value?


.. I added so many ``print`` statements I get inundated with output.
.. -----------------------------------------------------------------

Coloquei tanto ``print`` no meu programa que não consigo ver nada
-----------------------------------------------------------------

.. One of the problems with using ``print`` statements for debugging is
   that you can end up buried in output. There are two ways to proceed:
   simplify the output or simplify the program.

Um dos problemas em usar comandos ``print`` para depuração é 
que o programa pode acabar exibindo tanto valor de variável ou
mensagem que se torna difícil enxergar qualquer coisa.
Existem duas maneiras de se proceder: simplifique a saída 
ou simplifique o programa.

..
   To simplify the output, you can remove or comment out ``print``
   statements that aren't helping, or combine them, or format the output
   so it is easier to understand.

Para simplificar a saída do programa, você pode remover ou comentar
alguns comandos ``print`` que não estão ajudando, ou combinar eles,
ou formatar a saída de tale maneira que facilite a compreensão
das mensagens.

..
   To simplify the program, there are several things you can do. First,
   scale down the problem the program is working on. For example, if you
   are sorting an array, sort a *small* array. If the program takes input
   from the user, give it the simplest input that causes the problem.

Para simplificar o programa existem várias coisas que você pode fazer.
Primeiro reduza o tamanho da entrada com o qual o programa está trabalhando.
Por exemplo, se você está ordenando os elemento de uma lista, 
ordene os elementos de uma lista menor. Se o programa recebe os 
dados que um usuário está digitante, digite o menor número
de valores que fazem com que ocorra um erro no programa. 

..
   Second, clean up the program. Remove dead code and reorganize the
   program to make it as easy to read as possible. For example, if you
   suspect that the problem is in a deeply nested part of the program,
   try rewriting that part with simpler structure. If you suspect a large
   function, try splitting it into smaller functions and testing them
   separately.


Segundo, limpe o programa. Remova código que não está sendo usado e
reorganize o programa de modo a fazê-lo o mais legível possível.  Por
exemplo, se você suspeita que o erro está em uma parte muita aninhada
do programa (por exemplo, em um ``while`` dentro de um ``while``
dentro de um ``for`` ...), tente reescrever essa parte com estruturas
mais simples.  Se você suspeita que o erro está em uma função muito
longa, tente quebrar a função em funções menores e testar cada uma
separadamente.

..
   Often the process of finding the minimal test case leads you to the
   bug. If you find that a program works in one situation but not in
   another, that gives you a clue about what is going on.

Frequentemente o processo de encontra um teste minimal que faz
com que o problema se manifeste acaba conduzindo-nos ao ponto
do programa em que está o erro. Se você descobre que o programa
funciona em uma situação, mas não funciona em outra, isso pode
dar uma dica de onde está o programa. 

..
   Similarly, rewriting a piece of code can help you find subtle bugs. If
   you make a change that you think doesn't affect the program, and it
   does, that can tip you off.

Similarmente, reescrever um pedaço de código pode ajudá-lo a encontra
um erro sútil. Se você faz uma lateração que você acredita que não
deveria afetar a execução do programa e ela afeta, isso pode lhe
alertar sobre algo.

..
   You can also wrap your debugging print statements in some
   condition, so that you suppress much of the output. For example, if
   you are trying to find an element using a binary search, and it is
   not working, you might code up a debugging print statement inside
   a conditional:  if the range of candidate elements is less that 6,
   then print debugging information, otherwise don't print. 

Você também pode envolver os seus comandos ``print`` para depuração em
alguma condição, assim você poderá se concentrar em examinar as
mensagens de depuração que realmente interessam.  Por exemplo, se você
está tentando encontrar um elemento em uma lista ordenada com busca
binária (*binary search*), e o programa está com algum erro, você pode
colocar um comando ``print`` para depuração dentro de uma condição: se
a sub-lista que o programa está examinando tem menos de 6 elementos,
imprima informação para depuração, em caso contrário não imprima coisa
alguma.

..
   Similarly, breakpoints can be made conditional: you can set a breakpoint
   on a statement, then edit the breakpoint to say "only break if this
   expression becomes true".

Similarmente, pontos de pausa pode ser feito condicionalmente: você
pode definir o ponto de pausa em um comando e editar a sua
configuração para que "somente pause neste ponto se uma dada expressão
seja verdadeira".


.. Semantic errors
.. ---------------

Erros semânticos
----------------

..
   In some ways, semantic errors are the hardest to debug, because the
   compiler and the runtime system provide no information about what is
   wrong. Only you know what the program is supposed to do, and only you
   know that it isn't doing it.

De certa forma, erros semânticos (*semantic erros*) são os mais
difíceis de serem corrigidos pois nem o compilador e nem o interpretador
Python fornecem alguma informações sobre o que está errado. 
Somente você sabe qual é o comportamento esperado do programa, 
somente você sabe que ele não está fazendo o que deveria.

..
   The first step is to make a connection between the program text and
   the behavior you are seeing. You need a hypothesis about what the
   program is actually doing. One of the things that makes that hard is
   that computers run so fast.

O primeiro passo é fazer uma conexão entre o programa e o 
comportamento que você está vendo. Você precisa sobre o que o programa
está de fato fazendo. Uma coisa que torna isso difícil é que programas
são executados muito rapidamente. Outra dificuldade
é que programas fazem o que ordenamos que façam
e não o que gostaríamos que fizessem.

.. You will often wish that you could slow the program down to human
   speed, and with some debuggers you can. But the time it takes to
   insert a few well-placed ``print`` statements is often short compared to
   setting up the debugger, inserting and removing breakpoints, and
   walking the program to where the error is occurring.

Você frequentemente gostaria de desacelerar o seu programa para 
a velocidade de humanos, e como alguns programas para depuração (*debuggers*)
você pode. Mas o tempo que é gasto para colocar alguns comandos ``print``
em lugares estratégicos é frequentemente mais curto comparado com 
o tempo gasto para preparar o *debugger*, inserir e remover pontos de
pausa (*breakpoints*) e acompanhar a execução do programa até que
o erro ocorra. 
 

.. My program doesn't work.
.. ------------------------

Meu programa não funciona
-------------------------

.. You should ask yourself these questions:

Você deve se fazer as seguintes perguntas:

..
   #. Is there something the program was supposed to do but which doesn't
      seem to be happening? Find the section of the code that performs that
      function and make sure it is executing when you think it should.
   #. Is something happening that shouldn't? Find code in your program
      that performs that function and see if it is executing when it
      shouldn't.
   #. Is a section of code producing an effect that is not what you
      expected? Make sure that you understand the code in question,
      especially if it involves invocations to functions or methods in other
      Python modules. Read the documentation for the functions you invoke.
      Try them out by writing simple test cases and checking the results.

#. Há alguma coisa que o programa deveria estar fazendo mas não 
   está? Encontra a seção do seu código que é responsável essa
   função e certifique-se de que está fazendo o que você acredita
   que deveria estar.
#. Há alguma coisa que está ocorrendo mas não deveria? Encontre no 
   seu código a seção que é responsável por essa tarefa e veja se 
   algo está sendo feito quando não deveria.
#. Há uma seção do código que está produzindo um efeito que não
   é o que você espera? Certifique-se que você entende o trecho
   de código em questão, especialmente se envolve a invocação 
   a funções ou métodos de outros módulos. Leia a documentação das 
   funções que você esta invocando. Experimente-as através de
   testes simples e verifique os resultados produzidos. 
   Para isso algumas vezes é útil utilizarmos o Python shell.

..
   In order to program, you need to have a mental model of how programs
   work. If you write a program that doesn't do what you expect, very
   often the problem is not in the program; it's in your mental model.

Para programar você deve ter um modelo mental de como programas
trabalham. Se você escreve um programa que não faz o que você 
espera, frequentemente (sempre?) o problema não é o programa,
mas sim o seu modelo mental.

..
   The best way to correct your mental model is to break the program into
   its components (usually the functions and methods) and test each
   component independently. Once you find the discrepancy between your
   model and reality, you can solve the problem.

A melhor maneira para corrigir o seu modelo mental é quebrar 
o programa em componentes (usualmente funções e métodos) e 
testar cada componente *independentemente*. Uma vez que você 
encontra discrepância entre o seu modelo e a realidade, 
você pode resolver o problema.

..
   Of course, you should be building and testing components as you
   develop the program. If you encounter a problem, there should be only
   a small amount of new code that is not known to be correct.

É claro que, você deveria construir e testar componentes a medida
que você desenvolve o programa. Se você encontrar um problema,
deveria haver apenas um parte pequena de novo código que 
não temos certeza que está correto.


.. I've got a big hairy expression and it doesn't do what I expect.
.. ----------------------------------------------------------------

Minha expressão cabeluda não faz o que eu esperava
--------------------------------------------------

..
   Writing complex expressions is fine as long as they are readable, but
   they can be hard to debug. It is often a good idea to break a complex
   expression into a series of assignments to temporary variables.

Escrever expressões complexas não é ruim contanto que elas seja
razoavelmente claras e legíveis, mas elas podem ser difíceis
de serem depuradas. É frequentemente uma boa ideia quebrar um
expressão complexa em um série de atribuições a variáveis 
temporárias.

.. For example:

Por exemplo:

.. sourcecode:: python
    
    self.hands[i].addCard (self.hands[self.findNeighbor(i)].popCard())

.. This can be rewritten as:

Pode ser reescrito como:

.. sourcecode:: python
    
    neighbor = self.findNeighbor (i)
    pickedCard = self.hands[neighbor].popCard()
    self.hands[i].addCard (pickedCard)

..
   The explicit version is easier to read because the variable names provide
   additional documentation, and it is easier to debug because you can check the
   types of the intermediate variables and display or inspect their values.

A versão explícita é mais legível pois os nome das variáveis fornece
documentação adicional, e é mais fácil de ser depurada já que você pode
verificar o tipo das variáveis intermediárias e exibir ou inspecionar os
seu valores. 

..
   Another problem that can occur with big expressions is that the order of
   evaluation may not be what you expect. For example, if you are translating the
   expression ``x/2pi`` into Python, you might write:

Outro problema que pode ocorrer com expressões grandes é que a ordem que
ele é avaliada pode não ser o que você gostaria. Por exemplo, se você traduz
a expressão ``x/2pi`` para Python, você pode escrever:


.. sourcecode:: python
    
    y = x / 2 * math.pi;

..
   That is not correct because multiplication and division have the same
   precedence and are evaluated from left to right. So this expression computes
   ``(x/2)pi``.

Isto não está correto pois multiplicação e divisão tem a mesma precedência e
são avaliada da esquerda para a direita. Assim, essa expressão computa
``(x/2)pi``.

..
   A good way to debug expressions is to add parentheses to make the order of
   evaluation explicit:

Uma boa maneira de depurar expressões é adicionar parênteses para fazer 
a ordem da avaliação explícita:

.. sourcecode:: python
    
    y = x / (2 * math.pi);

..
   Whenever you are not sure of the order of evaluation, use parentheses.  Not
   only will the program be correct (in the sense of doing what you intended), it
   will also be more readable for other people who haven't memorized the rules of
   precedence.

Sempre que você não tem certeza sobre a ordem da avaliação, use parênteses.
Além do programa estar correto (no sentido que ele faz o que você desejava),
ele também será mais legível para outras pessoas que não memorizaram as
regras de precedência.


.. I've got a function or method that doesn't return what I expect.
.. ----------------------------------------------------------------


Minha função ou método não retorna o que eu espero
--------------------------------------------------

..
   If you have a ``return`` statement with a complex expression, you don't have a
   chance to print the ``return`` value before returning. Again, you can use a
   temporary variable. For example, instead of:


Se você tem um comando ``return`` com uma função complexa, você não tem 
a chance de imprimir o valor antes dele ser retornado. Novamente, você pode
usar variáveis temporárias. Por exemplo, em vez de:


.. sourcecode:: python
    
    return self.hands[i].removeMatches()

.. you could write:

você pode escrever:

.. sourcecode:: python
    
    count = self.hands[i].removeMatches()
    return count

.. Now you have the opportunity to display or inspect the value of ``count`` before
.. returning.

Agora, você tem a oportunidade de exibir e inspecionar o valor de
``count`` antes de retorna-lo.

.. I'm really, really stuck and I need help.
.. -----------------------------------------

Eu estou realmente travado e necessito ajuda
---------------------------------------------

..
   First, try getting away from the computer for a few minutes. Computers emit
   waves that affect the brain, causing these effects:

Primeiro, tente ficar loge do computador por alguns minutos.
Computadores emitem ondas que afetam o seu célebro, causando os seguintes
efeitos:

#. Frustação e/ou ódio.
#. Crenças superticiosas (o computador me odeia) e pensamentos mágicos 
   (o programa só funciona quando uso meu chapéu preto).
#. Programação com método passei aletório (tentativa de programa escrevendo 
   todo os programa possívesi a escolhendo o que faz o que deve).
#. Mais crenças superticiosas (na minha casa funciona).

..
   #. Frustration and/or rage.
   #. Superstitious beliefs ( the computer hates me ) and magical thinking ( the
      program only works when I wear my hat backward ).
   #. Random-walk programming (the attempt to program by writing every possible
      program and choosing the one that does the right thing).

..
   If you find yourself suffering from any of these symptoms, get up and go for a
   walk. When you are calm, think about the program. What is it doing? What are
   some possible causes of that behavior? When was the last time you had a working
   program, and what did you do next?

Se você estiver sofrendo de qualquer um desses sintomas, levantesse e vá andar. Quando
você estiver calmo, pense sobre o programa. O que ele está fazendo? 
O que possivelmente pode causar esse comportamento? Quando foi a última vez que
o programa parecia estar funcionando e o que você alterou?

..
   Sometimes it just takes time to find a bug. We often find bugs when we are away
   from the computer and let our minds wander. Some of the best places to find
   bugs are trains, showers, and in bed, just before you fall asleep.


.. No, I really need help.
.. -----------------------

Não, eu realmente preciso de ajuda
----------------------------------

..
   It happens. Even the best programmers occasionally get stuck.  Sometimes you
   work on a program so long that you can't see the error.  A fresh pair of eyes
   is just the thing.

Isso acontece.
Mesmo os melhores programadores as vezes ficam travados em um problema.
Algumas vezes você trabalha tanto tempo em um programa que você não
consegue ver o seu erro. O para fresco de olhos pode ajudar.

 
..
   Before you bring someone else in, make sure you have exhausted the techniques
   described here. Your program should be as simple as possible, and you should be
   working on the smallest input that causes the error. You should have ``print``
   statements in the appropriate places (and the output they produce should be
   comprehensible). You should understand the problem well enough to describe it
   concisely.

Antes de você trazer outra pessoa para olhar o seu programa, certifique-se
que você exauriu as técnicas descritas aqui. O seu programa deve ser o mais simples
possível e você deve estar trabalhando com a menor entrada que causa o erro.
Você deve ter colocado alguns comandos ``print`` em lugares estratégicos para 
exibir valores intermediários (a saída que eles produzem deve ser compreensível).
Você deve entender o problema suficientemente para descrevê-lo sucintamente.
 
..
   When you bring someone in to help, be sure to give them the information they
   need:

   #. If there is an error message, what is it and what part of the program does
      it indicate?
   #. What was the last thing you did before this error occurred? What were the
      last lines of code that you wrote, or what is the new test case that fails?
   #. What have you tried so far, and what have you learned?


Quando você traz alguém para ajudar, certifique-se em dar as informações
que elas necessitam:

#. Se há uma mensagem de erro, que mensagem é essa e qual a parte do programa
   que ela indica?
#. Qual foi a última coisa que você fez antes desse erre ocorrer?
   Quais foram as últimas linhas de código que você escreveu ou qual 
   é o novo teste onde o programa falha?
#. O que você tentou até agora, e o que você aprendeu?


..
   Good instructors and helpers will also do something that should not 
   offend you: they won't believe when you tell them *"I'm sure all the input
   routines are working just fine, and that I've set up the data correctly!"*.
   They will want to validate and check things for themselves.  
   After all, your program has a bug.  
   Your understanding and inspection of the code have not found it yet. So you
   should expect to have your assumptions challenged.  And as you gain skills
   and help others, you'll need to do the same for them.


Bons instrutores e monitores farão algo que não deveria ofendê-lo.
eles não acreditarão no que você diz a eles *"Estou certo de que todas
as rotinas de entrada estão funcionando e que eu forneci os dados corretamente!"*.
Eles desejarão verificar tudo pessoalmente.
Afinal de contas, o seu programa tem um erro.
A sua compreensão e inspeção do código não encontrou o erro ainda.
Logo, você deveria esperar ter as suas convicções desafiadas.
A medida que você ganhar prática para ajudar outros, você necessitará fazer 
a mesma coisa.
 

.. When you find the bug, take a second to think about what you could have done to
   find it faster. Next time you see something similar, you will be able to find
   the bug more quickly.

Quando você encontrar o erro (ou *bug*), gaste alguns momentos pensando no que
você poderia ter feito para encontrá-lo mais rapidamente. Na próxima vez que
você ver algo similar, você será capas de encontrar o *bug* mais rapidamente.

 
.. Remember, the goal is not just to make the program work. The goal is to learn
.. how to make the program work.

Lembre-se, o objetivo não é apenas fazer o programa funcionar.
O objetivo e aprender como fazer programas corretos.
