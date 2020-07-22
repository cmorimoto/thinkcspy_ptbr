.. while loop - malha while ou as vezes comando while
.. loop variable - variável de controle
.. indentation - recuo além de tabulação
.. nested conditionals - 

..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".
    
..  shortname:: MaisSobreIteração
..  description:: Esse capítulo traz mais informação sobre iteraçao e o comando while

Mais sobre Iteração
===================

.. index:: iteração, atribuição, comando de atribuição, reatribuição

.. index::
    single: comando; atribuição
   
    
.. Computers are often used to automate repetitive tasks. Repeating
   identical or similar tasks without making errors is something that
   computers do well and people do poorly.

Realizar tarefas repetitivas sem cometer erros é algo que os
computadores fazem bem e as pessoas nem tanto. É por isso que os
computadores são utilizados muitas vezes para automatizar esses tipos
de tarefas.

.. Repeated execution of a sequence of statements is called
   **iteration**.  Because iteration is so common, Python provides
   several language features to make it easier. We've already seen the
   ``for`` statement in Chapter 3.  This is a very common form of
   iteration in Python. In this chapter we are also going to look at
   the ``while`` statement --- another way to have your program do
   iteration.

A execução repetida de uma sequência de instruções é chamada de
**iteração** (*iteration*). Como iterar é muito comum, Python tem
várias características para torná-la mais fácil. Nós já vimos o
comando ``for`` no Capítulo 3. Esta é uma forma muito comum de
iteração em Python. Neste capítulo também vamos ver o comando
``while`` --- como uma outra maneira de fazer iterações em seus
programas.

.. admonition:: Scratch Editor

    .. actex:: scratch_7_1


.. index:: for loop

.. The ``for`` loop revisited

Mais sobre o comando ``for``
----------------------------

.. Recall that the ``for`` loop processes each item in a list.  Each item in turn is (re-)assigned to the loop variable, and the body of the loop is executed. We saw this example in an earlier chapter.

Lembre-se que o comando ``for`` processa cada item em uma lista. Cada item, por sua vez, é (re)atribuído a variável de contagem, e o corpo do laço é executado. Vimos este exemplo em um capítulo anterior.

.. activecode:: ch07_for1

    for f in ["Joe", "Amy", "Brad", "Angelina", "Zuki", "Thandi", "Paris"]:
        invitation = "Hi " + f + ".  Please come to my party on Saturday!"
        print(invitation) 
        
.. We have also seen iteration paired with the update idea to form the accumulator pattern.  For example, to compute the sum of the first n integers, we could create a for loop using the ``range`` to produce the numbers 1 thru n. Using the accumulator pattern, we can start with a running total and on each iteration, add the current value of the loop variable.  A function to compute this sum is shown below.

Vimos também que uma iteração pode ser combinada com a idéia de atualização para formar o padrão acumulador. Por exemplo, para calcular a soma dos primeiros n números inteiros, é possível criar um loop usando o comando ``range`` para produzir os números de 1 a n. Usando o padrão acumulador, podemos começar com um total parcial e, a cada iteração, adicionar o valor atual à variável de controle. Uma função para calcular esta soma é mostrado abaixo.

.. activecode:: ch07_summation

    def someAte(limite):
        soma = 0
        for numero in range(1, limite+1):
            soma = soma + numero

        return soma

    print(someAte(4))

    print(someAte(1000))

.. To review, the variable ``theSum`` is called the accumulator.  It
   is initialized to zero before we start the loop.  The loop
   variable, ``aNumber`` will take on the values produced by the
   ``range(1,aBound+1)`` function call.  Note that this produces all
   the integers starting from 1 up to the value of ``aBound``.  If we
   had not added 1 to ``aBound``, the range would have stopped one
   value short since ``range`` does not include the upper bound.

Para rever, a variável ``soma`` é chamado de acumulador. Ela é
inicializada com zero antes de iniciar o laço. A variável do laço,
``numero`` irá assumir os valores retornados pela chamada de função
``range(1, limite+1)``. Note que esta chamada produz uma lista com
todos os inteiros a partir de 1 até o valor de ``limite+1``. Se não
tivéssemos adicionado 1 em ``limite`` a função range teria devolvido
uma lista sem o valor ``limite`` pois essa função não inclui o limite
superior.

.. The assignment statement, ``theSum = theSum + aNumber``, updates
   ``theSum`` each time thru the loop.  This accumulates the running
   total.  Finally, we return the value of the accumulator.
 
O comando de atribuição, ``soma = soma + numero``, atualiza o valor de
``soma`` a cada iteração do laço. A variável ``soma`` recebe portanto
o total parcial até um determinado instante da execução. Finalmente, a
função ``someAte`` retorna o valor do acumulador.

.. admonition:: Scratch Editor

    .. actex:: scratch_7_2


O comando ``while``
-------------------

.. video:: whileloop
   :controls:
   :thumb: ../_static/whileloop.png

   http://media.interactivepython.org/thinkcsVideos/whileloop.mov
   http://media.interactivepython.org/thinkcsVideos/whileloop.webm


Há um outro comando Python que pode ser usado para construir uma
iteração. Ele é o comando ``while``. O ``while`` fornece um mecanismo
muito mais geral para a iteração. Semelhante ao comando ``if``, ele
usa uma expressão booleana para controlar o fluxo de execução. O corpo
do ``while`` será repetido enquanto a expressão booleana de controle
for avaliada como ``True``.

A figura a seguir mostra o fluxo de controle.

.. image:: Figures/while_flow.png

Podemos usar o ``while`` para criar qualquer tipo de iteração,
incluindo tudo o que já fizemos com um comando ``for``. Por exemplo, o
programa na seção anterior poderia ser reescrito usando o ``while``.
Ao invés de utilizar a função ``range`` para produzir os números para
calcular a somatória, vamos precisar programar uma forma de
produzi-los. Para isso, vamos criar uma variável chamada ``numero`` e
inicializá-la com 1, o primeiro número da somatória. Cada iteração irá
adicionar ``numero`` ao total parcial até que todos os valores tenham
sido usados. Para controlar a iteração, temos de criar uma expressão
booleana que deve ser avaliada como ``True`` enquanto desejarmos
acrescentar valores ao total. Neste caso, a somatória deve continuar
enquanto o ``numero`` for menor ou igual ao limite.

A seguir ilustramos uma nova versão do programa que calcula a somatória utilizando o comando while.

.. activecode:: ch07_while1
    
    def someAte(limite):
        """ Retorna a soma de 1+2+3 ... n """
        
        soma  = 0
        numero = 1
        while numero <= limite:
            soma = soma + numero
            numero = numero + 1
        return soma
        
    print(someAte(4))

    print(someAte(1000))



.. You can almost read the ``while`` statement as if it were in
   natural language. It means, while ``aNumber`` is less than or equal
   to ``aBound``, continue executing the body of the loop. Within the
   body, each time, update ``theSum`` using the accumulator pattern
   and increment ``aNumber``. After the body of the loop, we go back
   up to the condition of the ``while`` and reevaluate it.  When
   ``aNumber`` becomes greater than ``aBound``, the condition fails
   and flow of control continues to the ``return`` statement.

Você quase pode ler o ``while`` como se fosse em linguagem natural
como se fosse a palavara ``enquanto``. Isso significa que, enquanto
``numero`` for menor ou igual a ``limite``, continue a executar o
corpo do laço. Dentro do corpo, atualize ``soma`` usando o padrão
acumulador e incremente ``numero`` para produzir o próximo elemento da
somatória. Ao final da execução do corpo do laço, vamos voltar a
testar a condição do ``while``. Quando ``numero`` tornar-se maior que
``limite``, a condição falha e o próximo comando a ser executado de
acordo com o fluxo de execução do ``while`` é o comando ``return``.

.. The same program in codelens will allow you to observe the flow of
   execution.
 
O mesmo programa no codelens lhe permitirá observar esse fluxo de execução.

.. codelens:: ch07_while2
    
    def someAte(limite):
        """ Retorna a soma de 1+2+3 ... n """
        
        soma  = 0
        numero = 1
        while numero <= limite:
            soma = soma + numero
            numero = numero + 1
        return soma
        
    print(someAte(4))

.. note:: Os nomes das variáveis foram escolhidos para facilitar a leitura do código.

.. More formally, here is the flow of execution for a ``while`` statement:

Formalmente, este é o fluxo de execução do comando ``while``:

.. #. Evaluate the condition, yielding ``False`` or ``True``.
.. #. If the condition is ``False``, exit the ``while`` statement and continue
   execution at the next statement.
.. #. If the condition is ``True``, execute each of the statements in the body and then go back to step 1.

