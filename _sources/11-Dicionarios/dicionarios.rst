..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".
    
..  shortname:: Dicionários
..  description:: Essa é uma introdução ao tipo de dado dicionário

Dicionários
===========

.. index:: dicionário, tipo de mapeamento, chave, valor, par chave-valor

Todos os tipos de dados compostos que estudamos em detalhes até agora --- strings,
listas e tuplas --- são coleções sequenciais. Isto significa que os
itens na coleção estão ordenados da esquerda para a direita e eles
usam números inteiros como índices para acessar os valores que eles contêm.

**Dicionário** é um tipo diferente de coleção. 
Ele é um **tipo de mapeamento** nativo do Python.
Um mapa é uma coleção associativa desordenada. A associação, ou mapeamento,
é feita a partir de uma **chave**, que pode ser qualquer tipo imutável,
para um **valor**, que pode ser qualquer objeto de dados do Python.

Como exemplo, vamos criar um dicionário para traduzir palavras em
inglês para Espanhol. Para este dicionário, as chaves são strings.

Uma maneira de criar um dicionário é começar com o dicionário vazio e adicionar
**pares chave-valor**. O dicionário vazio é denotado ``{}``

.. codelens:: chp12_dict1
    
    eng2sp = {}
    eng2sp['one'] = 'uno'
    eng2sp['two'] = 'dos'
    eng2sp['three'] = 'tres'


A primeira atribuição cria um dicionário chamado ``eng2sp``. As outras
atribuições adicionam novos pares chave-valor para o dicionário. O
lado esquerdo define o dicionário e a chave a ser associada. O lado direito
define o valor a ser associado a essa chave. 
Nós podemos imprimir o valor atual do dicionário da maneira usual.
Os pares chave-valor do dicionário são separados por vírgulas. cada par
contém uma chave e um valor separado por dois pontos.

A ordem dos pares pode não ser a que você esperava. O Python usa
algoritmos complexos, projetados para acesso muito rápido, para
determinar onde os pares chave-valor são armazenadas em um dicionário.
Para os nossos propósitos, podemos pensar que esta ordenação é imprevisível.

Outra maneira de criar um dicionário é fornecer uma lista de pares
chave-valor usando a mesma sintaxe que a saída anterior.

.. codelens:: chp12_dict2
    
    
    eng2sp = {'three': 'tres', 'one': 'uno', 'two': 'dos'}
    print(eng2sp)

Não importa em que ordem escrevemos os pares. Os valores em um dicionário são
acessados com chaves, não com índices, por isso não há necessidade de
se preocupar com a ordenação. 

O exemplo mostra como usar uma chave para pesquisar o valor correspondente.

.. codelens:: chp12_dict3
    

    eng2sp = {'three': 'tres', 'one': 'uno', 'two': 'dos'}

    value = eng2sp['two']


A chave ``'two'`` resulta no valor ``'dos'``.

.. admonition:: Scratch Editor

  .. actex:: dict_scratch_1


**Teste seu entendimento**

.. mchoice:: test_question11_1_1 
    - False
    - True
   :correct: b
    - Dicionários associam chaves com valores mas não há uma ordenação das entradas.
    - Sim, dicionários são coleções associativas, o que significa que eles armazenam pares chave-valor.

   Um dicionário é uma coleção não ordenada de pares chave-valor.


.. mchoice:: test_question11_1_2

    O que é impresso pelos seguintes comandos?
    
    .. sourcecode:: python

        mydict = {"cat":12, "dog":6, "elephant":23}
        print(mydict["dog"])

    - 12

      - 12 está associado com a chave cat.

    - 6

      + Yes, 6 está associado com a chave dog.

    - 23

      - 23 está associado com a chave elephant.

    - Erro, você não pode usar o operador índice [ ] com um dicionário.

      - O operador [ ], quando usado com dicionário, vai procurar um valor baseado na chave.
   

.. index:: comando del, del; comando

Operações com dicionários
-------------------------

O comando ``del`` remove um par chave-valor de um dicionário. Por exemplo,
o seguinte dicionário contém os nomes de várias frutas e o número de
cada fruta em estoque. Se alguém compra todas as peras, podemos remover a entrada do dicionário.

.. codelens:: ch12_dict4
    
    inventario = {'kiwis': 430, 'bananas': 312, 'laranjas': 525, 'peras': 217}
    
    del inventario['peras']


