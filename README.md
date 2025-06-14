import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;

public class TextFileOperations {

    public static void main(String[] args) {
        String fileName = "example.txt";

        // Write to file
        writeToFile(fileName, "Hello, World!");
        System.out.println("Written to file: example.txt");

        // Read from file
        String content = readFromFile(fileName);
        System.out.println("File Content: " + content);

        // Modify file content
        modifyFileContent(fileName, "Hello, Universe!");
        System.out.println("Modified file content");

        // Read modified file content
        content = readFromFile(fileName);
        System.out.println("Modified File Content: " + content);
    }

    // Method to write to file
    public static void writeToFile(String fileName, String content) {
        try (FileWriter writer = new FileWriter(fileName)) {
            writer.write(content);
        } catch (IOException e) {
            System.err.println("Error writing to file: " + e.getMessage());
        }
    }

    // Method to read from file
    public static String readFromFile(String fileName) {
        try (Scanner scanner = new Scanner(new File(fileName))) {
            StringBuilder content = new StringBuilder();
            while (scanner.hasNextLine()) {
                content.append(scanner.nextLine());
            }
            return content.toString();
        } catch (IOException e) {
            System.err.println("Error reading from file: " + e.getMessage());
            return "";
        }
    }

    // Method to modify file content
    public static void modifyFileContent(String fileName, String newContent) {
        writeToFile(fileName, newContent);
    }

Output:

Written to file: example.txt
File Content: Hello, World!
Modified file content
Modified File Content: Hello, Universe!
