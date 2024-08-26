# chess_system-java
Projeto que visa aplicar os conhecimentos de lógica e POO, para o desenvolvimento de um sistema de jogo de xadrez 


# BOARDGAME LAYER

## Classe "Position"
A classe position possui dois atributos
- __private int__ column
- __private int__ row

Essa classe se refere a posição em que a pessoa está.

---

## Classe "Piece"
A classe piece possui dois atributos com diferentes tipos e encapsulamento e um metodo
- __protected Position__ position
- __private Board__ board

O método é protected para que, apenas quem está dentro do package boardgame possa acessa-lo 
```
protected Board getBoard() {
        return board;
    }
```
O construtor dessa classe é dado por:
```
public Piece(Board board) {
        this.board = board;
        position = null;
    }
````
board é iniciado normalmente como board, já position inicia como `null`

A classe Piece é


---

## Classe "Board"
A classe Board possui três atributos
- __private int__ row
- __private int__ column
- __private Piece__ pieces
-  __private Piece[ ][ ]__ pieces

O construtor da classe Board é instanciado da seguinte forma:
```
public Board(int rows, int columns) {
        this.rows = rows;
        this.columns = columns;
        pieces = new Piece[rows][columns];
    }
```

`pieces` está sendo instanciando usando a matriz Piece e a preenchendo com o numero de `rows` e `columns`

Os dois metodos que retornam a matriz:
```
public Piece piece(int row, int column) {
        return pieces[row][column];
}

public Piece piece(Position position) {
        return pieces[position.getRow()][position.getColumn()];
}
```

---

## CHESS LAYER

## Classe "ChessMatch"
A classe chess match tem um atributo e dois metodos

- __private Board__ board


```
// Instanciando um novo tabuleiro já no construtor

public ChessMatch() {
    board = new Board(8, 8);
}

// 
public ChessPiece[][] getPieces() {
    ChessPiece[][] mat = new ChessPiece[board.getRows()][board.getColumns()];
        
        for (int i = 0; i < board.getRows(); i++) {
            for (int j = 0; j < board.getColumns(); j++) {
                mat[i][j] = (ChessPiece) board.piece(i, j);
            }
        }
        return mat;
    }
```


