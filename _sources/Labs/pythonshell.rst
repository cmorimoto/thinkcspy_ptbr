.. This work CC  Brad Miller is released under the Creative Commons
   Attribution-ShareAlike License CC BY-SA as well as the GNU FDL 1.3


.. Python Beyond the Browser

Python Além do Navegador
=========================


Embora seja conveniente ter o Python disponível para uso direto no navegador, existem algumas limitações, e o Python é uma linguagem de programação real usada para desenvolver aplicativos reais por empresas muito grandes e impressionantes. Neste tópico avançado, mostraremos como usar o  Python `shell` junto com um editor de texto simples. Em um tópico avançado posterior, apresentaremos a você algo chamado Ambiente de Desenvolvimento Integrado ou IDE (do inglês *integrated development environment*) que vai facilitar muito sua vida quando você for trabalhar em um projeto grande usando Python.


O Python Shell
----------------



Uma das maneiras mais importantes de aprender Ciência da Computação é simplesmente experimentar ou testar as coisas. Ao contrário da química, onde você pode explodir coisas e causar danos reais, na Ciência da Computação, você realmente não pode errar apenas experimentando um pouco. Na pior das hipóteses, talvez você precise reiniciar o computador, mas é muito difícil causar danos duradouros.

Para aqueles que gostam de interfaces gráficas, o Python shell parece um pouco primitivo, mas não se deixe enganar pela falta de uma interface sofisticada, pois o shell lhe permite fazer muitas coisas poderosas. Em um Mac ou Linux, o Python já vem instalado para você. Há um breve link de vídeo no final deste tópico, que explica como baixar e instalar o Python no Windows. Aqui está um exemplo de como o shell se parece depois de inicializado.

.. image::  Figures/python_shell.png


Para executar o Python shell, você primeiro precisará iniciar o program "Terminal". No Mac, você pode encontrar o Terminal dentre os Utilitários, na pasta de Aplicativos.
Na maioria das versões do Linux você pode encontrá-lo no menu de acessórios.
Depois de iniciar um terminal, basta digitar `python` e pressionar a tecla Enter. Para iniciar o shell no Windows, basta ir ao menu Iniciar e escolher
`Python (linha de comando)` no menu.


Agora que você iniciou o Python shell, pode se perguntar o que pode fazer com ele.
No shell, você pode fazer qualquer coisa que você faria em um programa Python. Qualquer dos exemplos que você viu neste capítulo podem ser digitados diretamente no shell.
Qualquer expressão Python pode ser inserida no shell e você verá
o resultado impresso para você logo abaixo. Aqui estão alguns exemplos
usando as funções e expressões apresentadas neste capítulo.


.. image:: Figures/shell_expressions.png



É uma boa idéia adquirir o hábito de usar o shell. Muitas vezes se você
tiver uma dúvida sobre como algo funciona, você pode esclarecer sua dúvida para você mesmo, simplesmente experimentando no shell. Se você precisar de uma calculadora realmente poderosa, você pode simplesmente iniciar seu shell e usá-lo para calcular praticamente qualquer coisa. Em breve você se encontrará escrevendo pequenos programas em Python para resolver todos os tipos de coisas.


Executando um programa em Python
---------------------------------

Obviamente, o problema com o Python shell é que você não pode salvar nada,
então você sempre precisará redigitar o que quiser fazer novamente. É também
difícil fazer algo além de algumas linhas, porque se você fizer um erro de digitação, você acaba tendo de repetir tudo. Felizmente, existe uma solução para isso também. O Python permite que você escreva um programa e salve-o como um arquivo de texto com a extensão `.py` e, em seguida, você pode executar esse programa diretamente da linha de comando.

Aqui está um exemplo simples de um programa Python.

.. sourcecode::  python

    print('Hello World')
    print('2 + 3 = ', 2+3)


Vamos supor que você digitou as linhas acima usando um editor como o Bloco de Notas ou TextEdit ou algum editor semelhante. Mas se você já conhece o emacs ou vi, então você é incrível! Agora salve o arquivo como `testprog1.py` e volte ao terminal. Agora digite `python testprog1.py` na linha de comando do terminal, e você verá a seguinte saída

.. sourcecode:: python

    bmiller@chronos> python testprog1.py
    Hello World
    2 + 3 =  5


Tudo o que fizermos nos próximos capítulos que apareça em janela de edição dentro do seu navegador,  pode ser feito exatamente da mesma forma no terminal (shell), assim como o pequeno exemplo acima. Este exemplo ilustra uma diferença muito importante entre inserir expressões no Python shell e escrever um programa em Python. O Python shell usa o que chamamos de *loop* de leitura-avaliação-impressão. Isto é, o Python **lê** uma expressão na linha de comando,
então **avalia** essa expressão e, finalmente, **imprime** o resultado. Em um
programa Python que você executa usando o interpretador Python,
você precisa ser explícito sobre o que deseja imprimir. É por isso que em
um programa Python usamos a função `print` nas duas linhas do arquivo.


Instalando Python no Windows
----------------------------

Se você estiver usando Windows, precisará instalar o Python por conta própria. Esse é um vídeo que explica como fazê-lo.

.. raw:: html

    <iframe width = "425" height = "349" src = "http://www.youtube.com/embed/9EfGpN1Pnsg"
            frameborder = "0" allowfullscreen> </iframe>

Estamos assumindo que você vai usar o Python 3.x. No momento em que escrevo esse texto, a versão mais atual é o Python 3.2.1. Este link mostra como atualizar ou instalar
Python no Linux, Mac ou Windows. 

`Installing Python <https://diveintopython3.net/installing-python.html>`_


Glossário
---------

.. glossary::

    terminal
        Um terminal é um programa não muito popular hoje em dia, mas não há muitos anos atrás, os cientistas da computação faziam seu trabalho em um dispositivo de hardware chamado terminal. O terminal era conectado por cabo ou linha telefônica a um computador em algum outro lugar. Sim, a internet nem sempre esteve por aqui.

    linha de comando
        O termo "linha de comando" geralmente é usado como sinônimo de terminal, pois quando você estiver usando o terminal, você também está usando a linha de comando. É o lugar onde você digita comandos e, em seguida, o computador interpreta os comandos e responde imprimindo os resultados.
