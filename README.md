# tic_tac_toe
it's a tictactoe game in python


import random

player_info = set()
cpu_info = set()

slot = {'7': ' ', '8': ' ', '9': ' ',
        '4': ' ', '5': ' ', '6': ' ',
        '1': ' ', '2': ' ', '3': ' '}


def printBoard(slot):
    print(slot['7'] + '|' + slot['8'] + '|' + slot['9'])
    print('-+-+-')
    print(slot['4'] + '|' + slot['5'] + '|' + slot['6'])
    print('-+-+-')
    print(slot['1'] + '|' + slot['2'] + '|' + slot['3'])


def Turn(player):
    turn = 'X'

    if (player == 'user'):
        turn = 'X'
        for i in range(1, 10):
            move = input()


            if (slot[move] == ' '):
                slot[move] = turn
                player_info.add(move)
                break
            else:
                print('try an other place')
                continue





    elif (player == 'cpu'):
        turn = 'O'
        for i in range(1, 10):
            move = str(random.randint(1, 9))
            if (slot[move] == ' '):
                cpu_info.add(move)
                slot[move] = turn
                break
            else:

                continue


def checkWinner(player_info, cpu_info):
    up_row = {'1', '2', '3'}
    mid_row = {'4', '5', '6'}
    low_row = {'7', '8', '9'}
    up_col = {'1', '4', '7'}
    mid_col = {'8', '5', '2'}
    low_col = {'9', '6', '3'}
    cross1 = {'7', '5', '3'}
    cross2 = {'1', '5', '9'}

    condition = []
    condition.append(up_row)
    condition.append(mid_row)
    condition.append(low_row)
    condition.append(up_col)
    condition.append(mid_col)
    condition.append(low_col)
    condition.append(cross1)
    condition.append(cross2)

    if ((cpu_info in condition) == True):
        return "oops you loss the game"
    elif (player_info in condition) == True:
        return "you won the game"

    elif (len(player_info) + len(cpu_info) == 9):
        return 'please try again . it\'s a tie'
    else:
        return ''

def main():
    printBoard(slot)

    while True:
        print('enter the position')

        Turn('user')



        x=checkWinner(player_info, cpu_info)
        if(x!=''):
            print(x)
            printBoard(slot)
            break

        Turn('cpu')

        y=checkWinner(player_info, cpu_info)
        if (y != ''):
            print(y)
            printBoard(slot)
            break

        printBoard(slot)

if __name__ == "__main__":
    main()
