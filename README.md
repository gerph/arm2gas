# arm2gas
Migrate legacy ARM syntax assembly to GNU syntax (GAS)

## Usage

`arm2gas.pl [options] file1 [file2...]`

### Options

| Switch                  | Descriptions                                            |
| :---------------------- | :------------------------------------------------------ |
| `-c, --compatible`      | Keeps compatibility with armclang assembler             |
| `-h, --help`            | Show this help text                                     |
| `-i, --verbose`         | Show a message on every suspicious convertions          |
| `-n, --no-comment`      | Discard all the comments in output                      |
| `-o, --output=<file>`   | Specify the output filename                             |
| `-r, --return-code`     | Print return code definitions                           |
| `-s, --strict`          | Error on directives that have no equivalent counterpart |
| `-v, --version`         | Show version info                                       |
| `-w, --no-warning`      | Suppress all warning messages                           |
| `-x, --suffix=<string>` | Suffix of the output filename [default: '.out']         |

## Supported conversions

- [X] [Comments](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Comments?lang=en)
- [X] [Labels\*](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Labels?lang=en)
- [X] [Numeric local labels](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Numeric-local-labels?lang=en)
- [X] [Functions](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Functions?lang=en)
- [X] [Sections](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Sections?lang=en)
- [X] [Symbols with special characters](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Symbol-naming-rules?lang=en)
- [X] [Numeric literals](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Numeric-literals?lang=en)
- [X] [Operators](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Operators?lang=en)
- [X] [Aligment](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Alignment?lang=en)
- [X] [PC-relative addressing](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/PC-relative-addressing?lang=en)
- [X] [Directives: Conditional](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Conditional-directives?lang=en)
- [X] [Directives: Data definition](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Data-definition-directives?lang=en)
- [X] [Directives: Instruction set](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Instruction-set-directives?lang=en)
- [ ] [Directives: Symbol definition](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Symbol-definition-directives?lang=en)
- [X] [Directives: Miscellaneous](https://developer.arm.com/documentation/dui0742/g/Migrating-ARM-syntax-assembly-code-to-GNU-syntax/Miscellaneous-directives?lang=en)

## Cautions
By default (without `--strict`), for those directives that have no equivalentin GNU format, `arm2gas` will try best to convert and generate warning information on the specific line. Therefore, a 'warning' does **NOT** necessarily mean no issue, please check the conversion result to ensure it works as expected.

Note that `arm2gas` will *assume that the input file is in the **correct** syntax*, otherwise, the conversion result is **UNEXPECTED**