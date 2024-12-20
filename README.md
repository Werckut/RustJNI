# RustJNI
[![shield](https://shieldsio.boemskats.com/crates/dv/jni_macro/1.0.1?color=ffc933&label=create.io&logo=data%3Aimage%2Fsvg%3Bbase64%2CPHN2ZyByb2xlPSJpbWciIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48dGl0bGU%2BSGFjayBUaGUgQm94PC90aXRsZT48cGF0aCBkPSJtMjIuNTEwNiA2LjQ1NjYuMDAwOC0uMDEyM2EuODg4Ljg4OCAwIDAgMC0uMjcxNy0uNjM4NGMtLjAwODQtLjAwODQtLjAxOC0uMDE1NS0uMDI2Ny0uMDIzNS0uMDE4Ni0uMDE2Ni0uMDM3MS0uMDMzMy0uMDU3Mi0uMDQ4NC0uMDE5My0uMDE0Ny0uMDQtLjAyNzYtLjA2MDctLjA0MDYtLjAwOTYtLjAwNi0uMDE4Mi0uMDEzMS0uMDI4MS0uMDE4OEwxMi40NTc2LjEyNjZhLjg5MS44OTEgMCAwIDAtLjkyMjMuMDA0M0wxLjkzMyA1LjY3NDRjLS4wMTA3LjAwNjItLjAyMDMuMDE0LS4wMzA3LjAyMDUtLjAwNzMuMDA0Ny0uMDE1LjAwOC0uMDIyMy4wMTI4LS4wMDcuMDA0Ny0uMDEzLjAxMDYtLjAyLjAxNTVhLjg3NjkuODc2OSAwIDAgMC0uMTQ3LjEzMzNsLS4wMDI2LjAwM2EuODg3Mi44ODcyIDAgMCAwLS4yMjE4LjU4NDdsLjAwMDkuMDE0Yy0uMDAwMi4wMDg4LS4wMDE1LjAxNzYtLjAwMTUuMDI2NHYxMS4wNzA4YzAgLjMyNzcuMTgwMi42Mjg4LjQ2OS43ODM2bDkuNTk4NiA1LjU0MTdjLjAwNzYuMDA0NC4wMTU4LjAwNzUuMDIzNi4wMTE3YS44NzU0Ljg3NTQgMCAwIDAgLjE2Ni4wNjg3Yy4wMTM0LjAwNC4wMjY2LjAwODMuMDQwMS4wMTE3YS44NzkzLjg3OTMgMCAwIDAgLjA3Mi4wMTQyYy4wMTE3LjAwMTkuMDIzMi4wMDQ1LjAzNDkuMDA2YS44MzUuODM1IDAgMCAwIC4yMTU3IDBjLjAxMTctLjAwMTUuMDIzMi0uMDA0MS4wMzQ4LS4wMDZhLjkuOSAwIDAgMCAuMDcyLS4wMTQyYy4wMTM1LS4wMDM0LjAyNjctLjAwNzcuMDQtLjAxMTdhLjg5NS44OTUgMCAwIDAgLjA2NDYtLjAyMTcuOTEzNC45MTM0IDAgMCAwIC4xMDE1LS4wNDdjLjAwNzgtLjAwNDIuMDE2LS4wMDcyLjAyMzYtLjAxMTdsOS41OTg2LTUuNTQxN2EuODg4OC44ODg4IDAgMCAwIC40NjktLjc4MzZWNi40Nzc5YzAtLjAwNzEtLjAwMTItLjAxNDItLjAwMTQtLjAyMTN6TTUuMjU0MyA2LjA4MjJsNi41MzY3LTMuNzc0YS40MTgyLjQxODIgMCAwIDEgLjQxODIgMGw2LjUzNjYgMy43NzRhLjQxODIuNDE4MiAwIDAgMSAwIC43MjQzbC02LjUzNjcgMy43NzRhLjQxODIuNDE4MiAwIDAgMS0uNDE4MiAwbC02LjUzNjYtMy43NzRhLjQxODIuNDE4MiAwIDAgMSAwLS43MjQzem01LjYxMzQgMTQuMzQ0OWEuNDE3Mi40MTcyIDAgMCAxLS42MjYuMzYxM0wzLjcxOCAxNy4wMjE4YS40MTczLjQxNzMgMCAwIDEtLjIwODYtLjM2MTNWOS4xMjc5YS40MTcyLjQxNzIgMCAwIDEgLjYyNTgtLjM2MTNsNi41MjQgMy43NjY2YS40MTcyLjQxNzIgMCAwIDEgLjIwODYuMzYxNHY3LjUzMjV6bTkuNjIzLTMuNzY2NmEuNDE3My40MTczIDAgMCAxLS4yMDg2LjM2MTNsLTYuNTIzOSAzLjc2NjZhLjQxNzIuNDE3MiAwIDAgMS0uNjI1OS0uMzYxM3YtNy41MzI1YzAtLjE0OS4wNzk2LS4yODY4LjIwODctLjM2MTRsNi41MjM5LTMuNzY2NmEuNDE3Mi40MTcyIDAgMCAxIC42MjU4LjM2MTN2Ny41MzI2eiIvPjwvc3ZnPg%3D%3D)](https://crates.io/crates/jni_macro)

[Русская версия README](https://github.com/Werckut/RustJNI/wiki/RU)

## jni_macro

`jni_macro` is a macro library for simplifying JNI (Java Native Interface) work in Rust. It allows you to easily create functions that can be called from Java by automatically generating the necessary code for interaction between Rust and Java. This simplifies the creation of native methods and helps you avoid writing boilerplate code manually.

## Description

This library provides macros for simplifying the creation of JNI-compatible methods in Rust. With these macros, you can automatically generate the required code to work with JNI, making it significantly easier to maintain and develop code that interacts with Java. The macros convert Rust methods into a format that Java can understand, automatically creating the necessary wrappers and taking into account JNI syntax.

**Important:** When using the macros, the `env` and `class` variables are still present in the method body, and the compilation will succeed. However, currently, IDEs (such as IntelliJ IDEA or Rust Rover) may not correctly recognize these variables and may highlight them as errors. It is important to note that this will not affect compilation or the execution of the program, as the Rust compiler knows that these variables exist. In the future, IDE support for macros may improve.

## Installation

To add `jni_macro` to your project, add the following line to your project's `Cargo.toml` file:

```toml
[dependencies]
jni_macro = "1.0.1"
```

## Example Usage
Here is an example using the `#[jni_method]` macro to create native methods:

```rust
#[jni_method("org.company.RustCalculator")]
pub fn add(a: jdouble, b: jdouble) -> jdouble {
    a + b
}

#[jni_method("org.company.RustCalculator")]
pub fn div(a: jdouble, b: jdouble) -> jdouble {
    a / b
}

#[jni_method("org.company.RustCalculator")]
pub fn sqrt_fn(a: jdouble) -> jdouble {
    a.sqrt()
}
```

Without using the macro, you would have to write these methods manually as follows:

```rust
#[no_mangle]
pub extern "C" fn Java_org_company_RustCalculator_add(
    env: JNIEnv,
    class: JClass,
    a: jdouble,
    b: jdouble,
) -> jdouble {
    a + b
}

#[no_mangle]
pub extern "C" fn Java_org_company_RustCalculator_div(
    env: JNIEnv,
    class: JClass,
    a: jdouble,
    b: jdouble,
) -> jdouble {
    a / b
}

#[no_mangle]
pub extern "C" fn Java_org_company_RustCalculator_sqrtFn(
    env: JNIEnv,
    class: JClass,
    a: jdouble,
) -> jdouble {
    a.sqrt()
}
```

On the Java side, you would use the methods like this:

```java
static {
    System.loadLibrary("native_rust");  // Load our library
}

public native double add(double a, double b);
public native double div(double a, double b);
public native double sqrtFn(double a);  // The macro converts the name from snake_case to camelCase
```
