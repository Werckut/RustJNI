# RustJNI

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