#. Avalie a condição, que deve resultar em ``False`` ou ``True``.
#. Se o resultado for ``False``, saia do comando ``while`` e continue o programa executando o próximo comando.
#. Se o resultado da condição for ``True``, execute os comandos dentro do corpo do ``while`` e, ao final, retorne ao passo 1.

.. The body consists of all of the statements below the header with
   the same indentation.

O corpo do ``while`` é constituído por todas as instruções abaixo do cabeçalho com a mesma tabulação.

.. This type of flow is called a **loop** because the third step loops
   back around to the top. Notice that if the condition is ``False``
   the first time through the loop, the statements inside the loop are
   never executed.

Este tipo de fluxo é chamado de **laço** (*loop*) porque o terceiro
passo volta para o topo, fechando o ``laço``. Observe que se a
condição é avaliada como ``False`` no início do laço, os comandos
dentro do corpo nunca são executados.

.. The body of the loop should change the value of one or more
   variables so that eventually the condition becomes ``False`` and
   the loop terminates. Otherwise the loop will repeat forever. This
   is called an **infinite loop**. An endless source of amusement for
   computer scientists is the observation that the directions on
   shampoo, lather, rinse, repeat, are an infinite loop.

O corpo do laço deve alterar o valor de uma ou mais variáveis para que
a condição se torne ``False`` e faça o laço terminar. Caso contrário,
o ciclo se repetirá para sempre. Isso é chamado de um **laço
infinito**.  Uma boa piada para os cientistas da computação são as
instruções que acompanham alguns xampus: ensaboe, enxague, repita; que
resulta em um laço infinito.

.. In the case shown above, we can prove that the loop terminates
   because we know that the value of ``n`` is finite, and we can see
   that the value of ``v`` increments each time through the loop, so
   eventually it will have to exceed ``n``. In other cases, it is not
   so easy to tell.
 
No exemplo anterior, podemos provar que o laço termina pois nós
sabemos que o valor de ``limite`` é finito e que o valor de ``numero``
é incrementado a cada iteração do laço. Portanto, a cada iteração, o
valor de ``numero`` fica mais próximo do ``limite``, até
ultrapassá-lo, quando o laço termina. Há outros casos onde não é tão
fácil dizer se o laço termina.

.. note::

	A introdução do comando while nos leva a pensar sobre os tipos
	de iteração que já vimos. O comando ``for`` sempre itera em
	uma sequência de valores, como a lista de nomes para o partido
	ou a lista de números criados por ``range``. Com nós sabemos
	que ele vai repetir uma vez para cada valor desse conjunto,
	dizemos que o ``for`` cria um laço do tipo **iteração
	definida** (*definite iteration*) pois nós sabemos
	definitivamente quantas vezes vamos iteragir. Por outro lado,
	o ``while`` depende de uma condição que precisa ser avaliada
	como ``False`` para que o laço termine. Uma vez que não
	sabemos necessariamente quando isso vai acontecer, ele cria o
	que nós chamamos de **iteração indefinida** (*indefinite
	iteration*).Iteração indefinida significa simplesmente que não
	sabemos quantas vezes vamos repetir mas, eventualmente, a
	condição de controle da iteração irá falhar e a iteração vai
	parar. (A menos que tenhamos um laço infinito, que é,
	naturalmente, um problema)


Você deve notar que o ``while`` dá mais trabalho para você --- o
programador --- do que o equivalente ``for``. Ao usar um ``while``
você mesmo é que tem que controlar a variável do laço. Você deve
fornecer um valor inicial, criar a condição de saída e depois
certificar-se de mudar alguma coisa no corpo de modo que o laço
termine.

Então, para que precisamos de dois tipos de laços se o ``for`` parece
mais fácil? Este próximo exemplo mostra uma iteração indefinida onde
precisamos do poder extra que nós temos usando o ``while``.

.. admonition:: Scratch Editor

    .. actex:: scratch_7_3

**Teste seu entendimento**

.. mchoicemf:: test_question7_2_1
   :answer_a: Verdadeiro
   :answer_b: Falso
   :correct: a
   :feedback_a: Embora o ``while`` tenha uma sintaxe diferente, ele é tão poderoso quanto o ``for`` e geralmente mais flexível.
   :feedback_b: Geralmente o ``for`` é mas natural e conveniente para uma tarefa, mas essa mesma tarefa pode sempre ser expressa usando um ``while``.

   Verdadeiro ou Falso: você pode reescrever qualquer ``for`` na forma de um ``while``.
   
.. mchoicemf:: test_question7_2_2
   :answer_a: n começa com 10 e é incrementado de 1 a cada iteração do laço, de forma que ele é sempre positivo.
   :answer_b: ``resposta`` começa em 1 e é incrementado de n a cada iteração, de forma que ele é sempre positivo
   :answer_c: Você não pode comparar n com zero em um ``while``. Você precisa comparar n com uma outra variável.
   :answer_d: No corpo de um ``while``, nós devemos tornar n ``False`` e esse código não faz isso.
   :correct: a
   :feedback_a: O laço será executado enquanto n for positivo. Nesse caso, podemos ver que n nunca se tornará não-positivo.
   :feedback_b: Apesar de ser verdade que ``resposta`` é sempre positivo, essa variável não é usada na condição de controle do laço.
   :feedback_c: É perfeitamente válido comparar n com zero. Embora indiretamente, isso é o que causa o laço infinito.
   :feedback_d: A condição do laço deve se tornar falsa para que o laço termine, mas n, por si só, não é a condição nesse caso.

   O seguinte pedaço de código contém um laço infinito. Qual é a melhor explicação para o motivo desse laço não terminar?
     <pre>
     n = 10
     resposta = 1
     while ( n > 0 ):
       resposta = resposta + n
       n = n + 1
     print resposta
     </pre>

Caminhadas Aleatórias de Tartarugas
-----------------------------------

Suponha que nós queremos nos divertir assistindo uma tartaruga passear aleatoriamente pela tela. Ao executar o programa, queremos que a tartaruga e o programa se comportem da seguinte maneira:

#. A tartaruga começa no centro da tela.
#. Jogue uma moeda. Se der cara, vire 90 graus para a esquerda. Se der coroa, vire 90 graus à direita.
#. Dê 50 passos para a frente.
#. Se a tartaruga passou para fora da tela então pare. Caso contrário, volte para o passo 2 e repita.

Observe que não podemos prever quantas vezes a tartaruga terá de jogar a moeda antes que ela passe para fora da tela, de modo que não podemos usar um ``for`` neste caso. De fato, embora muito pouco provável, este programa pode nunca acabar e, por isso, nós chamamos esta iteração de indefinida.

Assim, com base na descrição do problema acima, podemos descrever um programa tal como:

.. sourcecode:: python

    crie uma janela e uma tartaruga

    while a tartaruga estiver na janela:
        gere um número aleatório entre 0 e 1
        if o número == 0 (cara):
            vire à esquerda
        else:
            vire à direita
        mova a tarturuga 50 passos para frente

Agora, provavelmente a única coisa que possa estar um pouco confusa
para você é a parte sobre se ou não a tartaruga ainda está na
tela. Mas esta é a parte boa da programação, nós podemos atrasar a
solução das coisas difíceis e obter *algo* em nosso programa que
funciona imediatamente. A maneira como vamos fazer isso é delegar o
trabalho de decidir se a tartaruga ainda está na tela ou não para uma
função booleana. Vamos chamar esta função booleana de
``estaNaTela``. Nós podemos escrever uma versão muito simples dessa
função booleana fazendo-a retornar sempre ``True``, ou fazendo-a
retornar um valor aleatório. O ponto é implementar algo simples para
que possamos nos concentrar nas partes que já sabemos como fazer bem e
fazê-las funcionar.  Como fazer a função retornar sempre o valor
``True`` não seria uma boa idéia, vamos escrever a nossa versão para
retornar um valor aleatoriamente. Vamos dizer que há uma chance de 90%
da tartaruga ainda permanecer na janela e 10% que a tartaruga tenha
escapado.

.. activecode:: iter_randwalk1

    import random
    import turtle


    def estaNaTela(tela, tar):
        if random.random() > 0.1:
            return True
        else:
            return False


    t = turtle.Turtle()
    wn = turtle.Screen()

    t.shape('turtle')
    while isInScreen(wn,t):
        coin = random.randrange(0,2)
        if coin == 0:              # heads
            t.left(90)
        else:                      # tails
            t.right(90)

        t.forward(50)

    wn.exitonclick()

Agora, temos um programa funcional que desenha um passeio aleatório da
tartaruga que tem 90% de chance de ficar na tela. Estamos em uma boa
posição, visto que uma grande parte do nosso programa está funcionando
e podemos nos concentrar na próxima parte do trabalho - decidir se a
tartaruga está dentro dos limites da tela ou não.

