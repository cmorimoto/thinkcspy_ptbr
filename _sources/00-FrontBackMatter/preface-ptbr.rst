..  Copyright (C)  Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".


Prefácio à terceira edição
==========================

por Jeffrey Elkner



A edição local de Rhodes (RLE)
==============================

por Peter Wentworth

.. Admonition:: Uma palavra de agradecimento ...

    Mudamos de Java para Python em nossos cursos introdutórios há um
    ano atrás e até agora pensamos que os resultados são
    positivos. Mais, o tempo dirá. 

    Este livro foi um grande ponto de partida para nós, especialmente
    por causa da permissão liberal para mudar as coisas. Ter nossas
    próprios notas de aula internas ou folhetos nos permite adaptar e
    ficar atualizados, reorganizar, ver o que funciona,
    e nos dá agilidade. Nós também podemos garantir que todos os
    alunos do curso recebam uma cópia das apostilas --- algo que não
    acontece sempre ao prescrever livros caros em um país em
    desenvolvimento ou do terceiro mundo.

    Muito obrigado a todos os contribuintes e os autores por tornar
    público o seu árduo trabalho, disponibilizando-o à comunidade
    Python e aos nossos alunos. 

Um colega e amigo, Peter Warren, uma vez fez a observação de que um curso
introdutório de programação é tanto sobre o ambiente quanto sobre a
linguagem de programação.

Eu sou um grande fã de IDEs (Integrated Development Environments ---
ambientes de desenvolvimento integrado). Eu quero que a ajuda seja 
integrada no meu editor, como um cidadão de primeira classe,
disponível ao simples toque de um botão.
Quero que a sintaxe seja destacada.
Quero que os comandos sejam verificadas imediatamente e que as
palavras sejam completadas automaticamente de forma sensata.

Eu gosto particularmente de ter um depurador de programa passo-a-passo
com breakpoints e com inspeção
de código embutido. Estamos tentando construir um modelo conceitual de
execução de programas na mente do aluno, por isso eu acho mais útil
para o ensino ter as variáveis e a pilha de
chamadas explicitamente visíveis,
e de ser capaz de inspecionar imediatamente o resultado da
execução de um comando.

Minha filosofia, então, é não olhar para uma linguagem para ensinar,
mas para procurar por uma combinação de IDE e de linguagem que venham
empacotadas juntas e avaliadas como um todo.

Eu fiz algumas alterações bastante profundas no livro original para
refletir isso (e vários outros pontos de vista que sustento), e eu não
tenho nenhuma dúvida de que mais 
alterações seguirão se chegarmos às versões 2, 3 ou 4 do RLE.

Aqui estão algumas das principais coisas que abordei de forma diferente:

* Nossa situação local exige que um grande número de alunos de cursos de
  serviço façam um curso introdutório de apenas 3 ou 4 semanas, e
  então continuamos em outro semestre com os alunos
  do nosso programa principal. Assim, o livro é dividido em duas
  partes: nós cobrimos os cinco primeiros capítulos no curso geral
  para "molhar as canelas", e o resto do material em um semestre separado. 
* Estamos usando Python 3. É mais limpo, mais orientada a objeto, e
  tem menos irregularidades ad-hoc do que as versões anteriores do Python.
* Estamos usando PyScripter como nosso IDE, no Windows. E ele está
  integrado a partes dessas notas, com imagens de telas, etc. 
* Eu não uso mais GASP.
* Para os gráficos, começamos com o módulo Turtle. Com o avanço do
  curso, usamos PyGame para gráficos avançados. (Nesta revisão, o 
  exercícios e tutoriais sobre o PyGame ainda não foram incluídos.)
* Eu tentei introduzir noções de orientação a objetos mais cedo, sem
  pedir aos alunos para sintetizar objetos ou escrever suas próprias
  classes. Assim, por exemplo, no capítulo sobre o módulo turtle, criamos
  várias instâncias de Turtle, falamos sobre os seus atributos e
  estado (cor, posição, etc), e incentivamos o estilo de chamada de
  método para mover as tartarugas, ou seja, ``tess.forward(100)``.
  Da mesma forma, quando usamos números aleatórios, evitamos o "hidden
  singleton generator" no módulo random --- criamos uma instância de
  um gerador e invocamos os métodos da instância. 
