# Android Kotlin Development Presentation

This presentation covers Android development using Kotlin, from basic language concepts to advanced Android components.

### Prerequisites

- **[marp](https://github.com/marp-team/marp-cli)** 

### Installation

#### macOS: 

```bash
brew install marp-cli
```

<!-- https://github.com/Homebrew/homebrew-core/blob/master/Formula/m/marp-cli.rb -->

#### Windows: **[Scoop](https://scoop.sh/)**

```cmd
scoop install marp
```
### Build

- HTML
```bash
 marp --template bespoke KOTLIN_ANDROID.MD
 or
 marp KOTLIN_ANDROID.MD --theme graph_paper.css --html  
```

- PDF
```bash
 marp --pdf KOTLIN_ANDROID.MD
```

- PPTX
```bash
 marp --pptx KOTLIN_ANDROID.MD
 or
 marp --pptx KOTLIN_ANDROID.MD --theme graph_paper.css --html
```

## 🎯 Presentation Content

### Part 1: Kotlin Fundamentals
- Hello World and basic syntax
- Variables and null safety
- Operators and control flow
- Collections (Arrays, Sets, Maps)
- Functions and lambdas

### Part 2: Object-Oriented Programming
- Classes and data classes
- Inheritance and interfaces
- Access modifiers
- Encapsulation
- Companion objects and extensions

### Part 3: Advanced Kotlin Features
- Scope functions (let, run, apply, with)
- Delegation
- Generics and type safety

### Part 4: Android Development
- Application fundamentals
- Activities and lifecycle
- Intents and navigation
- Broadcast receivers
- Services
- UI development with Compose

## 🔧 Troubleshooting

### Common Issues

1. **Theme not loading**: Ensure `graph_paper.css` is in the same directory
2. **Code not highlighting**: Check that code blocks use `kotlin` language specification
3. **Images not showing**: Use relative paths and ensure images exist

### Getting Help

- [Marp Documentation](https://marpit.marp.app/)
- [Marp CLI Documentation](https://github.com/marp-team/marp-cli)

## 📄 License

MIT License - Feel free to use and modify for your own presentations!
