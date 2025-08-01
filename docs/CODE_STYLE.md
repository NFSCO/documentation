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

#ifndef BUILD_PRODUCTION
	/* ... */
#endif

// correct.
#if defined(BUILD_DEBUG)
	/* ... */
#endif

#if !defined(BUILD_PRODUCTION)
	/* ... */
#endif
```

* Indent preprocessor directives.
```cpp
// incorrect.
#if defined(BUILD_PRODUCTION)
#define EXAMPLE_DIRECTIVE /* ... */
#else
#define EXAMPLE_DIRECTIVE /* ... */
#endif

// correct.
#if defined(BUILD_PRODUCTION)
	#define EXAMPLE_DIRECTIVE /* ... */
#else
	#define EXAMPLE_DIRECTIVE /* ... */
#endif
```

* Use a trailing return type declaration for functions that return types longer than 4 characters.
```cpp
// incorrect.
std::size_t size();

// correct.
auto size() -> std::size_t;
```

* Use `::` when accessing classes, functions, or variables inside the global namespace.
```cpp
// incorrect.
const auto process = GetCurrentProcess();

// correct.
const auto process = ::GetCurrentProcess();
```

* Use `this` when accessing classes, functions, or variables inside a class.
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