Podemos descobrir a largura e altura da tela usando as funções
``window_width`` e ``window_height`` do objeto *screen* (tela do
computador).  No entanto, lembre-se que a tartaruga começa na posição
0,0, no meio do tela. Por isso, não queremos que a tartaruga siga além
da metade da largura da tela, tanto para a direita quanto para a
esquerda. Nós também não queremos que a tartaruga siga para além da
metade da altura tanto para baixo quanto para cima. Uma vez que nós
sabemos os limites da tela, podemos criar condições para verificar a
posição da tartaruga e retornar ``False`` se a tartaruga está fora ou
``True`` se a tartaruga está dentro.

Uma vez obtidos os limites da tela podemos usar condições que testam a
posição atual da tartaruga para tomar uma decisão. Aqui está uma
implementação:

.. sourcecode:: python

    def isInScreen(wn,t):
        leftBound = - wn.window_width()/2
        rightBound = wn.window_width()/2
        topBound = wn.window_height()/2
        bottomBound = -wn.window_height()/2

        turtleX = t.xcor()
        turtleY = t.ycor()

        estaDentro = True
        if turtleX > rightBound or turtleX < leftBound:
            estaDentro = False
        if turtleY > topBound or turtleY < bottomBound:
            estaDentro = False

        return estaDentro


.. There are lots of ways that the conditional could be written.  In
   this case we have given ``stillIn`` the default value of ``True``
   and use two ``if`` statements to set the value to ``False``.  You
   could rewrite this to use nested conditionals or ``elif``
   statements and set ``stillIn`` to ``True`` in an else clause.
 
Há várias formas de escrever a condição. Nesse caso nós atribuímos a
``estaDentro`` o valor default ``True`` e usamos dois comandos ``if``
para mudar o valor para ``False``. Você pode reescrever essa
verificação para usar condições encaixadas ou comandos ``elif`` e
atribuir ``True`` para ``estaDentro`` usando uma cláusula ``else``.



.. Here is the full version of our random walk program.

Esta é a versão completa do nosso programa de caminhada aleatória.

.. activecode:: iter_randwalk2

    import random
    import turtle
       
    def isInScreen(w,t):
        leftBound = - w.window_width()/2
        rightBound = w.window_width()/2
        topBound = w.window_height()/2
        bottomBound = -w.window_height()/2

        turtleX = t.xcor()
        turtleY = t.ycor()

        stillIn = True
        if turtleX > rightBound or turtleX < leftBound:
            stillIn = False
        if turtleY > topBound or turtleY < bottomBound:
            stillIn = False

        return stillIn

    t = turtle.Turtle()
    wn = turtle.Screen()

    t.shape('turtle')
    while isInScreen(wn,t):
        coin = random.randrange(0,2)
        if coin == 0:
            t.left(90)
        else:
            t.right(90)

        t.forward(50)

    wn.exitonclick()


.. We could have written this program without using a boolean
   function, You might try to rewrite it using a complex condition on
   the while statement, but using a boolean function makes the program
   much more readable and easier to understand.  It also gives us
   another tool to use if this was a larger program and we needed to
   have a check for whether the turtle was still in the screen in
   another part of the program.  Another advantage is that if you ever
   need to write a similar program, you can reuse this function with
   confidence the next time you need it.  Breaking up this program
   into a couple of parts is another example of functional
   decomposition.

Nós poderíamos ter escrito este programa sem usar a função
booleana. Você pode tentar reescrevê-la usando uma condição complexa
no comando while, mas o uso da função booleana torna o programa bem
mais legível e fácil de entender. Isso também nos fornece uma outra
ferramenta para ser usada caso este fosse um programa maior e
precisássemos verificar se a tartaruga ainda se encontra na tela em
alguma outra parte do programa. Uma outra vantagem é que se você
precisar escrever um programa parecido algum dia, você pode reutilizar
esta função com confiança da próxima vez que você precisar
dela. Dividir este programa em partes é um outro exemplo de
decomposição funcional.

.. admonition:: Scratch Editor

    .. actex:: scratch_7_4



.. index:: 3n + 1 sequence  

**Teste seu entendimento**

.. mchoicemf:: test_question7_3_1
   :answer_a: um loop for ou um loop while
   :answer_b: somente um loop for
   :answer_c: somente um loop while
   :correct: a
   :feedback_a: Embora você não saiba quantas iterações serão realizadas antes do programa começar a rodar, depois de escolher um número aleatório, o Python sabe exatamente quantas iterações o loop será realizado, assim tanto o loop for quanto o loop while funcionam.
   :feedback_b: Como você aprendeu na seção 7.2, um loop while pode ser sempre utilizado no lugar de um loop-for.
   :feedback_c: Embora você não saiba quantas iterações serão realizadas antes do programa começar a rodar, depois de escolher um número aleatório, o Python sabe exatamente quantas iterações o loop deve realizar, e portanto este é um exemplo com um número definido de iterações, onde o loop for pode ser utilizado naturalmente.

   Que tipo de loop pode ser usado para realizar a seguinte iteração: você escolhe um número inteiro positivo aleatório e então imprime os números inteiros a partir de 1 até o número escolhido.

..  Which type of loop can be used to perform the following iteration:
     You choose a positive integer at random and then print the
     numbers from 1 up to and including the selected integer.
   
.. mchoicemf:: test_question7_3_2
   :answer_a: Retorna True se a tartaruga ainda está na tela e False se a tartaruga não está mais na tela.
   :answer_b: Usa um loop while para mover a tartaruga aleatoriamente até que ela saia da tela.
   :answer_c: Vira a tartaruga para a direita ou esquerda aleatoriamente e move a tartaruga 50 para frente.
   :answer_d: Calcula e retorna a posição da tartaruga na janela.
   :correct: a
   :feedback_a: A função isInScreen calcula o resultado booleado se a tartaruga ainda está na tela. Ela torna a condição do loop while na parte principal do programa mais simples.
   :feedback_b: A função isInScreen não contém um loop while. Esse loop está fora da função isInScreen.
   :feedback_c: A função isInScreen não move a tartaruga.
   :feedback_d: Embora a função isInScreen utilize o tamanho da janela e a posição da tartaruga, ela não retorna a posição da tartaruga.
   
   No programa de caminhada aleatória exibido nesta seção, o que faz a função "isInScreen"?

..  In the random walk program in this section, what does the
     isInScreen function do?





A sequência 3n + 1
------------------

.. The 3n + 1 Sequence
.. -------------------

Para ilustrar um outro exemplo com número indefinido de iterações,
vamos olhar para uma sequência que tem fascinado matemáticos por
vários anos.

.. As another example of indefinite iteration, let's look at a sequence that has fascinated mathematicians for many years.

A regra para criar a sequência é começar com um dado ``n``, e gerar o
próximo termo da sequência a partir de ``n`` da seguinte forma: se
``n`` for par dividimos ``n`` por 2, ou senão, multiplicamos ``n`` por
3 e somamos 1 quando ``n`` for impar. A sequência termina quando ``n``
se tornar 1.

.. The rule  for creating the sequence is to start from some given ``n``, and to generate the next term of the sequence from ``n``, either by halving ``n``,  whenever ``n`` is even, or else by multiplying it by three and adding 1 when it is odd.  The sequence terminates when ``n`` reaches 1. 

Esta função em Python implementa esse algoritmo. Tente rodar este
programa várias vezes usando valores de n distintos.

.. This Python function captures that algorithm.  Try running this program several times supplying different values for n.

.. activecode:: ch07_indef1
    
    def seq3np1(n):
        """ Print the 3n+1 sequence from n, terminating when it reaches 1."""
        while n != 1:
            print(n)
            if n % 2 == 0:        # n is even
                n = n // 2
            else:                 # n is odd
                n = n * 3 + 1
        print(n)                  # the last print is 1

    seq3np1(3)


    
A condição para loop while é ``n != 1``. Esse loop continuará
executando até que ``n == 1`` (que torna a condição falsa).

.. The condition for this loop is ``n != 1``.  The loop will continue
   running until ``n == 1`` (which will make the condition false).

A cada iteração do loop, o programa imprime o valor de ``n`` e então
verifica se esse valor é par ou ímpar usando o operador resto. Se ele
for par, o valor de ``n`` é dividido por 2 (usando divisão
inteira). Se ele for ímpar, o valor é substituído por ``n * 3 + 1``.
Teste para vários valores de n.

.. Each time through the loop, the program prints the value of ``n``
   and then checks whether it is even or odd using the remainder
   operator. If it is even, the value of ``n`` is divided by 2 using
   integer division. If it is odd, the value is replaced by ``n * 3 +
   1``.  Try some other examples.
    
Como ``n`` às vezes cresce e outras diminui, não há uma prova óbvia de
que ``n`` atinge o valor 1, ou que o programa termina. Para alguns
valores particulares de ``n``, podemos provar a terminação. Por
exemplo, se o valor inicial é uma potência de 2, então o valor de
``n`` será par em todas as iterações do loop até atingir o valor 1.

