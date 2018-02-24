---
layout: post
title: "How to validate a Sudoku"
author: "学习的Yang"
categories: techynotes
tags: [code,game]
techy: true
---
The question can be found [here](https://leetcode.com/problems/valid-sudoku/description/)

![](/assets/img/sudoku.png?raw=true)

The Sudoku board could be partially filled, where empty cells are filled with the character '.'.
A partially filled sudoku which is valid.

```
public class SudokuTest {
    @Test
    public void shouldValidTheBoard() {
        // Given
        char[][] board = {
                ".87654321".toCharArray(),
                "2........".toCharArray(),
                "3........".toCharArray(),
                "4........".toCharArray(),
                "5........".toCharArray(),
                "6........".toCharArray(),
                "7........".toCharArray(),
                "8........".toCharArray(),
                "9........".toCharArray()};

        // When
        assertTrue(isValidSudoku(board));
    }
}
```


Note:
A valid Sudoku board (partially filled) is not necessarily solvable. Only the filled cells need to be validated.
    

```
public class Sudoku {
    public static boolean isValidSudoku(char[][] board) {
        // write your code here
        boolean[] visited = new boolean[9];

        // row
        for (int i = 0; i < 9; i++) {
            Arrays.fill(visited, false);
            for (int j = 0; j < 9; j++) {
                if (!isValid(visited, board[i][j])) {
                    return false;
                }
            }
        }

        // column
        for (int i = 0; i < 9; i++) {
            Arrays.fill(visited, false);
            for (int j = 0; j < 9 ; j++) {
                if (!isValid(visited, board[j][i])) {
                    return false;
                }
            }
        }

        // sub matrix
        for(int i = 0; i < 9; i += 3){
            for(int j = 0; j < 9; j += 3){
                Arrays.fill(visited, false);
                for(int k = 0; k < 9; k++){
                    if(!isValid(visited, board[i + k / 3][ j + k % 3])) {
                        return false;
                    }
                }
            }
        }
        return true;
    }

    private static boolean isValid(boolean[] visited, char cell) {
        if (cell == '.') {
            return true;
        }

        int num = cell - '0';
        if (num < 1 || num > 9 || visited[num - 1]) {
            return false;
        }

        visited[num - 1] = true;
        return true;
    }
}


```

