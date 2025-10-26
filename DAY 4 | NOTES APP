import java.util.*;
import java.io.*;

public class NotesApp {

    private static final String FILE_NAME = "notes.txt";

    private static void addNote(Scanner sc) {
        try {
            FileWriter writer = new FileWriter(FILE_NAME, true);
            System.out.print("Enter your note: ");
            String note = sc.nextLine();
            writer.write(note + "\n");
            writer.close();
            System.out.println("Note saved successfully!");
        } catch (IOException e) {
            System.out.println("An error occurred while saving the note.");
        }
    }

    private static void viewNote() {
        try {
            File file = new File(FILE_NAME);
            if (!file.exists()) {
                System.out.println("No notes found!");
                return;
            }
            BufferedReader reader = new BufferedReader(new FileReader(file));
            String line;
            int count = 1;
            System.out.println("\n--- Your Notes ---");
            while ((line = reader.readLine()) != null) {
                System.out.println(count + ". " + line);
                count++;
            }
            reader.close();
        } catch (IOException e) {
            System.out.println("An error occurred while reading notes.");
        }
    }

    private static void deleteNote(Scanner sc) {
        try {
            File file = new File(FILE_NAME);
            if (!file.exists()) {
                System.out.println("No notes to delete!");
                return;
            }
            List<String> notes = new ArrayList<>();
            BufferedReader reader = new BufferedReader(new FileReader(file));
            String line;
            while ((line = reader.readLine()) != null) {
                notes.add(line);
            }
            reader.close();
            if (notes.isEmpty()) {
                System.out.println("No notes to delete!");
                return;
            }
            System.out.println("\n--- Your Notes ---");
            for (int i = 0; i < notes.size(); i++) {
                System.out.println((i + 1) + ". " + notes.get(i));
            }
            System.out.print("Enter the number of the note to delete: ");
            int index = sc.nextInt();
            sc.nextLine();
            if (index < 1 || index > notes.size()) {
                System.out.println("Invalid note number.");
                return;
            }
            notes.remove(index - 1);
            FileWriter writer = new FileWriter(FILE_NAME);
            for (String n : notes) {
                writer.write(n + "\n");
            }
            writer.close();
            System.out.println("Note deleted successfully!");
        } catch (IOException e) {
            System.out.println("An error occurred while deleting the note.");
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int choice;
        do {
            System.out.println("\n===== Notes App =====");
            System.out.println("1. Add a Note");
            System.out.println("2. View Notes");
            System.out.println("3. Delete a Note");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            choice = sc.nextInt();
            sc.nextLine();
            switch (choice) {
                case 1:
                    addNote(sc);
                    break;
                case 2:
                    viewNote();
                    break;
                case 3:
                    deleteNote(sc);
                    break;
                case 4:
                    System.out.println("Exiting...");
                    break;
                default:
                    System.out.println("Invalid choice! Try again.");
                    break;
            }
        } while (choice != 4);
        sc.close();
    }
}