* A facilidade para construir listas o laço ``for`` parecem ser
  vencedores no Python, por isso, em vez de usar o comando tradicional
  ``input`` para leitura de dados da linha de comando, dei preferência
  pelo uso de loops e listas logo de início, como:

  .. sourcecode:: python
  
        friends = ["Amy", "Joe", "Bill"]
        for f in friends:
           invitation = "Hi " + f + ".  Please come to my party on Saturday!"
           print(invitation)
	   
  Isto também significa que eu empurrei ``range`` para uma exposição
  precoce. Prevejo que, com o tempo, vamos ver mais oportunidades para
  explorar listas e iteração mais cedo, em suas formas mais simples.
* Joguei fora ``doctest``: é um pouco peculiar para o meu gosto. Por
  exemplo, ele falha um teste se o espaçamento entre os elementos da
  lista não é precisamente a mesma do string de saída, ou se o Python
  imprime um string com aspas simples, mas você escreveu o caso de
  teste com aspas duplas.
  Casos como esses também confunde bastante os alunos (e
  instrutores)::

      def sum(xs):
         """
           >>> xs = [2, 3, 4]
           >>> sum(xs)
           9
         """
        ...
   
   Se você pode explicar a diferença nas regras de escopo e tempo de
   vida entre o parâmetro ``xs`` e a variável doctest ``xs``
   elegantemente, por favor me avise. (Sim, eu sei que doctest cria
   seu próprio escopo sem a gente perceber, mas isso é confuso. Parece que
   os doctests são aninhados dentro do escopo da função, mas não são. Os
   alunos pensam que o parâmetro recebe seu valor pela atribuição no
   doctest!)
   
   Eu também acho que manter o conjunto de testes separado das funções
   sob teste leva a uma relação mais clara entre função chamadora e
   função chamada, e dá uma maior chance de ensinar os conceitos sobre
   parâmetros / passagem de argumentos corretamente.

   Há um bom módulo para unidades de teste em Python, (e o PyScripter
   oferece suporte integrado para ele, com geração automatizada de
   esqueletos de módulos de teste), mas isso parecia demasiado avançado
   para iniciantes pois exige conceitos multi-módulo.

   Assim eu dei preferência para a minha própria estrutura de teste no
   Capítulo 6 (cerca de 10 linhas de código) que os alunos devem inserir em
   qualquer arquivo que eles estejam trabalhando.
* Eu removi, sempre que possível, entrada / processo / saída via linha
  de comando. Muitos dos nossos alunos nunca viu um terminal de linha
  de comando, que pode ser muito intimidante.
* Voltamos para uma abordagem mais "clássica / estática" para escrever
  as nossas classes e objetos. O Python (em companhia de linguagens como
  Javascript, Ruby, Perl, PHP, etc.) realmente não enfatizar noções de
  classes "fechadas" ou membros "privados", ou mesmo "instâncias
  seladas". 

  Assim, uma abordagem de ensino é alocar cada instância como um
  recipiente vazio e, posteriormente, permitir que os clientes
  externos da classe procurem novos membros (métodos ou atributos) em
  diferentes instâncias, como eles desejarem. É uma abordagem muito
  dinâmica, mas talvez uma que não incentiva o pensamento em
  abstrações, camadas, contratos, dissociação, etc. Pode até ser o
  tipo de coisa que se poderia escrever um daqueles artigos sobre
  *"x, y, z ... são considerados nocivos"*.

  Em nossa abordagem mais conservadora, colocamos um inicializador em
  cada classe, determinamos durante a instanciação do objeto que
  membros queremos, e inicializamos a instância de dentro da
  classe. Então ficamos mais próximos em filosofia de C# / Java.

* Nosso próximo passo pretendido é introduzir mais algoritmos no
  curso. O Python é uma linguagem de ensino eficiente --- podemos
  fazer um progresso rápido. Mas com os ganhos que obtemos, ao invés
  de investir em "mais coisas do Python", queremos nos aprofundar em
  resolução de problemas e algoritmos mais complexos. Isto irá
  provavelmente ser separado do texto principal, talvez em um adendo
  ou apêndice. 

