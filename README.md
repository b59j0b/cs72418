java cProject 2: Connect 4
Due date and time: Monday, 2/19/25, 11:59 pm 
Checkpoint: Monday, 2/12/24, 11:59 am

Available for all students M-F before 8am  after 5pm, all day Sat/Sun

Overview
For this project, you will implement three versions of a Python console-based Connect Four game:
1.2-player mode 
2.1 player vs. AI 
3.1 player vs. internet AI
Project Goals
1.Implement each mode separately in its own Python file.
2.Reuse as much code as possible across the different versions.
3.Do not modify the provided connect4.py game logic.

Game Details
●Traditional Connect Four Rules
○Connect Four is a 2 player game where one is red and the other is yellow. 
○Players take turns to drop or pop a disc of their color. 
○Connect 4 discs of your color horizontally, vertically, or diagonally to win. 
○If you're not familiar with the rules of the game, you can review the rules on Wikipedia's Connect Four page.
●Variation
○Implement both traditional rules and the "Pop Out" variation. 
○At each turn, you can pop out (remove) a disc of your color from the bottom row of the board instead of dropping another disc in.  
●Flexible Board Sizes
○Support board sizes from 4x4 to 20x20. 
●Red Moves First: 
○Red player always moves first.

Getting Started
●From the project 2 folder, download the project2_starter.zip file containing  starter files shown below. Unzip the file and place all starter files into the same working directory.  

●A client_short.py file will be provided after lab 7’s due date.
○This file is only required for the part 3 of this project.
●Read the provided code to understand how the game logic works



Program 1: Local 2-player Game
Functionality:
●Allow two players to play Connect Four using Python shell.
●To start, ask users to specify the board size before starting the game.
●At each turn, display the current state of the board and indicate whose turn it is.
●Clearly instruct users on how to specify the board size and make moves.
●Allow column selection using numbers (e.g., 1 for the far-left column).
●Validate moves and handle invalid inputs gracefully, providing error messages as needed.
●When the user is asked to specify a move but an invalid one is specified (such as dropping into a column that is full), an error message should be printed and the user should be asked again to specify a move. In general, erroneous input at the Python shell should not cause the program to crash; it should simply cause the user to be asked to specify his or her move again.
○Ex: “Invalid Move”
●The game proceeds, one move at a time, until the game ends, at which point the program ends.
Requirements:
●connect4.py, which contains the provided connect four game logic.
○Note: You must not modify this module but build your game on top of it.
○Recommendation: Read through the provided code, docstrings, and comments to understand how the game logic works.
○Experimentation: Use the Python shell to experiment with the module and comprehend its functionalities.
●connect4_ui.py, which contains utility functions for the 2 player game. The  required functions are described below. You can create additional helper functions as appropriate:
○make_new_game()
■Asks the user for the number of rows and columns.
■The number of rows and columns can be from 4 to 20.
■Once the user provides valid rows and columns, create new game and return the connect4.Gamestate
○print_board(state)
■Returns a string holding the contents of a game board, given a GameState
■The string should contain all lines of the appropriate display
■An example board display is shown below
●Note the spacing difference when the column number requires 2 digits. 
■If it’s red’s turn, display “RED’s turn” after the board
■If it’s yellow’s turn, display “YELLOW’s turn” after the board
■If red wins, display “RED wins!”
■If yellow wins, display “YELLOW wins!” 
○choose_move(state)
■Asks the user to choose a move, returning a tuple whose first element is DROP or POP and whose second element is a valid column number.
■Asks the user for a move, should only return a valid move
■Keep asking user if wrong move type or column is detected
○make_move(state, move)
■Makes the given move against the given state, returning the new state.
■For a valid move, return the new state. 
■Raise connect4.InvalidMoveError if invalid operation detected.
■Implement exception handler to catch this exception. If connect4.InvalidMoveError exception is caught, return the original state.
●connect4_console.py, which implements the 2-player game.
○All code should be implemented inside the provided run_console_ui() function. 
○Utilize functions defined in connect4 and connect4_ui modules.
○If a move is illegal, such as dropping a disc into a full column or popping a column where the bottom disc is not the player’s color, the program should indicate “Invalid Move” and ask the same player for another move. This applies to both players.







Here is an example of a game with 20 columns and 5 rows:



 

Here is an example of how Pop works:

