import 'dart:io';
import 'dart:math';


String getPlayerMove() {
  print("Would you like (R)ock, (P)aper, or (S)cissors?");
  String selection = stdin.readLineSync().toUpperCase();
  
  switch (selection) {
    case "R":
      return "Rock";
      break;
    case "P":
      return "Paper";
      break;
    case "S":
      return "Scissors";
      break;
    default:  //if anything but R, P, or S
      return "Quit";
      break;
  }
}


String getComputerMove() {
  Random rand = new Random();
  int move = rand.nextInt(3);  //random int from 0 to 2
  
  switch (move) {
    case 0:
      return "Rock";
      break;
    case 1:
      return "Paper";
      break;
    case 2:
      return "Scissors";
      break;
    default:
      break;
  }
}


String whoWon(String playerMove, String computerMove) {
  if (playerMove == computerMove) {  //if the same, it's a tie
    return "Tie";
  } else if (playerMove == "Rock" && computerMove == "Scissors") {
    return "You Win!";
  } else if (playerMove == "Scissors" && computerMove == "Paper") {
    return "You Win!";
  } else if (playerMove == "Paper" && computerMove == "Rock") {
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
