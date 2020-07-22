..  Copyright (C)  Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".


Prefácio da primeira e segunda edições
========================================

por Jeffrey Elkner

Este livro deve sua existência à colaboração tornada possível pela Internet e o movimento do software livre. Seus três autores --- um professor universitário, um professor de escola média, e um programador profissional --- nunca se encontraram cara a cara para trabalhar no livro, mas temos sido capazes de colaborar estreitamente, auxiliado por muitas outras pessoas que tomaram seu tempo e energia para nos enviar o seu feedback.

Nós pensamos que este livro é um testemunho dos benefícios e possibilidades futuras deste tipo de colaboração, o arcabouço para o qual tenha sido posto em prática por
Richard Stallman e da Free Software Foundation.


Como e por que eu vim a usar Python
-----------------------------------

Em 1999, o exame College Board's Advanced Placement (AP) em Ciência da Computação foi dado em C++ pela primeira vez. Como em muitas escolas de ensino médio em todo o país, a decisão de mudar linguagens teve um impacto direto no currículo de ciência de computação da Yorktown High School, em Arlington, Virginia, onde eu leciono.
Até este ponto, Pascal era a língua de ensino, tanto para o
primeiro ano quanto nos cursos avançados. De acordo com as práticas do passado de dar aos estudantes dois anos de exposição para a mesma língua, nós tomamos a decisão de mudar para C++ no primeiro ano de curso para o ano escolar de 1997-1998 para que estivéssemos em sintonia com a mudança do exame AP no ano seguinte.

Dois anos mais tarde, eu estava convencido de que C++ foi uma má escolha para
introduzir os alunos à ciência da computação. Embora seja certamente uma poderosa
linguagem de programação, ela também é uma linguagem extremamente difícil de aprender e ensinar. Encontrei-me constantemente lutando com a sintaxe difícil do C++ e suas
várias maneiras de fazer as coisas, e eu estava perdendo muitos alunos desnecessariamente como resultado. Convencido de que deveria existir uma linguagem melhor para o nosso curso do primeiro ano, fui à procura de uma alternativa para C++.

Eu precisava de uma linguagem que pudesse rodar nas máquinas em nosso laboratório de GNU/Linux, bem como nas plataformas Windows e Macintosh que a maioria dos alunos tinham em casa. Eu queria que fosse software livre, para que os alunos pudessem usá-lo em casa, independentemente de sua renda. Eu queria uma linguagem que fosse usado por programadores profissionais, e que tivesse uma comunidade ativa de desenvolvedores em torno dela. Tinha que suportar tanto programação procedural quanto orientada a objetos. E o mais importante, ela tinha que ser fácil de aprender e ensinar. Quando eu investiguei as escolhas com essas metas em mente, Python se destacou como o melhor candidato.

Perguntei a um dos estudantes talentosos de Yorktown, Matt Ahrens, para fazer uma tentativa em Python. Em dois meses ele não só aprendeu a língua, mas escreveu uma aplicação chamada pyTicket que permitiu que a nossa equipe relatar problemas de tecnologia através da Web. Eu sabia que Matt não poderia ter finalizado uma aplicação daquele porte em tão pouco em C++, e esta realização, combinada com a avaliação positiva de Matt sobre Python, sugeriu que Python era a solução que eu estava procurando.


Encontrar um livro didático
---------------------------

Tendo decidido usar Python em minhas duas turmas de introdução à ciência da computação no ano seguinte, o problema mais urgente era a falta de um
livro didático.

O conteúdo livre veio para o resgate. No início do ano, Richard Stallman 
me apresentou a Allen Downey. Ambos havíamos escrito a Richard expressando
interesse em desenvolver materiais educativos livres. Allen já tinha escrito um
livro introdutório de ciência da computação, *Como pensar como um cientista da computação*.
Quando eu li este livro, eu soube imediatamente que eu queria usá-lo em minha classe.
Ele foi o texto mais claro e mais útil de ciência da computação que eu tinha visto. Ele enfatizava os processos de pensamento envolvidos na programação e não as
características de uma determinada linguagem. Lê-lo me tornou um melhor
professor imediatamente.

