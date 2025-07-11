
# 🔄 Code Modernization Diff: CalcEngineTests.cpp

This document highlights key **before-and-after differences** in the code to show how modern C++ features were applied.

---

## ✅ 1. `auto` Type Deduction

**Before:**
```cpp
for (wstring const& str : validBinStrs)
```

**After:**
```cpp
for (const auto& str : validBinStrs)
```

---

## ✅ 2. Range-Based For Loops

**Before:**
```cpp
for (size_t i = 0; i < validBinStrs.size(); ++i)
{
    VERIFY_ARE_EQUAL(0, m_calcEngine->IsNumberInvalid(validBinStrs[i], ...));
}
```

**After:**
```cpp
for (const auto& str : validBinStrs)
{
    VERIFY_ARE_EQUAL(0, m_calcEngine->IsNumberInvalid(str, ...));
}
```

---

## ✅ 3. Smart Pointers Modernization

**Before:**
```cpp
m_calcEngine = std::unique_ptr<CCalcEngine>(new CCalcEngine(...));
```

**After:**
```cpp
m_calcEngine = std::make_unique<CCalcEngine>(...);
```

---

## ✅ 4. `constexpr` Constants

**Before:**
```cpp
#define MAX_HISTORY_SIZE 20
```

**After:**
```cpp
constexpr size_t MAX_HISTORY_SIZE = 20;
```

---

## ✅ 5. `noexcept` Functions

**Before:**
```cpp
TEST_METHOD_INITIALIZE(CommonSetup)
```

**After:**
```cpp
TEST_METHOD_INITIALIZE(CommonSetup) noexcept
```

---

## ✅ 6. Resetting Smart Pointers

**Before:**
```cpp
m_calcEngine = nullptr;
```

**After:**
```cpp
m_calcEngine.reset();
```

---

## 🔥 Summary of Benefits

| Feature         | Benefit                               |
|-----------------|----------------------------------------|
| `auto`          | Reduces verbosity                     |
| Range-for loops | Cleaner and safer iteration           |
| Smart pointers  | Prevents memory leaks                 |
| `constexpr`     | Compile-time constant evaluation      |
| `noexcept`      | Enables compiler optimizations        |