Dicionários também são mutáveis. Como vimos antes, com listas, isso significa que o dicionário pode ser modificado pela referência a uma associação no lado esquerdo de um comando de atribuição. No exemplo anterior, em vez de excluir a entrada para ``peras``, poderíamos ter definido o inventário para ``0``.

.. codelens:: ch12_dict4a
    
    inventario = {'kiwis': 430, 'bananas': 312, 'laranjas': 525, 'peras': 217}
    
    inventario['peras'] = 0



Similarmente, um novo carregamento de bananas pode ser tratado assim.

.. codelens:: ch12_dict5

    inventario = {'kiwis': 430, 'bananas': 312, 'laranjas': 525, 'peras': 217}
    inventario['bananas'] = inventario['bananas'] + 200


    numItems = len(inventario)

Observe que há agora 512 bananas --- o dicionário foi modificado. Note também que a função ``len`` também funciona em dicionários. Ela retorna o número de pares chave-valor:


.. admonition:: Scratch Editor

  .. actex:: dict_scratch_2


**Teste seu entendimento**

.. mchoice:: test_question11_2_1
   
    O que é impresso pelos seguintes comandos?
    
    .. sourcecode:: python
        
        mydict = {"cat":12, "dog":6, "elephant":23}
        mydict["mouse"] = mydict["cat"] + mydict["dog"]
        print(mydict["mouse"])

    - 12
    
      - 12 está associado à chave cat.
    
    - 0
    
      - A chave mouse ficará associada com a soma de dois valores.
    
    - 18
    
      + Sim, some o valor para cat e o valor para dog (12 + 6) e crie uma nova entrada para mouse.
    
    - Erro, não há entrada com a chave "mouse".

      - Como a nova chave é introduzida na esquerda de um comando de atribuição, um novo par chave-valor é adicionado ao dicionário.
   



Métodos de dicionários
----------------------

Dicionários possuem vários métodos nativos úteis. A seguinte tabela fornece um resumo e mais detalhes podem ser encontrados em
`Python Documentation <http://docs.python.org/py3k/library/stdtypes.html#mapping-types-dict>`_.

==========  ==============      =======================================================
Método      Parâmetros          Descrição
==========  ==============      =======================================================
keys        nenhum              Retorna uma vista das chaves no dicionário
values      nenhum              Retorna uma vista dos valores no dicionário 
items       nenhum              Retorna uma vista dos pares chave-valor no dicionário  
get         key                 Retorna o valor associado com a chave; ou None
get         key,alt             Retorna o valor associado com a chave; ou alt
==========  ==============      =======================================================

O método ``keys`` retorna o que o Python 3 chama de **vista** (view) das chaves.
Podemos iterar sobre a vista ou transformar a vista em uma lista usando a função
``list`` de conversão. 

.. activecode:: chp12_dict6
    
    inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}  
  
    for akey in inventory.keys():     # the order in which we get the keys is not defined
       print("Got key", akey, "which maps to value", inventory[akey])     
       
    ks = list(inventory.keys())
    print(ks)
    
    for k in inventory:     
       print("Got key", k)
    
É tão comum iterar sobre as chaves em um dicionário que você pode omitir a chamada ao método ``keys`` na malha ``for`` --- iterar sobre um dicionário itera implicitamente sobre suas chaves.

.. activecode:: chp12_dict7
    
    inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}  
    
    for k in inventory:     
       print("Got key", k)

 
Como vimos anteriormente com strings e listas, métodos de dicionário usam a notação de ponto, que especifica o nome do método para a direita do ponto e o nome do objeto sobre o qual se aplica o método imediatamente à esquerda do ponto. O parênteses vazio, no caso de ``keys`` indicam que este método não tem parâmetros.

Os métodos  ``values`` e ``items`` são semelhantes ao ``keys``. Eles retornam objetos vista que podem ser transformados em listas ou iterada diretamente. Note que os itens são mostrados como tuplas contendo a chave e o valor associado.

.. activecode:: chp12_dict8
    
    inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}  
    
    print(list(inventory.values()))
    print(list(inventory.items()))

    for (k,v) in inventory.items():
        print("Got",k,"that maps to",v)

    for k in inventory:
        print("Got",k,"that maps to",inventory[k])
    
Note que os tuplas são muitas vezes úteis para obter tanto a chave quanto o valor ao mesmo tempo, enquanto você está iterando no laço. Os dois laços fazer a mesma coisa.

