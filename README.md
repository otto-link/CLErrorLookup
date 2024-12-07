# CLErrorLookup

CLErrorLookup is a lightweight library for decoding OpenCL error codes into human-readable strings and descriptions.

## Features

- Retrieve short or detailed descriptions of OpenCL error codes.
- Throw exceptions with detailed error messages for easier debugging.

## Getting the Sources

Clone the repository using `git`:

```bash
git clone git@github.com:otto-link/CLErrorLookup.git
```

## Build and Test

### Prerequisites
- A C++ compiler with C++17 support or higher.
- CMake version 3.15 or newer.

### Build Instructions
1. Create a build directory:
   ```bash
   mkdir build && cd build
   ```
2. Run CMake to configure the build:
   ```bash
   cmake ..
   ```
3. Build the project using `make`:
   ```bash
   make
   ```

### Run Tests
After building, you can run the tests to verify the build:
```bash
bin/test
```

## CMake Integration

To integrate CLErrorLookup into your CMake-based project, follow these steps:

1. Add the library to your project's `CMakeLists.txt`:
   ```cmake
   add_subdirectory(CLErrorLookup)
   target_link_libraries(your_project_target clerrorlookup)
   ```
2. Link the `clerrorlookup` library to your target, as shown above.

## Usage Example

### Basic Example
```cpp
#include <clerrorlookup.hpp>

// OpenCL error code
int code = -42;

// Get a short description
std::string short_desc = clerror::get_error_str(code);  // "CL_INVALID_BINARY [-42]"

// Get a detailed description
std::string full_desc = clerror::get_error_full(code);  // See output example below

// Throw an exception with a detailed error message
if (code != 0) {
    clerror::throw_opencl_error(code);
}
```

### Example Output
For an error code `-42`:
- **Short description** (`get_error_str`):
  ```
  CL_INVALID_BINARY [-42]
  ```
- **Detailed description** (`get_error_full`):
  ```
  CL_INVALID_BINARY [-42]: If the program is created with clCreateProgramWithBinary and devices listed in device_list do not have a valid program binary loaded. The provided binary is unfit for the selected device. Compile-time Errors (driver-independent).
  ```

## License

This project is licensed under the GPL-3.0 License. See the `LICENSE` file for details.