*Como pensar como um cientista da computação* não era apenas um livro excelente, mas
tinha sido liberado sob a licença pública GNU, o que significava que ele poderia ser usada livremente e modificado para atender às necessidades de seu usuário. Uma vez que eu decidi usar Python, ocorreu-me que eu poderia traduzir a versão Java original de Allen do livro para uma nova linguagem. Enquanto eu não teria sido capaz de escrever um livro sozinho, tendo o livro de Allen para trabalhar tornou possível para mim fazê-lo, ao mesmo tempo que demonstra que o modelo de desenvolvimento cooperativo
tão bem utilizado em software também poderia trabalhar para materiais educativos.

Trabalhar neste livro nos últimos dois anos tem sido gratificante tanto para os meus alunos quanto para mim, e meus alunos desempenharam um papel importante no processo. Como eu podia fazer mudanças instantâneas sempre que alguém encontrasse um erro de ortografia ou passagem difícil, encorajei-os a procurar erros no livro, dando-lhes um
ponto de bónus cada vez que uma sugestão resultasse numa alteração no
texto. Isto teve o duplo benefício de incentivá-los a ler o texto com mais
cuidado e de ter o texto totalmente revisado por seus críticos mais importantes, os alunos que o utilizam para aprender ciência da computação.

Para a segunda metade do livro sobre programação orientada a objetos, eu sabia que
alguém com experiência em programação mais real do que a minha
seria necessário para fazer-lo direito. O livro permaneceu em estado inacabado durante quase um ano até que a comunidade de código aberto mais uma vez fornecesse os meios necessários para a sua conclusão.

Eu recebi um email de Chris Meyers manifestando interesse no livro. Chris é um programador profissional que começou a ensinar um curso de programação no ano passado usando Python no Lane Community College em Eugene, Oregon. A perspectiva de
ensinar o curso levou Chris ao livro, e ele começou a ajudar imediatamente. Até o final do ano letivo ele tinha criado um 
projeto paralelo no nosso site em `http://openbookproject.net <http://openbookproject.net>`__ chamado `*Python for Fun* <http://openbookproject.net/py4fun>`__ e foi
trabalhando com alguns dos meus alunos mais avançados como orientador, guiando-os além de onde eu poderia levá-los.


Introduzindo programação com Python
-----------------------------------

O processo de tradução e usando *Como pensar como um cientista da computação*
nos últimos dois anos confirmou a adequação do Python para o ensino de
estudantes iniciantes. O Python simplifica bastante os exercícios de programação e torna idéias importantes de programação mais fáceis de ensinar.

O primeiro exemplo do texto ilustra este ponto. É o tradicional programa "hello, world", que na versão Java do livro se parece com:

.. sourcecode:: java 

    class Hello {

      public static void main (String[] args) {
          System.out.println ("Hello, world.");
      }
    }

que na versão Python se torna:

.. sourcecode:: python
    
    print "Hello, World!"

Mesmo que este seja um exemplo trivial, as vantagens do Python se destacam.
O curso Ciência da Computação I de Yorktown não tem pré-requisitos, de forma que muitos dos alunos que veem esse exemplo estão olhando para o seu primeiro programa. Alguns deles ficam, sem dúvida, um pouco nervosos, tendo ouvido que a programação de computadores é difícil de aprender. A versão Java sempre me forçou a escolher entre duas opções insatisfatórias: ou explicar os comandos `class Hello`, `public static void main`, `String[] args`, `{`, e `}`, correndo o risco
de confundir ou intimidar alguns dos alunos logo no início, ou simplesmente dizer para não se preocupar com todas essas coisas agora; vamos falar sobre isso
mais tarde, e correr o mesmo risco. Os objetivos educacionais neste momento no
curso é apresentar aos alunos a idéia de uma instrução de programação e
levá-los a escrever seu primeiro programa, introduzindo-os assim ao
ambiente de programação. O Python tem exatamente o que é necessário
para fazer essas coisas e nada mais.

