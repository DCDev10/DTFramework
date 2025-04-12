# DTFramework

## Overview
**DTFramework** is a high-performance C++20 framework designed for building real-time, cross-platform applications. It provides a modular architecture with components like a thread-safe logger, event system, threading utilities, and platform abstractions, optimized for low-latency and scalability.

## Project Structure
The project is organized as follows:
/DTFramework
/src                # Source code
/core            # Core utilities and TypeSystem
/event_system    # Signal/Slot and EventLoop mechanisms
/threading       # ThreadPool and threading abstractions
/platform        # Cross-platform abstractions (Timer, etc.)
/logger          # Thread-safe logging system
/tests             # Unit tests and benchmarks
/docs              # Documentation (API, guides)
/demo              # Demo applications
CMakeLists.txt     # CMake build configuration


## Prerequisites
To build and develop RealTimeCpp, ensure your environment meets these requirements:
- **Operating System**:
  - Windows 10/11
  - Linux (Ubuntu 22.04 LTS or equivalent)
  - macOS (supported later, Week 4-5)
- **Compiler**:
  - Clang 15+ or GCC 11+ (Linux)
  - MSVC (Visual Studio 2022) (Windows)
- **C++ Standard**: C++20
- **Tools**:
  - CMake 3.20+
  - Git
  - (Optional) Ninja for faster builds

## Development Tools
The project uses the following tools to ensure code quality and productivity:
- **IDE**: Visual Studio Code (with C++, CMake Tools, GitLens, Clang-Format extensions) or Visual Studio 2022 (Windows).
- **Formatter**: `clang-format` (Google style).
- **Static Analysis**: `cppcheck`, `clang-tidy`.
- **Testing**: GoogleTest (unit tests), Google Benchmark (performance).
- **CI/CD**: GitHub Actions for automated build, test, and code quality checks.
- **Documentation**: Doxygen for API docs, Markdown for guides.

## Build Instructions
Follow these steps to build the project:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/username/RealTimeCpp.git
   cd RealTimeCpp
2. **Create a build directory**:
    ```bash
    mkdir build && cd build
3. **Configure with CMake**:
    ```bash
    cmake .. -DCMAKE_BUILD_TYPE=Release
    - Use -G Ninja if you have Ninja installed for faster builds.
    - For debug builds, use -DCMAKE_BUILD_TYPE=Debug.
4. **Build the project**:
    ```bash
    cmake --build .
5. **Run test**:
    ```bash
    ctest --output-on-failure

## Notes
- Ensure your compiler supports C++20 (std::atomic, Future/Promise, etc.).
- For Windows, Visual Studio 2022 must be installed with the "Desktop development with C++" workload.
- CI pipelines run automatically on push/pull requests to main and develop branches.
For detailed setup or contribution guidelines, see /docs/setup.md or contact the team.