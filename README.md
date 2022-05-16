# LP_Code
#-------Depth first search-------
'''graph={'A':['B','C'],
       'B':['C','D'],
       'C':['X'],
       'D':['v']}

visited=set()
def dfs(visited,graph,node):
    if node not in visited:
        print(node)
        visited.add(node)
        for i in graph[node]:
            dfs(visited,graph,i)
print("Here is the depth-first search")
dfs(visited,graph,'B')'''



#------Breadth first serach------
'''graph = {
'A' : ['B','C'],
'B' : ['D', 'E'],
'C' : ['F'],
'D' : [],
'E' : ['F'],
'F' : []
}

visited=[]
queue=[]
def Bfs(visited,graph,node):
    visited.append(node)
    queue.append(node)

    while queue:
        m=queue.pop(0)
        print(m,end=" ")
        for i in graph[m]:
            if i not in visited:
                visited.append(i)
                queue.append(i)

print('breadth first search is below')
Bfs(visited,graph,'C')'''

#-----N Queen Problem-----
n = int(input("Enter the value of n"))
board = []


def getBoard():
    for i in range(n):
        nthList = []
        for j in range(n):
            nthList.append(0)
        board.append(nthList)


def printBoard():
    for i in range(n):
        for j in range(n):
            print(board[i][j], end=" ")
        print("")


def isSafe(row, col):
    for i in range(n):
        if board[row][i] == 1:
            return False
    for j in range(n):
        if board[j][col] == 1:
            return False

    i = row - 1
    j = col - 1
    while (i >= 0 and j >= 0):
        if board[i][j] == 1:
            return False
        i = i - 1
        j = j - 1

    i = row - 1
    j = col + 1
    while (i >= 0 and j < n):
        if board[i][j] == 1:
            return False
        i = i - 1
        j = j + 1

    i = row + 1
    j = col - 1
    while (i < n and j >= 0):
        if board[i][j] == 1:
            return False
        i = i + 1
        j = j - 1

    i = row + 1
    j = col + 1
    while (i < n and j < n):
        if board[i][j] == 1:
            return False
        i = i + 1
        j = j + 1
    return True


def Put(n, count):
    if count == n:
        return True
    for i in range(n):
        for j in range(n):
            if isSafe(i, j):
                board[i][j] = 1
                count = count + 1
                if Put(n, count) == True:
                    return True
                board[i][j] = 0
                count = count - 1
    return False


getBoard()
Put(n, 0)
printBoard()