Os operadores ``in`` e ``not in`` podem testar se uma chave está no dicionário:

.. activecode:: chp12_dict9
    
    inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}
    print('apples' in inventory)
    print('cherries' in inventory)

    if 'bananas' in inventory:
        print(inventory['bananas'])
    else:
        print("We have no bananas")
     

Este operador pode ser muito útil pois acessar uma chave inexistente em um
dicionário provoca um erro de execução.

O método ``get`` nos permite acessar o valor associado a uma chave, similar ao operador ``[]``. A diferença importante é que ``get`` não irá causar um erro de execução se a chave não está presente. Ao invés disso, retorna None. Existe uma variação de ``get`` que permite o retorno de um valor alternativo quando a chave não está presente.

.. activecode:: chp12_dict10
    
    inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}
    
    print(inventory.get("apples"))
    print(inventory.get("cherries"))

    print(inventory.get("cherries",0))

**Teste seu entendimento**

.. mchoice:: test_question11_3_1

    O que é impresso pelos seguintes comandos?
    
    .. sourcecode:: python
        
        mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
        keylist = list(mydict.keys())
        keylist.sort()
        print(keylist[3])

    - cat

      - keylist é uma lista de todas as chaves que é então ordenada. cat teria o índice 1.

    - dog

      - keylist é uma lista de todas as chaves que é então ordenada. dog teria o índice 2.

    - elephant

      + Sim, a lista de chaves é ordenada e o item de índice 3 é impresso.

    - bear

      - keylist é uma lista de todas as chaves que é então ordenada. bear teria o índice 0.
   
   
.. mchoice:: test_question11_3_2

    O que é impresso pelos seguintes comandos?
    
    .. sourcecode:: python
        
        mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
        answer = mydict.get("cat")//mydict.get("dog")
        print(answer)
   

    - 2

      + get retorna o valor associado com uma dada chave, assim o programa divide 12 por 6.

    - 0.5

      - 12 é dividido por 6, não o inverso.

    - bear

      - Dê uma nova olhada no exemplo de get dado acima. get retorna o valor associado com uma dada chave.

    - Erro, divisão não é uma operação válida em dicionários.

      - O operador de divisão inteira está sendo usado sobre os valores retornados pelo método get, não sobre o dicionário.

   
.. mchoice:: test_question11_3_3

    O que é impresso pelos seguintes comandos?
    
    .. sourcecode:: python
        
        mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
        print("dog" in mydict)

    - True

      + Sim, dog é uma chave no dicionário.

    - False

      - O operador in retorna True se a chave está no dicionário, False em caso contrário.
   

.. mchoice:: test_question11_3_4

    O que é impresso pelos seguintes comandos?
    
    .. sourcecode:: python
        
        mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
        print(23 in mydict)

    - True

      - 23 é um valor no dicionário, não uma chave.

    - False

      + Sim, o operador in retorna True se a chave está no dicionário, False em caso contrário.


.. mchoice:: test_question11_3_5
   
    O que é impresso pelos seguintes comandos?
    
    .. sourcecode:: python
        
        total = 0
        mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
        for akey in mydict:
            if len(akey) > 3:
                total = total + mydict[akey]
         print(total)

    - 18

      - Some os valores que tem chaves maiores que 3, não iguais a 3.

    - 43

      + Sim, o laço for itera sobre as chaves. Ele soma os valores das chaves que tem comprimento maior que 3.

    - 0

      - Este é o padrão de acumulação. total começa com 0 mas muda a medida que a iteração prossegue.

    - 61

      - Nem todos os valores são somados. O comando if escolhe apenas alguns. 
   
.. index:: aliases

Apelidos and cópias
-------------------

Como os dicionários são mutáveis, você precisa estar ciente de apelidos (ou aliasing, como vimos com listas). Sempre que duas variáveis se referem ao mesmo objeto no dicionário, a mudança de uma afeta a outra.
Por exemplo, ``opposites`` é um dicionário que contém pares
de opostos.

.. activecode:: ch12_dict11
    
    opposites = {'up': 'down', 'right': 'wrong', 'true': 'false'}
    alias = opposites

    print(alias is opposites)

    alias['right'] = 'left'
    print(opposites['right'])
    


Como você pode notar do operador ``is``, ``alias`` e ``opposites`` se referem ao mesmo objeto.

