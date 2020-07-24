..  Copyright (C)  Brad Miller, David Ranum
    Permission is granted to copy, distribute and/or modify this document
    under the terms of the GNU Free Documentation License, Version 1.3 or 
    any later version published by the Free Software Foundation; with 
    Invariant Sections being Forward, Prefaces, and Contributor List, 
    no Front-Cover Texts, and no Back-Cover Texts.  A copy of the license
    is included in the section entitled "GNU Free Documentation License".
    
..  shortname:: Files
..  description:: This is the introduction to the basic idea of a text file

.. Working with Data Files
.. =======================

Trabalhando com Arquivos
========================

..
   So far, the data we have used in this book have all been either coded
   right into the program, or have been entered by the user.  In real
   life data reside in files.  For example the images we worked with in
   the image processing unit ultimately live in files on your hard drive.
   Web pages, and word processing documents, and music are other examples
   of data that live in files.  In this short chapter we will introduce
   the Python concepts necessary to use data from files in our programs.

Até agora, os dados que temos usado nos programas deste livro ou estão
inseridos diretamente no código ou são digitados pelo usuário a medida
que são lidos. Na vida real dados estão em um arquivo. Por exemplo as 
imagens na unidade de processamento de imagens residem em arquivos que
estão no disco rígido (*hard drive*) do seu computador. Página na 
Internet, documentos, músicas são outros exemplos de dados que vivem
em arquivos. Neste capítulo apresentaremos de maneira sucinta os 
conceitos de Python necessários para usar em programas dados que
estão em arquivos. 


..
   For our purposes, we will assume that our data files are text
   files--that is, files filled with characters. The Python programs that
   you write are stored as text files.  We can create these files in any
   of a number of ways. For example, we could use a text editor to type
   in and save the data.  We could also download the data from a website
   and then save it in a file. Regardless of how the file is created,
   Python will allow us to manipulate the contents.

Para os nossos propósitos, suporemos que os nosso arquivos de dados
contém texto--isto é, arquivos de caracteres. Os programas em Python
que você escreve são armazenados em arquivos de texto. Podemos criar
esses arquivos de diversas maneiras. Por exemplo, podemos usar um
editor de textos para digitar e salvar os dados. Podemos também baixar
(*download*) os dados de uma página na Internet (*website*) e salvá-los
em um arquivo. Não importa como os arquivos são criados, Python nos permitira
manipular o seu conteúdo.


..
   In Python, we must **open** files before we can use them and **close**
   them when we are done with them. As you might expect, once a file is
   opened it becomes a Python object just like all other
   data. :ref:`Table 1<filemethods1a>` shows the methods that can be used
   to open and close files.

Em Python, devemos **abrir** (*open*) arquivos antes de usá-los e **fechar**
(*close*) os arquivos depois de que tivermos terminado de utilizá-los.
Como você pode imaginar, depois de aberto um arquivo passa a ser um objeto
Python de maneira semelhante que outros dados. :ref:`Table 1<filemethods1a>`
mostra os métodos que podem ser usados para abrir e fechar arquivos.


.. .. _filemethods1a:

   ================ ======================== =====================================================
   **Method Name**   **Use**                  **Explanation**
   ================ ======================== =====================================================
   ``open``          ``open(filename,'r')``    Open a file called filename and use it for reading.  This will return a reference to a file object. 
   ``open``          ``open(filename,'w')``    Open a file called filename and use it for writing.  This will also return a reference to a file object. 
   ``close``        ``filevariable.close()``   File use is complete. 
   ================ ======================== =====================================================


.. _filemethods1a:

================== ========================== =============================================================
**Nome de Método**  **Uso**                    **Explicação**
================== ========================== =============================================================
``open``           ``open(nome_arquivo,'r')``    Abre um arquivo chamado nome_arquivo e o usa para leitura.  Retorna uma referëncia para um objeto *file*. 
``open``           ``open(nome_arquivo,'w')``    Abre um arquivo chamado nome_arquivo e o usa para escrita.  Retorna uma referëncia para um objeto *file*. 
``close``          ``ref_arquivo.close()``       Utilização do arquivo referenciado pela variável ref_arquivo terminou.
================== ========================== =============================================================


.. Finding a File on your Disk
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~


Encontrando um arquivo disco
----------------------------

