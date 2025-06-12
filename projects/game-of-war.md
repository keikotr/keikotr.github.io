---
layout: project
type: project
image: img/game-of-war/war-project-icon.jpg
title: "Simple game of War"
date: 2022-03-04
published: false
labels:
  - Java
  - Game
summary: "A simple card game of War for my ICS 211 class."
---

<img class="img-fluid" src="../img/game-of-war/war-header.jpg" alt="Playing cards with a king of spades as the center card.">

The main purpose of this project was to use abstract data structures to simulate a simple card game of <a href="https://bicyclecards.com/how-to-play/war/">War</a>.

The goal of War is to be the first player to win all 52 cards. A deck of cards is divided evenly with each player receiving 26 cards, dealt one at a time face down. Each player will turn up a card at the same time and the player with the higher card value takes both cards face down on the bottom of their stack. If the cards are the same rank, war is initiated. Each player will place three cards down and one card up. The player with the higher faced-up card wins the war, takes all the cards, and places them on the bottom of their pile.

My role was to create a program that simulates a card game of War given these files:
- <a href="http://courses.ics.hawaii.edu/ics211s22/morea/090.stacks/IStack211.java">IStack211</a>: An interface that includes methods for implementing our own stack data structure.
- <a href="http://courses.ics.hawaii.edu/ics211s22/morea/090.stacks/IGameOfWar.java">IGameOfWar</a>: An interface that includes methods for starting the game, rounds, and players' decks.
- <a href="http://courses.ics.hawaii.edu/ics211s22/morea/090.stacks/Rank.java">Rank.java</a>: An enumeration of the ranks of cards from TWO through ACE.
- <a href="http://courses.ics.hawaii.edu/ics211s22/morea/090.stacks/Suit.java">Suit.java</a>: An enumeration of the suits of cards (CLUBS, DIAMONDS, HEARTS, and SPADES).
- <a href="http://courses.ics.hawaii.edu/ics211s22/morea/090.stacks/Card.java">Card.java</a>: Represents a single card.
- <a href="http://courses.ics.hawaii.edu/ics211s22/morea/090.stacks/Deck.java">Deck.java</a>: Represents a deck of cards.
- <a href="http://courses.ics.hawaii.edu/ics211s22/morea/090.stacks/GameOfWarTest.java">GameOfWarTest</a>: A JUnit test.

The given files were written by my professor and the program that implements the files by my professor was written entirely by me with the help of teaching assistants and various class materials.

While this project did not include any fancy graphics or user interfaces, I learned from this experience that I am capable of creating more kinds of games using more optimal algorithms and utilizing data structures to enhance gameplay efficiency.
