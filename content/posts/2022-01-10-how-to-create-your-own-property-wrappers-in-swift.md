---
title: How to create your own property wrappers in Swift
description: A quick guide on how to create our own property wrapper in Swift
date: '2022-01-10T03:23:29.772Z'
preview: null
draft: null
lead: A quick guide on how to create our own property wrapper in Swift
tags:
    - swift
categories: null
---

Property wrappers is a type that wraps a given value in order to attach additional logic to it. It allows us to avoid writing a lot of repetitive code for our getter or setter logic. `@State`, `@AppStorage` and `@Binding` are some examples of property wrappers that are being used in SwiftUI.

In this post, we are going to learn how to create our own property wrapper.

# How to create Property Wrappers

To create a property wrapper we need to satisfy these requirements:

1. It need to be annotated with `@propertyWrapper` annotation
2. It must contain a non-static property named `wrappedValue`

## Example

For example, we can use property wrapper named `@TrimmedWhitespace` to trim any whitespaces in a `String`.


```swift
@propertyWrapper struct TrimmedWhitespace {
    var wrappedValue: String {
        didSet {
            wrappedValue = wrappedValue.replacingOccurrences(of: " ", with: "")
        }
    }
    
    init(wrappedValue: String) {
        self.wrappedValue = wrappedValue.replacingOccurrences(of: " ", with: "")
    }
}
```

To use our newly define `@TrimmedWhitespace` property wrapper, we can annotate it on any of the `String` properties like the following

```swift
struct Foo {
    @TrimmedWhitespace var bar: String
}

let foo = Foo(bar: "Hello world")
print(foo.bar) // Helloworld
```

That is all for today!