..
   Opening a file requires that you, as a programmer, and Python agree
   about the location of the file on your disk.  The way that files are
   located on disk is by their **path** You can think of the filename as
   the short name for a file, and the path as the full name.  For example
   on a Mac if you save the file ``hello.txt`` in your home directory the
   path to that file is ``/Users/yourname/hello.txt`` On a Windows
   machine the path looks a bit different but the same principles are in
   use.  For example on windows the path might be ``C:\Users\yourname\My
   Documents\hello.txt``

Abrir um arquivo requer que você, como programador, e o Python entre em
acordo sobre onde está o arquivo no seu disco. A maneira que os arquivos
são localizados no disco e através do seu **caminho** (*path*). Você pode
pensar em ``nome_arquivo`` como o *primeiro nome* do arquivo e o caminho
como o *nome completo*. Por exemplo em um Mac se o usuário ``hofstadter`` salvar
o arquivo  ``penny.txt`` no seu diretório (*home directory*) o caminho é 
``/Users/hofstadter/penny.txt``. 
No Linux caminho poderia ser ``/home/hofstadter/penny.txt`` . 
No computadores com o sistema operacional Windows o caminho parece um 
pouco diferente, mas os princípios são os mesmos. Por exemplo no Windows
o caminho poderia ser ``C:\Users\hofstadter\My Documents\penny.txt``.    

..
   You can access files in folders, also called directories, under your
   home directory by adding a slash and the name of the folder.  For
   example we have been storing files to use with PyCharm in the CS150
   folder inside the PyCharmProjects folder under your home directory.
   The full name for ``hello.py`` stored in the CS150 folder would be
   ``/Users/yourname/PyCharmProjects/CS150/hello.py``

