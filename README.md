# CAPTCHA Generator 1.0

A lightweight, simple, and efficient CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart) generator built with Python. This project generates random alphanumeric CAPTCHAs with special characters for basic security implementations.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Customization](#customization)
- [Project Structure](#project-structure)
- [Code Explanation](#code-explanation)
- [Example Output](#example-output)
- [Limitations](#limitations)
- [Future Enhancements](#future-enhancements)
- [Contributing](#contributing)
- [License](#license)
- [Author](#author)

## 🔍 Overview

This is the basic and simplest version of CAPTCHA Generator 1.0 using Python. The application generates random text-based CAPTCHAs by combining uppercase letters, lowercase letters, numbers, and special characters. It's designed to be a foundational project for understanding CAPTCHA generation and can be integrated into web applications, forms, or security systems.

**Author:** Pareekshith.P  
**Release Date:** August 24, 2023  
**Version:** 1.0

## ✨ Features

- **Random CAPTCHA Generation**: Creates unique CAPTCHAs every time the script runs
- **Multi-Character Support**: Includes uppercase letters, lowercase letters, numbers, and special characters
- **Customizable Length**: Easy configuration for character count from each category
- **Lightweight**: Uses only Python's built-in `random` module - no external dependencies
- **Simple Implementation**: Clean, readable code suitable for beginners
- **Fast Execution**: Generates CAPTCHAs instantly

## 💻 Requirements

- **Python**: Version 3.x or higher
- **Operating System**: Windows, macOS, Linux (platform-independent)
- **Dependencies**: None (uses only Python standard library)

## 📥 Installation

1. **Clone or Download the Repository**

   ```bash
   git clone https://github.com/yourusername/captcha_generator-1.0.git
   cd captcha_generator-1.0
   ```

2. **Verify Python Installation**

   ```bash
   python --version
   ```

   or

   ```bash
   python3 --version
   ```

3. **No Additional Dependencies Required**  
   This project uses only Python's standard library, so no pip installations are needed.

## 🚀 Usage

### Basic Usage

1. Navigate to the project directory:

   ```bash
   cd captcha_generator-1.0
   ```

2. Run the script:

   ```bash
   python "CaptchaCreator 1.0.py"
   ```

   or

   ```bash
   python3 "CaptchaCreator 1.0.py"
   ```

3. The CAPTCHA will be displayed in the terminal:
   ```
   AB@cd1
   ```

### Running Multiple Times

Each execution generates a new random CAPTCHA:

```bash
python "CaptchaCreator 1.0.py"  # Output: XY#mn5
python "CaptchaCreator 1.0.py"  # Output: PQ$gh9
python "CaptchaCreator 1.0.py"  # Output: KL@uv2
```

## 🔧 How It Works

The CAPTCHA generator operates using the following process:

1. **Character Pool Definition**: Four separate lists are defined containing:

   - Numbers (0-9)
   - Special characters (!@#$%^&\*)
   - Lowercase letters (a-z)
   - Uppercase letters (A-Z)

2. **Random Selection**: The `random.choice()` function randomly selects characters from each pool

3. **String Concatenation**: Selected characters are joined together to form the final CAPTCHA string

4. **Display**: The generated CAPTCHA is printed to the console

### Default CAPTCHA Structure

| Component          | Characters | Count | Example |
| ------------------ | ---------- | ----- | ------- |
| Uppercase Letters  | A-Z        | 2     | AB      |
| Special Characters | !@#$%^&\*  | 1     | @       |
| Lowercase Letters  | a-z        | 2     | cd      |
| Numbers            | 0-9        | 1     | 1       |

**Default Output Format**: 6 characters total (e.g., `AB@cd1`)

## ⚙️ Customization

### Changing CAPTCHA Length

To modify the number of characters from each category, edit the `display_captcha` section:

```python
display_captcha = (
    ''.join(random.choice(captcha_cletter) for _ in range(2)) +        # 2 uppercase
    ''.join(random.choice(captcha_charectersequence) for _ in range(1)) +  # 1 special char
    ''.join(random.choice(captcha_letter) for _ in range(2)) +         # 2 lowercase
    ''.join(random.choice(captcha_numbersequence) for _ in range(1))   # 1 number
)
```

**Examples:**

- For an 8-character CAPTCHA (3 uppercase, 2 special, 2 lowercase, 1 number):

  ```python
  display_captcha = (
      ''.join(random.choice(captcha_cletter) for _ in range(3)) +
      ''.join(random.choice(captcha_charectersequence) for _ in range(2)) +
      ''.join(random.choice(captcha_letter) for _ in range(2)) +
      ''.join(random.choice(captcha_numbersequence) for _ in range(1))
  )
  ```

- For a 10-character CAPTCHA (3, 2, 3, 2):
  ```python
  display_captcha = (
      ''.join(random.choice(captcha_cletter) for _ in range(3)) +
      ''.join(random.choice(captcha_charectersequence) for _ in range(2)) +
      ''.join(random.choice(captcha_letter) for _ in range(3)) +
      ''.join(random.choice(captcha_numbersequence) for _ in range(2))
  )
  ```

### Adding More Characters

To expand the character pools, simply add more characters to the respective lists:

```python
# Add more special characters
captcha_charectersequence = ["!", "@", "#", "$", "%", "^", "&", "*", "~", "+", "=", "?"]

# Add more numbers (if needed for custom sequences)
captcha_numbersequence = ["1", "2", "3", "4", "5", "6", "7", "8", "9", "0"]
```

### Shuffling the CAPTCHA

To randomize the order of character types, you can shuffle the result:

```python
import random

# After generating display_captcha
captcha_list = list(display_captcha)
random.shuffle(captcha_list)
display_captcha = ''.join(captcha_list)
```

## 📁 Project Structure

```
captcha_generator-1.0/
│
├── CaptchaCreator 1.0.py    # Main Python script
├── README.md                 # Project documentation
└── .git/                     # Git repository folder
```

## 📝 Code Explanation

### Imports

```python
import random
```

The `random` module provides functions for generating random selections, which is essential for creating unpredictable CAPTCHAs.

### Character Pools

```python
captcha_numbersequence = ["1", "2", "3", "4", "5", "6", "7", "8", "9", "0"]
captcha_charectersequence = ["!", "@", "#", "$", "%", "^", "&", "*"]
captcha_letter = ["a", "b", "c", "d", "e", ..., "z"]
captcha_cletter = ["A", "B", "C", "D", "E", ..., "Z"]
```

These lists define all possible characters that can appear in the CAPTCHA.

### CAPTCHA Generation

```python
display_captcha = (
    ''.join(random.choice(captcha_cletter) for _ in range(2)) +
    ''.join(random.choice(captcha_charectersequence) for _ in range(1)) +
    ''.join(random.choice(captcha_letter) for _ in range(2)) +
    ''.join(random.choice(captcha_numbersequence) for _ in range(1))
)
```

- `random.choice(list)`: Selects a random element from the list
- `for _ in range(n)`: Repeats the selection n times
- `''.join(...)`: Concatenates all selected characters into a single string
- The `+` operator combines strings from different character categories

### Display

```python
print(display_captcha)
```

Outputs the generated CAPTCHA to the console.

## 📊 Example Output

Running the script multiple times produces different CAPTCHAs:

```
AB@cd1
XY#mn5
PQ$gh9
KL@uv2
DE%wx7
FG^ab3
HI&pq8
JK*st4
MN!ef6
OP@yz0
```

## ⚠️ Limitations

- **Text-only**: No image-based CAPTCHA generation
- **No Graphical Interface**: Console output only
- **Basic Security**: Not suitable for high-security applications
- **No Validation**: Does not include user input validation functionality
- **Fixed Pattern**: Character type order is predictable (uppercase → special → lowercase → number)
- **No Storage**: Generated CAPTCHAs are not saved for verification
- **No Distortion**: Characters are plain text without visual obfuscation

## 🚀 Future Enhancements

**CAPTCHA Generator 2.0** will include:

- ✅ Image-based CAPTCHA generation with visual distortion
- ✅ Background noise and line patterns
- ✅ Custom fonts and text styling
- ✅ Color variations and gradients
- ✅ CAPTCHA validation system
- ✅ Database storage for verification
- ✅ Web interface integration
- ✅ Audio CAPTCHA for accessibility
- ✅ Configurable difficulty levels
- ✅ API endpoints for easy integration

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/YourFeature`
3. **Commit your changes**: `git commit -m 'Add some feature'`
4. **Push to the branch**: `git push origin feature/YourFeature`
5. **Open a Pull Request**

### Contribution Ideas

- Add image generation capabilities
- Implement CAPTCHA validation
- Create a GUI interface
- Add more character sets (Unicode, emojis)
- Write unit tests
- Improve documentation

## 📄 License

This project is open-source and available for educational and personal use. Please provide appropriate credit when using or modifying this code.

**Note**: This is a basic implementation intended for learning purposes. For production environments requiring robust security, consider using established CAPTCHA services like Google reCAPTCHA, hCaptcha, or more advanced custom solutions.

---

_Last Updated: August 24, 2023_
