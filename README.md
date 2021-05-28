# TicTacToe2
class assignment for tic tac toe

/**
 * Represents a tic tac toe board on the console, positions are shown below:
 * -------------
 * | 1 | 2 | 3 |
 * -------------
 * | 4 | 5 | 6 |
 * -------------
 * | 7 | 8 | 9 |
 * -------------
 *
 * An example board in mid play looks like this:
 * -------------
 * | X |   |   |
 * -------------
 * |   | O |   |
 * -------------
 * | O |   | X |
 * -------------
 *
 * @author Vinayak Rao
 *
 */
import java.util.Scanner;

public class TicTacToe2
{
    public enum Marker
    {
        EMPTY,
        X,
        O
    };

    private static Marker position1 = Marker.EMPTY;
    private static Marker position2 = Marker.EMPTY;
    private static Marker position3 = Marker.EMPTY;
    private static Marker position4 = Marker.EMPTY;
    private static Marker position5 = Marker.EMPTY;
    private static Marker position6 = Marker.EMPTY;
    private static Marker position7 = Marker.EMPTY;
    private static Marker position8 = Marker.EMPTY;
    private static Marker position9 = Marker.EMPTY;

    private static Marker turn = Marker.X;


    public static void main (String args[])
    {
      System.out.println("-------------");
      System.out.println("| 1 | 2 | 3 |");
      System.out.println("-------------");
      System.out.println("| 4 | 5 | 6 |");
      System.out.println("-------------");
      System.out.println("| 7 | 8 | 9 |");
      System.out.println("-------------");
      System.out.println();
      System.out.println("The following above displays the Tic Tac Toe positions.");

      Scanner scan = new Scanner(System.in);

      for (int x = 0; x <= 9; x++)
      {
        if (hasWon(Marker.X) == true)
        {
          System.out.println("Player X won!");
          System.exit(0);
        }
        if (hasWon(Marker.O) == true)
        {
          System.out.println("Player O won!");
          System.exit(0);
        }
        boolean tie = isTie();
        if (tie == true)
        {
          System.out.println("Tie!");
        }
        else
        {
          if (x % 2 == 1)
          {
            boolean playerO = true;
            System.out.println("Player O enter a position number.");
            while (playerO == true)
            {
              Marker blank = Marker.EMPTY;
              turn =  Marker.O;
              int pos = scan.nextInt();
              if (isValidMove(pos) == true)
              {
                markTheBoard(turn, pos);
                printBoard();
                playerO = false;
              }
              else
              {
                System.out.println("Sorry, position " + pos + " is already taken or invalid. Plese enter another position number.");
              }
            }
          }
          else
          {
            boolean playerX = true;
            System.out.println("Player X enter a position number.");
            while (playerX == true)
            {
              Marker blank = Marker.EMPTY;
              turn = Marker.X;
              int pos = scan.nextInt();
              if (isValidMove(pos) == true)
              {
                markTheBoard(turn, pos);
                printBoard();
                playerX = false;
              }
              else
              {
                System.out.println("Sorry, position " + pos + " is already taken or invalid. Plese enter another position number.");
              }
            }
          }
        }
      }
    }




    public static String printMarker (Marker m)
    {
      if (m == Marker.O)
      {
        return "O";
      }
      else if (m == Marker.X)
      {
        return "X";
      }
      else
      {
        return " ";
      }
    }

    /**
      * This function returns true if the spot is empty, false if not.
      */
    public static boolean isValidMove(int pos)
    {
      if (pos > 0 && pos < 10)
      {
        Marker m = Marker.EMPTY;
        switch(pos)
        {
          case 1:
          {
            m = position1;
            break;
          }
          case 2:
          {
            m = position2;
            break;
          }
          case 3:
          {
            m = position3;
            break;
          }
          case 4:
          {
            m = position4;
            break;
          }
          case 5:
          {
            m = position5;
            break;
          }
          case 6:
          {
            m = position6;
            break;
          }
          case 7:
          {
            m = position7;
            break;
          }
          case 8:
          {
            m = position8;
            break;
          }
          case 9:
          {
            m = position9;
            break;
          }
        }
          if (m == Marker.EMPTY)
          {
            return true;
          }
          else
          {
            return false;
          }
      }
      else
      {
        return false;
      }
    }

    /**
     * This method will print the board as shown in the above example.
     */
    public static void printBoard()
    {
      System.out.println("-------------");
      System.out.println("| " + printMarker(position1) + " | " + printMarker(position2) + " | " + printMarker(position3) + " | ");
      System.out.println("-------------");
      System.out.println("| " + printMarker(position4) + " | " + printMarker(position5) + " | " + printMarker(position6) + " | ");
      System.out.println("-------------");
      System.out.println("| " + printMarker(position7) + " | " + printMarker(position8) + " | " + printMarker(position9) + " | ");
      System.out.println("-------------");


    }

    /**
     * Checks if a particular player has won.
     *
     * @param m The player to check
     * @return true if the player won, false if not
     */
    public static boolean hasWon(Marker m)
    {
      if ((position1 == m  && position2 == m && position3 == m)
          ||(position4 == m  && position5 == m && position6 == m)
          ||(position7 == m  && position8 == m && position9 == m)
          ||(position1 == m  && position4 == m && position7 == m)
          ||(position2 == m  && position5 == m && position8 == m)
          ||(position3 == m  && position6 == m && position9 == m)
          ||(position1 == m  && position5 == m && position9 == m)
          ||(position3 == m  && position5 == m && position7 == m))
        {
          return true;
        }
      return false;
    }

    /**
     * Checks if the board is full with no winner
     * @return true if the board is full with no winner, false otherwise
     */
    public static boolean isTie()
    {
      boolean tie = true;
      Marker m = Marker.EMPTY;
      if (position1 != m && position2 != m && position3 != m
          && position4 != m && position5 != m && position6 != m
          && position7 != m && position8 != m && position9 != m)
          {
            return tie;
          }
      else
      {
        tie = false;
        return tie;
      }
    }

    /**
     * Mark the given position with the given marker
     * @param m The marker of the player given
     * @param pos The position that we are marking
     */

    public static void markTheBoard(Marker m, int pos)
    {
      switch (pos)
      {
        case 1:
        {
          position1 = m;
          break;
        }
        case 2:
        {
          position2 = m;
          break;
        }
        case 3:
        {
          position3 = m;
          break;
        }
        case 4:
        {
          position4 = m;
          break;
        }
        case 5:
        {
          position5 = m;
          break;
        }
        case 6:
        {
          position6 = m;
          break;
        }
        case 7:
        {
          position7 = m;
          break;
        }
        case 8:
        {
          position8 = m;
          break;
        }
        case 9:
        {
          position9 = m;
          break;
        }
      }
    }
}
