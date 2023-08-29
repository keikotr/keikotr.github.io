---
layout: project
type: project
image: img/cotton/cotton-square.png
title: "Simple game of War"
date: 2022-03-04
published: true
labels:
  - Java
  - Game
summary: "A simple card game of War for my ICS 211."
---

<img class="img-fluid" src="../img/cotton/cotton-header.png">

This project was about using abstract data structures to simulate a simple card game of War.

The goal of War is to be the first player to win all 52 cards. A deck of cards is divided evenly with each player receiving 26 cards, dealt one at a time face down. Each player will turn up a card at the same time and the player with the higher card value takes both cards face down on the bottom of their stack. If the cards are the same rank, war is initiated. Each player will place three cards down and one card up. The player with the higher faced-up card wins the war, takes all the cards, and places them on the bottom of their pile.

My role was to create a program that simulates a card game of War with these files:
- IStack211<E>: An interface which we had to create a class Stack<E> that implements it.
- IGameOfWar: An interface that includes starting the game, rounds, and players' decks.
- Rank.java: An enumeration of the ranks of cards from TWO through ACE.
- Suit.java: An enumeration of the suits of cards (CLUBS, DIAMONDS, HEARTS, and SPADES).
- Card.java: Represents a single card.
- Deck.java: Represents a deck of cards.
- GameOfWarTest: A JUnit test.

The given files were written by my professor and the program that implements the files by my professor was written entirely by me with the help of teaching assistants and various class materials written by the professor.

While this project did not include any fancy graphics or user interfaces, I learned from this experience that I am capable of creating more simple-to-follow games using more optimal algorithms and utilizing data structures.
