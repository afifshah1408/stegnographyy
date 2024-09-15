# Image Steganography Tool

This is a Python script that allows you to embed secret messages inside `.png` image files using steganography. The script uses the `stegano` library to perform Least Significant Bit (LSB) steganography.

## Features
- **Embed messages** in `.png` image files.
- **Extract messages** from `.png` image files.
- **Optional password protection** to secure the embedded message.

## Prerequisites
- Python 3.x
- `stegano` library

## Installation
1. **Python 3**: Make sure Python 3 is installed on your system. If not, you can download it from the [official Python website](https://www.python.org/downloads/).
   
2. **Install Required Python Libraries**:
   ```bash
   pip install stegano
   ```

## Usage
The script has two main functionalities:
1. **Embedding a Message**: Hide a secret message inside a `.png` image file.
2. **Extracting a Message**: Reveal the hidden message from a `.png` image file.

### Command Line Arguments
- `-f`: Specifies the path to the `.png` image file.
- `-e`: Specifies the message to embed in the image.
- `-x`: Extracts the message from the image.
- `-p`: (Optional) Specifies a password for embedding/extracting the message. If not provided, a default value `no_password_given` is used.

### Example Commands
#### 1. Embed a Message
To embed a secret message into an image:
```bash
python stego.py -f <filename.png> -e "your_secret_message" -p <password (Optional)>
```
- `<filename.png>`: Path to the `.png` image file.
- `"your_secret_message"`: The secret message to embed.
- `<password>`: (Optional) Password to protect the embedded message.

**Example**:
```bash
python stego.py -f image.png -e "This is a secret" -p mypassword
```

#### 2. Extract a Message
To extract the secret message from an image:
```bash
python stego.py -f <filename.png> -x -p <password>
```
- `<filename.png>`: Path to the `.png` image file containing the embedded message.
- `<password>`: The password used when embedding the message.

**Example**:
```bash
python stego.py -f secret_image.png -x -p mypassword
```

## Notes
- Only `.png` files are supported for embedding and extracting messages.
- When embedding a message, a new image file with the hidden message will be created and saved as `secret<number>.png`.
- If you embed a message without a password, use the `-p` flag without a value during extraction:
  ```bash
  python stego.py -f secret_image.png -x -p
  ```

## Error Handling
- If the specified file is not found, an error message will be displayed.
- If incorrect arguments are used, an error message with suggestions will be shown.

## Example Workflow
1. **Embed** a message in an image:
   ```bash
   python stego.py -f original.png -e "Hello, World!" -p secret123
   ```
   This creates a new image (e.g., `secret42.png`) with the hidden message.

2. **Extract** the message from the steganography image:
   ```bash
   python stego.py -f secret42.png -x -p secret123
   ```
   Output:
   ```
   The secret Message is Hello, World!
   ```

## License
This project is licensed under the MIT License.