Program 2: 1 Player game against AI 
Functionality:
●Allow a human player (red) to play against an AI player (yellow).
●AI is always the 2nd player in yellow.
●Maintain the same user interaction and board display rules as in Program 1.
●Implement a simple AI based on random selection.
●Extra credit: implement a more sophisticated AI for the Connect 4 AI Tournament. More details provided later in the document.
Requirements:
●connect4_ui_ai.py, which implements the ai player functionality.
○ai_move(state)
■Takes connect4.GameState as input
■Asks the AI to choose a move, and the AI will return a tuple with the following format (move, column number).
■The move is either DROP or POP, which are constants defined as 1 for DROP and 2 for POP
■The column number should be from 1 to the number of columns for the board.
■For full credit, you can simply implement the AI with random numbers.
●For extra credit, you can implement a more complex AI for the ICS 32 Connect 4 AI Tournament. More details are presented at the end of this doc.
■Note: the AI only needs to return a tuple consisting of a valid move and a column within the valid range of columns. The entire move may still be invalid due to certain circumstances. We will address this issue inside of connect4_console_ai.py.
■Hint: helper functions would be useful here.
●connect4_console_ai.py, which implements the 1 player game against AI
○All of the code needs to reside inside the run_console_ui() function.
○Utilize functions defined in connect4, connect4_ui, and connect4_ui_ai.py modules.
○If a move is illegal, such as dropping a disc into a full column or popping a column where the bottom disc is not the player’s color, the program should indicate “Invalid Move” and ask the same player for another move. This applies to both the human and AI players.

Program 3: Networked Connect 4 vs Server AI
Functionality:
●Play Connect Four against an AI server over the network, by connecting to a server that I will provide. 
●Your program will act as a client that connects to a server.
●When this program starts, the user will need to specify the host (either an IP address, such as 192.168.1.101, or a hostname, such as www.ics.uci.edu) where a Connect Four server is running, along with the port on which that server is listening.
●Once the user has specified where to connect, the program should attempt to connect to the server. If the connection is unsuccessful, print an error message specifying why and end the program. If, on the other hand, the connection is successful, the game should proceed, with the client acting as the red player (and moving first) and the server AI acting as the yellow player. (Of course, the user will need to specify the size of the board before the game starts.) For red player moves, the user should specify the move at the Python shell, as in your first program; for yellow player moves, the program should instead communicate with the server and let the server determine what move should be made.
●As in the first program, the game proceeds, one move at a time, until the game ends, at which point the program ends.
●User Inputs:
○Host (IP address or hostnam代 写program、Python
代做程序编程语言e) where the server is running.
○Port number of the server.
●Connection Handling:
○Attempt to connect to the server.
○If the connection fails, print an error message and end the program. If successful, proceed with the game.
●Game Interaction:
○The red player (user) specifies moves, while the server determines yellow player moves.
○Follow the same move validation and error handling practices as in Program 1.
●Protocol
○Need to follow the CFSP protocol to be described later in this document.

Requirements:
●client_short.py, which implements the networking functions via sockets.
○You should have implemented this during the lab.
○We are providing fully functional networking code for you to utilize.
○Do not change the code in this file.
●connect4_network_client.py, which implements the game vs the internet AI.
○All of your  code needs to reside inside the run_console_network() function.
○Utilize functions defined in connect4, connect4_ui, connect4_ui_ai.py, and client_short modules.

