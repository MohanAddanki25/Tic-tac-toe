#tic-tac-toe gaame
def play(l,s,Name):
  print(f'{Name} Turn')
  row,col=(int(input("Enter Row : "))-1),(int(input("Enter column : "))-1)
  if(row<0 or row>2 or col<0 or col>2):
    return 1
  pos=row*3+col
  if(l[pos]!='   '):
    return 1
  l[pos]=s
def printGame(l):
  print(f'''

          {l[0]} | {l[1]} | {l[2]}
         __ __ __ __ __ __

          {l[3]} | {l[4]} | {l[5]}
         __ __ __ __ __ __

          {l[6]} | {l[7]} | {l[8]}

        ''')
def checkWin(l,p):
  for i in winPatterns:
    if(l[i[0]]==l[i[1]] and l[i[0]]==l[i[2]] and l[i[1]]==p):
      return True
  return False
Name1,turn=input('Enter name of player-1 ( X ) : '),' X '
Name2,flag=input('Enter name of player-2 ( O ) : '),0
Curr=Name1
l=["   " for x in range(9)]
winPatterns=[[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]]
while('   ' in l):
  if play(l,turn,Curr)==1:
      print("\nPosition not available. Try again.\n")
      continue
  printGame(l)
  if(checkWin(l,turn)):
    print(f'\n{Curr} Wins !')
    flag=1
    break
  turn=' O ' if turn==' X ' else ' X '
  Curr=Name1 if Curr==Name2 else Name2
if(flag==0 and '   ' not in l):
  print('\nTie !')