Comparando-se o texto explicativo do programa em cada versão do livro ilustra melhor o que isso significa para o aluno iniciante. Há sete parágrafos de explicação do "Hello world!" na versão Java; na versão Python, existem apenas algumas frases. Mais importante, os seis parágrafos que faltam não se tratam de grandes idéias em programação de computadores, mas de minúcias da sintaxe de Java. Eu encontrei a mesma coisa acontecendo ao longo de todo o livro. Parágrafos inteiros simplesmente desaparecem da versão Python do texto porque a sintaxe muito mais clara do Python os torna desnecessários.

Usando uma linguagem de muito alto nível como Python, permite ao professor adiar
falar sobre detalhes de baixo nível da máquina até que os alunos tenham os fundamentos necessários para fazer melhor sentido dos detalhes. Ela cria assim
a capacidade de colocar as primeiras coisas primeiro pedagogicamente. Um dos melhores exemplos disso é a maneira do Python lidar com as variáveis. Em Java uma variável é um nome para um lugar que tem um valor se for um tipo nativo, e uma referência para um objeto caso contrário. Explicar esta distinção requer uma discussão
de como o computador armazena dados. 
Assim, a idéia de uma variável está ligada ao hardware da máquina.
O conceito fundamental e poderoso de variável já é difícil o suficiente para alunos iniciantes (tanto em ciência da computação quanto álgebra). Bytes e endereços não ajudam o assunto. Em Python uma variável é um nome que se refere a uma coisa. Este é um conceito muito mais intuitivo para alunos iniciantes e está muito mais próximo do significado da variável que aprenderam em seus cursos de matemática. Eu tive uma dificuldade bem menor para ensinar variáveis neste ano que no passado, e eu perdi menos tempo ajudando os alunos com problemas para usá-las.

Outro exemplo de como Python ajuda no ensino e aprendizagem de programação está na sua sintaxe para funções. Meus alunos sempre tiveram uma dificuldade grande para entender funções. O principal problema gira em torno da diferença entre a definição de uma função e uma chamada de função, e a distinção relacionada entre um parâmetro e um argumento. Python vem para o resgate com uma sintaxe nada menos que linda.
As definições de função começam com a palavra-chave ``def``, então eu simplesmente digo aos meus alunos, Quando você define uma função,
comece com ``def``, seguido do nome da função que você está definindo;
quando você chamar uma função, basta chamar (escrever) o seu nome. Parâmetros vão com 
definições; argumentos vão com as chamadas. Não existem tipos de retorno, tipos de parâmetros, ou parâmetros por valor ou referência para atrapalhar, então eu agora sou capaz de ensinar funções em menos de metade do tempo que isto me tomava anteriormente, com melhor compreensão.

O uso de Python melhorou a eficácia do nosso programa de ciência da computação para todos os alunos. Eu notei um nível de sucesso geral mais elevado e um menor nível de
frustração do que eu sentia ensinando com C++ ou Java. Eu avancei mais rápido
com melhores resultados. Mais alunos concluíram o curso com a capacidade de criar
programas significativos e com uma atitude positiva com relação à experiência de
programação que isso traz.


Construindo uma comunidade
--------------------------

Tenho recebido e-mails de todo o mundo de pessoas que usam este livro para
aprender ou ensinar programação. Uma comunidade de usuários começou a surgir, e muitas pessoas têm contribuido para o projeto pelo envio de materiais para a 
sítio em `http://openbookproject.net/pybiblio <http://openbookproject.net/pybiblio>`__.

Com o contínuo crescimento do Python, espero que o crescimento da comunidade de usuários continue e acelere. O surgimento desta comunidade de usuários e a
possibilidade que isso sugere de colaboração semelhante entre educadores tem sido para mim as partes mais interessantes de trabalhar neste projeto. Trabalhando juntos,
podemos aumentar a qualidade dos materiais disponíveis para nosso uso e economizar tempo valioso. Convido você a se juntar à nossa comunidade e estamos ansiosos para ouvir você.
Por favor, escreva-me para `jeff@elkner.net <mailto:jeff@elkner.net>`__.

| Jeffrey Elkner
| Governor's Career and Technical Academy in Arlington 
| Arlington, Virginia