Se você deseja modificar um dicionário e manter uma cópia do original, use o método ``copy`` de dicionários. como *acopy* é uma cópia do dicionário, mudanças nesse dicionário não afetarão o original.

.. sourcecode:: python
    
    acopy = opposites.copy()
    acopy['right'] = 'left'    # does not change opposites

**Teste seu entendimento**

.. mchoice:: test_question11_4_1

    O que é impresso pelos seguintes comandos?
    
    .. sourcecode:: python
        
        mydict = {"cat":12, "dog":6, "elephant":23, "bear":20}
        yourdict = mydict
        yourdict["elephant"] = 999
        print(mydict["elephant"])

    - 23

      - mydict e yourdict são ambos nomes do mesmo dicionário.

    - None

      - O dicionário é mutável, assim mudanças podem ser feitas para as chaves e valores.

    - 999

      + Sim, como yourdict é um apelido para mydict, o valor para a chave elephant foi trocada.

    - Erro, há duas chaves de nome elephant.

      - Há apenas um dicionário com somente uma chave chamada elephant. O dicionário tem dois nome diferentes, mydict e yourdict.


.. index:: matrix

Matrizes esparsas
-----------------

Nós usamos anteriormente uma lista de listas para representar um matrix. Essa é uma boa escolha para uma matriz com a maioria de seus valores diferentes de zero, mas considere uma `matriz esparsa
<http://en.wikipedia.org/wiki/Sparse_matrix>`__ como esta:

.. image:: Figures/sparse.png
   :alt: sparse matrix 

A representação usando listas contém muitos zeros:

.. sourcecode:: python
    
    matrix = [[0, 0, 0, 1, 0],
              [0, 0, 0, 0, 0],
              [0, 2, 0, 0, 0],
              [0, 0, 0, 0, 0],
              [0, 0, 0, 3, 0]]

Uma alternativa é a utilização de um dicionário. Para as chaves, podemos usar tuplas que contêm os números de linha e coluna. Aqui está a representação da mesma matriz usando dicionário.

.. sourcecode:: python
    
    matrix = {(0, 3): 1, (2, 1): 2, (4, 3): 3}

Nós precisamos de apenas 3 pares chave-valor, um para cada elemento não-zero da matriz. Cada chave é uma tupla e cada valor é um inteiro.

Para acessar um elemento da matriz, nós podemos usar o operador ``[]``::
  
    matrix[(0, 3)]

Observe que a sintaxe para a representação de um dicionário não é o mesma que a
sintaxe da representação lista aninhada. Em vez de dois índices inteiros,
utilizamos um índice que é uma tupla de inteiros.

Existe um problema. Se especificarmos um elemento que é zero, teremos um erro pois
não há nenhum elemento no dicionário com essa chave.
A versão alternativa do método ``get`` resolve este problema.
O primeiro argumento será a chave. O segundo argumento é o valor que ``get`` deve
retornar caso a chave não esteja no dicionário (o que seria 0, uma vez que é uma matriz esparsa).

.. activecode:: chp12_sparse

   matrix = {(0, 3): 1, (2, 1): 2, (4, 3): 3}
   print(matrix.get((0,3)))

   print(matrix.get((1, 3), 0))


.. admonition:: Lab

    * `Counting Letters <../Labs/lab12_01.html>`_ Nesse exercício dirigido de laboratório vamos trabalhar com um exercício que vai usar dicionários para generalizar a solução para contar as ocorrências de todas as letras em um string. 



.. admonition:: Lab

    * `Letter Count Histogram <../Labs/lab12_02.html>`_ Combina o laboratório anterior com o exemplo de histogramas.



    
Glossário
---------

.. glossary::
       
    chave
        Um item de dados que é *mapeado* para um valor em um dicionário. As chaves são utilizadas para acessar os respectivos valores em um dicionário.

    dicionário
        Uma coleção de pares chave-valor que mapeiam chaves em valores. As chaves podem ser de qualquer tipo imutável e os valores podem ser de qualquer tipo.

    gráfico de chamadas
        Um gráfico consistindo de nós que representam chamadas de funções (ou  invocações), e arestas (linhas com setas) mostrando que chamadas deram origem a outras chamadas.
	
    memorando
        O armazenamento temporário de valores pré-computadas para evitar a duplicação da mesma computação.

    par chave-valor
        Um dos pares de elementos de um dicionário. Os valores são acessados em um dicionário pelas suas chaves.
	
    tipo de mapeamento
        Um tipo de mapeamento é um tipo de dados composto por uma coleção de chaves e valores associados. O único tipo de mapeamento nativo do Python é o dicionário. Dicionários implementam o tipo de dados abstrato ---  `vetores associativos <http://en.wikipedia.org/wiki/Associative_array>`.


