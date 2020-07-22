..  Copyright (C)  Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. Configuring Ubuntu for Python Development
.. =========================================

Configurando Ubuntu para Desenvolvimento em Python
==================================================

    ..
       *Note:* the following instructions assume that you are connected to
       the Internet and that you have both the ``main`` and ``universe``
       package repositories enabled.  All unix shell commands are assumed to
       be running from your home directory ($HOME).  Finally, any command that
       begins with ``sudo`` assums that you have administrative rights on your
       machine.  If you do not --- please ask your system administrator about
       installing the software you need.

    *Nota:* as instruções a seguir supõem que você está conectado a
    Internet e que você tem os repositórios de pacotes ``main`` e
    ``universe``habilitados.  É suposto que todos os shells de
    comandos unix são executados a partir do se *home directory*
    ($HOME). Finalmente, todo comando que começa dom ``sudo`` supõe
    que você tem poderes de administrador do seu computador. Se você não
    tem --- por favor peça ao administrador para instalar os programas
    necessários.


..
   What follows are instructions for setting up an Ubuntu 9.10 (Karmic) home
   environment for use with this book. I use Ubuntu GNU/Linux for both development
   and testing of the book, so it is the only system about which I can personally
   answer setup and configuration questions.

A seguir estão instruções para configurar o ambiente do Ubuntu 9.10 (Karmic)
para usar com este livro (N.d.T. mais recente do Ubuntu é 14.10 (Utopic)).
Eu uso Ubuntu GNU/Linux para ambos desenvolvimento e teste deste livro, 
logo este é apena o sistema sobre o qual eu posso pessoalmente responder 
questões sobre configuração.

..
   In the spirit of software freedom and open collaboration, please contact me if
   you would like to maintain a similar appendix for your own favorite system. I'd
   be more than happy to link to it or put it on the Open Book Project site,
   provided you agree to answer user feedback concerning it.


No espírito de software livre e colaboração aberta, por favor, contacte-me se 
se você desejar manter um apêndice similar para o seu sistema favorito. 
Eu ficarei mais do que feliz em colocar um link para ele no projeto do livro aberto
(*Open Book Project*), contanto que você concorde em responder algumas questões
de retorno em relação a ele.

Obrigado!

.. Thanks!

| `Jeffrey Elkner <mailto:jeff@elkner.net>`__
| Governor's Career and Technical Academy in Arlington 
| Arlington, Virginia


Vim
---

..
   `Vim <http://www.vim.org>`__ can be used very effectively for Python
   development, but Ubuntu only comes with the `vim-tiny` package installed by
   default, so it doesn't support color syntax highlighting or auto-indenting.

`Vim <http://www.vim.org>`__ pode ser usado muito efetivamente para o desenvolvimento
de programas em Python, mas Ubuntu vem apenas com o pacote `vim-tiny` instalado por 
default, assim ele não suporta o sistema de coloração ou auto tabulação do programa.

.. To use Vim, do the following:

Para usar Vim, faça o seguinte:

..
   #. From the unix command prompt, run::

#. Na linha de comando do prompt do unix execute::

       $ sudo apt-get install vim-gnome

#. Crie um arquivo em seu diretório (*home directory*) chamado `.vimrc` 
que contém::

       syntax enable
       filetype indent on
       set et
       set sw=4
       set smarttab
       map <f2> :w\|!python %

.. 
   #. Create a file in your home directory named `.vimrc` that contains the
      following::

..
   When you edit a file with a `.py` extension, you should now have color systax
   highlighting and auto indenting. Pressing the key should run your program, and
   bring you back to the editor when the program completes.

Quando você editar um arquivo com a extensão `.py`, você agora texto colorido
de acordo com a sintaxe e tabulação automática. Pressionando a tecla isso deve 
executar o seu programa, e voltar ao editor quando o programa terminar a sua
execu,cão.
 
.. To learn to use vim, run the following command at a unix command
   prompt::

Para aprender a usar vim, execute o seguinte comando no prompt do shell do unix::

    $ vimtutor


.. _installing-gasp:

GASP
----

.. Several of the case studies use GASP (Graphics API for Students for Python),
.. which is the only additional library needed to use this book.

Vários estudos de caso usam GASP (Graphics API for Students for Python),
que é a única biblioteca adicional necessária para usar este livro.

.. To install GASP on Ubuntu 9.04 (Jaunty) or later, run the following command
   at a unix command prompt::

Para instalar GASP no Ubuntu 9.04 (Jaunty) ou versões mais recentes, execute o 
seguinte comando no prompt do shell do unix::

    $ sudo apt-get install python-gasp

.. or use the synaptic package manager.

ou use o administrador de pacotes synaptic.


Getting GASP from Launchpad
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. To install the latest version of GASP into your home directory, run the
   following commands at a unix command prompt::

Para instalar a última versão do GASP no seu diretório (*home directory*), 
execute os comandos a seguir na linha do prompt do unix::

    $ sudo apt-get install bzr
    $ bzr branch lp:gasp-code    
    

.. `$HOME` environment
.. -------------------

Ambiente `$HOME` 
----------------

.. The following creates a useful environment in your home directory for
   adding your own Python libraries and executable scripts:

O que está a seguir cria um ambiente útil no seu diretório para 
acrescentar suas próprias bibliotecas em Python e *scripts* executáveis:

..
   #. From the command prompt in your home directory, create `bin` and
      `lib/python` subdirectories by running the following commands::

#. Na linha de comando do prompt do unix em seu diretório, crie os 
   subdiretórios `bin` e  `lib/python` executando os seguintes comandos::

        $ mkdir bin lib
        $ mkdir lib/python

.. 
   #. Add the following lines to the bottom of your `.bashrc` in your home
      directory::

      This will set your prefered editor to Vim, add your own `lib/python`
      subdirectory for your Python libraries to your Python path, and add your own 
      `bin` directory as a place to put executable scripts. You need to logout and 
      log back in before your local `bin` directory will be in your `search path
      <http://en.wikipedia.org/wiki/Path_(variable)>`__.

#. Acrescente a linhas a seguir no final do arquivo `.bashrc` que está no 
   seu diretório::

        PYTHONPATH=$HOME/lib/python
        EDITOR=vim
    
        export PYTHONPATH EDITOR

   This will set your prefered editor to Vim, add your own `lib/python`
   subdirectory for your Python libraries to your Python path, and add your own 
   `bin` directory as a place to put executable scripts. You need to logout and 
   log back in before your local `bin` directory will be in your `search path
   <http://en.wikipedia.org/wiki/Path_(variable)>`__.


Making a python script executable and runnable from anywhere
------------------------------------------------------------

On unix systems, Python scripts can be made *executable* using the following
process:

#. Add this line as the first line in the script:

   .. sourcecode:: python
    
       #!/usr/bin/env python

#. At the unix command prompt, type the following to make `myscript.py`
   executable::

       $ chmod +x myscript.py

#. Move `myscript.py` into your `bin` directory, and it will be runnable from
   anywhere.
