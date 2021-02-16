```python
from IPython.display import clear_output
clear_output()
```


```python
row1 = [' ',' ',' ']
row2 = [' ',' ',' ']
row3 = [' ',' ',' ']
posp1 = 0
posp2 = 0
movestore = []
gameon = True

def boarddisp():
    print('Player 1 is X. Player 2 is O.')
    print('     |     |               |     |     ')
    print('  {}  |  {}  |  {}         1  |  2  |  3'.format(row1[0],row1[1],row1[2]))
    print('_____|_____|_____     _____|_____|_____')
    print('     |     |               |     |     ')
    print('  {}  |  {}  |  {}         4  |  5  |  6'.format(row2[0],row2[1],row2[2]))
    print('_____|_____|_____     _____|_____|_____')
    print('     |     |               |     |     ')
    print('  {}  |  {}  |  {}         7  |  8  |  9'.format(row3[0],row3[1],row3[2]))
    print('     |     |               |     |     ')

def wingame():
    checkval = False
    global pwin
    pwin = 0
    
    if set(row1) == set(['X']) or set(row2) == set(['X']) or set(row3) == set(['X']):
        checkval = True
        pwin = 1
    if set(row1) == set(['O']) or set(row2) == set(['O']) or set(row3) == set(['O']):
        checkval = True
        pwin = 2
        
    if row1[0]==row2[0]==row3[0]=='X' or row1[1]==row2[1]==row3[1]=='X' or row1[2]==row2[2]==row3[2]=='X' or row1[0]==row2[1]==row3[2]=='X' or row1[2]==row2[1]==row3[0]=='X':
        checkval = True
        pwin = 1
    if row1[0]==row2[0]==row3[0]=='O' or row1[1]==row2[1]==row3[1]=='O' or row1[2]==row2[2]==row3[2]=='O' or row1[0]==row2[1]==row3[2]=='O' or row1[2]==row2[1]==row3[0]=='O':
        checkval = True
        pwin = 2
    return checkval

```


```python
while gameon:
    
    # Player 1 makes a move
    while posp1 not in range(1,10) or posp1 in movestore:
        boarddisp()
        pos1 = input('Player 1 please pick a position (1-9): ')
        clear_output()
        if pos1.isnumeric():
            posp1 = int(pos1)
        else:
            print('Please pick a number from 1 to 9!')
            posp1 = 0
        if posp1 in movestore:
            print('This position has been taken!')
    movestore.append(posp1)
    if posp1 <= 3:
        p1 = posp1 - 1
        row1[p1] = 'X'
    elif posp1 <= 6:
        p1 = posp1 - 4
        row2[p1] = 'X'
    else:
        p1 = posp1 - 7
        row3[p1] = 'X'
    
    # Check winning streak
    gameon = not(wingame())
    if not gameon:
        boarddisp()
        print(f'Congrats! Player {pwin} has won the game!')
        ans = 'A'
        while ans not in ['Y','N']:
            ans = input('Do you want to play another game? Type Y or N: ')
        if ans == 'Y':
            row1 = [' ',' ',' ']
            row2 = [' ',' ',' ']
            row3 = [' ',' ',' ']
            posp1 = 0
            posp2 = 0
            movestore = []
            gameon = True
            continue
        else:
            print('Good game!')
            break            
              
    # Player 2 makes a move
    while posp2 not in range(1,10) or posp2 in movestore:
        boarddisp()
        pos2 = input('Player 2 please pick a position (1-9): ')
        clear_output()
        if pos2.isnumeric():
            posp2 = int(pos2)
        else:
            print('Please pick a number from 1 to 9!')
            posp2 = 0
        if posp2 in movestore:
            print('This position has been taken!')
    movestore.append(posp2)
    if posp2 <= 3:
        p2 = posp2 - 1
        row1[p2] = 'O'
    elif posp2 <= 6:
        p2 = posp2 - 4
        row2[p2] = 'O'
    else:
        p2 = posp2 - 7
        row3[p2] = 'O'
    
    # Check winning streak
    gameon = not(wingame())
    if not gameon:
        boarddisp()
        print(f'Congrats! Player {pwin} has won the game!')
        ans = 'A'
        while ans not in ['Y','N']:
            ans = input('Do you want to play another game? Type Y or N: ')
        if ans == 'Y':
            row1 = [' ',' ',' ']
            row2 = [' ',' ',' ']
            row3 = [' ',' ',' ']
            posp1 = 0
            posp2 = 0
            movestore = []
            gameon = True
            continue
        else:
            print('Good game!')
            break
```

    Player 1 is X. Player 2 is O.
         |     |               |     |     
      X  |  X  |  X         1  |  2  |  3
    _____|_____|_____     _____|_____|_____
         |     |               |     |     
         |  O  |            4  |  5  |  6
    _____|_____|_____     _____|_____|_____
         |     |               |     |     
         |     |  O         7  |  8  |  9
         |     |               |     |     
    Congrats! Player 1 has won the game!
    Do you want to play another game? Type Y or N: N
    Good game!
    


```python

```