.. Since ``n`` sometimes increases and sometimes decreases, there is
   no obvious proof that ``n`` will ever reach 1, or that the program
   terminates. For some particular values of ``n``, we can prove
   termination. For example, if the starting value is a power of two,
   then the value of ``n`` will be even each time through the loop
   until it reaches 1.

Você pode se divertir com esse programa tentando encontrar um valor
inicial de n que leve mais de uma centena de iterações para terminar.

.. You might like to have some fun and see if you can find a small
   starting number that needs more than a hundred steps before it
   terminates.


.. admonition:: Lab

    * `Experimenting with the 3n+1 Sequence <../Labs/sequencelab.html>`_ In this guided lab exercise we will try to learn more about this sequence.


A menos de alguns valores particulares, a questão interessante é se
podemos provar que esta sequência termina para *todos* os valores de
``n``. Até hoje, ninguém foi capaz de provar se essa afirmação é
verdadeira ou falsa.

.. Particular values aside, the interesting question is whether we can
   prove that this sequence terminates for *all* values of ``n``. So
   far, no one has been able to prove it *or* disprove it!

Pense cuidadosamente sobre o que seria necessário para provar que a
hipótese *"A sequência 3n+1 converge para 1 para todo inteiro
positivo"*. Usando computadores rápidos, já se testaram todos os
inteiros até um valor bem grande mas, até agora, todos eles acabam
convergindo uma hora para 1. Mas isso não significa que não exista um
inteiro, ainda não testado, que não seja reduzido para 1.

.. Think carefully about what would be needed for a proof or disproof of the hypothesis *"All positive integers will eventually converge to 1"*.  With fast computers we have been able to test every integer up to very large values, and so far, they all eventually end up at 1.  But this doesn't mean that there might not be some as-yet untested number which does not reduce to 1.   


Você vai notar que se você não parar de calcular a sequência quando
ela chega em 1, a sequência entra em um loop: 1, 4, 2, 1, 4, 2, 1, 4,
e assim por diante. Uma possibilidade é que existam outros ciclos que
ainda não foram encontrados e que não contenham o 1.

.. You'll notice that if you don't stop when you reach one, the sequence gets into its own loop:  1, 4, 2, 1, 4, 2, 1, 4, and so on.  One possibility is that there might be other cycles that we just haven't found.  


.. admonition: Choosing between ``for`` and ``while``

dica:: Como escolher entre ``for`` e ``while``
   
   Use um loop ``for`` se você sabe o número de vezes que o corpo do
   loop deve ser executado. Por exemplo, ao varrer uma lista ou quando
   for possível utilizar o iterador ``range``, então escolha o loop
   ``for``.

..   Use a ``for`` loop if you know the maximum number of times that you'll  need to execute the body.  For example, if you're traversing a list of elements,   or can formulate a suitable call to ``range``, then choose the ``for`` loop.

   Assim, qualquer problema como "itere esse modelo meteorológico por 1000 ciclos", ou "procure 
   essa lista de palavras", ou "verifique todos os inteiros até 10000 para ver quais são números primos", o uso do loop ``for`` é melhor. 

..  So any problem like "iterate this weather model run for 1000
     cycles", or "search this list of words", "check all integers up
     to 10000 to see which are prime" suggest that a ``for`` loop is
     best.

   Já quando você precisa repetir o corpo do loop até que uma condição seja satisfeita, 
   como fizemos no problema da sequência 3n+1, você deve usar o loop ``while``

..   By contrast, if you are required to repeat some computation until some condition is 
..   met, as we did in this 3n + 1 problem, you'll need a ``while`` loop. 

   Como dissemos anteriormente, o primeiro caso é chamado de
   **iteração definida** --- nós temos alguns limites definidos do que
   é necessário.  O segundo caso é chamado **iteração indefinida** --
   nós não temos certeza de quantas iterações serão necessárias ---
   nós nem podemos definir um limite superior!

..   As we noted before, the first case is called **definite iteration** --- we have some definite bounds for 
..   what is needed.   The latter case is called **indefinite iteration** --- we are not sure
..   how many iterations we'll need --- we cannot even establish an upper bound!    

   Existem ferramentas de visualização fantásticas que ajudam você a seguir
   o fluxo de execução e a entender pequenos trechos de código em Python.
   Dentre esses sugerímos que você de uma olhada
   em http://netserv.ict.ru.ac.za/python3_viz 

.. There are also some great visualization tools becoming available to help you 
.. trace and understand small fragments of Python code.  The one we recommend is at 
.. http://netserv.ict.ru.ac.za/python3_viz 

.. admonition:: Scratch Editor

    .. actex:: scratch_7_5

.. index::
    single: Newton's method

**Teste seu entendimento**

.. mchoicemf:: test_question7_4_1
   :answer_a: Sim.
   :answer_b: Não.
   :answer_c: Ninguém sabe.
   :correct: c
   :feedback_a: Não há prova de que a sequência 3n+1 termina para qualquer valor de n.
   :feedback_b: Não há contra-prova de que a sequência 3n+1 termina para qualquer valor de n. Em outras palavras, pode existir algum valor de n para o qual essa sequência não termina. Nós apenas não conseguimos encontrá-lo ainda.
   :feedback_c: Como não há prova nem contra-prova de que essa sequência termina, ninguém sabe se o loop while sempre terminará ou não.

   Considere o código que imprime a sequência 3n+1 na caixa
   ActiveCode 6. Será que o loop while nesse programa sempre termina
   para qualquer valor de n?

..  Consider the code that prints the 3n+1 sequence in ActiveCode
     box 6.  Will the while loop in this code always terminate for any
     value of n?



.. Newton's Method
.. ---------------

Método de Newton
----------------

.. Loops are often used in programs that compute numerical results by starting
.. with an approximate answer and iteratively improving it.

Laços são frequentemente utilizados em programas que calculam
resultados númericos partindo de um valor estimado (um chute inicial)
e melhorando o resultado iterativamente.


.. For example, one way of computing square roots is Newton's method.  Suppose
.. that you want to know the square root of ``n``. If you start with almost any
.. approximation, you can compute a better approximation with the following
.. formula:

Um exemplo típico é o método de Newton para o cálculo da raiz quadrada
de ``n``. Começando com um valor qualquer, você pode calcular um valor
mais próximo da raiz quadrada verdadeira usando a seguinte fórmula:

.. sourcecode:: python
    
    melhor =  1/2 * (aprox + n/aprox)

..    better =  1/2 * (approx + n/approx)
    
.. Execute this algorithm a few times using your calculator.  Can you
.. see why each iteration brings your estimate a little closer?  One of the amazing
.. properties of this particular algorithm is how quickly it converges to an accurate
.. answer.    

Execute esse algoritmo algumas vezes usando a sua calculadora. Você
consegue ver por que a cada iteração o valor aproximado fica um pouco
mais perto da solução? Uma das fatásticas propriedades desse algoritmo
em particular é a velocidade com que ele converge para uma resposta
acurada.

.. The following implementation of Newton's method requires two parameters.  The first is the
.. value whose square root will be approximated.  The second is the number of times to iterate the
.. calculation yielding a better result.

A seguinte implementação do método de Newton necessita de 2
parâmetros. O primeiro é o valor cuja raiz quadrada queremos calcular
e o segundo é o número de vezes que desejamos refinar o cálculo para
se obter um resultado melhor.

.. activecode:: chp07_newtonsdef
    
    def newtonSqrt(n, howmany):
        approx = 0.5 * n
        for i in range(howmany):
            betterapprox = 0.5 * (approx + n/approx)
            approx = betterapprox
        return betterapprox

    print(newtonSqrt(10,3))
    print(newtonSqrt(10,5))
    print(newtonSqrt(10,10))


.. You may have noticed that the second and third calls to ``newtonSqrt`` in the previous example both returned the same value for the square root of 10.  Using 10 iterations instead of 5 did not improve the the value.  In general, Newton's algorithm will eventually reach a point where the new approximation is no better than the previous.  At that point, we could simply stop.
.. In other words, by repeatedly applying this formula until the better approximation gets close
.. enough to the previous one, we can write a function for computing the square root that uses the number of iterations necessary and no more.  

Você deve ter notado que a segunda e terceira chamadas para
``newtonSqrt`` no exemplo anterior devolvem o mesmo valor para a raiz
quadrada de 10. Usando 10 iterações ao invés de 5 não melhora o
resultado. Em geral, o algoritmo de Newton vai sempre atingir um ponto
onde a nova aproximação não é melhor que a anterior. Nesse ponto,
poderíamos simplesmente parar.  Em outras palavras, ao aplicar essa
fórmula repetidamente até que uma aproximação fica suficientemente
próxima da anterior, nós podemos escrever uma função para o cálculo da
raiz quadrada que execute apenas o número necessário de iterações e
nada mais.

