# RustJNI

## jni_macro

`jni_macro` — это библиотека макросов для упрощения работы с JNI (Java Native Interface) в Rust. Она позволяет вам легко создавать функции для вызова из Java, автоматически генерируя нужный код для взаимодействия между Rust и Java. Это упрощает создание нативных методов и помогает избежать написания шаблонного кода вручную.

## Описание

Библиотека предоставляет макросы для упрощения создания JNI-совместимых методов в Rust. С помощью макросов вы можете автоматически генерировать необходимый код для работы с JNI, что значительно упрощает поддержку и разработку кода, взаимодействующего с Java. Макросы преобразуют методы Rust в формат, понятный Java, автоматически создавая нужные обертки и учитывая особенности синтаксиса JNI.

**Важно:** Используя макросы, переменные `env` и `class` все еще присутствуют в теле метода, и компиляция пройдет успешно. Однако на данный момент IDE (например, IntelliJ IDEA или Rust Rover) не могут корректно определить эти переменные и могут подсвечивать их как ошибочные. Важно помнить, что это не повлияет на компиляцию и выполнение программы, так как компилятор Rust знает, что эти переменные существуют. В будущем возможно улучшение поддержки макросов в IDE.

## Установка

Чтобы добавить `jni_macro` в свой проект, добавьте следующую строку в файл `Cargo.toml` вашего проекта:

```toml
[dependencies]
jni_macro = "1.0.1"
```

## Пример использования

Пример с использованием макроса `#[jni_method]` для создания нативных методов:

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

Без использования макроса вам пришлось бы писать такие методы вручную:

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

```java
static {
    System.loadLibrary("native_rust");  // Подключаем нашу библиотеку
}

public native double add(double a, double b);
public native double div(double a, double b);
public native double sqrtFn(double a);  // Макрос преобразует имя из snake_case в camelCase
```
