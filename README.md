# hospital_system

## Project overview

This is a small Java hospital management simulation. The program reads commands from a CSV file (`INPUT.csv`), executes operations (add/remove entities, queries) against an in-memory `Hospital` model, and writes human-readable results to a text output file.

## Project structure

- `src/` - Java source files grouped by package: `view`, `control`, `model`, `utils`, `exceptions`, `enums`, `autopilot`.
- `bin/` - compiled classes (if already compiled).
- `INPUT.csv` - input file with commands (must be in the project root when running).
- `StandardOutput.txt` - output produced by the application (created when the program runs).

Key entry points and utilities:
- `view.Main` - main application class. Reads `INPUT.csv` and executes commands.
- `utils.CSVExporter` - simple CSV importer used to read `INPUT.csv`.
- `utils.MyFileLogWriter` - writes program output to `StandardOutput.txt`.

## Requirements

- Java JDK 8 or later.
- A POSIX shell to run the example build commands (macOS Terminal, Linux). On Windows, use equivalent commands or run from an IDE.

## Build and run (command line)

1. Open a terminal in the project root (the folder that contains `src` and `INPUT.csv`).

2. Compile all sources into the `bin` directory:

```bash
mkdir -p bin
javac -d bin $(find src -name "*.java")
```

3. Run the program (ensure `INPUT.csv` is present in the current directory):

```bash
java -cp bin view.Main
```

4. When finished, check `StandardOutput.txt` for the program output. Note: `view.Main` prints a message that references `output.txt`, but the logger implementation writes to `StandardOutput.txt`.

## Run from IDE

- Import the project as a plain Java project in your IDE (IntelliJ IDEA, Eclipse).
- Make sure the project SDK is Java 8+ and `src` is marked as source root.
- Run the `view.Main` class. Place `INPUT.csv` in the project working directory (project root) before running.

## Input format

- `INPUT.csv` is a comma-separated file where each row begins with a command name followed by parameters. `view.Main` uses `utils.CSVExporter.importCSV("INPUT.csv")` to parse it.

## Output

- The program writes readable text output using `utils.MyFileLogWriter` into `StandardOutput.txt` in the project root.

## Notes

- If you prefer a different output file name, edit `utils/MyFileLogWriter.java` (the `outputLogFile` name) or update the message string in `view.Main` to match.
- The project has no external build tool configuration (Maven/Gradle). You can add one if you want to manage dependencies or simplify builds.

---

If you want, I can also:
- add a small script (`build_and_run.sh`) to automate compilation and execution, or
- create a Gradle or Maven wrapper for easier building.
