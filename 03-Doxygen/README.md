# Doxygen

## Introduction

Doxygen is an open-source documentation generator used to create documentation directly from source code. It reads specially formatted comments and generates reference manuals for functions, classes and modules.

It supports C, C++, Python, Java and other programming languages.

## Features

- Generates HTML, LaTeX and PDF documentation.
- Documents functions, classes and modules.
- Creates cross-references and diagrams.
- Supports Markdown and LaTeX formulas.
- Can be integrated with Git and CI/CD workflows.

## Installation

**Windows:** Download the installer from https://www.doxygen.nl/download.html

**Linux:**
```bash
sudo apt-get install doxygen
```

**macOS:**
```bash
brew install doxygen
```

Check installation:
```bash
doxygen --version
```

## Basic Workflow

1. Write documentation comments in your source code.
2. Generate a configuration file:

```bash
doxygen -g Doxyfile
```

3. Edit the `Doxyfile` according to your requirements.
4. Generate documentation:

```bash
doxygen Doxyfile
```

5. Open `html/index.html` in your browser.

## Writing Documentation Comments

Doxygen uses special comments to describe program elements.

Example in C++:

```cpp
/**
 * @brief Adds two numbers.
 * @param a First number
 * @param b Second number
 * @return Sum of the numbers
 */
int add(int a, int b) {
    return a + b;
}
```

### Common Doxygen Tags

| Tag | Purpose |
|---|---|
| `@brief` | Short description |
| `@param` | Describes a parameter |
| `@return` | Describes return value |
| `@author` | Author information |
| `@version` | Version information |
| `@see` | Related reference |
| `@note` | Additional information |

## Documenting Classes

```cpp
/**
 * @class Car
 * @brief Represents a car object.
 */
class Car {
public:
    /**
     * @brief Starts the engine.
     * @return True if successful.
     */
    bool startEngine();
};
```

## Doxygen Configuration

The `Doxyfile` controls how documentation is generated.

Some important settings:

```text
GENERATE_HTML  = YES
GENERATE_LATEX = YES
GENERATE_RTF   = NO
GENERATE_XML   = NO
HAVE_DOT       = YES
```

- HTML generates web documentation.
- LaTeX generates printable documentation.
- RTF and XML provide other output formats.
- `HAVE_DOT` enables Graphviz-based diagrams when Graphviz is installed.

## Output

Doxygen can generate:

- HTML documentation for browsing.
- LaTeX/PDF manuals.
- Class and inheritance diagrams.
- Function call graphs.
- Cross-references between code elements.

## Best Practices

- Write meaningful comments for functions and classes.
- Explain the purpose of the code clearly.
- Use consistent documentation tags.
- Keep the `Doxyfile` in your GitHub repository.
- Update comments whenever the code changes.

## Practical Exercise

1. Install Doxygen.
2. Create a small C++ program.
3. Add Doxygen comments.
4. Generate a `Doxyfile`.
5. Run Doxygen.
6. Open the generated HTML documentation.

## References

- https://www.doxygen.nl/manual/
- https://www.doxygen.nl/download.html