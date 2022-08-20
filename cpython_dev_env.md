## CPython: Setup dev env on macOS

- Clone cpython repo
- Setup VScode
- Needed VSCode extensions: 
    - Task explorer
    - C/C++
    - reStructuredText
    - Python

- Add task explorer file (`cpython/.vscode/tasks.json`):
```
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "build",
            "type": "shell",
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "osx":{
                "command": "make -j4 -s"
            }
        },
        {
            "label": "clean",
            "type": "shell",
            "group": {
                "kind": "clean",
                "isDefault": true
            },
            "osx":{
                "command": "make -s clean"
            }
        }
    ]
}
```
- Install Brew
- Install dependencies `brew install openssl xz zlib gdbm sqlite` 

- Run ./configure:

```
CPPFLAGS="-I$(brew --prefix zlib)/include" \ 
LDFLAGS="-L$(brew --prefix zlib)/lib" \
./configure --with-openssl=$(brew --prefix openssl) \
--with-pydebug
```

*Note: `brew --prefix openssl` checks where package is installed by Brew
- In task explorer run build task in VS Code
- To run build Python run `build/python.exe`