.. This implementation, shown in codelens,
.. uses a ``while`` condition to execute until the approximation is no longer changing.  Each time thru the loop we compute a "better" approximation using the formula described earlier.  As long as the "better" is different, we try again.  Step thru the program and watch the approximations get closer and closer.

A seguinte implementação, feita em codelens, usa um comando ``while``
para repetir até que a aproximação não mude mais. A cada execução do
laço nós computamos uma aproximação ``melhor`` usando a fórmula
descrita anteriormente. Enquanto o ``melhor`` for diferente, nós
continuamos o processo. Execute o programa passo-a-passo e veja a
aproximação ficar cada vez mais próxima da solução.

.. codelens:: chp07_newtonswhile
    
    def newtonSqrt(n):
        approx = 0.5 * n
        better = 0.5 * (approx + n/approx)
        while  better !=  approx:
            approx = better
            better = 0.5 * (approx + n/approx)
        return approx

    print(newtonSqrt(10))

.. note::

	O comando ``while`` mostrado acima compara dois números reais
	na condição. Como os números reais no computador (usando ponto
	flutuante) são eles mesmos aproximações de números reais na
	matemática, em geral é melhor comparar se os resultados estão
	próximos, dentro de um pequeno intervalo ao redor do resultado
	que você procura.

.. 	The ``while`` statement shown above uses comparison of two floating point numbers in the condition.  Since floating point numbers are themselves approximation of real numbers in mathematics, it is often
..	better to compare for a result that is within some small threshold of the value you are looking for.












.. index:: algoritmo 


.. admonition:: Scratch Editor

    .. actex:: scratch_7_6


Revisão de Algoritmos
---------------------

O método de Newton é um exemplo de um **algoritmo**: é um processo
mecânico para resolver uma categoria de problemas (neste caso, o
cálculo de raízes quadradas).

Não é fácil definir um algoritmo. Talvez seja mais simples começar com
algo que não seja um algoritmo. Quando você aprendeu a multiplicar
números de um dígito, você provavelmente memorizou a tabela de
multiplicação. Na verdade, você memorizou 100 soluções
específicas. Esse tipo de conhecimento não é algoritmico.

Mas se você fosse preguiçoso, você poderia ter trapaceado aprendendo
alguns truques. Por exemplo, para encontrar o produto de n e 9, você
pode escrever n - 1 como o primeiro dígito e 10 - n como o segundo
dígito. Este truque é uma solução geral para multiplicar qualquer
número de um dígito por 9. Isso é um algoritmo!

Da mesma forma, as técnicas que você aprendeu para adição com
transporte, subtração com empréstimos e divisão longa são todos
algoritmos. Uma característica de algoritmos é que eles não requerem
nenhuma inteligência para executar. Eles são processos mecânicos em
que cada passo segue o anterior de acordo com um conjunto simples de
regras.

Por outro lado, o entendimento de que problemas difíceis podem ser
resolvidos por algoritmos passo-a-passo é um dos grandes avanços
simplificadores que trouxe enormes benefícios. Assim, embora a
execução de um algoritmo possa ser chata e não requeira inteligência,
o racioncínio algorítmico ou computacional causou um grande impacto. É
o processo de concepção de algoritmos que é interessante,
intelectualmente desafiador e uma parte central do que chamamos de
programação.

Algumas coisas que as pessoas fazem naturalmente, sem dificuldade ou
pensamento consciente, são as mais difíceis de expressar através de
algoritmos. Entendimento de linguagem natural é um bom exemplo. Todos
nós fazemos isso, mas até agora ninguém foi capaz de explicar *como* o
fazemos, pelo menos não na forma de um algoritmo passo-a-passo.



.. index:: tabela, logaritmo, Intel, Pentium, sequência de escape, tab, newline,
           cursor

.. admonition:: Scratch Editor

    .. actex:: scratch_7_7


Tabelas Simples
---------------

Os comandos de repetição (laços) são muito úteis na geração de dados
tabulares.  Antes da invenção dos computadores, as pessoas tinham que
calcular logaritmos, senos e cossenos e outras funções matemáticas
manualmente.  Para facilitar essas tarefas, livros de matemática
continham longas tabelas com os valores dessas funções.  A criação das
tabelas era um processo lento e chato, e era comum encontrar vários
erros.

Quando os computadores apareceram em cena, uma das reações iniciais
foi, *"Isso é ótimo! Podemos usar os computadores para gerar as
tabelas, então não haverá erros."* Que acabou por ser verdade (na
maioria dos casos), mas míope. Logo depois, computadores e
calculadoras ficaram tão comuns que as tabelas se tornaram obsoletas.

Bem, quase. Para algumas operações, os computadores usam tabelas de
valores para obter uma resposta aproximada e, em seguida, executar
cálculos para melhorar a aproximação.  Em alguns casos, houve erros
nas tabelas de base, mais notoriamente na tabela do chip do
processador Intel Pentium usado para realizar a divisão de ponto
flutuante.

Apesar de uma tabela de potências de 2 não seja mais tão útil como já
fora, ela ainda é um bom exercício de iteração.  O seguinte programa
gera uma sequência de valores na coluna da esquerda e 2 elevado à
potência daquele valor na coluna da direita:

.. activecode:: ch07_table1

    print("n",'\t',"2**n")     #table column headings
    print("---",'\t',"-----")   
 
    for x in range(13):        # generate values for columns
        print(x, '\t', 2**x)

O string ``'\t'`` representa um **caractere de tabulação** (ou
**tab**). A barra invertida em ``'\t'`` indica o início de uma
**sequência de escape**. As sequências de escape são usados para
representar caracteres invisíveis, como tabs e mudanças de linhas. A
sequência ``\n`` representa uma **nova linha**.

Uma sequência de escape pode aparecer em qualquer lugar em uma string. Neste exemplo, o sequência de escape para tab é a única coisa na string. 
seqüência de escape é a única coisa na cadeia. Como você acha que 
uma barra invertida é representada em uma string?

Como caracteres e strings são exibidos na tela, um marcador invisível
chamado de **cursor** mantém o controle de onde o próximo cararactere é inserido. Depois de uma função ``print``, o cursor normalmente vai para o início da próxima
linha.

O caractere tab desloca o cursor para a direita até que ele atinja uma
das colunas de tabulação. Tabs são úteis para fazer colunas de texto
alinhadas, como na saída do programa anterior.  Devido ao caractere de
tabulação entre as colunas, a posição da segunda coluna não depende do
número de dígitos na primeira coluna.

.. admonition:: Scratch Editor

    .. actex:: scratch_7_8



.. index::
    single: variável local
    single: variável; local

**Teste seu entendimento**

.. mchoicemf:: test_question7_7_1
  :answer_a: Um tab vai alinhar itens na segunda coluna de tabulação, independentemente do número de caracteres colocados na primeira coluna, enquanto espaços não garantem que os itens fiquem alinhados.
  :answer_b: Não há diferença.
  :answer_c: Um tab é mais largo que uma sequência de espaços.
  :answer_d: Você deve usar tabs para criar tabelas. Você não pode usar espaços.
  :correct: a
  :feedback_a: Assumindo que o número de caracteres inseridos na primeira coluna seja sempre menor que um tab.
  :feedback_b: Tabs e espaços fazem, às vezes, com que as saídas seja visualmente diferentes. 
  :feedback_c: Um tab tem uma largura pré-definida que equivale a um dado número de espaços.
  :feedback_d: Você pode utilizar espaços para criar tabelas. As colunas podem parecer desalinhadas dependendo do número de itens em cada coluna.
  
  Qual a diferença entre um tab (\t) e uma sequência de espaços? 

Iteração Bidimensional: Processamento de Imagens
-------------------------------------------------

Tabelas bidimensionais (com 2 dimensões) possuem linhas e
colunas. Você provavelmente já viu muitas tabelas assim se você tiver
usado um programa de planilha eletrônica. Um outro objeto que pode ser
organizado em linhas e colunas é uma imagem digital. Nesta seção vamos
explorar como manipular essas imagens de forma iterativa.

Uma **imagem digital** é um conjunto finito de pequenos elementos discretos de imagem chamados de **pixels**. Estes pixels são organizados numa grade bidimensional. Cada pixel representa a menor quantidade de informação sobre a imagem 
disponível. Uma imagem de boa qualidade tem grande densidade de pixels, então cada pixel aparece como um pequeno "ponto".

