import 'dart:io';
import 'dart:math';

/// Get a player move via keyboard input
/// If the player does not enter a valid move
/// return "Quit" so that the main game loop
/// knows to end the game
String getPlayerMove() {
  print("Would you like (R)ock, (P)aper, or (S)cissors?");
  String selection = stdin.readLineSync().toUpperCase();
  
  switch (selection) {
    case "R":
      return "⛰️";
      break;
    case "P":
      return "📃";
      break;
    case "S":
      return "✂️";
      break;
    default:  //if anything but R, P, or S
      return "Quit";
      break;
  }
}

/// Return a random move in the form of a string of either
/// "Rock", "Paper", or "Scissors"
String getComputerMove() {
  Random rand = new Random();
  int move = rand.nextInt(3);  //random int from 0 to 2
  
  switch (move) {
    case 0:
      return "⛰️";
      break;
    case 1:
      return "📃";
      break;
    case 2:
      return "✂️";
      break;
    default:
      break;
  }
}

/// Determine if the player or the computer won
/// by comparing [playerMove] to [computerMove]
String whoWon(String playerMove, String computerMove) {
  if (playerMove == computerMove) {  //if the same, it's a tie
    return "Tie";
  } else if (playerMove == "⛰️" && computerMove == "✂️") {
    return "You Win!";
  } else if (playerMove == "✂️" && computerMove == "📃") {
    return "You Win!";
  } else if (playerMove == "📃" && computerMove == "⛰️") {
    return "You Win!";
  } else {  //if it's not a tie and you didn't win, computer won
    return "Computer Wins!";
  }
}

void main() {
  while(true) {  //main game loop (qusi infinite loop)
    print("Rock, Paper, Scissors Shoot!");
    String playerMove = getPlayerMove();
    
    if (playerMove == "Quit") {
      return;  //returning from void function exits it
    }
    
    print("You played $playerMove");
    String computerMove = getComputerMove();
    print("Computer played $computerMove");
    print(whoWon(playerMove, computerMove));
  }
}
