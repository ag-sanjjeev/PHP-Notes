## &#10162; File Handling:
File handling in PHP involves working with files on the server, such as creating, reading, writing, and manipulating files with their contents. This is essential tasks on server like storing and retrieving data, generating dynamic content, and managing file uploads.

### &#9780; Overview:
1. [Handling Directory](#-handling-directory)
2. [Handling File](#-handling-file)
3. [Uploading a file](#-uploading-a-file)
4. [Downloading a file](#-downloading-a-file)
5. [File Handling Flags](#-file-handling-flags)
6. [Common File Handling Functions](#-common-file-handling-functions)
7. [Security Considerations](#-security-considerations)

### &#10022; Handling Directory:
- Creating a Directory: using `mkdir()` function.
```php
mkdir("new_directory");
```

- Renaming a Directory: using `rename()` function.
```php
rename("old_directory", "new_directory");
```

- Removing a Directory: remove an empty directory using `rmdir()` function.
```php
rmdir("empty_directory");
```

### &#10022; Handling File:
- Creating a File: using `fopen()` with `w` write flag.
```php
$file = fopen("new_file.txt", "w");
fwrite($file, "Hello, world!");
fclose($file);
```

- File Pointer: When open a file, the handler has pointer that indicates the current position within a file.

- File Modes: Different modes for opening a file, such as "r" for reading, "w" for writing, "a" for appending, etc.

- Editing a File:
```php
$file = fopen("existing_file.txt", "r+");
$contents = fread($file, filesize("existing_file.txt"));
$contents = str_replace("old_text", "new_text", $contents);
rewind($file);
fwrite($file, $contents);
fclose($file);
```

- Reading a File:
```php
$file = fopen("existing_file.txt", "r");
while (!feof($file)) {
    $line = fgets($file);
    echo $line;
}
fclose($file);
```

- Replacing a File:
```php
$file = fopen("existing_file.txt", "w");
fwrite($file, "New content");
fclose($file);
```

- Removing a File:
```php
unlink("file_to_delete.txt");
```

### &#10022; Uploading a File:
To store the uploaded file in server using, `move_uploaded_file()` function.

```php
if (isset($_FILES['fileToUpload'])) {
    $targetDir = "uploads/";
    $targetFile = $targetDir . basename($_FILES["fileToUpload"]["name"]);
    move_uploaded_file($_FILES["fileToUpload"]["tmp_name"], $targetFile);
}
```

### &#10022; Downloading a File:

```php
header('Content-Description: File Transfer');
header('Content-Type: application/octet-stream');
header('Content-Disposition: attachment; filename="' . basename($file) . '"');
header('Expires: 0');
header('Cache-Control: must-revalidate');
header('Pragma: public');
readfile($file);
exit;
```

### &#10022; File Handling Flags:
These flags are passed as the second argument to the `fopen()` function.
- `r`: Open a file for reading only.
- `w`: Open a file for writing only. If the file doesn't exist, it creates a new one. If it exists, it truncates its contents.
- `a`: Open a file for appending. If the file doesn't exist, it creates a new one.
- `x`: Create a new file for exclusive access. If the file already exists, the function fails.
- `r+`: Open a file for reading and writing.
- `w+`: Open a file for reading and writing. If the file doesn't exist, it creates a new one. If it exists, it truncates its contents.
- `a+`: Open a file for reading and appending.
- `b`: Open the file in binary mode.
- `t`: Open the file in text mode (default).
- `FILE_USE_INCLUDE_PATH`: Search for the file in the include path.
- `FILE_IGNORE_NEW_LINES`: Omit newlines at the end of each array element when reading lines.
- `FILE_SKIP_EMPTY_LINES`: Skip empty lines when reading lines.

*Example:*
```php
// Open a file for reading
$handle = fopen("myfile.txt", "r");

// Open a file for writing, creating it if it doesn't exist
$handle = fopen("newfile.txt", "w");

// Open a file for appending, creating it if it doesn't exist
$handle = fopen("log.txt", "a");
```

### &#10022; Common File Handling Functions:
- `fopen()`: Opens a file and returns a file pointer.
   ```php
   $handle = fopen("myfile.txt", "r"); // Opens a file for reading
   ```
- `fclose()`: Closes an open file.
   ```php
   fclose($handle);
   ```
- `fread()`: Reads a specified number of bytes from a file.
   ```php
   $data = fread($handle, 1024);
   ```
- `fgets()`: Reads a line from a file.
   ```php
   $line = fgets($handle);
   ```
- `file_get_contents()`: Reads an entire file into a string.
   ```php
   $contents = file_get_contents("myfile.txt");
   ```
- `fwrite()`: Writes data to a file.
   ```php
   fwrite($handle, "Hello, world!");
   ```
- `file_put_contents()`: Writes data to a file.
   ```php
   file_put_contents("myfile.txt", "Hello, world!");
   ```
- `file_exists()`: Checks if a file exists.
   ```php
   if (file_exists("myfile.txt")) {
       // File exists
   }
   ```
- `filesize()`: Gets the size of a file in bytes.
   ```php
   $size = filesize("myfile.txt");
   ```
- `unlink()`: Deletes a file.
   ```php
   unlink("myfile.txt");
   ```
- `is_dir()`:Checks if a file is a directory.
   ```php
   $filename = 'myfile.txt';
   is_dir($filename);
   ```
- `is_file()`:Checks if a file is a regular file.
   ```php
   $filename = 'myfile.txt';
   is_file($filename);
   ```
- `mkdir()`: Creates a directory.
   ```php
   mkdir("new_directory");
   ```
- `rmdir()`: Deletes a directory.
   ```php
   rmdir("old_directory");
   ```
- `copy()`:** Copies a file.
   ```php
   copy($sourcefile, $destination);
   ```
- `scandir()`:** Lists files and directories in a directory.
   ```php
   scandir("directory_name");
   ```
- `flock()`:** Acquires an exclusive lock on a file.
   ```php
   flock($handle, 'w');
   ```
- `feof()`:** Checks if the end of a file has been reached.
   ```php
   feof($handle);
   ```
- `rewind()`:** Rewinds the position of the file pointer to the beginning.
   ```php
   rewind($handle);
   ```

### &#10022; Security Considerations:
- Validate and sanitize files: files, names and paths are sanitized to prevent security vulnerabilities like directory traversal attacks.
- Secure File Uploads: Validate files with their types, sizes, and destinations to prevent malicious uploads.
- File Permissions: Set appropriate file permissions to restrict access to sensitive files.
- Error Handling: Implement error handling to prevent information disclosure and security vulnerabilities.
- Regular Security Audits: Conduct regular security audits to identify and fix malicious files and vulnerabilities.

---
[&#8682; To Top](#-file-handling)

[&#10094; Previous Topic](./cookies.md) &emsp; [Next Topic &#10095;](./error-handling-and-debugging.md)

[&#8962; Goto Home Page](../README.md)