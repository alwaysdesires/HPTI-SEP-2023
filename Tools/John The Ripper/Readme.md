# John the Ripper

## Description
John the Ripper is a powerful, open-source password cracking tool. It is designed to help security professionals and enthusiasts assess the strength of passwords and improve their security. 
This README provides essential information on how to use and contribute to the Community Enhanced Version of John the Ripper.

## Installation
You can refer the [Document](https://github.com/gurusakharwade/HPTI-SEP-2023/tree/main/Tools/John%20The%20Ripper/Document) folder.

### Prerequisites
- A Unix-like operating system (Linux, macOS, etc.)
- GCC or another C compiler
- Make (specifies how to build the software. It ensures that you can easily compile and build the project from source code according to the provided instructions.)
- OpenSSL development package (libssl-dev)

### Building John the Ripper
1. Clone the repository:
   ```bash
   git clone https://github.com/magnumripper/JohnTheRipper.git
   cd JohnTheRipper/src
   ```

2. Configure and build the tool:
   ```bash
   ./configure && make -s clean && make -sj4
   ```

3. Run John the Ripper:
   ```bash
   ./john --help
   ```

## Usage
- To crack passwords, use the `john` command followed by the target file containing hashed passwords.
   ```bash
   ./john hashes.txt
   ```

- For more advanced usage and options, consult the [documentation](https://openwall.info/wiki/john/johnny).

## Contributing
H4U Intern: HPTI-SEP23-053

We welcome contributions from the community. To contribute to John the Ripper, please follow these steps:
1. Fork the repository on GitHub.
2. Create a feature or bugfix branch.
3. Make your changes and test thoroughly.
4. Submit a pull request to the main repository.

Please ensure your code adheres to the project's coding style and conventions.

## Security
Please use John the Ripper responsibly and only for ethical purposes. Unauthorized password cracking can be illegal and unethical. Always obtain proper authorization and follow applicable laws and regulations.
