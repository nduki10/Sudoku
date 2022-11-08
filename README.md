# Sudoku
Sudoku Solver
import numpy as np


grid = [[4,0,0,2,3,0,0,0,0],
        [2,5,9,6,7,0,0,1,8],
        [0,3,1,9,8,0,2,6,4],
        [0,9,0,0,0,8,7,2,0],
        [0,0,0,4,0,9,0,3,1],
        [5,0,0,1,0,0,0,0,0],
        [8,0,5,0,0,0,1,4,0],
        [0,0,0,0,0,2,0,0,7],
        [0,1,7,8,0,0,0,0,0]]
def possible(row, col, number):
    global grid
    for i in range(0,9):
        if grid[row][i] == number:
            return False
    for i in range(0,9):
        if grid[i][col] == number:
            return False
    x0 = (col // 3) * 3
    y0 = (row // 3) * 3
    for i in range(1,3):
        for j in range(1,3):
            if grid[y0+i][x0+j] == number:
                return False
            
    return True
def solve():
    global grid
    for row in range(0,9):
        for col in range(0,9):
            if grid[row][col] == 0:
                for number in range(1,10):
                    if possible(row, col, number):
                        grid[row][col] = number
                        solve()
                        grid[row][col] = 0
                
                return
    print(np.matrix(grid))
    input('more possible solution')
solve()