Where is the ICS 32 Connect 4 server?
●Information about where the server is running will be distributed on Ed Discussion; I'll also keep you posted about planned downtime.
●Please note that the ICS 32 Connect Four server is running on a machine on the ICS network that is not exposed to the open Internet. In order to connect to it, you will need to be connected to the campus network, which means you'll either need to be on campus or you'll need to be connected to something called the campus VPN, which allows you to access the campus' network from off-campus. Note, also, that certain residential areas are not connected to a part of the campus network that will allow you direct access to the ICS 32 Connect Four server, so you'll need to use the campus VPN in those cases. In general, if you're not able to connect to the ICS 32 Connect Four server, the first thing you should try is using the campus VPN.
●Connecting to the campus VPN requires that you install some software, which you can obtain from UCI's Office of Information Technology at the following link:
●Campus VPN software
●Open the link above, find the section titled Software VPN (as opposed to WebVPN, which won't work for this purpose), and click the link to download the appropriate version of the VPN software for your host operating system. This will require you to log in with your UCInetID and password. Download the one that's appropriate for your host operating system and install it; instructions for setting it up are available from that page, as well.


The Connect Four Server Protocol (CFSP)
Though each of you will be writing a completely separate program, your programs are expected to be able to connect to the Connect Four server via the Internet. There is only one server that we'll all share, so that requires us to agree on a single way to communicate with it.
Any time you want programs to be able to communicate with the Internet, there needs to be a protocol, which is a set of rules governing what each party will send and receive, and when they will do it. 
You can think of a protocol like rules you follow when talking on 2 walkie-talkies. Each participant knows its role, so that it will know what to say and what to expect the other participant to say at any given time. 

Many protocols have been defined that govern how various programs send and receive information via the Internet. For example, the Hypertext Transfer Protocol (HTTP) is what your browser uses to connect to a web server, request a web page, and receive a response. 
For this project, we will use a custom protocol called the ICS 32 Connect Four Server Protocol: CFSP.
CFSP conversations are relatively simple. They are predominantly centered around sending moves back and forth, with the assumption that both parties can determine the game's state by applying these moves locally.
Below is an example sequence of messages between the client and server. Each cell shows the data sent by the corresponding party. In the first row, Client sends “GAME 5 5”. The Server receives this message and sends “START”. Once the Client receives “START”, it sends “USER 0 5”. This continues for 4 turns. The client detects the winning condition and closes the connection.

Client	Server
GAME 5 5	
	START
USER 1 5	
	RECEIVED
MOVE	
	1
COLUMN	
	4
USER 1 4	
	RECEIVED
MOVE	
	1
COLUMN	
	3
USER 1 3	
	RECEIVED
MOVE	
	1
COLUMN	
	2
USER 1 3	
	RECEIVED
MOVE	
	1
COLUMN	
	1
Once the client connects to the server, the CFSP dictates the following sequence of communication. All messages should end with the end-of-line sequences of “\r\n”. (This two-character sequence, which is common in Internet protocols, is called a carriage return and line feed sequence, a sequence so common that it's sometimes abbreviated CRLF.)
1.To start the game, the client sends “Game num_rows num_columns“, where num_rows and num_columns should be replaced by integers representing the board dimensions.
a.Ex: “Game 10 10”
2.Upon receiving this message, the server will respond with “START”
3.Once the client receives “START”, it will start the game.
4.After starting the game, the client should prompt the user for their move. Once a valid move is made by the user, the client will send the following message to the server:
a.“USER move column”, where move should be DROP or POP and column should be an integer indicating the column to perform the action on.
b.Ex: “USER 1 3”
5.Once the Server receives the user’s move, the Server sends “RECEIVED” to confirm receipt of the user’s move.
6.After sending the user move, the client sends the following message to wait for the server AI’s move
a.“MOVE”
7.The server will only send the AI’s move after receiving the “MOVE” message from the client.
a.The server will send a string holding an integer value. “1” for DROP or “2” for POP.
8.After receiving the server’s move, the client will send the following message to prompt the AI for the column
a.“COLUMN”
9.The server will only send the column info after receiving “COLUMN”
a.The server will send a string holding an integer value (i.e. “9”) to indicate the column for the action. 
10.This process repeats itself until one player wins. At each step, the state of the board is printed.
11.The client is responsible for detecting the winning condition. After the winning condition is detected, the client will call print_board and print out the return value. Then, the client will close the connection to the server.


Extra Credit Details:
●There will be a separate Gradescope submission for the AI Tournament. 
●Only submit the connect4_ui_ai.py file. ai_move function will be used to evaluate your AI.
●Up to 10% extra credit for submitting an AI player which can consistently win against the server. Best out of 10 random games with randomly sized boards.
○2% for every game won after winning 5 games.
○Ex: winning 8 games = 6% extra credit 
○Judged by autograder
●Additional 10% extra credit for top 10% placement in the AI Connect 4 AI Tournament.
●Note: your AI player will have limited memory and compute resources. Your player will time out and lose a turn if a turn takes over 10 seconds. If the program times out more than 6 times, the player forfeits the match. 

Additional Information for Students
●Zip and Unzip instructions:
○macOS:

Submission Guidelines
●To submit your work, follow these instructions
○High level design document
■project2_design.pdf
○Your submission should include only the files provided and the design document. 
■Do not change the file names.
○Make sure all of the .py files are all in the same directory. 
○Zip up all the files for the submission
■Do not include and subdirectory in your zip file
○Submit the zip file to Gradescope
○For the testing of the networked connect 4, you need to connect to the server arcala-1.ics.uci.edu at port number 8000 with your client program. Make sure to use the updated client_short.py file which provides you with your IP and timestamp. 
■Play a complete game. 
■Record the IP, start time, and complete time.
■Enter this info along with your name in this document:
■This will be manually graded. No Gradescope submission necessary for this portion in the Gradescope assignment.

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
