# TSZig

**TypeScript-like syntax → Memory-safe Zig code**

TSZig is a transpiler that enables JavaScript/TypeScript developers to write systems-level code using familiar syntax while generating memory-safe, high-performance Zig code.

## 🚀 Features

- **Familiar Syntax**: Write TypeScript-like code with types, interfaces, and ES6+ features
- **Memory Safety**: Automatic resource cleanup with `@defer` annotation system
- **Zero Memory Leaks**: Smart detection of file handles, allocations, and resources
- **Native Performance**: Generates optimized Zig code that compiles to native executables
- **C-Style Extensions**: Support for `printf()`, compound operators, ternary expressions

## 📦 Installation

### From Source

```bash
git clone https://github.com/TSZig/tszig
cd tszig
zig build
```

### Using Zig Package Manager

```zon
.{
    .dependencies = .{
        .tszig = .{
            .url = "https://github.com/TSZig/tszig/archive/refs/tags/v1.0.0.tar.gz",
            .hash = "...",
        },
    },
}
```

## 🎯 Quick Start

### 1. Create a TypeScript file

```typescript
// hello.ts
function greet(name: string): void {
    printf("Hello, %s!\n", name);
}

function main(): void {
    greet("World");
}
```

### 2. Transpile to Zig

```bash
tszig transpile hello.ts
```

### 3. Compile and Run

```bash
zig build-exe output.zig -o hello
./hello
# Output: Hello, World!
```

## 📖 Examples

### Arrow Functions

```typescript
const add = (a: number, b: number): number => a + b;
const double = (x: number): number => x * 2;

function main(): void {
    const result: number = add(5, 3);
    printf("5 + 3 = %d\n", result);
}
```

### Template Literals

```typescript
function main(): void {
    const name: string = "TSZig";
    const version: number = 1;
    const message: string = `Welcome to ${name} v${version}!`;
    console.log(message);
}
```

### Automatic Resource Cleanup

```typescript
function processFile(path: string): string {
    // @defer automatically detects and cleans up resources
    const file = fs.openSync(path, "r");
    const content = fs.readFileSync(file, "utf8");
    return content;  // file.close() auto-injected via defer
}

function main(): void {
    const data = processFile("config.json");
    // allocator.free(data) auto-injected via defer
    printf("Config: %s\n", data);
}
```

## 🛠️ CLI Commands

```bash
tszig transpile <file.ts>    # Transpile TypeScript to Zig
tszig build <file.ts>        # Transpile + compile to executable
tszig run <file.ts>          # Transpile + compile + run
tszig check <file.ts>        # Type check only
tszig --help                 # Show help
tszig --version              # Show version
```

## 📚 Documentation

- [Getting Started](docs/getting-started.md)
- [Language Features](docs/features.md)
- [API Reference](docs/api.md)
- [Examples](https://github.com/TSZig/tszig-examples)

## 🏗️ Architecture

TSZig is composed of several modular packages:

| Package | Description |
|---------|-------------|
| [tszig-core](https://github.com/TSZig/tszig-core) | Core transpilation engine |
| [tszig-runtime](https://github.com/TSZig/tszig-runtime) | Runtime support library |
| [tszig-stdlib](https://github.com/TSZig/tszig-stdlib) | Standard library mappings |
| [tszig-types](https://github.com/TSZig/tszig-types) | TypeScript definitions for IDEs |

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](https://github.com/TSZig/.github/blob/main/CONTRIBUTING.md).

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

## 🔗 Links

- [GitHub Organization](https://github.com/TSZig)
- [Examples Repository](https://github.com/TSZig/tszig-examples)
- [Issue Tracker](https://github.com/TSZig/tszig/issues)

---

<p align="center">
  <b>TSZig</b> = <b>T</b>ranspiled <b>S</b>yntax + <b>Zig</b>
</p>
