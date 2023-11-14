---
comments: false
layout: post
title: Week0 Update
description: What I have accomplished after Week0
type: hacks
courses: { csp: {week: 0}}
---
 
# Week0 Update

## Uses of Tools

Github: Github is where we store our code in repositories and can view a shorthand version of our code.

VScode: An interactive code editor which can help with editing and organizing basic functionality.

Jupyter Notebooks: An interactive shell that makes it easy to develop code in Javascript and Python for all sorts of things. 

## Errors and Problems I Faced:

Biggest problem I faced was trying to get my make command to run so that I could access my website through the web user interface. At the beginning I was working toward figuring out the setup process which worked really well when I was able to successfully install everything. I was pretty familiar with the linux terminal, as I have operated linux machines countless times. However, after the first tech talk, there was an issue regarding my make command. Throughout the whole session and day I was trying to figure out the problem. Until I realized that within my student file the teacher file was located. I kept getting an error about nav_home.html file messing up the ability for my server to connect and access my website. The solution was a simple fix, deleting the teacher repository all together, and cloning again except this time not in my student directory. (I realized while trying to drag and drop my linux shell file I might have grabbed the wrong file.) Regardless I was able to move away from that, and start reading and looking into the hacks...

I also discovered that I need to remove the watch part of the youtube url and add 
/embed/ before the url in order to get the link to show up and for youtube not to keep giving me the error "refused to connect." 

## Technical Achievements

1. I customized my homepage with a pre-existing theme

2. I embedded youtube video links and my Freeform image

3. I installed all the required software, worked to understand each element so that I am better prepared when it comes to actually programming. 

4. Started on programming a visual calculator with the help of chat gpt. Working on how to incorporate it onto my website.

## Completed Hacks

1. Markdown Student Page

2. Tools and Equipment Overview

3. Pair Programming

4. VSCode, GitHub Pages Setup

## Ongoing Hacks

1. Build a Project

2. All week 1 and 2 items

## Goals

- I want to use a better theme for my blog, the one I used so far is temporary.

- I want to be able to get a firm understanding of the Javascript and Python material and finish all the hacks from week 1 by this weekend.

- I want to incorporate my calculator onto my website (still figuring that out). 

<html>
<head>
    <title>Rock, Paper, Scissors Game</title>
    <script>
        function getComputerChoice() {
            var choices = ['rock', 'paper', 'scissors'];
            var randomIndex = Math.floor(Math.random() * choices.length);
            return choices[randomIndex];
        }

        function determineWinner(userChoice, computerChoice) {
            if (userChoice === computerChoice) {
                return "It's a tie!";
            } else if (
                (userChoice === 'rock' && computerChoice === 'scissors') ||
                (userChoice === 'paper' && computerChoice === 'rock') ||
                (userChoice === 'scissors' && computerChoice === 'paper')
            ) {
                return "You win!";
            } else {
                return "Computer wins!";
            }
        }

        function playAgain() {
            return confirm("Do you want to play again?");
        }

        function playGame() {
            alert("Let's play Rock, Paper, Scissors!");

            while (true) {
                var userChoice = prompt("Enter your choice (rock/paper/scissors):").toLowerCase();
                while (['rock', 'paper', 'scissors'].indexOf(userChoice) === -1) {
                    userChoice = prompt("Invalid choice. Please enter rock, paper, or scissors:").toLowerCase();
                }

                var computerChoice = getComputerChoice();

                var result = determineWinner(userChoice, computerChoice);
                alert("You chose " + userChoice + ", and the computer chose " + computerChoice + ".\n" + result);

                if (!playAgain()) {
                    alert("Thanks for playing!");
                    break;
                }
            }
        }
    </script>
</head>
<body>
    <button onclick="playGame()">Play Rock, Paper, Scissors</button>
</body>
</html>