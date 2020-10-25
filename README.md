# How to clone this repository
1. Start by creating directory on your local machine where all your github projects should be placed. In this example we will call the directory for github projects.
2. Navigate to the previously created directory using either the bash command cd or by locating it and opening a terminal in your current directory (Type cmd in address bar on windows / right click in your folder and select 'Open in Terminal' on OS x/linux).
3. On github, you must click the 'Fork' button on the top-right. This creates a copy of the repository on your own github, meaning no changes that you do will occur on my repository.
4. Now it is time to clone the repository, you do this by finding the https clone link on github. **For my repository, it is https://github.com/lass7965/test.git, but for yours it will be different**
	```git
	git clone https://github.com/lass7965/test.git
	```
5. A folder has now been created in your current directory which contains the files from the cloned repository. To view the contents of your current directory you can do 'ls' on linux/OS x and 'dir' on windows.
# How to play the game:
## Starting the first game out:
1. On the very first turn, you will have to decide which one of you starts.
2. If it is your turn do:
	```git
	git pull
	```
3. Open the .tex document using your favorite text editor, and eligible spot.
4. Compile the .tex document and check that you are satisfied with the changes in the created pdf file:
	```git
	pdflatex TicTacToe.tex
	```
5. Compiling the latex document created 5 new files, which git does not know exists, we need to make git know that the pdf file exists. Do the following command to check which files has been changed and which are "untracked"
6. We only want to add the pdf file to git, the rest can remain untracked:
	```git
	git add TicTacToe.pdf
	```
7. Now we want to prepare sending our changes to the shared git repository, we do this using the commit command:
	```git
	git commit -m "I have now made the winning move, you lose!"
	```
	The '-m' defines that you wish to define a message to the changes you made. The -m is followed by the message, where you should describe the changes you made.
8. Finally you push the changes to the git repository, making it available for your competitors in our game, but usually only available to you fellow collaborators, which concludes your turn. 
	```git
	git push
	```
## When it is your turn:
1. You start out your turn by pulling the latests changes to the repository.
	```git
	git pull
	```
2. Open the pdf, check that the player before you's move has been added, and check if that player has won. Should it not be added you need to go back and figure out what went wrong.
3. Open the .tex document using your favorite text editor, and eligible spot.
4. Compile the .tex document and check that you are satisfied with the changes in the modified pdf file (If you already had the pdf open, you might have to close it before compiling):
	```git
	pdflatex tictactoe.tex
	```
5. Now we want to prepare sending our changes to the shared git repository, we do this using the commit command:
	```git
	git commit -m "Veni vidi vici"
	```
	Having two different commits with the same commit message is permitted in git, but we advise not doing to, as commit messages are used when having to go back to previous version of your code, should something break in later versions (Yes, it happens. Alot)
6. You finish you turn by pushing your changes to the git repository, which makes it available for the next players.
	```git
	git push
	```
## When a game ends:
TODO

# Handling merge conflicts:
1. Not all games are turn based, and neither is collaborating on github. Therefore something called a merge conflicts can occur. If you do not know or is unsure of what an merge conflict is, we recommend reading **Merge conflict explained** below in this same readme.	
## Merge conflict explained:
A merge conflict occurs when two or more changes are made by two or more persons, while working on the same base file. Imagine having a file with the following task written in it:
```java
public static void main(String[] args){
	//Make this function print the result of 2+2
}
```
Two different persons decides to do this task simultaneously, which causes them both to do the git pull command. They now both have the file with the unfinished task.
The first person is fast to do this function and quickly commit and push the following to github:
```java
public static void main(String[] args){
	//Make this function print the result of 2+2
	System.out.println("4");
}
```
The second persons could be even just a tiny bit slower to do the task, and commit and push the finished task, which we does as follows:
```java
public static void main(String[] args){
	//Make this function print the result of 2+2
	System.out.println(2+2);
}
```
This second person would get a merge conflict as git does not know how to handle this as it does not know which of the codes are the most correct. Git knows that the second person is unaware of the changes made by the first person and thereby directly rejects the push, and instead advises the second person to fix the merge conflict.
