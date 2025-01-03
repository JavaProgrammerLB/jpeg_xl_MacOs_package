To package your Java program for macOS, often as `.dmg` or `.app` files on GitHub releases, you can use tools like `jpackage` or `javapackager`. Here's how you can do it:

### 1. Ensure Your Java Program is Ready
Your `HelloWorld` Java program should be compiled into a `.jar` file first. For example, the `HelloWorld.java` file:

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### 2. Compile the Java Code
Run the following command in the terminal to compile the `HelloWorld.java` file:

```bash
javac HelloWorld.java
```

This generates a `HelloWorld.class` file.

### 3. Create the `.jar` File
Now, create the `.jar` file using the following command:

```bash
jar cvfe HelloWorld.jar HelloWorld HelloWorld.class
```

This will generate a `HelloWorld.jar` file.

### 4. Package as `.dmg` or `.app` for macOS
Use **jpackage** (available in JDK 14 and later) to package the application.

For example, to create a `.dmg` file:

```bash
jpackage \
  --type dmg \
  --name HelloWorldApp \
  --input path/to/jar/directory \
  --main-jar HelloWorld.jar \
  --main-class HelloWorld \
  --java-options "-Djava.awt.headless=true" \
  --icon path/to/icon.icns \
  --app-version 1.0
```

- `--type dmg`: Specifies the output format as `.dmg`.
- `--name`: The name of the application.
- `--main-jar`: The `.jar` file for your Java application.
- `--main-class`: The main class to run.
- `--icon`: Path to a macOS icon file (optional but recommended).
- `--app-version`: Application version.

### 5. Test the `.dmg` File
After running the `jpackage` command, you will get a `.dmg` file. You can mount the `.dmg` and verify that your app is working correctly.

### 6. Upload to GitHub
Finally, you can upload the `.dmg` or `.app` file to the **Releases** page of your GitHub repository for distribution.

This is the standard way to package and distribute Java applications for macOS via GitHub releases.