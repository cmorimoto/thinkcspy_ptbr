Glossário
---------

.. glossary::

    caso básico
        Um ramo da instrução condicional em uma função recursiva que
        não dá origem a novas chamadas recursivas.

    tipo de dado imutável
        Um tipo de dado que não pode ser modificado. Atribuições a elementos ou
        fatias de tipos imutáveis causam um erro de execução.

    recursão infinita
        Uma função que chama a si mesma de forma recursiva, sem nunca
	atingir o caso básico. Eventualmente, uma recursão infinita
	causa um erro de execução. 

    tipo de dado mutável
        Um tipo de dado que pode ser modificado. Todos os tipos
	mutáveis são tipos compostos. As listas e dicionários (ver
	próximo capítulo) são tipos de dados mutáveis. Strings e
	tuplas não são.

    recursão
        O processo de chamar a função que já está em execução.

    chamada recursiva
        O comando que chama uma função já em execução. A recursão pode
        mesmo ser indireta --- função `f` pode chamar `g` que chama `h`,
        e `h` poderia fazer uma chamada de volta para `f`.

    definição recursiva
        Uma definição que define algo em termos de si mesmo. Para ser útil
        ele deve incluir *casos básicos* que não são recursivos. Desta maneira
        difere de uma *definição circular*. Definições recursivas muitas vezes
        fornecem uma maneira elegante de expressar estruturas de dados complexas.



Exercícios de programação
-------------------------

#. Escreva uma função recursiva que calcula o fatorial de um número.

   .. actex:: ex_rec_1

#. Escreva uma função recursiva para inverter uma lista.

   .. actex:: ex_rec_2
   
#. Modifique o programa de árvore recursiva utilizando algumas (ou todas) das
   seguintes idéias:

   - Modifique a espessura dos ramos de modo que à medida que ``branchLen``
     fica menor, a linha fica mais fina.

   - Modifique a cor dos ramos de modo que quando ``branchLen`` ficar
     muito curto ele seja colorido como uma folha.

   - Modifique o ângulo utilizado para virar a tartaruga para que em
     cada ramo de bifurcação o ângulo seja selecionado aleatoriamente
     dentro de algum intervalo. Por exemplo, experimente o intervalo
     entre 15 e 45 graus. Modifique esses valores até encontrar algo 
     que pareça bom.

   - Modifique o ``branchLen`` recursivamente, de modo que em vez de sempre
     subtrair a mesma quantidade, subtraia uma quantidade aleatória
     dentro de algum intervalo.

   Se você implementar todas as idéias acima, você vai obter desenhos
   mais realistas de árvores.
   
   .. actex:: ex_rec_3

#. Encontre ou invente um algoritmo para desenhar uma montanha
   fractal. Dica: uma maneira possível é usar triângulos novamente.

   .. actex:: ex_rec_4

#. Escreva uma função recursiva que calcula a sequência de
   Fibonacci. Como o desempenho dessa função recursiva se compara à da
   função iterativa?

   .. actex:: ex_rec_5

#. Usando o módulo gráfico turtle, escreva um programa recursivo para
   desenhar a curva de Hilbert. 

   .. actex:: ex_rec_6
   
#. Usando o módulo gráfico turtle, escreva um programa recursivo para
   desenhar o floco de neve de Koch.

   .. actex:: ex_rec_7