Cada imagem (grade de pixels) tem a sua própria largura e sua própria altura. A largura é o número de colunas e a altura é o número de linhas. Podemos indicar um pixel na grade pelo número da coluna e número da linha (como uma coordenada). No entanto, é muito importante lembrar
que os cientistas da computação gostam de começar a contar do 0! Isso significa que, se há 20 linhas, elas serão nomeados 0,1,2, e assim por diante até 19. Isso será muito útil mais tarde, quando usarmos `range` para iterar.

Na figura abaixo, o pixel de interesse se encontra na coluna **c** e linha **r**.
.. image:: Figures/image.png

O Modelo de Cor RGB
^^^^^^^^^^^^^^^^^^^

Cada pixel da imagem representa uma única cor. A cor específica
depende de uma fórmula que mistura quantidades de três cores básicas:
vermelho, verde e azul. Esta técnica para a criação de cor é conhecido
como o **modelo de cor RGB** (RGB do inglês Red - vermelho, Green -
verde e Blue - azul).  A quantidade de cada cor básica, às vezes
chamada de **intensidade da cor**, nos permite ter um controle muito
fino sobre a cor resultante.

O valor mínimo de intensidade para uma cor básica é 0. Por exemplo, se
a intensidade da cor vermelha é 0, então não há vermelho no pixel. O
valor máximo de intensidade é 255. Isto significa que há realmente 256
valores diferentes de intensidade para cada cor básica. Como há três
cores básicas, isso significa que você pode criar 256\ :sup:`3` cores
distintas, utilizando o modelo de cor RGB.


Aqui estão as intensidades de vermelho, verde e azul para algumas
cores comuns. Observe que "Black" é representado por um pixel sem
nenhuma cor básica (intensidade 0). Por outro lado, o "White" tem
valores máximos para todos os três componentes de cores básicas.

	=======  =======  =======  =======
	Cor      Red      Green    Blue
	=======  =======  =======  =======
	Red      255      0        0
	Green    0        255      0
	Blue     0        0        255
	White    255      255      255
	Black    0        0        0
	Yellow   255      255      0
	Magenta  255      0        255
	=======  =======  =======  =======

A fim de manipular uma imagem, temos de ser capazes de acessar pixels
individuais. Esta capacidade é fornecida pelo um módulo chamado
**image**. O módulo image define duas classes: ``Image`` e ``Pixel``.

Cada objeto Pixel tem três atributos: a intensidade do vermelho
(componente Red), do verde (Green) e do azul (Blue). Um pixel fornece
três métodos que nos permite pedir os valores de intensidade. Eles são
chamados de ``getRed``, ``getGreen``, e ``getBlue``. Além disso,
podemos pedir a um pixel para alterar um valor de intensidade usando
os métodos ``setRed``, ``setGreen``, e ``setBlue``.


    ============  ================            ===============================================
    Método        Exemplo                     Comentário
    ============  ================            ===============================================
    Pixel(r,g,b)  Pixel(20,100,50)            Cria um novo pixel com R=20, G=100, e B=50
    getRed()      r = p.getRed()              Retorna a intensidade do componente red.
    getGreen()    r = p.getGreen()            Retorna a intensidade do componente green.
    getBlue()     r = p.getBlue()             Retorna a intensidade do componente blue.
    setRed()      p.setRed(100)               Muda o valor de red para 100.
    setGreen()    p.setGreen(45)              Muda o valor de green para 45.
    setBlue()     p.setBlue(156)              Muda o valor de blue para 156.
    ============  ================            ===============================================

No exemplo abaixo, primeiro criamos um pixel com 45 unidades de
vermelho, 76 unidades de verde, e 200 unidades de azul.  Em seguida,
imprimimos a quantidade atual de vermelho, alteramos a quantidade de
vermelho e, finalmente, definimos a quantidade de azul para ser a
mesma que a quantidade atual de verde.

.. activecode::  pixelex1a
    
    import image

    p = image.Pixel(45,76,200)
    print(p.getRed())
    p.setRed(66)
    print(p.getRed())
    p.setBlue(p.getGreen())
    print(p.getGreen(), p.getBlue())

**Teste seu entendimento**

.. mchoicemf:: test_question7_8_1_1
   :answer_a: Vermelho escuro
   :answer_b: Vermelho claro
   :answer_c: Verde escuro
   :answer_d: Verde claro
   :correct: a
   :feedback_a: Como todos os valores estão perto de 0, a cor deve ser escura. Como o valor do vermelho é maior que os demais, o pixel deve aparecer vermelho.
   :feedback_b: Quanto mais próximos do 0, mais escura será a cor.
   :feedback_c: O primeiro valor no modelo RGB é o vermelho. O segundo é o verde. Portanto essa cor não possui verde.
   :feedback_d: O primeiro valor no modelo RGB é o vermelho. O segundo é o verde. Portanto essa cor não possui verde.
  
   Se você tem um pixel cujo valor RGB é (20, 0, 0), qual a cor desse pixel?

Objetos Image
^^^^^^^^^^^^^

Para acessar os pixels em uma imagem real, precisamos primeiro criar
um objeto ``Image``. Objetos Image podem ser criados de duas
maneiras. Em primeiro lugar, um objeto Image pode ser construído a
partir de arquivos que armazenam imagens digitais. O objeto Image tem
um atributo correspondente à largura, à altura e à coleção de pixels
da imagem.

É também possível criar um objeto Image que seja "vazio" (empty em
inglês). Um objeto ``EmptyImage`` tem uma largura e uma altura. No
entanto, a coleção de pixels é composta por pixels todos "White"
(brancos).

Podemos pedir a um objeto Image para retornar seu tamanho usando os
métodos ``getWidth`` e ``getHeight``. Nós também podemos obter um
pixel de um local específico na imagem usando ``getPixel`` e mudar o
pixel em um determinado local usando ``setPixel``.


A classe Image é mostrada abaixo. Observe que as duas primeiras
entradas mostram como criar objetos de imagem. Os parâmetros são
diferentes dependendo se você estiver usando um arquivo de imagem ou
criando uma imagem vazia.

    =================== =============================== ==================================================
    Método              Example                         Comentário
    =================== =============================== ==================================================
    Image(filename)     img = image.Image("cy.png")     Cria um objeto Image do arquivo cy.png.
    EmptyImage()        img = image.EmptyImage(100,200) Cria um objeto Image com todos os pixels brancos
    getWidth()          w = img.getWidth()              Retorna a largura da imagem em pixels. 
    getHeight()         h = img.getHeight()             Retorna a altura da imagem em pixels.
    getPixel(col,row)   p = img.getPixel(35,86)         Retorna o valor do pixel da coluna 35 e linha 86.
    setPixel(col,row,p) img.setPixel(100,50,mp)         Muda o valor do pixel na coluna 100 e linha 50 para mp.
    =================== =============================== ==================================================

Considere a imagem mostrada abaixo. Suponha que a imagem é armazenada
em um arquivo chamado "luther.jpg". A linha 2 abre o arquivo e usa o
conteúdo para criar um objeto Image que é referenciado por
``img``. Uma vez que temos um objeto Image, podemos usar os métodos
descritos acima para acessar informações sobre a imagem ou para obter
o valor de pixel e verificar suas intensidades de cores básicas.



.. raw:: html

    <img src="../_static/LutherBellPic.jpg" id="luther.jpg">


.. activecode::  pixelex1

    import image
    img = image.Image("luther.jpg")

    print(img.getWidth())
    print(img.getHeight())

    p = img.getPixel(45,55)
    print(p.getRed(), p.getGreen(), p.getBlue())


Quando você roda o programa você pode ver que a imagem tem 400 pixels
de largura e 244 pixels de altura. Além disso, o pixel da coluna 45,
linha 55, tem valores RBG de 165, 161 e 158. Experimente algumas
outras posições de pixel trocando os argumentos de ``getPixel`` e
rodando o programa novamente.

**Teste seu entendimento**

.. mchoicemf:: test_question7_8_2_1
   :answer_a: 149 132 122
   :answer_b: 183 179 170
   :answer_c: 165 161 158
   :answer_d: 201 104 115
   :correct: a
   :feedback_a: Correto, os valores RGB são 149 132 122 na linha 100 e coluna 30.
   :feedback_b: Esses são os valores para o pixel na linha 30, coluna 100. Pegue os valores para a linha 100 e coluna 30 usando p=img.getPixel(100,30).
   :feedback_c: Esses são os valores do exemplo original (linha 45, coluna 55). Pegue os valores para a linha 100 e coluna 30 usando p=img.getPixel(100,30).
   :feedback_d: Esses valores foram inventados que podem ou não estarem na imagem. Pegue os valores para a linha 100 e coluna 30 usando p=img.getPixel(100,30).
  
   No exemplo 10 do ActiveCode, quais são os valores dos componentes RGB do pixel na linha 100, coluna 30?
   

Processamento de imagem e iteração encaixada
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

