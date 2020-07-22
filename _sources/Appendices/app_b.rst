..  Copyright (C)  Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. An odds-and-ends Workbook
.. =========================

Etceteras
=========

.. *This workbook is still very much under construction.*

*Este parte do livro ainda está em construção*

.. The Five Strands of Proficiency
.. -------------------------------

Cinco habilidadee para proficiência
-----------------------------------

.. This was an important study commissioned by the President in the USA. It
.. looked at what was needed for students to become proficient in maths.  

Este foi um estudo importante feito por uma comissão da presidência dos EUA.
Ela olha no que é necessário que os estudantes sejam proficientes em matemática.

.. But it is also an amazingly accurate fit for what we need for proficiency
.. in Computer Science, or even for proficiency in playing Jazz! 

Entretanto, é surpreendente absolutamente preciso para o que necessitamos de
proficiência em Ciência da Computação, ou mesmo proficiência em tocar Jazz!



.. image:: Figures/strands.jpg  

#. **Fluência procedural** (*procedural fluency*): Aprenda a sintaxe. 
   Aprenda o tipo. Aprenda o seu caminho entre as suas ferramentas.
#. **Entendimento conceitual** (*conceptual understandig*): entenda a razão das 
   partes se encaixarem como elas se encaixam.
#. **Competência estratégica** (*strategic competence*): Você consegue ver o próximo passo?
   Você pode formular esse problema na sua notação?
   Você pode conduzir a música para onde você deseja?
#. **Raciocínio adaptativo** (*adaptive reasoning*): Você consegue ver como mudar o 
   que você aprendeu para resolver esse novo problema?
#. **Disposição produtiva** (*productive disposition*) Precisamos daquela atitude *Conseguimos fazer!* !
    a. Você habitualmente pensa que vale a pena estudar essas coisas.
    b. Você é constante e disciplinado o suficiente para quebrar em pedaços esse conhecimento novo,
       e colocar em sua horas de prática.
    c. Você desenvolveu um senso de *eficiência* --- que você pode fazer as coisas acontecerem!
 
.. #. **Procedural Fluency:**  Learn the syntax.  Learn to type.  Learn your way around your tools
      Learn and practice your scales.  Learn to rearrange formulae.
.. #. **Conceptual Understanding:**  Understand why the bits fit together like they do.   
.. #. **Strategic Competence:**  Can you see what to do next?  
      Can you formulate this word problem into your
      notation?  Can you take the music where you want it to go?
.. #. **Adaptive Reasoning:** Can you see how to change what you've learnt for this new problem?
.. #. A **Productive Disposition:**  We need that *Can Do!* attitude! 
   .. a. You habitually think it is worthwhile studying this stuff.
   .. b. You are diligent and disciplined enough to grind through the tough stuff, 
         and to put in your practice hours.
   .. c. You develop a sense of *efficacy* --- that you can make things happen!

Verifique http://mason.gmu.edu/~jsuh4/teaching/strands.htm ou 
o livro de Kilpatrick em http://www.nap.edu/openbook.php?isbn=0309069955 

.. Check out http://mason.gmu.edu/~jsuh4/teaching/strands.htm, or 
.. Kilpatrick's book at http://www.nap.edu/openbook.php?isbn=0309069955 
    
    
.. Sending Email
.. -------------

Enviando email
--------------

..
   Sometimes it is fun to do powerful things with Python --- remember
   that part of the "productive disposition" we saw under the 
   five threads of proficiency included *efficacy* --- the sense of 
   being able to accomplish something useful.  Here is a Python
   example of how you can send email to someone. 

Algumas vezes é divertido fazer coisas poderosas com Python ---
lembre-se daquela parte sobre "disposição produtiva"
nos vimos que entre as cinco trilhas de proficiência havia 
*eficiência* --- o senso de ser capaz de fazer algo útil.
Aqui esta um exemplo de como você pode enviar emails para alguém usando 
Python.

.. sourcecode:: python
    :linenos:
    
    import smtplib, email.mime.text
    
    eu = 'joao@my.org.com'                  # coloque o seu email aqui 
    amigo = 'amigo@his.org.com'              # e o email do seu amigo aqui
    your_mail_server = 'mail.my.org.com'    # Pergunte ao admin do sistema

    # Crie um texto contendo o corpo de um email.
    # Você pode lera esse texto de um arquivo.
    msg = email.mime.text.MIMEText("""Oi Amigo,

    Estarei dando uma festa, por favor venha as 20h.
    Traga um pizza e umas bebidas.

    Joao""" )

    msg['From'] = eu              # acrescente um cabeçalho a mensagem
    msg['To'] = amigo
    msg['Subject'] = 'Festa no sabado 21/mar'

    # crie uma conexao com o seu servidor de email
    svr = smtplib.SMTP(your_mail_server)                
    response = svr.sendmail(eu, amigo, msg.as_string())  # envie a mensagem
    if response != {}:
        print("Envio falhou por ", response)
    else:
        print("Mensagem enviada.")

    svr.quit()                                         # feche a conexao

..
   In the context of the course, notice how we use the two objects in
   this program: we create a message object on line 9, and set some attributes 
   at lines 16-18.  We then create a connection object at line 23, and ask it
   to send our message.

No contexto desta disciplina, note como usamos os dois objetos nesse 
programa: nós criamos um objeto mensagem na linha 9 e definimos alguns
atributos nas linha 16-18. Nós então criamos um objeto conexão na linha 23 e
pedidos que ele envie nossa mensagem.     
    
