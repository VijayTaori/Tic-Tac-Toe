

```python
# Tic-Tac-Toe with Board class
# Adopted from Christian Thompson and Sentdex
# Python 3.7
```


```python
import os
from colorama import Fore, Back, Style, init
init(autoreset=True)
from collections import Counter
```


```python
# Creating a Board
class Board():
	def __init__(self):
		self.cells = ['X','1','2','3','4','5','6','7','8','9','O']
		'''To understand presence of cells 'X' and 'O' goto check_for_tie(self)'''
	def display(self):
		print(Fore.YELLOW +' %s '%(self.cells[1])+Style.RESET_ALL+'|'+
				Fore.YELLOW +' %s '%(self.cells[2])+Style.RESET_ALL+'|'+
				Fore.YELLOW +' %s '%(self.cells[3])+Style.RESET_ALL)
				#print(' %s | %s | %s' %(self.cells[1], self.cells[2], self.cells[3]))
		print('-----------')
		print(Fore.YELLOW +' %s '%(self.cells[4])+Style.RESET_ALL+'|'+
				Fore.YELLOW +' %s '%(self.cells[5])+Style.RESET_ALL+'|'+
				Fore.YELLOW +' %s '%(self.cells[6])+Style.RESET_ALL)
				#print(' %s | %s | %s' %(self.cells[4], self.cells[5], self.cells[6]))
		print('-----------')
		print(Fore.YELLOW +' %s '%(self.cells[7])+Style.RESET_ALL+'|'+
				Fore.YELLOW +' %s '%(self.cells[8])+Style.RESET_ALL+'|'+
				Fore.YELLOW +' %s '%(self.cells[9])+Style.RESET_ALL)
				#print(' %s | %s | %s' %(self.cells[7], self.cells[8], self.cells[9]))
				
	def update_spot(self,spot_number, player):
		if self.cells[spot_number] == str(spot_number):
			self.cells[spot_number] = player
		else:
			print("You have entered a wrong value/nYou loose your turn")
			
	def print_current_cells_list(self):
		print(self.cells)
		
	def check_for_a_win(self,player):
		# Horizontal win
		if self.cells[1] == self.cells[2] == self.cells[3] == player:
			return True
			print('Horizontal Win!!')
		if self.cells[4] == self.cells[5] == self.cells[6] == player:
			return True
			print('Horizontal Win!!')
		if self.cells[7] == self.cells[8] == self.cells[9] == player:
			return True
			print('Horizontal Win!!')
		#verticle win
		if self.cells[1] == self.cells[4] == self.cells[7] == player:
			return True
			print('Verticle Win!!')
		if self.cells[2] == self.cells[5] == self.cells[8] == player:
			return True
			print('Verticle Win!!')
		if self.cells[3] == self.cells[6] == self.cells[9] == player:
			return True
			print('Verticle Win!!')
		if self.cells[1] == self.cells[5] == self.cells[9] == player:
			return True
			print('Diagonal Win!!')
		if self.cells[3] == self.cells[5] == self.cells[7] == player:
			return True
			print('Diagonal Win!!')
		return False
		print('Did anyone win yet?')
		
	def check_for_tie(self):
		dict_items = dict(Counter(self.cells))
		'''This will create a dictionary.
		It will store each unique elements as key.
		The value corresponding to each key represents
		the number of times it is present in the list self.cells'''
		
		''' The reason we had 'X' and 'O' 
		in the begining in the self.cells 
		is that dict_items['X']+dict_items['O'] will 
		throw an error if no 'X' and 'O' are present
		'''
		if dict_items['X']+dict_items['O'] == 11:
			return True
	
	def restart_board(self):
		self.cells = ['X','1','2','3','4','5','6','7','8','9','O']
		refresh_screen()
	
	def check_for_input(self,player):
		print('Hello')
		
		

board = Board()
```


```python
# Part 1b: Getting started with clear board

def print_header():
    print('Welcome to Tic-Tac-Toe\n')
print_header()

def print_header():
    print('Welcome to Tic-Tac_Toe\n')
	
def refresh_screen():
    #Clear the screen
    os.system("cls")
    
    #Print the header
    print_header()
    
    #Show the board
    board.display()
```

    Welcome to Tic-Tac-Toe
    
    


```python
refresh_screen()
```

    Welcome to Tic-Tac_Toe
    
     1 | 2 | 3 
    -----------
     4 | 5 | 6 
    -----------
     7 | 8 | 9 
    


