# Pong-game-on-RISC-V-with-VGA
This repository belongs to the Mini Project of Max Berglund and Milla Gradin for the KTH course IS1500.

# Description
This repository contains a two-player Pong game written in C-code which can be run on a RISC-V board with a VGA output. The outer switches on the RISC-V board are used to control the player paddles, while other switches can be used to alter the game in different ways such as making the ball move at different speeds or making the paddles behave differently. A player increases their score by making the ball touch the border behind their opponent, and the game ends when a player reaches a certain score. The push button can be used to restart the game.

# Implementation
The Pong game has two main parts of its implementation. 

1. The game logic which can be found in pong.c. The main game loop is although found in labmain.c.
2. The graphical display using VGA that can be found in labmain.c.

The game logic is based upon use of 2D coordinates (x, y) and their respective velocity vectors (dx, dy). The relevant coordinates for the ball and the player paddles are tracked as global integer variables and updated as needed once each 100ms using the main game loop. The game makes use of the switches, push-button and the builtin timer of the RISC-V board. The statuses of all of the switches is checked each loop iteration and if certain switches are activated, different special game modes are enabled which affect the game logic in certain ways. The push-button is used to at any time restart the game.

The graphical display implementation uses the builtin VGA features of the RISC-V board to write different colors to the 320*240 screen. Each main game loop iteration, all pixels on the screen are reset to black and the new position of the ball and player paddles are marked out using white pixels. When the game is finished, the whole screen is made green and a cross is put in the center of the screen to signify that the game is over. The players can at any time see on the 7-segment displays on the actual RISC-V board what the score is, and the surpassed seconds and minutes since the start of the current game.

# How to run
Our version of the Pong game requires a Dtek RISC-V board and an external screen with a VGA input to operate. To load the code to the board, the code must first be compiled by using the 'make' statement in the repository where the files are located. Thereafter you must run the binary file 'main.bin' using the dtekv-tools by writing 'dtekv-run .../.../main.bin', and the game will show up on the screen.