Exercícios
----------

#. Escreva um programa que lê em uma sequência da linha de comando e retorna uma tabela com as letras do alfabeto em ordem alfabética que ocorrem na sequência junto com o número de vezes que cada letra ocorre. Ignore se as letras são maiúsculas ou minúsculas. Um exemplo de execução do programa ficaria assim::

       $ python letter_counts.py "ThiS is String with Upper and lower case Letters."
       a  2
       c  1
       d  1
       e  5
       g  1
       h  2
       i  4
       l  2
       n  2
       o  1
       p  2
       r  4
       s  5
       t  5
       u  1
       w  2
       $

   .. actex:: ex_11_01

#. Forneça a resposta do interpretador Python para cada uma das questões seguintes, assumindo que os comandos são dados continuamente na mesma sessão:

   a.
      .. sourcecode:: python
        
          >>> d = {'apples': 15, 'bananas': 35, 'grapes': 12} 
          >>> d['banana'] 

   b.
      .. sourcecode:: python
        
          >>> d['oranges'] = 20
          >>> len(d) 

   c.
      .. sourcecode:: python
        
          >>> 'grapes' in d
          
   d.
      .. sourcecode:: python
        
          >>> d['pears']
          
   e.
      .. sourcecode:: python
        
          >>> d.get('pears', 0)
          
   f.
      .. sourcecode:: python
        
          >>> fruits = d.keys()
          >>> fruits.sort()
          >>> print(fruits)
          
   g.
      .. sourcecode:: python
        
          >>> del d['apples']
          >>> 'apples' in d 
          

   Certifique-se de que você entendeu a razão de cada resultado. Então aplique o que você aprendeu para preencher o corpo da função abaixo:

   .. sourcecode:: python
    
       def add_fruit(inventory, fruit, quantity=0): 
            pass
       
       # faça esses testes funcionarem...
       new_inventory = {}
       add_fruit(new_inventory, 'strawberries', 10)
       test('strawberries' in new_inventory, True)
       test(new_inventory['strawberries'], 10)
       add_fruit(new_inventory, 'strawberries', 25)
       test(new_inventory['strawberries'] , 35)      

#. Escreva um programa chamado ``alice_words.py`` que cria um arquivo de texto chamado ``alice_words.txt`` contendo uma lista alfabética de todas as palavras, e o número de vezes que cada palavra ocorre, na versão de texto do `Alice's Adventures in Wonderland`. (Você pode obter uma versão em texto puro gratuita do livro, junto com muitos outros, a partir de http://www.gutenberg.org.) As primeiras 10 linhas do seu arquivo de saída devem se parecer com:

    =========== ===========
    Palava         Contador
    =========== ===========
    a                 631
    a-piece           1
    abide             1
    able              1
    about             94
    above             3
    absence           1
    absurd            2
    =========== ===========

   Quantas vezes a palavra ``alice`` aparece no livro? Se você está usando o activecode, simplesmente imprima os resultados ao invés de escrever em um arquivo.
   
   .. actex:: ex_11_02
   
#. Qual é a palavra mais comprida no livro ``Alice in Wonderland``? Quantos caracteres ela possui?
   
   .. actex:: ex_11_03
   
#. A seguinte tabela contém tradução de algumas palavras em inglês para a língua dos piratas

    ==========  ==============
    Inglês      Pirata
    ==========  ==============
    sir	        matey
    hotel	    fleabag inn
    student	    swabbie
    boy	        matey
    madam	    proud beauty
    professor	foul blaggart
    restaurant	galley
    your	    yer
    excuse	    arr
    students	swabbies
    are	        be
    lawyer	    foul blaggart
    the	        th'
    restroom	head
    my	        me
    hello	    avast
    is	        be
    man	        matey
    ==========  ==============
    
    Escreva um programa que pergunta ao usuário uma frase em inglês e imprime a tradução da frase para a língua dos piratas.
    
    .. actex:: ex_11_04
    

    