O **processamento de imagem** refere-se à capacidade de manipular os
pixels individuais de uma imagem digital. A fim de processar todos os
pixels, é preciso ser capaz de visitar sistematicamente todas as
linhas e colunas da imagem. A melhor maneira de fazer isso é usando
uma **iteração encaixada**.

Iteração encaixada simplesmente significa que vamos colocar uma
iteração (comando de repetição ou laço) dentro de outra. Vamos chamar
essas iterações de **iteração exterior** e **iteração interior**.
Para ver como isso funciona, considere a iteração simples abaixo.

.. sourcecode:: python

    for i in range(5):
       print(i)

Vimos isso várias vezes para saber que o valor de ``i`` será 0, em
seguida, 1, depois 2, e assim sucessivamente até a 4.  O ``print``
será realizada uma vez para cada passagem.  No entanto, o corpo do
laço pode conter quaisquer afirmações incluindo outra iteração (outra
indicação ``for``). Por exemplo,

.. sourcecode:: python

    for i in range(5):
       for j in range(3):
            print(i,j)

O ``for i`` é a iteração exterior e o ``for j`` é a iteração
interior. Cada passagem da iteração externa irá resultar na
transformação completa da iteração interna do começo ao fim. Isto
significa que a saída da iteração encaixada vai mostrar que para cada
valor de ``i``, todos os valores de ``j`` vão ocorrer.

Aqui está o mesmo exemplo em activecode. Experimente. Note que o valor
de ``i`` permanece o mesmo enquanto o valor de ``j`` muda. A iteração
interna, de fato, está se movendo mais rápido do que a iteração
exterior.

.. activecode:: nested1

    for i in range(5):
       for j in range(3):
            print(i,j)

Outra maneira de ver isso com mais detalhes é examinar o comportamento
usando o codelens. Siga passo-a-passo através das iterações para ver o
fluxo de controle à medida que iteração encaixada avança. Mais uma
vez, para cada valor de ``i``, todos os valores de ``j`` vão
ocorrer. Você pode ver que a iteração interna completa antes de ir
para o próximo passo da iteração externa.

.. codelens:: nested2

    for i in range(5):
       for j in range(3):
            print(i,j)

Nosso objetivo com o processamento de imagem é visitar cada
pixel. Usaremos uma iteração para processar cada `linha`. Dentro dessa
iteração, vamos usar uma iteração encaixada para processar cada
`coluna`. O resultado é uma iteração encaixada, semelhante ao visto
acima, onde o laço do ``for`` exterior processa as linhas, a partir de
0 até (mas não incluindo) a altura da imagem.  O laço do ``for``
interior vai processar cada coluna de uma linha, novamente a partir de
0 até (mas não incluindo) a largura da imagem.

O código resultante será parecido com o seguinte. Agora nós estamos livres para fazer qualquer coisa que desejamos cada pixel da imagem.

.. sourcecode:: python

	for col in range(img.getWidth()):
	    for lin in range(img.getHeight()):
	        #faça algo com o pixel na posição (col,lin)
	
Um dos mais fáceis algoritmos de processamento de imagem serve para
criar o que é conhecido como imagem **negativa**. A imagem negativa
significa simplesmente que cada pixel será o `oposto` do que era
originalmente. Mas o que significa oposto?

No modelo de cor RGB, podemos considerar o oposto do componente
vermelho como a diferença entre o vermelho original e 255. Por
exemplo, se o componente vermelho original 50, então o oposto, ou
valor vermelho negativo seria `` 255-50`` ou 205. Em outras palavras,
os pixels com um monte de vermelho terá negativos com pouco vermelho e
pixels com pouco vermelho terá negativos com um monte. Nós fazemos o
mesmo para o azul e o verde também.

O programa abaixo implementa este algoritmo usando a imagem
anterior. Execute o programa para ver a imagem negativa
resultante. Note que há um monte de processamento ocorrendo e isso
pode demorar alguns segundos para ser concluído. Além disso, aqui
estão duas outras imagens que você pode usar. Altere o nome do arquivo
na chamada ``image.Image ()`` para ver como essas imagens se parecem
com negativos. Além disso, observe que há uma chamada do método
``exitonclick`` no final que irá fechar a janela quando você clica
nela. Isso permitirá que você "limpe a tela" antes de desenhar o
próximo negativo.

.. raw:: html

    <img src="../_static/cy.png" id="cy.png">
    cy.png

.. raw:: html

    <img src="../_static/goldygopher.png" id="goldygopher.png">
    goldygopher.png



.. activecode::  acimg_1

    import image

    img = image.Image("luther.jpg")
    newimg = image.EmptyImage(img.getWidth(),img.getHeight())
    win = image.ImageWin()

    for col in range(img.getWidth()):
        for lin in range(img.getHeight()):
           p = img.getPixel(col,lin)    

           newred = 255-p.getRed()    
           newgreen = 255-p.getGreen()
           newblue = 255-p.getBlue()

           newpixel = image.Pixel(newred,newgreen,newblue)

           newimg.setPixel(col,lin,newpixel)

    newimg.draw(win)
    win.exitonclick()

Vamos dar uma olhada no código. Depois de importar o módulo image,
criamos dois objetos Image. O primeiro, ``img``, representa uma foto
digital típica. A segunda, ``newimg``, é uma imagem vazia que será
"preenchida" a medida que nós processamos a imagem original pixel a
pixel. Note que a largura e altura da imagem vazia são definidas
usando os mesmos valores correspondentes da imagem original.

As linhas 8 e 9 criam a iteração encaixada que discutimos
anteriormente. Isto nos permite processar cada pixel na imagem. A
linha 10 recebe um pixel individual.

As linhas 12-14 criam os valores de intensidade negativa extraindo os
valores da intensidade original e subtraindo de 255. Uma vez que temos
os valores ``newred``, ``newgreen``, e ``newblue``, podemos criar um
novo pixel (Linha 16).

Finalmente, é preciso inserir o novo pixel na imagem vazia no local
correspondente ao pixel original da foto digital.

.. admonition:: Outra manipulação de pixel

	Há um grande número de diferentes algoritmos de processamento
	de imagem que seguem o mesmo padrão como mostrado acima. Ou
	seja, tomar o pixel original, extrair as intensidades de
	vermelho, verde e azul e, em seguida, criar um pixel novo a
	partir desses valores. O pixel novo é inserido uma imagem
	vazia no local correspondente ao original.

	Por exemplo, você pode criar um pixel em **escala de cinza**
	pela média das intensidades de vermelho, verde e azul e, em
	seguida, usar esse valor para todas as intensidades.

	A partir da escala de cinza você pode criar uma imagem
	**binária** definindo um limiar e inserindo um pixel branco ou
	um pixel preto na imagem vazia dependendo se o nível de cinza
	é maior ou menor que o limiar.

	Você também pode fazer um pouco de aritmética complexa e criar efeitos interessantes, como
	`Sepia Tone <http://en.wikipedia.org/wiki/Sepia_tone#Sepia_toning>`_

.. admonition:: Scratch Editor

    .. actex:: scratch_7_9


Você acabou de passar um ponto muito importante em seu estudo de
programação Python. Embora ainda haja um caminho longo a percorrer,
você aprendeu todos os blocos de construção básicos que são
necessários para resolver muitos problemas interessantes. Sob o ponto
de vista de algoritmos, agora você pode implementar programas com
seleção e iteração. Você também pode resolver problemas ao dividi-los
em partes menores, escrevendo funções para essas partes e, em seguida,
chamar as funções para concluir a implementação.  Resta ainda ver
maneiras de melhorar as formas de representação de problemas em termos
de dados que nós manipulamos. Agora vamos voltar nossa atenção para
estudar as principais estruturas de dados fornecidas pelo Python.

**Teste seu entendimento**

.. mchoicemf:: test_question7_8_3_1
   :answer_a: Saída a
   :answer_b: Saída b
   :answer_c: Saída c
   :answer_d: Saída d
   :correct: a
   :feedback_a: i começa com o valor 0 e então j itera de 0 a 1. Em seguida, i recebe 1 e j itera de 0 a 1. Finalmente, i recebe 2 e j itera de 0 a 1.
   :feedback_b: O laço for interno controla o segundo dígito (j). O laço for deve ser concluído antes que o laço externo possa avançar.
   :feedback_c: O laço for interno controla o segundo dígito (j). Note que o laço for interno percorre a lista [0, 1].
   :feedback_d: O laço for externo itera 3 vezes (0, 1, 2) e o laço interno roda duas vezes para cada iteração do laço externo. Então esse programa imprime 6 linhas exatamente. 
  
   O que a seguinte iteração encaixada vai imprimir? (Nota: se você estiver com dificuldade nessa questão, reveja CodeLens 3).
    <pre>
    for i in range(3):
      for j in range(2):
        print(i,j)  
    </pre>
    a.
    <pre>
    0	0
    0	1
    1	0
    1	1
    2	0
    2	1
    </pre>
    b.
    <pre>
    0   0
    1   0
    2   0
    0   1
    1   1
    2   1
    </pre>
    c. 
    <pre>
    0   0
    0   1 
    0   2
    1   0 
    1   1
    1   2
    </pre>
    d.
    <pre>
    0   1
    0   1
    0   1 
    </pre>


