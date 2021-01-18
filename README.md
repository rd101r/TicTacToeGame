# TicTacToeGame
#A small try towards game programming with the help of youtube(reference clever-programmer tictactoe with python) .



game_still_going =True
winner=None
current_player="X"

board=["-", "-","-",
       "-", "-","-",
       "-", "-","-"]


def play_game():
    display_board()

    while game_still_going:
        handle_turn(current_player)

        check_if_game_over()

        flip_player()

    if (winner=="X" or winner=="O"):
         print(winner+" WON!")

    elif winner==None:
        print("TiE!")
    
      
def display_board():
    print(board[0]+"|"+board[1]+"|"+board[2] + 
    "   1 | 2 | 3")
    print(board[3]+"|"+board[4]+"|"+board[5] + 
    "   4 | 5 | 6")
    print(board[6]+"|"+board[7]+"|"+board[8] + 
    "   7 | 8 | 9")


def handle_turn(player):

  
  print(player + "'s turn.")
  position = input("Choose a position from 1-9: ")

  
  valid = False
  while not valid:

    
    while position not in ["1", "2", "3", "4", "5", "6", "7", "8", "9"]:
      position = input("Choose a position from 1-9: ")
 
    
    position = int(position) - 1

    
    if board[position] == "-":
      valid = True
    else:
      print("You can't go there. Go again.")

  
  board[position] = player

  
  display_board()




def check_if_game_over():
    check_for_winner()
    check_for_tie()
    return

def check_for_winner():
    #check rows
    global winner
    row_winner=check_rows()
    #check col
    col_winner=check_col()

    #check dig
    dig_winner=check_dig()

    if row_winner:
        winner= row_winner
    elif col_winner:
        winner=col_winner
    elif dig_winner:
        winner=dig_winner

    else:
        winner=None

  
    

def check_rows():
    global game_still_going

    row_1=board[0]==board[1]==board[2] != "-"
    row_2=board[3]==board[4]==board[5] != "-"
    row_3=board[6]==board[7]==board[8] != "-"

    if row_1 or row_2 or row_3:
        game_still_going= False
    if row_1:
        return board[0]
    if row_2:
        return board[3]
    if row_3:
        return board[6]
    return 

def check_col():
    

    global game_still_going

    col_1=board[0]==board[3]==board[6] != "-"

    col_2=board[1]==board[4]==board[7] != "-"
    col_3=board[2]==board[5]==board[8] != "-"

    if col_1 or col_2 or col_3:
        game_still_going=False
    if col_1:
        return board[0]
    if col_2:
        return board[3]
    if col_3:
        return board[6]
    return 
    
def check_dig():

    global game_still_going
  
    diagonal_1 = board[0] == board[4] == board[8] != "-"
    diagonal_2 = board[2] == board[4] == board[6] != "-"
  
    if diagonal_1 or diagonal_2:
        game_still_going = False
  
    if diagonal_1:
        return board[0] 
    elif diagonal_2:
        return board[2]
  
    else:
        return None
    

def check_for_tie():
    global game_still_going
    if "-"not in board:
        game_still_going=False
    
    return

def flip_player():
    global current_player
    if current_player=="X":
        current_player="O"
    elif current_player=="O":
        current_player="X"

    return




play_game()
