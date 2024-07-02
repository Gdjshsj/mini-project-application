board=[[' ',' ',' '],[' ',' ',' '],[' ',' ',' ']]
def print_board(board):
    print(*board[0],sep=' |')
    print("--------")
    print(*board[1],sep=' |')
    print("--------")
    print(*board[2],sep=' |')
def get_markers():
    marker1=input("player1 choice either (x or o): ".upper())
    marker2=' '
    if marker1=='x' or marker2=='o':
        return['x','o']
    elif marker1=='o' or marker2=='x':
        return['x','o']
    else:
        print("invalid input")
        return get_markers()
def get_coordinates():
    x,y=list(map(int,input("enter the coordinates: ").split()))
    if x in [0,1,2] and y in [0,1,2]:
        return [x,y]
    else:
        print("invalid input")
        return get_coordinates()
def check_for_win(board):
    for row in board:
        if row[0]==row[1]==row[2] and row[0]!=' ':
            return True
    for i in range(len(board)):
        if board[0][i]==board[1][i]==board[2][i] and board[2][i]!=' ':
            return True
        if board[0][0]==board[1][1]==board[2][2] and board[2][2]!=' ':
            return True
        if board[0][2]==board[1][1]==board[2][0] and board[2][0]!=' ':
            return True
        return False
def update_board(board,chance,marker,x,y):
    if chance==True:
        board[x][y]=marker
        if check_for_win(board):
            print("player1 wins")
            return "game over"
        return False
    else:   
        board[x][y]=marker
        if check_for_win(board):
            print("player2 wins")
            return "game over"
        return True
def play_game():
    player1=0
    player2=0
    m1,m2=get_markers()
    print(f'player1:{m1},player2:{m2}')
    chance=True
    while True:
        print_board(board)
        x,y=get_coordinates()
        if chance:
            chance=update_board(board,chance,m1,x,y)
            if chance=="game over":
                break
        else:
            chance=update_board(board,chance,m2,x,y)
            if chance=="game over":
                break
play_game()
