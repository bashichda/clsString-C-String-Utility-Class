# 🔤 clsString — C++ String Utility Class

![C++](https://img.shields.io/badge/Language-C%2B%2B-blue?style=flat-square&logo=cplusplus)
![Type](https://img.shields.io/badge/Type-Header--Only%20Library-teal?style=flat-square)
![OOP](https://img.shields.io/badge/Paradigm-OOP-blueviolet?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)

A **header-only C++ utility class** that wraps `std::string` with a rich set of static and instance methods for string manipulation. Each method is available both as a **static function** (works on any string) and as an **instance method** (works on the object's internal value) — giving you maximum flexibility.

---

## 📦 Installation

No build system needed. Just copy `clsString.h` into your project and include it:

```cpp
#include "clsString.h"
```

---

## 🚀 Quick Start

```cpp
#include <iostream>
#include "clsString.h"
using namespace std;

int main() {
    // Instance usage
    clsString s("  hello world  ");
    s.Trim();
    s.UpperFirstLetterOfEachWord();
    cout << s.Value; // "Hello World"

    // Static usage (no object needed)
    cout << clsString::CountWords("one two three"); // 3
    cout << clsString::CountVowels("Hello");        // 2

    return 0;
}
```

---

## 📋 API Reference

### 🏗️ Constructors

```cpp
clsString();               // Empty string ""
clsString("Hello World");  // Initialize with value
```

### ⚙️ Property

```cpp
s.Value = "new text";   // setter
string v = s.Value;     // getter
```

---

### 📏 Length & Word Count

| Method | Signature | Description |
|---|---|---|
| `Length` | `static short Length(string)` | Returns string length |
| `Length` | `short Length()` | Instance version |
| `CountWords` | `static short CountWords(string)` | Counts words separated by spaces |
| `CountWords` | `short CountWords()` | Instance version |

```cpp
clsString::Length("Hello");          // 5
clsString::CountWords("one two three"); // 3
```

---

### 🔠 Case Manipulation

| Method | Description |
|---|---|
| `UpperAllString` | Converts entire string to UPPERCASE |
| `LowerAllString` | Converts entire string to lowercase |
| `UpperFirstLetterOfEachWord` | Capitalizes first letter of every word |
| `LowerFirstLetterOfEachWord` | Lowercases first letter of every word |
| `InvertAllLettersCase` | Flips case of every character |
| `InvertLetterCase` | Flips case of a single character |

```cpp
clsString::UpperAllString("hello");           // "HELLO"
clsString::LowerAllString("WORLD");           // "world"
clsString::UpperFirstLetterOfEachWord("hi there"); // "Hi There"
clsString::InvertAllLettersCase("Hello");     // "hELLO"
clsString::InvertLetterCase('a');             // 'A'
```

---

### 🔢 Counting Letters

| Method | Signature | Description |
|---|---|---|
| `CountCapitalLetters` | `static short CountCapitalLetters(string)` | Count uppercase letters |
| `CountSmallLetters` | `static short CountSmallLetters(string)` | Count lowercase letters |
| `CountSpecificLetter` | `static short CountSpecificLetter(string, char, bool MatchCase=true)` | Count occurrences of a letter |
| `CountVowels` | `static short CountVowels(string)` | Count vowels (a, e, i, o, u) |
| `CountLetters` | `static short CountLetters(string, enWhatToCount)` | Count by category |
| `IsVowel` | `static bool IsVowel(char)` | Check if a character is a vowel |

```cpp
clsString::CountCapitalLetters("Hello World"); // 2
clsString::CountSmallLetters("Hello World");   // 8
clsString::CountVowels("Hello World");         // 3
clsString::CountSpecificLetter("Hello", 'l');  // 2
clsString::CountSpecificLetter("Hello", 'L', false); // 2 (case-insensitive)
clsString::IsVowel('a');                       // true
```

**`enWhatToCount` enum:**
```cpp
clsString::CountLetters("Hello", clsString::SmallLetters);   // 4
clsString::CountLetters("Hello", clsString::CapitalLetters); // 1
clsString::CountLetters("Hello", clsString::All);            // 5
```

---

### ✂️ Trim

| Method | Description |
|---|---|
| `TrimLeft` | Removes leading spaces |
| `TrimRight` | Removes trailing spaces |
| `Trim` | Removes both leading and trailing spaces |

```cpp
clsString::TrimLeft("  hello");   // "hello"
clsString::TrimRight("hello  ");  // "hello"
clsString::Trim("  hello  ");     // "hello"
```

---

### 🔀 Split & Join

| Method | Signature | Description |
|---|---|---|
| `Split` | `static vector<string> Split(string, string Delim)` | Splits string by delimiter into vector |
| `JoinString` | `static string JoinString(vector<string>, string Delim)` | Joins vector of strings with delimiter |
| `JoinString` | `static string JoinString(string[], short Length, string Delim)` | Joins array of strings with delimiter |

```cpp
vector<string> v = clsString::Split("a,b,c", ",");  // ["a", "b", "c"]
clsString::JoinString(v, "-");                        // "a-b-c"
```

---

### 🔄 Other Utilities

| Method | Signature | Description |
|---|---|---|
| `ReverseWordsInString` | `static string ReverseWordsInString(string)` | Reverses word order in a string |
| `ReplaceWord` | `static string ReplaceWord(string, string from, string to, bool MatchCase=true)` | Replaces a word in a string |
| `RemovePunctuations` | `static string RemovePunctuations(string)` | Strips all punctuation characters |

```cpp
clsString::ReverseWordsInString("Hello World");        // "World Hello"
clsString::ReplaceWord("I love C", "C", "C++");        // "I love C++"
clsString::ReplaceWord("Hello hi", "hi", "hey", false);// "Hello hey" (case-insensitive)
clsString::RemovePunctuations("Hello, World!");         // "Hello World"
```

---

## 🧠 Design Pattern — Static vs Instance

Every method in `clsString` comes in two forms:

```cpp
// Static — use without creating an object
string result = clsString::UpperAllString("hello");

// Instance — operates on the object's internal _Value
clsString s("hello");
s.UpperAllString();       // modifies s._Value in place
cout << s.Value;          // "HELLO"
```

This dual design makes `clsString` useful both as a **utility toolkit** and as a **string wrapper object**.

---

## 🗂️ Project Structure

```
clsString/
│
├── clsString.h    # Full class definition (header-only)
└── README.md      # Documentation
```

---

## 🛠️ Technologies Used

- **Language:** C++
- **Libraries:** `<iostream>`, `<string>`, `<vector>`, `<cctype>`
- **Concepts:** OOP, Classes, Static Methods, Properties (`__declspec`), Enums, Iterators, Header-Only Design

---

## 🔮 Possible Improvements

- [ ] Add `Contains(string)` — check if substring exists
- [ ] Add `StartsWith(string)` / `EndsWith(string)`
- [ ] Add `Repeat(int n)` — repeat string n times
- [ ] Add `PadLeft(int, char)` / `PadRight(int, char)` — padding
- [ ] Add `IndexOf(string)` — find position of substring
- [ ] Remove `__declspec` for cross-platform compatibility

---

## 👨‍💻 Author

> Built with ❤️ as part of a C++ OOP learning journey.

Feel free to fork, star ⭐, or contribute!

---

## 📄 License

This project is licensed under the **MIT License** — free to use and modify.
