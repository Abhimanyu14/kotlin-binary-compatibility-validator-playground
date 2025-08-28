# Overview

This is a playground to test how a given change impact API and ABI compatibility.

# Structure

1. Library A - Compiled and used in Library B and app.
2. Library B - Used in app code.
3. App - Demo app.

# Public API Changes

The public API of a Kotlin library can change in the following ways.

## Class

| Changes                                                                                         | ABI Compatibility |
|:------------------------------------------------------------------------------------------------|:------------------|
| Adding a new top-level public class                                                             | ✅                 |
| Adding a new public companion object                                                            | ✅                 |
| Changing a class to an interface                                                                | ❓                 |
| Changing a class to an object                                                                   | ❓                 |
| Making a `public open class` `final`                                                            | ❓                 |
| Making a `public class` `abstract`                                                              | ❓                 |
| Making a member `final` in an `open class`                                                      | ❓                 |
| Removing a supertype if consumers relied on it                                                  | ❓                 |
| Adding an abstract member to a public non-abstract class or interface                           | ❓                 |
| Renaming public class                                                                           | ❓                 |
| Removing a public class                                                                         | ❓                 |
| Adding a supertype to an existing public class/interface (if no new abstract members/conflicts) | ❓                 |
| Narrowing visibility (e.g., `public` to `internal`)                                             | ❓                 |
| Widening visibility (e.g., `internal` to `public`)                                              | ✅                 |
| Removing a supertype from a public class/interface                                              | ❓                 |

## Enum class

| Changes                                              | ABI Compatibility |
|:-----------------------------------------------------|:------------------|
| Adding a new top-level public enum class             | ✅                 |
| Adding new enum constants                            | ❓                 |
| Changing a class/interface to an enum, or vice-versa | ❓                 |
| Renaming an enum constant                            | ❌                 |
| Removing enum constants                              | ❌                 |
| Removing a public enum class                         | ❌                 |

## Data class

| Changes                                  | ABI Compatibility |
|:-----------------------------------------|:------------------|
| Adding a new top-level public data class | ✅                 |
| Removing a public data class             | ❓                 |

## Object

| Changes                              | ABI Compatibility |
|:-------------------------------------|:------------------|
| Adding a new top-level public object | ✅                 |
| Renaming public object               | ❓                 |
| Changing an object to a class        | ❓                 |
| Removing a public object             | ❌                 |

## Interface

| Changes                                 | ABI Compatibility |
|:----------------------------------------|:------------------|
| Adding a new top-level public interface | ✅                 |
| Changing an interface  to a class       | ❓                 |
| Renaming public interface               | ❌                 |
| Removing a public interface             | ❌                 |

## Property

| Changes                                                 | ABI Compatibility |
|:--------------------------------------------------------|:------------------|
| Adding a new top-level public property (`val` or `var`) | ✅                 |
| Changing a `var` to a `val`                             | ❓                 |
| Changing a `val` to a `var`                             | ❓                 |
| Changing the return type of a public property           | ❓                 |
| Changing a property to a function                       | ❓                 |
| Renaming public property                                | ❌                 |
| Removing a public property                              | ❌                 |
| Changing the value of a public `const val`              | ❓                 |

## Function

| Changes                                                                                | ABI Compatibility |
|:---------------------------------------------------------------------------------------|:------------------|
| Adding a new top-level public function                                                 | ✅                 |
| Changing the return type of a public function                                          | ❓                 |
| Adding a new non-optional parameter without a default value                            | ❓                 |
| Adding a new optional parameter without a default value                                | ❓                 |
| Adding a new non-optional parameter with a default value                               | ❓                 |
| Adding a new optional parameter with a default value                                   | ❓                 |
| Adding new optional parameters to public functions/constructors (with a default value) | ❓                 |
| Removing a default value from an optional parameter                                    | ❓                 |
| Changing the default value of an optional parameter                                    | ❓                 |
| Changing a function to a property                                                      | ❓                 |
| Renaming public function                                                               | ❓                 |
| Removing a parameter from a public function                                            | ❓                 |
| Removing a public function                                                             | ❓                 |
| Changing the data type of a parameter in a public function                             | ❓                 |
| Changing the order of parameters in a public function                                  | ❓                 |
| Changing a parameter from optional with default to non-optional                        | ❓                 |
| Adding, removing, or changing type parameters (generics)                               | ❓                 |
| Changing bounds of type parameters                                                     | ❓                 |
| Adding or removing `suspend` modifier                                                  | ❓                 |
| Adding or removing `inline` modifier                                                   | ❓                 |
| Adding or removing `infix` or `operator` modifiers                                     | ❓                 |
| Changing a non-abstract member to `abstract`                                           | ❓                 |

## Annotation

| Changes                                                                         | ABI Compatibility |
|:--------------------------------------------------------------------------------|:------------------|
| Adding a new top-level public annotation                                        | ✅                 |
| Removing a public annotation                                                    | ❓                 |
| Changing annotations that affect JVM signature (e.g., `@JvmName`, `@JvmStatic`) | ❓                 |
| Changing other annotations (e.g., `@Throws`, nullability - impact varies)       | ❓                 |

## Typealias

| Changes                                                                           | ABI Compatibility |
|:----------------------------------------------------------------------------------|:------------------|
| Adding a new top-level public typealias                                           | ✅                 |
| Changing the underlying type of a public typealias (if not assignment-compatible) | ❓                 |
| Removing a public typealias                                                       | ❓                 |
