# PintOS - Development Base

**[PT-BR](#pt-br) | [EN](#en)**

---

<a name="pt-br"></a>

## 🇧🇷 Português (Brasil)

### 📋 Sobre o Projeto

Base de desenvolvimento otimizada para o **PintOS**, um sistema operacional educacional baseado em x86 desenvolvido pela Stanford. Este repositório contém melhorias na compilação, testes e debugging para facilitar o desenvolvimento de componentes do kernel.

### ✨ Melhorias Implementadas

Este repositório estende a base original do PintOS com otimizações de desenvolvimento, focando em produtividade e facilidade de debugging:

- **Configuração automática de paths**: Makefile pré-configurado com paths corretos, eliminando necessidade de export manual
- **Suporte multiplataforma**: Otimizações para Arch Linux, redução de tamanho do `loader.bin` para compatibilidade em diferentes ambientes
- **Testes granulares**: Sistema de testes modular com execução individual via `make test TEST=<nome>`, facilitando debug iterativo
- **Saída visual melhorada**: Testes exibem resultados em cores para melhor legibilidade e rapidez na identificação de falhas
- **Macro de debug simplificada**: `DEBUG_PRINT()` em `lib/debug.h` reduz boilerplate comparado a `printf` tradicional
- **Validação compile-time**: Assertions estáticas em structs críticas (ex: `inode_disk`) previnem erros silenciosos em tempo de execução

### 🔧 Pré-requisitos

| Ferramenta | Descrição | Instalação |
|-----------|-----------|-----------|
| **Make** | Sistema de build | `sudo apt install make` |
| **GCC** | Compilador C | `sudo apt install gcc` |
| **GDB** | Depurador | `sudo apt install gdb` |
| **QEMU** | Emulador (recomendado) | `sudo apt install qemu-system-i386` |

### 💻 Ambiente

- **Linux/WSL**: Suportado nativamente
- **WSL2**: Instale conforme [guia oficial da Microsoft](https://learn.microsoft.com/pt-br/windows/wsl/install)
- **QEMU vs Bochs**: Use QEMU para melhor compatibilidade

### 🚀 Início Rápido

#### Compilar e testar:

```bash
cd src/threads      # (ou userprog, vm, filesys)
make
make check
```

#### Executar teste específico:

```bash
make test TEST=alarm-single
```

#### Verbose mode (para debug):

```bash
make check VERBOSE=1
```

#### Limpar e recompilar:

```bash
cd build
make clean
make check
```

### 📁 Estrutura do Projeto

O projeto divide-se em 4 módulos principais:

| Módulo | Caminho | Descrição |
|--------|---------|-----------|
| **Threads** | `src/threads/` | Escalonamento, contexto, sincronização |
| **User Programs** | `src/userprog/` | Programas de usuário, syscalls |
| **Virtual Memory** | `src/vm/` | Paginação, memória virtual |
| **File System** | `src/filesys/` | Inodes, diretórios, cache |

### 📝 Testes

Os testes são gerados em `build/tests/` após execução:

```bash
# Rodar teste específico com resultado detalhado
make tests/threads/alarm-single.result

# Ver todos os testes disponíveis
ls src/tests/
```

### 🐛 Debugging

Use a macro de debug simplificada:

```c
#include "lib/debug.h"

DEBUG_PRINT("Variable value: %d\n", variable);
```

Mais informações em `lib/debug.h`.

### 📄 Licença

Veja LICENSE no diretório src/.

### 🙏 Agradecimentos

- Stanford Computer Systems Laboratory
- Projeto PintOS original pela Universidade de Stanford

---

<a name="en"></a>

## 🇬🇧 English

### 📋 About the Project

Optimized development base for **PintOS**, an educational operating system based on x86 developed by Stanford. This repository contains improvements in compilation, testing, and debugging to facilitate kernel component development.

### ✨ Implemented Improvements

This repository extends the original PintOS base with development optimizations, focusing on productivity and debugging ease:

- **Automatic path configuration**: Pre-configured Makefile with correct paths, eliminating manual export necessity
- **Cross-platform support**: Arch Linux optimizations, `loader.bin` size reduction for compatibility across environments
- **Granular testing**: Modular test system with individual execution via `make test TEST=<name>`, enabling iterative debugging
- **Enhanced visual output**: Tests display results in colors for improved readability and quick failure identification
- **Simplified debug macro**: `DEBUG_PRINT()` in `lib/debug.h` reduces boilerplate compared to traditional `printf`
- **Compile-time validation**: Static assertions in critical structs (e.g., `inode_disk`) prevent silent runtime errors

### 🔧 Requirements

| Tool | Description | Installation |
|------|-------------|--------------|
| **Make** | Build system | `sudo apt install make` |
| **GCC** | C compiler | `sudo apt install gcc` |
| **GDB** | Debugger | `sudo apt install gdb` |
| **QEMU** | Emulator (recommended) | `sudo apt install qemu-system-i386` |

### 💻 Environment

- **Linux/WSL**: Natively supported
- **WSL2**: Install as per [Microsoft's official guide](https://learn.microsoft.com/en-us/windows/wsl/install)
- **QEMU vs Bochs**: Use QEMU for better compatibility

### 🚀 Quick Start

#### Compile and test:

```bash
cd src/threads      # (or userprog, vm, filesys)
make
make check
```

#### Run specific test:

```bash
make test TEST=alarm-single
```

#### Verbose mode (for debugging):

```bash
make check VERBOSE=1
```

#### Clean and rebuild:

```bash
cd build
make clean
make check
```

### 📁 Project Structure

The project is divided into 4 main modules:

| Module | Path | Description |
|--------|------|-------------|
| **Threads** | `src/threads/` | Scheduling, context, synchronization |
| **User Programs** | `src/userprog/` | User programs, system calls |
| **Virtual Memory** | `src/vm/` | Paging, virtual memory |
| **File System** | `src/filesys/` | Inodes, directories, cache |

### 📝 Testing

Tests are generated in `build/tests/` after execution:

```bash
# Run specific test with detailed result
make tests/threads/alarm-single.result

# View all available tests
ls src/tests/
```

### 🐛 Debugging

Use the simplified debug macro:

```c
#include "lib/debug.h"

DEBUG_PRINT("Variable value: %d\n", variable);
```

More information in `lib/debug.h`.

### 📄 License

See LICENSE in src/ directory.

### 🙏 Acknowledgments

- Stanford Computer Systems Laboratory
- Original PintOS project by Stanford University
