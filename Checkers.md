# Checkers Data Model Concept

#### Game Process

1) Ask for the Player names per each color
2) Black player goes first
3) Player selects a GamePiece to move (Point location)
4) Player selects a position to move to (Point destination)
5) If the position is valid, GamePiece moves to destination
6) If the GamePiece passes over an opponent in its vector, the opponent GamePiece is removed and Player receives a point.
7) If the GamePiece reaches the end of the board, its status changes to KING

### CheckersEnums.java
```java
public enum PieceType {
	MAN, 
    KING
}

public enum PieceColor {
	LIGHT,
    DARK
}

public enum GameState {
	STARTING,
    PLAYING,
    FINISHED
}
```


### Checkers.java
```java
// Scoreboard for game.
private int lightScore;
private int darkScore;

// Game must have two players
private GamePlayer lightPlayer;
private GamePlayer darkPlayer;

// Turns can be calculated: (turnNumber % 2 == PieceColor) etc.
private int turnNumber;

private GameState gameState;
```

```java
/* 
Execution logic for the game is stored in the constructor. When a new
game is created, the program prepares the GamePlayers and starts the turn logic.
*/
public Checkers();

// Create dialog boxes to input player names and thus create our players or return
// them if they already exist
public GamePlayer getLightPlayer();
public GamePlayer getDarkPlayer();

// Build and getter functions to return the most current gameboard available
public AnchorPane build();
public AnchorPane getBoard();

// Getter and setter functions to keep track of the progression of the game
public GameState getGameState();
public void setGameState(GameState gameState);

// Ensures that a move is not only valid, but also checks for opponent pieces in the path
public void checkMove(PieceColor movingPieceColor, Point location, Point destination);


```


### GamePlayer.java

```java
private String playerName;

private PieceColor pieceColor;

private GamePiece[] gamePieces;

private int score;
```

```java
/*
Players have initial score of zero
*/
public GamePlayer();

public String getName();
public void setName(String name);

// Getter/setter functions to determine color and check move logic
public PieceColor getColor();
public void setColor(PieceColor color);

// Returns the players current score
public int getScore();
public void setScore(int score);
public void incScore();

public GamePiece[] getGamePieces();
public void setGamePieces(GamePiece[] gamePieces);

```


### GamePiece.java
```java
private PieceType pieceType;
private PieceColor pieceColor;
private Point location;
private Point destination;
```

```java
public GamePiece();

public PieceType getPieceType();
public void setPieceType(PieceType pieceType);
public void kingMe();

public PieceColor getPieceColor();
public void setPieceColor(PieceColor pieceColor);

public Point getLocation();
public void setLocation(Point location);

public Point getDestination();
public void setDestination(Point location);

```
