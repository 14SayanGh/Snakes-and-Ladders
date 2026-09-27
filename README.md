# Snakes and Ladders

A small Java command-line game based on a 3 × 3 numbered board. The player advances by rolling a simulated die, encounters one snake and one ladder, and wins when their position passes 9.

This is an early, minimal implementation rather than a full graphical or multiplayer game. Despite the original README description, it is a console application.

## Requirements

- Java Development Kit (JDK)
- Apache Maven for Maven builds (optional)

The repository is also configured as an Eclipse/Maven project.

## Run

Compile and start the game from the repository root:

```sh
mkdir -p out
javac -d out src/main/java/main/SnakeLadders.java
java -cp out main.SnakeLadders
```

The program prints the board, then prompts you to enter `y` to roll. Continue entering `y` to advance. The current implementation reports a win after your position becomes greater than 9.

To build with Maven, run:

```sh
mvn package
```

The project coordinates are `com.faceprep.sanke:SnakeLadders:0.0.1-SNAPSHOT`.

## Current game rules

- Board positions are numbered 1 through 9 in a 3 × 3 grid.
- Each simulated roll is an integer from 0 through 4.
- The snake is mapped to one board coordinate and subtracts 4 from the position.
- The ladder is mapped to one board coordinate and adds 5 to the position.
- The win condition is a position greater than 9.

The rules and movement are implemented directly in `SnakeLadders.java`. The die range, board size, and win threshold differ from many traditional Snakes and Ladders rulesets.

## Tests

JUnit tests are under `src/test/java/main/Test.java`. The test class initializes its `SnakeLadders` field only inside `Snaketest`; the ladder and game-over tests may therefore fail with `NullPointerException`, depending on test execution order. Initialize the object for each test (or call the static methods through the class) before relying on the test suite.

## Project structure

```text
pom.xml                                  Maven project configuration
src/main/java/main/SnakeLadders.java     Console game and game rules
src/test/java/main/Test.java             JUnit tests
```

## License

No license file is included. Contact the repository owner before redistributing or reusing this project beyond the rights granted by GitHub's default terms.