.. mchoicemf:: test_question7_8_3_2
   :answer_a: Seria uma versão avermelhada da imagem do sino.
   :answer_b: Seria um retângulo vermelho sólido de mesmo tamanho da imagem original
   :answer_c: Seria a mesma imagem originalimage
   :answer_d: Seria a mesma que a imagem negativa 
   :correct: a
   :feedback_a: Como estamos removendo os componentes verde e azul, mas mantendo as variações do componente vermelho, obteríamos a mesma imagem, mas avermelhada.
   :feedback_b: Como o valor de vermelho varia de pixel para pixel, a imagem não seria um vermelho sólido. Para ser sólido, todos os pixels deveriam receber o mesmo valor de vermelho.
   :feedback_c: Ao remover o azul e o verde dos pixels, a imagem ficará diferente, mesmo que a imagem original não aparente ter cores verde e azul (lembre-se que outras cores são formadas pela combinação de vermelho, verde e azul).
   :feedback_d: Como nós mudamos os valores dos pixels de forma diferente do código anterior, a imagem resultante não será igual a imagem negativa.
  
   Qual seria a imagem produzida pelo programa da caixa 12 do ActiveCode ao substituir as linhas:
   <pre>
   newred = 255-p.getRed()
   newgreen = 255-p.getGreen()
   newblue = 255-p.getBlue()
   </pre>
   pelas linhas:
   <pre>
   newred = p.getRed()
   newgreen = 0
   newblue = 0
   </pre>




Glossário
---------

.. glossary::


    algoritmo
        Um processo passo-a-passo para resolver uma categoria de problemas.

    contador
        Uma variável usada para contar algo, em geral inicializada com zero e
	incrementada no corpo de um laço.
	
    corpo
        Os comandos dentro de um laço.
        
    cursor
        Um marcador invisível que guarda a posição onde o próximo caracter
	deve ser inserido. 
	
    generalizar
        Substituir algo muito específico (como o valor de uma constante)
	por algo apropriadamente mais genérico (como uma variável ou parâmetro).
	A generalização torna o código mais versátil, melhora as chances dele ser
	reusado e, às vezes, até mais fácil de escrever.

    iteração
        Execução repetida de um conjunto de comandos de programação.

    iteração definida
        Um laço que possui um limite superior no número de vezes que
	seu corpo será executado. Uma iteração definida é melhor
	implementada, em geral, usando um comando ``for``.
        

    iteração indefinida
        Um laço que se repete até que alguma condição seja encontrada.
	Um comando ``while`` é mais apropriado nesses casos.

    laço
        Um comando ou grupo de comandos executados repetidamente até que
	uma condição de parada seja satisfeita.

    
    laço encaixado
        Um laço dentro do corpo de outro laço.
    
    laço infinito
        Uma laço cuja condição de parada nunca é satisfeita.
	
    newline
        Um caractere especial que faz o cursor se mover para
	o início da linha seguinte. 
        
        
    reatribuição
        Fazer mais de uma atribuição para a mesma variável
	durante a execução do programa.

    sequencia de escape
        Um caractere de escape, \\, seguido de um ou mais caracteres é usado
	para representar um caractere que não é impresso (não é visível no texto).
     
    tab
        Um caractere especial que faz o cursor se mover para a próxima
	coluna de tabulação na linha atual.
        
    variável do laço
        Uma variável usada como parte da condição de parada do laço
     

        
Exercícios
----------

Este capítulo nos mostrou como somar uma lista de itens e como contar
itens. O exemplo de contagem também usou um comando ``if`` que nos
permite contar apenas itens selecionados. No capítulo anterior vimos
também uma função ``find_first_2_letter_word`` que nos permite uma
"saída precoce" de dentro de um laço usando ``return`` quando alguma
condição se torna verdadeira.  Agora, também temos ``break`` para sair
de um laço (mas não da função), e ``continue`` para abandonar a
iteração atual do laço sem terminar o laço.

A composição de percorrer listas, somar, contar, testar condições e
saída precoce é uma rica coleção de blocos de construção que podem ser
combinados de maneiras poderosas para criar muitas funções que são
todas um pouco diferentes.

As seis primeiras questões são sobre funções típicas você deve ser
capaz de escrever usando apenas esses blocos de construção.

   
#. Adicione uma chamada para a função print à função ``sqrt`` de Newton
   para imprimir a palavra ``melhor`` toda vez que uma nova raiz é calculada.
   Chame a sua função modificada usando 25 como argumento e veja os resultados.

    .. actex:: ex_7_7

   
#. Escreva uma função ``print_triangular_numbers(n)`` que imprime os n primeiros
   números triangulares. Uma chamada da forma
   ``print_triangular_numbers(5)`` deve produzir a seguinte saída::
     
       1       1
       2       3
       3       6
       4       10
       5       15

   (*dica: faça uma busca na internet para saber o que é um número triangular.*)
   
   .. actex:: ex_7_8

   
#. Escreva uma função ``is_prime``, que recebe um único argumento inteiro e
   retorna ``True`` quando o argumento é um *número primo* e ``False``
   em caso contrário.
   
    .. actex:: ex_7_9


#. Modifique o programa Random turtle walk para que a tartaruga de meia volta
   quando ela bate na parede e volte na outra direção.
   Esse comportamento de bate e volta deve se repetir até que a tartaruga bata
   4 vezes na parede.

    .. actex:: ex_7_12

#. Modifique o programa anterior para que você tenha 2 tartarugas, cada uma
   com uma posição inicial aleatória. Faça as tartarugas se moverem, batendo
   nas paredes e voltando, até que as duas tartarugas colidam entre si.
   
    .. actex:: ex_7_13

#. Modifique o programa anterior para que, ao invés de virar para a esquerda
   ou direita, o ângulo de virada seja determinado aleatóriamente a cada passo.
   Quando a tartaruga bate na parede, você deve calcular o ângulo correto
   de reflexão.

    .. actex:: ex_7_14

#. Escreva uma função para remover todo o vermelho de uma imagem RGB.

    .. actex:: ex_7_15

#. Escreva uma função para converter uma imagem RGB para níveis de cinza.

    .. actex:: ex_7_16

#. Escreva uma função para converter uma imagem RGB para binária.
  
    .. actex:: ex_7_17

#. Sepia é um efeito que torna uma imagem RGB amarronzada, dando a impressão de foto antiga.
   A fórmula para criar esse efeito é a seguinte:

   .. sourcecode:: python
   
        newR = (R × 0.393 + G × 0.769 + B × 0.189)
        newG = (R × 0.349 + G × 0.686 + B × 0.168)
        newB = (R × 0.272 + G × 0.534 + B × 0.131)

   Escreva uma função para converter uma imagem para sepia.
   *Dica:* lembre que os valores rgb devem ser inteiros entre 0 e 255.
 
    .. actex:: ex_7_18

#. Escreva uma função para reduzir ou aumentar uma imagem de forma uniforme.
   Sua função deve receber uma imagem e um fator de escala. Para reduzir a
   imagem, o fator de escala deve estar no intervalo 0 e 1. Para aumentar a
   imagem, o fator de escala deve ser maior que 1.

    .. actex:: ex_7_19

#. Escreva uma função para rotacionar uma imagem. Sua função deve receber uma imagem
   e um ângulo em graus. O ângulo de rotação pode ser positivo ou negativo e deve ser
   múltiplo de 90 graus.

    .. actex:: ex_7_20

#. Após escalar uma imagem por um fator de escala grande a imagem parece quadriculada.
   Uma forma de reduzir esse efeito de blocos na imagem é substituir cada pixel com
   a média dos valores dos pixels ao seu redor. O efeito disso é suavizar as mudanças
   na cor. Escreva uma função que recebe uma imagem como parâmetro e retorna a imagem
   suavizada. 
   
    .. actex:: ex_7_21

#. Quando você digitaliza uma foto usando um escaneador, a imagem escaneada pode
   ter muito ruído devido a particulas de poeira (na foto e/ou no escaner),
   danificando a imagem. Uma forma de eliminar esse ruído é substituir cada pixel
   pela mediana dos pixels vizinhos.

    .. actex:: ex_7_22

#. Pesquise sobre o algoritmo de detecção de bordas de Sobel e implemente-o.

    .. actex:: ex_7_23

.. toctree::
    :hidden:

    ../Labs/sequencelab
