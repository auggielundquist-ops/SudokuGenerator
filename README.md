import java.util.ArrayList;

public class SudokuGenerator {

    int[][] board;

    public SudokuGenerator() {
        board = new int[9][9];
    }

    public static void main(String[] args) {

        SudokuGenerator s = new SudokuGenerator();

        s.makeBoard();
        s.fillBoard();
        s.display();
    }

    // initializes board with zeros (not really needed but kept)
    public void makeBoard() {
        for (int r = 0; r < 9; r++) {
            for (int c = 0; c < 9; c++) {
                board[r][c] = 0;
            }
        }
    }

    // creates list 1–9
    public ArrayList<Integer> makeBaseList() {
        ArrayList<Integer> nums = new ArrayList<Integer>();

        for (int i = 1; i <= 9; i++) {
            nums.add(i);
        }

        // homemade shuffle (not perfect but works)
        for (int i = 0; i < nums.size(); i++) {

            int randomIndex = (int)(Math.random() * 9);

            // swap values
            int temp = nums.get(i);
            nums.set(i, nums.get(randomIndex));
            nums.set(randomIndex, temp);
        }

        return nums;
    }

    // fills board using pattern
    public void fillBoard() {

        ArrayList<Integer> base = makeBaseList();

        for (int row = 0; row < 9; row++) {

            int shift = getShiftValue(row);

            for (int col = 0; col < 9; col++) {

                int index = col + shift;

                while (index >= 9) {
                    index = index - 9;
                }

                board[row][col] = base.get(index);
            }
        }
    }

    // calculates shift
    public int getShiftValue(int row) {

        int part1 = row * 3;
        int part2 = row / 3;

        int result = part1 + part2;

        while (result >= 9) {
            result = result - 9;
        }

        return result;
    }

    // prints board
    public void display() {

        for (int i = 0; i < 9; i++) {

            if (i == 0 || i == 3 || i == 6) {
                System.out.println("+-------+-------+-------+");
            }

            for (int j = 0; j < 9; j++) {

                if (j == 0 || j == 3 || j == 6) {
                    System.out.print("| ");
                }

                System.out.print(board[i][j] + " ");
            }

            System.out.println("|");
        }

        System.out.println("+-------+-------+-------+");
    }
}