Você também pode acessar arquivos em pastas (*folders*), também chamados de
diretórios (*directories*), no seu diretório adicionando um barra e o 
nome da pasta. Por exemplo, suponha que em um Mac o usuário ``hofstadter`
armazena arquivos para usar com o editor PyCharm na pasta MAC2166,
que por sua vez está dentro da pasta ProjetosPyCharm. 
O nome completo de um arquivo ``penny.py`` armazenado na pasta MAC2166 seria 
``/Users/hofstadter/ProjetosPyCharm/MAC2166/penny.py``
 
..
   Here's the important rule to remember: If your file and your Python
   program are in the same directory you can simply use the
   filename. ``open('myfile.txt','r')`` If your file and your Python
   program are in different directories then you should use the path to
   the file ``open(/Users/joebob01/myfile.txt)``.

Aqui está uma regra importante para ser lembrada: se o seu arquivo de dados e
o seu programa Python estão no mesmo diretório você pode usar simplesmente
o nome do arquivo. ``open('penny.txt','r')`` .
Se o seu arquivo de dados  e o seu programa Python estão em diretórios diferentes
então você deve usar o caminho até o arquivo 
``open('/Users/hofstadter/penny.txt','r')``.


.. Reading a File
.. ~~~~~~~~~~~~~~

.. Lendo um Arquivo
.. ----------------

Abrindo e fechando arquivos
---------------------------

..
   As an example, suppose we have a text file called ``qbdata.txt`` that contains
   the following data representing statistics about NFL quarterbacks. Although it
   would be possible to consider entering this data by hand each time it is used,
   you can imagine that it would be time-consuming and error-prone to do this. In
   addition, it is likely that there could be data from more quarterbacks and
   other years. The format of the data file is as follows::

Como exemplo, suponha que temos um texto chamado ``qbdata.txt`` que contem os dados
a seguir representando estatísticas sobre o *quarterbacks* da NFL. Apesar de ser
possível digitarmos esses dados cada vez que tivéssemos que usá-los, podemos imaginar
que além de tomar bastante tempo fazer isso também seria uma fonte de erros.  Além disso,
é provável que houvesse dados de outros *quarterbacks* e outros anos. O formato de
arquivo de dados é o seguinte::

    First Name, Last Name, Position, Team, Completions, Attempts, Yards, TDs Ints, Comp%, Rating

.. raw:: html

    <pre id="qbdata.txt">
    Colt McCoy QB, CLE  135 222 1576    6   9   60.8%   74.5
    Josh Freeman QB, TB 291 474 3451    25  6   61.4%   95.9
    Michael Vick QB, PHI    233 372 3018    21  6   62.6%   100.2
    Matt Schaub QB, HOU 365 574 4370    24  12  63.6%   92.0
    Philip Rivers QB, SD    357 541 4710    30  13  66.0%   101.8
    Matt Hasselbeck QB, SEA 266 444 3001    12  17  59.9%   73.2
    Jimmy Clausen QB, CAR   157 299 1558    3   9   52.5%   58.4
    Joe Flacco QB, BAL  306 489 3622    25  10  62.6%   93.6
    Kyle Orton QB, DEN  293 498 3653    20  9   58.8%   87.5
    Jason Campbell QB, OAK  194 329 2387    13  8   59.0%   84.5
    Peyton Manning QB, IND  450 679 4700    33  17  66.3%   91.9
    Drew Brees QB, NO   448 658 4620    33  22  68.1%   90.9
    Matt Ryan QB, ATL   357 571 3705    28  9   62.5%   91.0
    Matt Cassel QB, KC  262 450 3116    27  7   58.2%   93.0
    Mark Sanchez QB, NYJ    278 507 3291    17  13  54.8%   75.3
    Brett Favre QB, MIN 217 358 2509    11  19  60.6%   69.9
    David Garrard QB, JAC   236 366 2734    23  15  64.5%   90.8
    Eli Manning QB, NYG 339 539 4002    31  25  62.9%   85.3
    Carson Palmer QB, CIN   362 586 3970    26  20  61.8%   82.4
    Alex Smith QB, SF   204 342 2370    14  10  59.6%   82.1
    Chad Henne QB, MIA  301 490 3301    15  19  61.4%   75.4
    Tony Romo QB, DAL   148 213 1605    11  7   69.5%   94.9
    Jay Cutler QB, CHI  261 432 3274    23  16  60.4%   86.3
    Jon Kitna QB, DAL   209 318 2365    16  12  65.7%   88.9
    Tom Brady QB, NE    324 492 3900    36  4   65.9%   111.0   
    Ben Roethlisberger QB, PIT  240 389 3200    17  5   61.7%   97.0
    Kerry Collins QB, TEN   160 278 1823    14  8   57.6%   82.2
    Derek Anderson QB, ARI  169 327 2065    7   10  51.7%   65.9
    Ryan Fitzpatrick QB, BUF    255 441 3000    23  15  57.8%   81.8
    Donovan McNabb QB, WAS  275 472 3377    14  15  58.3%   77.1
    Kevin Kolb QB, PHI  115 189 1197    7   7   60.8%   76.1
    Aaron Rodgers QB, GB    312 475 3922    28  11  65.7%   101.2
    Sam Bradford QB, STL    354 590 3512    18  15  60.0%   76.5
    Shaun Hill QB, DET  257 416 2686    16  12  61.8%   81.3
    </pre>

..
   To open this file, we would call the ``open`` function. The variable,
   ``fileref``, now holds a reference to the file object returned by
   ``open``. When we are finished with the file, we can close it by using
   the ``close`` method. After the file is closed any further attempts to
   use ``fileref`` will result in an error.

Para abrir esse arquivo temos que usar a função ``open``. A variável 
``ref_arquivo`` mantém uma referência ao objeto do tipo ``file`` retornado por
``open``. Quando terminamos de usar o dados do arquivo, podemos fechá-lo usando 
o método ``close``. Depois que o arquivo estiver fechado, qualquer tentativa
de usar ``ref_arquivo`` resultará em erro.

    ::

            >>> ref_arquivo = open("qbdata.txt","r")
            >>>
            >>> ref_arquivo.close()
            >>>

.. Iterating over lines in a file
.. ------------------------------

Iterando sobre as linha de um Arquivo
-------------------------------------

..
   We will now use this file as input in a program that will do some data
   processing. In the program, we will **read** each line of the file and
   print it with some additional text. Because text files are sequences of
   lines of text, we can use the *for* loop to iterate through each line of
   the file.


Agora usaremos o arquivo ``qbdata.txt`` como entrada de um programa que
faz um pouco de processamento de dados. No programa nós iremos **ler**
(*read*) cada linha do arquivo e imprimi-la com algum texto adicional.
Como arquivos de texto são uma sequência de linhas com texto, nós 
usaremos um laço *for* para iterar sobre cada linha do arquivo.
 

..
   A **line** of a file is defined to be a sequence of characters up to and
   including a special character called the **newline** character. If you
   evaluate a string that contains a newline character you will see the
   character represented as ``\n``. If you print a string that contains a
   newline you will not see the ``\n``, you will just see its effects. When
   you are typing a Python program and you press the enter or return key on
   your keyboard, the editor inserts a newline character into your text at
   that point.

Um **linha** (*line*) de um arquivo é definida como uma sequência de
caracteres até e incluindo um caractere especial chamado de **nova
linha** (*newline*).  Se você examinar um string que contém um
caractere de nova linha você verá ele representado como ``\n``. Só
você imprime um string contendo um caractere de nova linha você não
verá o ``\n``, você verá apenas o seu efeito, ou seja, uma mudança de
linha. Quando estamos digitando um programa em Python e pressionamos a
tecla ``enter`` ou ``return``, o editor insere um caractere de nova
linha no texto naquele ponto.


..
   As the *for* loop iterates through each line of the file the loop
   variable will contain the current line of the file as a string of
   characters. The general pattern for processing each line of a text file
   is as follows:

A medida com o laço *for* itera sobre cada linha do arquivo a variável 
de controle do laço conterá uma referência para um string com 
o conteúdo da linha corrente do arquivo. O padrão geral para processar cada linha
de um arquivo texto é o seguinte:
 
::

        for linha in ref_arquivo:
            comando1
            comando2
            ...

..
   To process all of our quarterback data, we will use a *for* loop to
   iterate over the lines of the file. Using the ``split`` method, we can
   break each line into a list containing all the fields of interest
   about the quarterback. We can then take the values corresponding to
   first name, lastname, and passer rating to construct a simple sentence
   as shown in :ref:`Listing 1 <readingfile1>`.

Para processar todos os dados sobre os *quarterbacks*, usamos o laço
*for* para iterar sobre as linhas do arquivo. Usando o método ``split``
podemos quebrar cada linha em uma lista contendo todos os campos de interesse
sobre o *quarterback. Podemos pegar os valores correspondente ao 
*first name*, *last name* e examinar as avaliações para construir 
uma sentença simples como mostrada em :ref:`Listing 1 <readingfile1>`.


.. _readingfile1:

.. activecode:: files_for

    ref_arquivo = open("qbdata.txt","r")

    for linha in ref_arquivo:
        valores = linha.split()
        print('QB ', valores[0], valores[1], 'obteve a avaliacao ', valores[10] )

    ref_arquivo.close()



.. Alternative File Reading Methods
.. --------------------------------

Métodos alternativos para ler arquivos
--------------------------------------

..
   In addition to the ``for`` loop, Python provides three methods to read
   data from the input file. The ``readline`` method reads one line from
   the file and returns it as a string. The string returned by
   ``readline`` will contain the newline character at the end. This
   method returns the empty string when it reaches the end of the
   file. The ``readlines`` method returns the contents of the entire file
   as a list of strings, where each item in the list represents one line
   of the file. It is also possible to read the entire file into a single
   string with ``read``. :ref:`Table 2 <filemethods2a>` summarizes these
   methods and :ref:`Session 2 <filesession>` shows them in action.

Além do laço ``for`` Python fornece três métodos para lermos dados de
um arquivo. O método ``readline`` lê uma linha de um arquivo e retorna
essa linha como um string. O string retornado por ``readline`` conterá
o caractere de nova linha (``'\n'``) no final. Este método retorna o
string vazio (``""``) quando chegamos ao final do arquivo.  O método
``readlines`` retorna o todo o conteúdo do arquivo em uma lista de
strings, cada item da lista representa uma linha do arquivo.  Também é
possível ler todo o conteúdo de um arquivo em um único string como o
método ``read``.  :ref:`Table 2 <filemethods2a>` resume esses métodos
e :ref:`Session 2 <filesession>` mostra eles em ação.
  

..
   Note that we need to reopen the file before each read so that we start from
   the beginning. Each file has a marker that denotes the current read position
   in the file. Any time one of the read methods is called the marker is moved to
   the character immediately following the last character returned. In the case
   of ``readline`` this moves the marker to the first character of the next line
   in the file. In the case of ``read`` or ``readlines`` the marker is moved to
   the end of the file.

Note que necessitamos reabrir um arquivo antes de lê-lo a partir da primeira linha.
Cada arquivo de uma marca que indica a posição corrente do arquivo que está prestes
a ser lida. Cada vez que um desses métodos ;e chamado a marca se move para o 
caractere que vem em seguida do último caractere retornado. No caso de ``readline``
o marcado se move para o primeiro caractere da próxima linha. Nos caso de ``read``
ou ``readlines`` a marca se move para o final do arquivo.  

.. _filesession:

::

    >>> ref_arquivo = open("qbdata.txt","r")
    >>> linha = ref_arquivo.readline()
    >>> linha
    'Colt McCoy QB, CLE\t135\t222\t1576\t6\t9\t60.8%\t74.5\n'
    >>> 
    >>> ref_arquivo = open("qbdata.txt","r")
    >>> lista_de_linhas = ref_arquivo.readlines()
    >>> print(len(lista_de_linhas))
    34
    >>> print(lista_de_linhas[0:4])
    ['Colt McCoy QB, CLE\t135\t222\t1576\t6\t9\t60.8%\t74.5\n',
     'Josh Freeman QB, TB\t291\t474\t3451\t25\t6\t61.4%\t95.9\n',
     'Michael Vick QB, PHI\t233\t372\t3018\t21\t6\t62.6%\t100.2\n',
     'Matt Schaub QB, HOU\t365\t574\t4370\t24\t12\t63.6%\t92.0\n']
    >>> 
    >>> ref_arquivo = open("qbdata.txt","r")
    >>> string_arquivo = ref_arquivo.read()
    >>> print(len(string_arquivo))
    1708
    >>> print(string_arquivo[:256])
    Colt McCoy QB, CLE	135	222	1576	6	9	60.8%	74.5
    Josh Freeman QB, TB	291	474	3451	25	6	61.4%	95.9
    Michael Vick QB, PHI	233	372	3018	21	6	62.6%	100.2
    Matt Schaub QB, HOU	365	574	4370	24	12	63.6%	92.0
    Philip Rivers QB, SD	357	541	4710	30	13	66.0%	101.8
    Matt Ha
    >>>

.. _filemethods2a:

..
   ======================== =========================== ===================================== 
   **Method Name**           **Use**                     **Explanation**
   ======================== =========================== ===================================== 
   ``write``                 ``filevar.write(astring)``  Add astring to the end of the file. 
                                                         filevar must refer to a file that has 
                                                         been  opened for writing. 
   ``read(n)``               ``filevar.read()``          Reads and returns a string of ``n`` 
                                                         characters, or the entire file as a 
                                                         single string if  n is not provided. 
   ``readline(n)``           ``filevar.readline()``      Returns the next line of the file with
                                                         all text up to and including the 
                                                         newline character. If n is provided as 
                                                         a parameter than only n characters 
                                                         will be returned if the line is longer 
                                                         than ``n``. 
   ``readlines(n)``          ``filevar.readlines()``     Returns a list of strings, each 
                                                         representing a single line of the file. 
                                                         If n is not provided then all lines of
                                                         the file are returned. If n is provided
                                                         then n characters are read but n is 
                                                         rounded up so that an entire line is
                                                         returned.
   ======================== =========================== ===================================== 


==================== =========================== ========================================== 
**Método**           **Uso**                     **Efeito**
==================== =========================== ========================================== 
``write``            ``ref_arquivo.write(s)``    Adiciona o string ``s`` no final do arquivo. 
                                                 ref_arquivo deve ser uma referência a um arquivo que
                                                 foi aberto para escrita (``"w"``). 
``read(n)``          ``ref_arquivo.read()``      Lê e retorna um string de ``n`` caracteres ou o 
                                                 arquivo inteiro como um string se ``n`` não é 
                                                 fornecido.                                               
``readline(n)``      ``ref_arquivo.readline()``  Retorna a próxima linha do arquivo com todo o  
                                                 texto e incluindo o caractere de nova linha.
                                                 Se ``n`` é fornecido como argumento então somente n caracteres
                                                 são retornados se a linha tem mais do que ``n`` 
                                                 caracteres.
``readlines(n)``     ``ref_arquivo.readlines()`` Retorna uma lista de strings, cada um representado o 
                                                 conteúdo de uma linha do arquivo.
                                                 Se ``n`` não é fornecido, todas as linhas do arquivo são 
                                                 retornadas. Se ``n`` é fornecido como argumento então 
                                                 ``n`` caracteres serão lidos mas ``n`` é arrendondado
                                                 para cima de tal forma que uma linha inteira seja 
                                                 retornada.
==================== =========================== ========================================== 


..
   Now lets look at another method of reading our file using a ``while``
   loop.  This important because many other programming languages do not
   support the ``for`` loop style for reading file but they do support
   the pattern we'll show you here.

Agora olhemos outra maneira de lermos nosso arquivo usando um laço
``while``. Isto é importante pois muitas outras linguagens de programação
não tem algo semelhante ao estilo do laço ``for`` para ler arquivos mais
elas admitem algo semelhante ao padrão que mostraremos aqui.


.. activecode:: files_while

    ref_arquivo = open("qbdata.txt","r")
    linha = ref_arquivo.readline()
    while linha:
        valores = linha.split()
        print('QB ', valores[0], valores[1], 'obteve a avaliacao ', valores[10] )
        linha = ref_arquivo.readline()

    ref_arquivo.close()

..
   The important thing to notice is that on line two we have the
   statement ``line = ref_arquivo.readline()`` This is very important
   because the while condition needs to have a value for the ``line``
   variable.  We call this initial read the **priming read**.

Algo importante a ser notado é que na linha dois temos o 
comando ``linha = ref_arquivo.readline()``. Isto é muito 
importante pois a condição do ``while`` necessita que o valor 
da variável ``linha``. Chamamos essa leitura inicial de
**priming read**.  

.. Glossary
.. --------

Glossário
---------

.. glossary::

   open
       Devemos abrir (*open*)  um arquivo antes de ler o seu conteúdo: ``ref_arquivo = open(nome_arquivo,"r")``.
       Devemos também abrir um arquivo antes de escrever nele: ``ref_arquivo = open(nome_arquivo,"w")``.

   close
      devemos fechar (*close*) um arquivo depois que acabamos de manipulá-lo: ``ref_arquivo.close()``.

    
   read
      Método que lê e retorna o conteúdo inteiro de um arquivo em um string.  É frequentemented usado em um 
      comando de atribuição de tal forma que a variável seja uma referência para um string com o 
      conteúdo do arquivo: ``string_arquivo = ref_arquivo.read()``
	
   readline
      Método que lê e retorna o conteúdo da linha corrente de um arquivo como string: ``linha_str = ref_arquivo.readline()``.
      O caractere de nova linha e incluído no final do string.


   readlines
     Método que lê e retorna o conteúdo de um arquivo como uma lista de strings. 
     Cada linha do arquivo é representado por um string da lista:  ``lista_de_linhas = ref_arquivo.readlines()``.



.. Exercises
.. ---------

Exercícios
----------

.. The following sample file contains one line for each student in an
   imaginary class the students name is the first thing on each line,
   followed by some exam scores.

Aqui está um arquivo ``notas_estudantes.dat`` que contém uma
linha para cada aluno de uma turma de estudantes.  O nome de cada
estudante está no início da cada linha e é seguido pelas suas notas.
 
.. raw:: html

         <pre id="notas_estudantes.dat">
    jose 10 15 20 30 40
    pedro 23 16 19 22
    suzana 8 22 17 14 32 17 24 21 2 9 11 17
    gisela 12 28 21 45 26 10
    joao 14 32 25 16 89
         </pre>

..
   #. Using the text file ``student_data.dat`` write a program that prints out the names of
      students that have more than six quiz scores.

#. Usando o arquivo texto ``notas_estudantes.dat`` escreva um programa que imprime o
   nome dos alunos que têm mais de seis notas.
 
   .. actex:: ex_10_1
   
..
   #. Using the text file ``student_data.dat`` write a program that calculates the average grade
      for each student, and print out the student's name along with their average grade.

#. Usando o arquivo texto ``notas_estudantes.dat`` escreva um programa que calcula a 
   média das notas de cada estudante e imprime o nome e a média de cada estudante.

   .. actex:: ex_10_2

..
   #. Using the text file ``student_data.dat`` write a program that calculates the minimum
      and maximum grade grade for each student.  Print out the students name along with their    
      minimum and maximum scores.

#. Usando o arquivo texto ``notas_estudantes.dat`` escreva um programa que calcula a 
   nota mínima e máxima de cada estudante e imprima o nome de cada aluno junto com 
   a suam notá máxima e mínima.

   .. actex:: ex_10_3


..   Here is a file called ``lab_data.dat`` that contains some sample data from a lab experiment.

   Aqui está o arquivo chamado ``lab.dat`` que contém os dados de um experimento em um laboratório.

.. raw:: html

         <pre id='lab.dat'>
    44 71
    79 37
    78 24
    41 76
    19 12
    19 32
    28 36
    22 58
    89 92
    91 6
    53 7
    27 80
    14 34
    8 81
    80 19
    46 72
    83 96
    88 18
    96 48
    77 67
	</pre>
	
	
..
   4.  Using the data file ``lab_data.data`` each line contains a an x,y coordinate pair. 
       Write a function called ``plotRegression`` that reads the data from this file
       and uses a turtle to plot those points and a best fit line according to the following 
       formulas

4.  Cada linha do arquivo ``lab.dat`` contém um par x,y de coordenadas. 
    Escreva uma função chamada ``plot_regressao`` que le os dados desse arquivo 	
    e usa a tartaruga para desenhar pontos e a reta que melhor aproxima os dados de acordo
    com as formulas 
    

        y = \bar{y} + m(x - \bar{x})

        m = \frac{\sum{x_iy_i - n\bar{x}\bar{y}}}{\sum{x_i^2}-n\bar{x}^2}

     onde :math:`\bar{x}` é a média dos x-valores, :math:`\bar{y}` é a média do y-valores
     e :math:`n` é o número de pontos e :math:`\sum` é o operador somatório.  
     Por exmplo :math:`\sum{x_i}` é a soma de todos os x-valores.

     Seu programa deve analizar os pontos e corretamente dimensionar a janela 
     usando ``setworldcoordinates`` de tal forma que cada ponto possa ser desenhado.
     O seu programa deve desenhar a reta que melhor aproxima os dados usando uma
     cor diferente dos pontos.

..
        Your program should analyze the points and correctly scale the window using 
        ``setworldcoordinates`` so that that each point can be plotted.  Then you should
        draw the best fit line, in a different color, through the points.	

 .. actex:: ex_10_4


..
   5.  At the end of this chapter is a very long file called ``misterio.dat`` The lines of this 
       file contain either the word UP or DOWN or a pair of numbers.  UP and DOWN are instructions
       for a turtle to lift up or put down its tail.  The pair of numbers are some x,y coordinates.
       Write a program that reads the file ``misterio.dat`` and uses the turtle to draw the picture
       described by the commands and the set of points.

5.  No final deste capítulo há uma arquivo muito longo chamado ``misterio.dat`` 
    A linhas deste arquivo contém ou a palavra CIMA ot BAIXO ou um par de números. CIMA e BAIXO são
    instruções para a tartaruga colocar a sua cauda para cima ou para baixo. O par de números são 
    coordenadas x,y. Escreva um programa que lê o arquivo ``misterio.dat`` e usa a tartaruga 
    para desenhar a figura descrita pelos comandos e cojunto de pontos no arquivo.
    
    .. actex:: ex_10_5
    

.. raw:: html

   <pre id="misterio.dat">
   CIMA
   -218 185
   BAIXO
   -240 189
   -246 188
   -248 183
   -246 178
   -244 175
   -240 170
   -235 166
   -229 163
   -220 158
   -208 156
   -203 153
   -194 148
   -187 141
   -179 133
   -171 119
   -166 106
   -163 87
   -161 66
   -162 52
   -164 44
   -167 28
   -171 6
   -172 -15
   -171 -30
   -165 -46
   -156 -60
   -152 -67
   -152 -68
   CIMA
   -134 -61
   BAIXO
   -145 -66
   -152 -78
   -152 -94
   -157 -109
   -157 -118
   -151 -128
   -146 -135
   -146 -136
   CIMA
   -97 -134
   BAIXO
   -98 -138
   -97 -143
   -96 -157
   -96 -169
   -98 -183
   -104 -194
   -110 -203
   -114 -211
   -117 -220
   -120 -233
   -122 -243
   -123 -247
   -157 -248
   -157 -240
   -154 -234
   -154 -230
   -153 -229
   -149 -226
   -146 -223
   -145 -219
   -143 -214
   -142 -210
   -141 -203
   -139 -199
   -136 -192
   -132 -184
   -130 -179
   -132 -171
   -133 -162
   -134 -153
   -138 -145
   -143 -137
   -143 -132
   -142 -124
   -138 -112
   -134 -104
   -132 -102
   CIMA
   -97 -155
   BAIXO
   -92 -151
   -91 -147
   -89 -142
   -89 -135
   -90 -129
   -90 -128
   CIMA
   -94 -170
   BAIXO
   -83 -171
   -68 -174
   -47 -177
   -30 -172
   -15 -171
   -11 -170
   CIMA
   12 -96
   BAIXO
   9 -109
   9 -127
   7 -140
   5 -157
   9 -164
   22 -176
   37 -204
   40 -209
   49 -220
   55 -229
   57 -235
   57 -238
   50 -239
   49 -241
   51 -248
   53 -249
   63 -245
   70 -243
   57 -249
   62 -250
   71 -250
   75 -250
   81 -250
   86 -248
   86 -242
   84 -232
   85 -226
   81 -221
   77 -211
   73 -205
   67 -196
   62 -187
   58 -180
   51 -171
   47 -164
   46 -153
   50 -141
   53 -130
   54 -124
   57 -112
   56 -102
   55 -98
   CIMA
   48 -164
   BAIXO
   54 -158
   60 -146
   64 -136
   64 -131
   CIMA
   5 -152
   BAIXO
   1 -150
   -4 -145
   -8 -138
   -14 -128
   -19 -119
   -17 -124
   CIMA
   21 -177
   BAIXO
   14 -176
   7 -174
   -6 -174
   -14 -170
   -19 -166
   -20 -164
   CIMA
   -8 -173
   BAIXO
   -8 -180
   -5 -189
   -4 -201
   -2 -211
   -1 -220
   -2 -231
   -5 -238
   -8 -241
   -9 -244
   -7 -249
   6 -247
   9 -248
   16 -247
   21 -246
   24 -241
   27 -234
   27 -226
   27 -219
   27 -209
   27 -202
   28 -193
   28 -188
   28 -184
   CIMA
   -60 -177
   BAIXO
   -59 -186
   -57 -199
   -56 -211
   -59 -225
   -61 -233
   -65 -243
   -66 -245
   -73 -246
   -81 -246
   -84 -246
   -91 -245
   -91 -244
   -88 -231
   -87 -225
   -85 -218
   -85 -211
   -85 -203
   -85 -193
   -88 -185
   -89 -180
   -91 -175
   -92 -172
   -93 -170
   CIMA
   -154 -93
   BAIXO
   -157 -87
   -162 -74
   -168 -66
   -172 -57
   -175 -49
   -178 -38
   -178 -26
   -178 -12
   -177 4
   -175 17
   -172 27
   -168 36
   -161 48
   -161 50
   CIMA
   -217 178
   BAIXO
   -217 178
   -217 177
   -215 176
   -214 175
   -220 177
   -223 178
   -223 178
   -222 178
   CIMA
   -248 185
   BAIXO
   -245 184
   -240 182
   -237 181
   -234 179
   -231 177
   -229 176
   -228 175
   -226 174
   -224 173
   -223 173
   -220 172
   -217 172
   -216 171
   -214 170
   -214 169
   CIMA
   -218 186
   BAIXO
   -195 173
   -183 165
   -175 159
   -164 151
   -158 145
   -152 139
   -145 128
   -143 122
   -139 112
   -138 105
   -134 95
   -131 88
   -129 78
   -126 67
   -125 62
   -125 54
   -124 44
   -125 38
   -126 30
   -125 27
   -125 8
   -126 5
   -125 -9
   -122 -15
   -115 -25
   -109 -32
   -103 -39
   -95 -42
   -84 -45
   -72 -47
   -56 -48
   -41 -47
   -31 -46
   -18 -45
   -1 -44
   9 -43
   34 -45
   50 -52
   67 -61
   83 -68
   95 -80
   112 -97
   142 -115
   180 -132
   200 -146
   227 -159
   259 -175
   289 -185
   317 -189
   349 -190
   375 -191
   385 -192
   382 -196
   366 -199
   352 -204
   343 -204
   330 -205
   315 -209
   296 -212
   276 -214
   252 -208
   237 -202
   218 -197
   202 -193
   184 -187
   164 -179
   147 -173
   128 -168
   116 -164
   102 -160
   88 -158
   78 -159
   69 -162
   57 -164
   56 -165
   51 -165
   CIMA
   68 -144
   BAIXO
   83 -143
   96 -141
   109 -139
   119 -146
   141 -150
   161 -155
   181 -163
   195 -169
   208 -179
   223 -187
   241 -191
   247 -193
   249 -194
   CIMA
   -6 -141
   BAIXO
   -15 -146
   -29 -150
   -42 -154
   -51 -153
   -60 -152
   -60 -152
   CIMA
   -90 -134
   BAIXO
   -85 -131
   -79 -128
   -78 -123
   -80 -115
   -82 -106
   -80 -101
   -76 -101
   CIMA
   -81 -132
   BAIXO
   -76 -130
   -71 -126
   -72 -124
   CIMA
   43 -118
   BAIXO
   44 -125
   47 -135
   41 -156
   37 -160
   40 -166
   47 -171
   47 -171
   CIMA
   -106 -153
   BAIXO
   -107 -167
   -106 -178
   -109 -192
   -114 -198
   -116 -201
   </pre>
   mysteryt.dat
   