```python
# Part 2: Making a move

while True:
	refresh_screen()
	
	#If you like to check the self.cells un-hashtag below
	board.print_current_cells_list()
	
	#Get X input
	x_choice = int(input("\nPlayer X: Enter 1-9 for spot of your choice\nif you enter wrong value or occupied spot number you loose a turn "))
	
	#Update board
	board.update_spot(x_choice, "X")
	
	#Refresh the screen again so you can see the input from player X
	refresh_screen()
	if board.check_for_a_win('X'):
		print('\nX wins!!\n')
		play_again = input('Would you like to play again? Y/N > ').upper()
		if play_again == 'Y':
			board.restart_board()
		else:
			break
		
	if board.check_for_tie():
		print('\nIts a Tie!!\n')
		play_again = input('Would you like to play again? Y/N > ').upper()
		if play_again == 'Y':
			board.restart_board()
		else:
			break
	
	#If you like to check the self.cells un-hashtag below
	board.print_current_cells_list()
	
	#Get O input
	o_choice = int(input("\nPlayer O: Enter 1-9 for spot of your choice\nif you enter wrong value or occupied spot number you loose a turn "))
	
	#Update board
	board.update_spot(o_choice, "O")	
	#Refresh the screen again so you can see the input from player O
	refresh_screen()
	if board.check_for_a_win('O'):
		print('\nO wins!!\n')
		play_again = input('Would you like to play again? Y/N > ').upper()
		if play_again == 'Y':
			refresh_screen()
			board.restart_board()
			refresh_screen()
			board.restart_board()
		else:
			break
	if board.check_for_tie():
		print('\nIts a Tie!!\n')
		play_again = input('Would you like to play again? Y/N > ').upper()
		if play_again == 'Y':
			board.restart_board()
		else:
			break
```

    Welcome to Tic-Tac_Toe
    
     1 | 2 | 3 
    -----------
     4 | 5 | 6 
    -----------
     7 | 8 | 9 
    ['X', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'O']
    
    Player X: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 1
    Welcome to Tic-Tac_Toe
    
     X | 2 | 3 
    -----------
     4 | 5 | 6 
    -----------
     7 | 8 | 9 
    ['X', 'X', '2', '3', '4', '5', '6', '7', '8', '9', 'O']
    
    Player O: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 2
    Welcome to Tic-Tac_Toe
    
     X | O | 3 
    -----------
     4 | 5 | 6 
    -----------
     7 | 8 | 9 
    Welcome to Tic-Tac_Toe
    
     X | O | 3 
    -----------
     4 | 5 | 6 
    -----------
     7 | 8 | 9 
    ['X', 'X', 'O', '3', '4', '5', '6', '7', '8', '9', 'O']
    
    Player X: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 3
    Welcome to Tic-Tac_Toe
    
     X | O | X 
    -----------
     4 | 5 | 6 
    -----------
     7 | 8 | 9 
    ['X', 'X', 'O', 'X', '4', '5', '6', '7', '8', '9', 'O']
    
    Player O: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 4
    Welcome to Tic-Tac_Toe
    
     X | O | X 
    -----------
     O | 5 | 6 
    -----------
     7 | 8 | 9 
    Welcome to Tic-Tac_Toe
    
     X | O | X 
    -----------
     O | 5 | 6 
    -----------
     7 | 8 | 9 
    ['X', 'X', 'O', 'X', 'O', '5', '6', '7', '8', '9', 'O']
    
    Player X: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 5
    Welcome to Tic-Tac_Toe
    
     X | O | X 
    -----------
     O | X | 6 
    -----------
     7 | 8 | 9 
    ['X', 'X', 'O', 'X', 'O', 'X', '6', '7', '8', '9', 'O']
    
    Player O: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 6
    Welcome to Tic-Tac_Toe
    
     X | O | X 
    -----------
     O | X | O 
    -----------
     7 | 8 | 9 
    Welcome to Tic-Tac_Toe
    
     X | O | X 
    -----------
     O | X | O 
    -----------
     7 | 8 | 9 
    ['X', 'X', 'O', 'X', 'O', 'X', 'O', '7', '8', '9', 'O']
    
    Player X: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 7
    Welcome to Tic-Tac_Toe
    
     X | O | X 
    -----------
     O | X | O 
    -----------
     X | 8 | 9 
    
    X wins!!
    
    Would you like to play again? Y/N > y
    Welcome to Tic-Tac_Toe
    
     1 | 2 | 3 
    -----------
     4 | 5 | 6 
    -----------
     7 | 8 | 9 
    ['X', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'O']
    
    Player O: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 1
    Welcome to Tic-Tac_Toe
    
     O | 2 | 3 
    -----------
     4 | 5 | 6 
    -----------
     7 | 8 | 9 
    Welcome to Tic-Tac_Toe
    
     O | 2 | 3 
    -----------
     4 | 5 | 6 
    -----------
     7 | 8 | 9 
    ['X', 'O', '2', '3', '4', '5', '6', '7', '8', '9', 'O']
    
    Player X: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 2
    Welcome to Tic-Tac_Toe
    
     O | X | 3 
    -----------
     4 | 5 | 6 
    -----------
     7 | 8 | 9 
    ['X', 'O', 'X', '3', '4', '5', '6', '7', '8', '9', 'O']
    
    Player O: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 3
    Welcome to Tic-Tac_Toe
    
     O | X | O 
    -----------
     4 | 5 | 6 
    -----------
     7 | 8 | 9 
    Welcome to Tic-Tac_Toe
    
     O | X | O 
    -----------
     4 | 5 | 6 
    -----------
     7 | 8 | 9 
    ['X', 'O', 'X', 'O', '4', '5', '6', '7', '8', '9', 'O']
    
    Player X: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 4
    Welcome to Tic-Tac_Toe
    
     O | X | O 
    -----------
     X | 5 | 6 
    -----------
     7 | 8 | 9 
    ['X', 'O', 'X', 'O', 'X', '5', '6', '7', '8', '9', 'O']
    
    Player O: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 5
    Welcome to Tic-Tac_Toe
    
     O | X | O 
    -----------
     X | O | 6 
    -----------
     7 | 8 | 9 
    Welcome to Tic-Tac_Toe
    
     O | X | O 
    -----------
     X | O | 6 
    -----------
     7 | 8 | 9 
    ['X', 'O', 'X', 'O', 'X', 'O', '6', '7', '8', '9', 'O']
    
    Player X: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 6
    Welcome to Tic-Tac_Toe
    
     O | X | O 
    -----------
     X | O | X 
    -----------
     7 | 8 | 9 
    ['X', 'O', 'X', 'O', 'X', 'O', 'X', '7', '8', '9', 'O']
    
    Player O: Enter 1-9 for spot of your choice
    if you enter wrong value or occupied spot number you loose a turn 7
    Welcome to Tic-Tac_Toe
    
     O | X | O 
    -----------
     X | O | X 
    -----------
     O | 8 | 9 
    
    O wins!!
    
    Would you like to play again? Y/N > n
    
