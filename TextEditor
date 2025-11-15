import java.util.Stack;
import java.util.Queue;
import java.util.LinkedList;

class TextEditor {
    private String current; // Teks saat ini
    private Stack<String> undoStack; // Stack untuk undo
    private Queue<String> redoQueue; // Queue untuk redo

    public TextEditor() {
        this.current = ""; // Mulai dengan string kosong
        this.undoStack = new Stack<>();
        this.redoQueue = new LinkedList<>();
    }

    // Menambahkan teks ke akhir teks saat ini
    public void write(String text) {
        // Push state saat ini ke undoStack sebelum mengubah
        undoStack.push(current);
        // Update current dengan menambahkan text
        current += text;
        // Clear redoQueue karena write baru membuat cabang baru
        redoQueue.clear();
    }

    // Kembali ke state sebelumnya
    public void undo() {
        if (!undoStack.isEmpty()) {
            // Offer current ke redoQueue
            redoQueue.offer(current);
            // Pop dari undoStack ke current
            current = undoStack.pop();
        }
        // Jika undoStack kosong, tidak ada yang berubah
    }

    // Maju ke state berikutnya
    public void redo() {
        if (!redoQueue.isEmpty()) {
            // Push current ke undoStack
            undoStack.push(current);
            // Poll dari redoQueue ke current
            current = redoQueue.poll();
        }
        // Jika redoQueue kosong, tidak ada yang berubah
    }

    // Menampilkan teks saat ini
    public void show() {
        System.out.println(current);
    }

    // Getter untuk current
    public String getCurrent() {
        return current;
    }
}

// Contoh penggunaan (dalam main method)
public class Main {
    public static void main(String[] args) {
        TextEditor editor = new TextEditor();

        editor.write("Hello"); // Menulis "Hello"
        editor.show(); // Output: "Hello"

        editor.write(" World"); // Menambahkan " World", jadi "Hello World"
        editor.show(); // Output: "Hello World"

        editor.undo(); // Kembali ke "Hello"
        editor.show(); // Output: "Hello"

        editor.redo(); // Maju ke "Hello World"
        editor.show(); // Output: "Hello World"

        editor.write("!"); // Menambahkan "!", jadi "Hello World!"
        editor.show(); // Output: "Hello World!"

        editor.undo(); // Kembali ke "Hello World"
        editor.show(); // Output: "Hello World"

        editor.undo(); // Kembali ke "Hello"
        editor.show(); // Output: "Hello"

        editor.redo(); // Maju ke "Hello World"
        editor.show(); // Output: "Hello World"

        editor.redo(); // Maju ke "Hello World!"
        editor.show(); // Output: "Hello World!"
    }
}
