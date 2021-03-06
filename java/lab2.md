---
layout: default
title: Lab 2 de MAB 240
relpath: ..
---

MAB 240 - Computação II
=======================

Laboratório 2 - 04/05/2016
--------------------------

A classe `Motor` sofreu pequenas mudanças, para o uso das teclas de seta
poder funcionar. Baixe o novo arquivo [aqui](Motor.java), e copie ele
para a pasta do seu projeto.

Esse laboratório é uma continuação do [laboratório 1](lab1.html) da semana
passada, então faça uma revisão do que foi pedido no laboratório 1, e comece
terminando de implementar o que foi pedido lá. Depois prossiga para o que
está abaixo.

Nesse laboratório o objetivo é implementar o movimento do sapo (respondendo aos comandos
do teclado), assim como a colisão entre os sapos e os carros.

O movimento do sapo pode ser para cima, para baixo, para a esquerda, ou para a direita, usando
as setas. Quando uma das setas é pressionada o motor de jogo chama o método `tecla(String s)` da classe
`Jogo`, passando "up", "down", "left", ou "right", a depender se a tecla foi seta para cima, para baixo,
para a esquerda ou para a direita.

O sapo se move em "saltos" de 100 pixels, mas o salto não é instantâneo:
ele leva cerca de *1/3* de segundo para completar. Uma maneira simples de implementar isso
é fazer o sapo ter duas posições (cada uma composta por sua vez de uma coordenada x e uma
coordenada y): a primeira posição é onde o sapo está, a segunda (a "meta") é para onde ele tem que se
mover. Inicialmente essas duas posições são iguais.

As teclas de salto atualizam a segunda posição. A cada tique do relógio, as duas posições
são comparadas coordenada a coordenada, e se forem diferentes a primeira posição é atualizada
fazendo o sapo se mover na direção onde ele tem que ir, com uma velocidade de 300 pixels por
segundo (ou seja, ele vai se deslocar `300*dt` em cada coordenada).

Caso o sapo salte além dos cantos esquerdo ou direito da tela ele deve aparecer do outro lado, do mesmo
modo que os carros. A solução para esse problema não é difícil, mas é sutil. Pensem bem a respeito. O modo
mais fácil é implementar essa lógica no método que faz o sapo se mover em direção à sua "meta". Se o sapo já
chegou na calçada superior um salto para cima não deve fazer ele se mover mais para cima. O mesmo em relação
à calçada inferior e saltos para baixo.

A colisão deve ser verificada no método de atualização do jogo, após todo o movimento
ter sido feito. Use a classe [Hitbox](Hitbox.java) dada em sala para detectar as colisões.
Uma colisão do sapo com um dos carros faz o contador de vidas diminuir
em 1, e o sapo deve retornar para a posição inicial. Se o contador estiver em
0 no momento da colisão então o jogo termina: deve ser exibida uma mensagem de "GAME OVER"
no centro da tela, e o sapo some (os carros continuam se movendo).

Enviando
--------

Use [esse link](https://www.dropbox.com/request/j3Mu1Uk452XbQ8sprywA)
 para enviar os Laboratórios 1 e 2. O prazo para envio é quarta-feira, dia **18/05/2016**.

* * * * *

Última Atualização: {{ site.time | date: "%Y-%m-%d %H:%M" }}
