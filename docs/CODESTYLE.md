# Code Style
* Use `final` for classes that should not be derived from.
* Use `const` and `constexpr` where possible.
* Use `auto` for local variables where possible.
* Use range-based `for` loops where possible.

* Use `#if defined` and `#if !defined`.
```cpp
// incorrect.
#ifdef BUILD_DEBUG
	/* ... */
#endif

// correct.
#if defined(BUILD_DEBUG)
	/* ... */
#endif
```

* Indent preprocessor directives unless the scope encompasses the entire file.
```cpp
// incorrect.
#if defined(BUILD_PRODUCTION)
#define MODULE_IGNORE_PIPE /* ... */
#else
#define MODULE_IGNORE_PIPE /* ... */
#endif

// correct.
#if defined(BUILD_PRODUCTION)
	#define MODULE_IGNORE_PIPE /* ... */
#else
	#define MODULE_IGNORE_PIPE /* ... */
#endif

// if the scope encompasses the entire file...
#pragma once

#if defined(PLATFORM_WINDOWS)

#include /* ... */
#include /* ... */
#include /* ... */

namespace project
{
	/* ... */
}

#endif
```

* Use a trailing return type declaration for functions that return types longer than 4 characters.
```cpp
// incorrect.
std::uint32_t size();

// correct.
auto size() -> std::uint32_t;
```

* Use `::` when using classes, functions, or variables from the global namespace.
```cpp
// incorrect.
const auto handle = GetCurrentProcess();

// correct.
const auto handle = ::GetCurrentProcess();
```

* Use `this` when using classes, functions, or variables from a class.
```cpp
// incorrect.
++member_variable_;

// correct.
++this->member_variable_;
```

* Use `default` for empty `virtual` destructors.
```cpp
// incorrect.
virtual ~type()
{

}

// correct.
virtual ~type() = default;
```

* Use list-initialization where possible.
```cpp
// incorrect.
return std::vector<std::uint32_t>({ 1, 3, 3, 7 });

// correct.
return { 1, 3, 3, 7 };
```

* Use `push` and `ret` to jump back to the original code in assembly hooks.
```cpp
// incorrect.
constexpr auto address = 0x00112233;

__asm
{
	/* ... */

	jmp address;
}

// correct.
__asm
{
	/* ... */

	push 0x00112233;
	ret;
}
```
