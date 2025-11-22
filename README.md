# warm-up
ds2
package algs4;

import algs32.BST;
import stdlib.StdIn;
import stdlib.Stopwatch;

public class FillAndSearchTime {
    public static void main(String[] args) {
        StdIn.fromFile("data/tale.txt");
        String[] words = StdIn.readAllStrings();

        BinarySearchST<String, Integer> binarySearchTable = new BinarySearchST<>();
        BST<String, Integer> binarySearchTree = new BST<>();

        Stopwatch fillTimerBinary = new Stopwatch();
        for (String word : words) {
            Integer count = binarySearchTable.get(word);
            if (count == null) {
                binarySearchTable.put(word, 1);
            } else {
                binarySearchTable.put(word, count + 1);
            }
        }
        double fillTimeBinary = fillTimerBinary.elapsedTime();

        Stopwatch fillTimerBST = new Stopwatch();
        for (String word : words) {
            Integer count = binarySearchTree.get(word);
            if (count == null) {
                binarySearchTree.put(word, 1);
            } else {
                binarySearchTree.put(word, count + 1);
            }
        }
        double fillTimeBST = fillTimerBST.elapsedTime();

        Stopwatch searchTimerBinary = new Stopwatch();
        for (String word : words) {
            binarySearchTable.get(word);
        }
        double searchTimeBinary = searchTimerBinary.elapsedTime();

        Stopwatch searchTimerBST = new Stopwatch();
        for (String word : words) {
            binarySearchTree.get(word);
        }
        double searchTimeBST = searchTimerBST.elapsedTime();

        System.out.println("BinarySearchST total time (fill + search): "
                + (fillTimeBinary + searchTimeBinary));
        System.out.println("BST total time (fill + search): "
                + (fillTimeBST + searchTimeBST));
    }
}
