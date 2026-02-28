using System;

class Program
{
    static void Main()
    {
        while (true)
        {
           Console.Clear();
		Console.WriteLine("----Game Menu----");
		Console.WriteLine("Press 1 to start Tic Tac Toe(PVP)");
		Console.WriteLine("Press 2 to start Rock, Paper, Scissors (PVC)");
		Console.WriteLine("Press 3 to exit the game");
		Console.WriteLine("Please select an option");

           string choice = Console.ReadLine();

            if (choice == "1")
            {
                PlayTicTacToe();
            }
            else if (choice == "2")
            {
                PlayRockPaperScissors();
            }
            else if (choice == "3")
            {
                Console.WriteLine("Goodbye!");
                return;
            }
            else
            {
                Console.WriteLine("Invalid choice. Press Enter to try again...");
                Console.ReadLine();
            }
        }
    }


    // TIC TAC TOE
    static void PlayTicTacToe()
    {
        char[] board = new char[9];
        for (int i = 0; i < 9; i++) board[i] = ' ';

        char currentPlayer = 'X';

        while (true)
        {
            Console.Clear();
            Console.WriteLine(" Tic Tac Toe (2 players) ");
            Console.WriteLine($"Player {currentPlayer}'s turn\n");

            DrawBoard(board);

            int move = GetTicTacToeMove(board);
            board[move] = currentPlayer;

            if (CheckWinner(board, currentPlayer))
            {
                Console.Clear();
                Console.WriteLine(" Tic Tac Toe (2 players) \n");
                DrawBoard(board);
                Console.WriteLine($"\nPlayer {currentPlayer} wins!");
                PauseToMenu();
                return;
            }

            if (IsBoardFull(board))
            {
                Console.Clear();
                Console.WriteLine(" Tic Tac Toe (2 players) \n");
                DrawBoard(board);
                Console.WriteLine("\nIt's a draw!");
                PauseToMenu();
                return;
            }

            currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
        }
    }

    static void DrawBoard(char[] b)
    {
        // show numbers where spaces are empty (helps players choose)
        string C(int i) => b[i] == ' ' ? (i + 1).ToString() : b[i].ToString();

        Console.WriteLine($" {C(0)} | {C(1)} | {C(2)} ");
        Console.WriteLine("---+---+---");
        Console.WriteLine($" {C(3)} | {C(4)} | {C(5)} ");
        Console.WriteLine("---+---+---");
        Console.WriteLine($" {C(6)} | {C(7)} | {C(8)} ");
    }

    static int GetTicTacToeMove(char[] board)
    {
        while (true)
        {
            Console.Write("\nPick a square (1-9): ");
            string input = Console.ReadLine()?.Trim();

            if (!int.TryParse(input, out int pos))
            {
                Console.WriteLine("Please enter a number.");
                continue;
            }

            if (pos < 1 || pos > 9)
            {
                Console.WriteLine("Number must be from 1 to 9.");
                continue;
            }

            int index = pos - 1;
            if (board[index] != ' ')
            {
                Console.WriteLine("That square is already taken. Try again.");
                continue;
            }

            return index;
        }
    }

    static bool CheckWinner(char[] b, char p)
    {
        int[,] wins = new int[,]
        {
            {0,1,2}, {3,4,5}, {6,7,8}, // rows
            {0,3,6}, {1,4,7}, {2,5,8}, // cols
            {0,4,8}, {2,4,6}           // diagonals
        };

        for (int i = 0; i < wins.GetLength(0); i++)
        {
            int a = wins[i, 0];
            int c = wins[i, 1];
            int d = wins[i, 2];

            if (b[a] == p && b[c] == p && b[d] == p)
                return true;
        }

        return false;
    }

    static bool IsBoardFull(char[] board)
    {
        for (int i = 0; i < board.Length; i++)
        {
            if (board[i] == ' ') return false;
        }
        return true;
    }


    // ROCK PAPER SCISSORS
    static void PlayRockPaperScissors()
    {
        Random rng = new Random();
        int playerScore = 0;
        int computerScore = 0;

        while (true)
        {
            Console.Clear();
            Console.WriteLine(" Rock Paper Scissors ");
            Console.WriteLine("Type: r = Rock, p = Paper, s = Scissors");
            Console.WriteLine("Type: q = Quit to menu\n");
            Console.WriteLine($"Score: You {playerScore} - {computerScore} Computer\n");

            Console.Write("Your choice (r/p/s/q): ");
            string input = Console.ReadLine()?.Trim().ToLower();

            if (input == "q")
            {
                PauseToMenu();
                return;
            }

            string playerMove = ParseRpsMove(input);
            if (playerMove == null)
            {
                Console.WriteLine("Invalid input. Press Enter to try again...");
                Console.ReadLine();
                continue;
            }

            string[] moves = { "Rock", "Paper", "Scissors" };
            string computerMove = moves[rng.Next(0, 3)];

            Console.WriteLine($"\nYou chose: {playerMove}");
            Console.WriteLine($"Computer chose: {computerMove}");

            int result = CompareRps(playerMove, computerMove);
            if (result == 0)
            {
                Console.WriteLine("\nResult: Draw!");
            }
            else if (result == 1)
            {
                Console.WriteLine("\nResult: You win!");
                playerScore++;
            }
            else
            {
                Console.WriteLine("\nResult: Computer wins!");
                computerScore++;
            }

            Console.WriteLine("\nPress Enter to play again...");
            Console.ReadLine();
        }
    }

    static string ParseRpsMove(string input)
    {
        if (input == "r") return "Rock";
        if (input == "p") return "Paper";
        if (input == "s") return "Scissors";
        return null;
    }

    static int CompareRps(string player, string computer)
    {
        if (player == computer) return 0;

        // Player win
        if (player == "Rock" && computer == "Scissors") return 1;
        if (player == "Paper" && computer == "Rock") return 1;
        if (player == "Scissors" && computer == "Paper") return 1;
		
        return -1;
    }


    static void PauseToMenu()
    {
        Console.WriteLine("\nPress Enter to return to the menu...");
        Console.ReadLine();
    }
}
