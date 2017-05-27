# The Official raywenderlich.com Kotlin Style Guide (in progress)

This style guide is different from others you may see, because the focus is centered on readability for print and the web. We created this style guide to keep the code in our tutorials consistent.

Our overarching goals are __conciseness__, __readability__ and __simplicity__.

You should also check out our other style guides:

* [Swift](https://github.com/raywenderlich/swift-style-guide)
* [Objective-C](https://github.com/raywenderlich/objective-c-style-guide)
* [Java](https://github.com/raywenderlich/java-style-guide)

## Inspiration

This style-guide is somewhat of a mash-up between the existing Kotlin language style guides, and a tutorial-readability focused Swift style-guide. The language guidance is drawn from: 

- The [Kotlin Coding Conventions](https://kotlinlang.org/docs/reference/coding-conventions.html) 
- The [Android contributors style guide](https://source.android.com/source/code-style.html)
- The [Google Java Style Guide](https://google-styleguide.googlecode.com/svn/trunk/javaguide.html).

Alterations to support additional readability in tutorials were inspired by the [raywenderlich.com Swift style guide](https://github.com/raywenderlich/swift-style-guide).

## Android Studio Coding Style

It is possible to get Android Studio to adhere to these style guidelines, via a rather complex sequence of menus. To make it easier, we've provided a coding style that can be imported into Android Studio.

First, clone this repository and run `install.sh` (**UPDATED FILE COMING SOON**).

Then, open Android Studio. To set this codestyle as the default, select
__File > Other Settings > Default Settings...__:

**UPDATED IMAGE COMING SOON**

![Default Settings](resources/default_settings.png)

In __Editor > Code Style__, choose the __Scheme__ to be __raywenderlich.com__:

**UPDATED IMAGE COMING SOON**

![Setting the Scheme](resources/setting_scheme.png)

From now on, projects you create _should_ follow the correct style guidelines.


## Table of Contents

- [Nomenclature](#nomenclature)
  + [Packages](#packages)
  + [Classes & Interfaces](#classes--interfaces)
  + [Methods](#methods)
  + [Fields](#fields)
  + [Variables & Parameters](#variables--parameters)
  + [Misc](#misc)
- [Declarations](#declarations)
  + [Visibility Modifiers](#visibility-modifiers)
  + [Fields & Variables](#fields--variables)
  + [Classes](#classes)
  + [Enum Classes](#enum-classes)
- [Spacing](#spacing)
  + [Indentation](#indentation)
  + [Line Length](#line-length)
  + [Vertical Spacing](#vertical-spacing)
- [Semicolons](#semicolons)
- [Getters & Setters](#getters--setters)
- [Brace Style](#brace-style)
- [Switch Statements](#switch-statements)
- [Annotations](#annotations)
- [Types](#types)
  + [Type Inference](#type-inference)
  + [Constants vs. Variables](#constants-vs-variables)
  + [Companion Objects](#companion-objects)
  + [Optionals](#optionals)
- [XML Guidance](#xml-guidance)
- [Language](#language)
- [Copyright Statement](#copyright-statement)
- [Smiley Face](#smiley-face)
- [Credit](#credits)


## Nomenclature

On the whole, naming should follow Java standards, as Kotlin is a JVM-compatible language.

### Packages

Package names are similar to Java: all __lower-case__, multiple words concatenated together, without hypens or underscores:

__BAD__:

```kotlin
com.RayWenderlich.funky_widget
```

__GOOD__:

```kotlin
com.raywenderlich.funkywidget
```

### Classes & Interfaces

Written in __UpperCamelCase__. For example `RadialSlider`. 

### Methods

Written in __lowerCamelCase__. For example `setValue`.

### Fields

Written in __lowerCamelCase__.

Static fields should be written in __uppercase__, with an underscore separating words:

```kotlin
public static val THE_ANSWER = 42
```

As distasteful as it is, field naming should follow the Android source code naming conventions:

- Non-public, non-static field names start with an `m`.
- Static field names start with an `s`.

For example:

```kotlin
open class MyClass {
  public static val SOME_CONSTANT = 42
  public publicField: Int
  private static let sSingleton = MyClass()
  mPackagePrivate: Int?
  private mPrivate: Int?
  protected mProtected: Int? 
}
```

**TODO: UPDATE**
> __Note:__ You can set Android Studio to follow this convention. See this SO link for details http://stackoverflow.com/questions/22732722/intellij-android-studio-member-variable-prefix

### Variables & Parameters

Written in __lowerCamelCase__.

Single character values must be avoided, except for temporary looping variables.

### Misc

In code, acronyms should be treated as words. For example:

__BAD:__

```kotlin
XMLHTTPRequest
URL: String? 
findPostByID
```
__GOOD:__

```kotlin
XmlHttpRequest
url: String
findPostById
```

## Declarations

### Visibility Modifiers

Only include visibility modifiers if you need something other than the default of public.

**BAD:**

```kotlin
public val wideOpenProperty = 1
private val myOwnPrivateProperty = "private"
```

**GOOD:***

```kotlin
val wideOpenProperty = 1
private val myOwnPrivateProperty = "private"
```

### Access Level Modifiers

Access level modifiers should be explicitly defined for classes, methods and member variables.

### Fields & Variables

Prefer single declaration per line.

__GOOD:__

```kotlin
username: String
twitterHandle: String
```

### Classes

Exactly one class per source file, although inner classes are encouraged where scoping appropriate.


### Enum Classes

**TODO: UPDATE FOR KOTLIN** *(This is java-only and may not be true with Kotlin)*

Enum classes should be avoided where possible, due to a large memory overhead. Static constants are preferred. See http://developer.android.com/training/articles/memory.html#Overhead for further details.

Enum classes without methods may be formatted without line-breaks, as follows:

```kotlin
private enum CompassDirection { EAST, NORTH, WEST, SOUTH }
```

## Spacing

Spacing is especially important in raywenderlich.com code, as code needs to be easily readable as part of the tutorial. 

### Indentation

Indentation is using spaces - never tabs.

#### Blocks

Indentation for blocks uses 2 spaces (not the default 4):

__BAD:__

```kotlin
for (i in 0..9) {
    Log.i(TAG, "index=" + i);
}
```

__GOOD:__

```kotlin
for (i in 0..9) {
  Log.i(TAG, "index=" + i)
}
```

#### Line Wraps

Indentation for line wraps should use 4 spaces (not the default 8):

__BAD:__

```kotlin
val widget: CoolUiWidget =
        someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line)
```

__GOOD:__

```kotlin
val widget: CoolUiWidget =
    someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line)
```

### Line Length

Lines should be no longer than 100 characters long.


### Vertical Spacing

There should be exactly one blank line between methods to aid in visual clarity and organization. Whitespace within methods should separate functionality, but having too many sections in a method often means you should refactor into several methods.

## Semicolons

Semicolons ~~are dead to us~~ should be avoided wherever possible in Kotlin. 

__BAD__:

```kotlin
val horseGiftedByTrojans = true;
if (horseGiftedByTrojans) {
  bringHorseIntoWalledCity();
}
```

__GOOD__:

```kotlin
val horseGiftedByTrojans = true
if (horseGiftedByTrojans) {
  bringHorseIntoWalledCity()
}
```

## Getters & Setters

Unlike Java, direct access to fields in Kotlin is preferred. 

If getters and setters are required, they should be declared [following Kotlin conventions](https://kotlinlang.org/docs/reference/properties.html) rather than as separate methods.

## Brace Style

Only trailing closing-braces are awarded their own line. All others appear the same line as preceding code:

__BAD:__

```kotlin
class MyClass
{
  fun doSomething()
  {
    if (someTest)
    {
      // ...
    }
    else
    {
      // ...
    }
  }
}
```

__GOOD:__

```kotlin
class MyClass {
  fun doSomething() {
    if (someTest) {
      // ...
    } else {
      // ...
    }
  }
}
```

Conditional statements are always required to be enclosed with braces, irrespective of the number of lines required.

__BAD:__

```kotlin
if (someTest)
  doSomething()
if (someTest) doSomethingElse()
```

__GOOD:__

```kotlin
if (someTest) {
  doSomething()
}
if (someTest) { doSomethingElse() }
```


## Switch Statements

**TODO: UPDATE**

Switch statements fall-through by default, but this can be unintuitive. If you require this behavior, comment it.

Alway include the `default` case.

__BAD:__

```kotlin
switch (anInput) {
  case 1:
    doSomethingForCaseOne()
  case 2:
    doSomethingForCaseOneOrTwo()
    break;
  case 3:
    doSomethingForCaseOneOrThree()
    break;
}
```

__GOOD:__

```kotlin
switch (anInput) {
  case 1:
    doSomethingForCaseOne()
    // fall through
  case 2:
    doSomethingForCaseOneOrTwo()
    break;
  case 3:
    doSomethingForCaseOneOrThree()
    break;
  default:
    break;
}
```

## Annotations

Standard annotations should be used - in particular `override`. This should appear on the same line as the function declaration.

__BAD:__

```kotlin
fun onCreate(savedInstanceState: Bundle?) {
  super.onCreate(savedInstanceState);
}
```

__GOOD:__

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
  super.onCreate(savedInstanceState);
}
```

## Types 

Always use Kotlin's native types when available. Kotlin is JVM-compatible so **[TODO: more info]**

### Type Inference

Type inference should be preferred where possible to explicitly declared types. 

__BAD:__

```kotlin
val something: MyType = MyType()
val meaningOfLife: Int = 42
```

__GOOD:__

```kotlin
val something = MyType()
val meaningOfLife = 42
```

### Constants vs. Variables 

Constants are defined using the `val` keyword, and variables with the `var` keyword. Always use `val` instead of `var` if the value of the variable will not change.

*Tip*: A good technique is to define everything using `val` and only change it to `var` if the compiler complains!

### Companion Objects

** TODO: A bunch of stuff about companion objects **

### Optionals

Declare variables and function return types as optional with `?` where a `null` value is acceptable.

Use implicitly unwrapped types declared with `!!` only for instance variables that you know will be initialized before use, such as subviews that will be set up in `onCreate` for an Activity or `onCreateView` for a Fragment.

When naming optional variables and parameters, avoid naming them like `optionalString` or `maybeView` since their optional-ness is already in the type declaration.

When accessing an optional value, use optional chaining if the value is only accessed once or if there are many optionals in the chain:

```kotlin
editText?.setText("foo")
```

**TODO: Update the rest of this section from Swift**

Use optional binding when it's more convenient to unwrap once and perform multiple operations:

```swift
if let textContainer = self.textContainer {
  // do many things with textContainer
}
```

For optional binding, shadow the original name when appropriate rather than using names like unwrappedView or actualLabel.

```swift
Preferred:

var subview: UIView?
var volume: Double?

// later on...
if let subview = subview, let volume = volume {
  // do something with unwrapped subview and volume
}
```

Not Preferred:

```swift
var optionalSubview: UIView?
var volume: Double?

if let unwrappedSubview = optionalSubview {
  if let realVolume = volume {
    // do something with unwrappedSubview and realVolume
  }
}
``` 

## XML Guidance

Since Android uses XML extensively in addition to Kotlin and Java, we have some rules specific to XML. These can be found in our [Java code standards](https://github.com/raywenderlich/java-style-guide#xml-guidance


## Language

Use `en-US` English spelling. 🇺🇸

__BAD:__

```kotlin
val colourName = "red"
```

__GOOD:__

```kotlin
colorName = "red"
```

## Copyright Statement

The following copyright statement should be included at the top of every source file:

    /*
     * Copyright (c) 2017 Razeware LLC
     * 
     * Permission is hereby granted, free of charge, to any person obtaining a copy
     * of this software and associated documentation files (the "Software"), to deal
     * in the Software without restriction, including without limitation the rights
     * to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
     * copies of the Software, and to permit persons to whom the Software is
     * furnished to do so, subject to the following conditions:
     * 
     * The above copyright notice and this permission notice shall be included in
     * all copies or substantial portions of the Software.
     * 
     * Notwithstanding the foregoing, you may not use, copy, modify, merge, publish, 
     * distribute, sublicense, create a derivative work, and/or sell copies of the 
     * Software in any work that is designed, intended, or marketed for pedagogical or 
     * instructional purposes related to programming, coding, application development, 
     * or information technology.  Permission for such use, copying, modification,
     * merger, publication, distribution, sublicensing, creation of derivative works, 
     * or sale is expressly withheld.
     *
     * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
     * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
     * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
     * AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
     * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
     * OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
     * THE SOFTWARE.
     */

## Smiley Face

Smiley faces are a very prominent style feature of the raywenderlich.com site! It is very important to have the correct smile signifying the immense amount of happiness and excitement for the coding topic. The closing square bracket ] is used because it represents the largest smile able to be captured using ASCII art. A closing parenthesis ) creates a half-hearted smile, and thus is not preferred.

Bad:

    :)

Good:

    :]

## Credits

This style guide is a collaborative effort from the most stylish
raywenderlich.com team members:

- [Darryl Bayliss](https://github.com/DarrylBayliss)
- [Tom Blankenship](https://github.com/tgblank)
- [Sam Davies](https://github.com/sammyd)
- [Mic Pringle](https://github.com/micpringle)
- [Ellen Shapiro](https://github.com/designatednerd)
- [Ray Wenderlich](https://github.com/rwenderlich)
