# buck-cpp-debug

This repo contains a `cxx_binary` that segfaults.

```
buck run :app
```

To run in LLDB:

```
buck build :app#debug

lldb ./buck-out/gen/app
r
Process 74070 launched: './buck-out/gen/app' (x86_64)
Process 74070 stopped
* thread #1, queue = 'com.apple.main-thread', stop reason = EXC_BAD_ACCESS (code=1, address=0x0)
    frame #0: 0x0000000100000fa9 app`main at main.cpp:3
   1   	int main() {
   2   	  int* a = nullptr;
-> 3   	  int x = *a;
   4   	  return 0;
   5   	}
```

Environment:

```
uname
Darwin

buck --version
buck version 0391b98d8eae9587abefb0c2e86e2a227480a1aa

clang --version
clang version 4.0.1 (tags/RELEASE_401/final)
Target: x86_64-apple-darwin16.7.0
Thread model: posix
InstalledDir: /usr/local/opt/llvm/bin
```
