# Meson build for SafeInt library

URL: 

- [SafeInt Library](https://github.com/dcleblanc/SafeInt);

The subfolder "src" is a clone of git repository of a specified release version. 
unit-tests are not built as part of the meson-build.

## Versions

The "revision" of safeint.wrap and the version of this meson-build project matches the embedded submodule GSL version. 


## Usage

copy safeint.wrap to "subprojects" sub-folder of your main project directory.


in meson.build:

```
# import

safeint_dep = dependency('safeint')

# use
srcs = ['main.cpp', ...]

executable('test', srcs, dependencies: [safeint_dep, ...])

```

in main.cpp:

```cpp
#include <SafeInt/SafeInt.hpp>

void foo(int x){}

void bar(int i)
{
  foo(SafeInt<int>(i) * 1000); //ensures i*1000 does not overflow before passing to foo()
}
```



