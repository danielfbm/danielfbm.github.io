---
author:
  description: danielfbm
  email: danielfbm@gmail.com
  github: https://github.com/danielfbm
  image: /images/avatar-64x64.png
  name: danielfbm
  twitter: https://twitter.com/danielfbm
  website: http://danielfbm.github.io/
categories:
- golang
- programming languages
date: 2017-01-31T23:00:00+08:00
description: first post with Hugo website engine
tags:
- golang
- go
- programming languages
- introduction
- go setup
title: Golang introduction
draft: false

coverImage: http://res.cloudinary.com/dxucxgkq3/image/upload/c_scale,w_600/v1485922646/fiveyears_wlq0ez.jpg
coverCaption: "Gopher"
coverMeta: out
coverSize: partial
---

This is for those interested in the **go** programming language. This is my take as an introduction on this amazing language

Honestly there is plenty of resources on the web about [golang][golang] to fill a lot of content. This post is merely a summary of the things I find most useful and what attracts me the most while programming in [go][golang]


#### TL; DR

To install simply download the package for your OS in the [golang official download page][godownload]

If you are on macOS and have brew installed: `brew update && brew install golang` 

Check the examples on [this git repo](https://github.com/danielfbm/go-intro) to play:

```sh
# using the terminal of your choice navigate to the repo folder
go run <filename>.go
```

In general [golang][golang] is a very simple, modern and pleasant to use programming language. It is worth giving it a shot specially because of its impressive performance.

#### Download and Setup

If you don't have it installed head right to the official webpage and [download it][godownload].

After the setup, try the following command in your favorite terminal

```sh
go version
```

If everything was setup correctly you will be able to see the installed version and the platform in which you installed it.

As opposite to many languages, **go** uses *one main workspace* meaning that all your code, and the downloaded third party libraries will cohexist in the same folder structure. This sounds kind of weird in the beginning and most people would prefer to organize their projects in different paths. With time this will prove to become very useful. Besides, there are ways to overcome this limitation, as some would prefer in a enterprise environment.

To set a workspace just set the `GOPATH` environment variable. An example would be to set this environment in a `go` folder in the user's home folder:

```sh
export GOPATH=~/go
```

Inside the workspace you can create three folders:

- `bin` stores all the compiled *golang* projects
- `src` stores all the source code
- `pkg` stores your OS related tools

If you are using a UNIX like system, just add the `export GOPATH` command in your `.profile` or `.bash_profile` to be loaded as soon as the user is logged in the terminal.

You can find more information regarding the Go installation and workspace

- [Official documentation](https://golang.org/doc/install)
- [Post from William Kennedy](https://www.goinggo.net/2016/05/installing-go-and-your-workspace.html)



#### IDE

Although there are many idealists that follow the `vim` philosophy of coding, I prefer more complex and easier to use IDEs. Golang doesn't have any official IDE and probably never will, mostly because all the necessary tools either come with the **go** installer, or can be easily installed. 

Here I will explain the one I use and how to set it up for **go**.

##### Microsoft's Visual Studio Code

This lightweight IDE works perfectly for me and I have used it for several months. I really enjoy how you can integrate with the golang standard tooling. You can [download it here](https://code.visualstudio.com/Download).

By itself this IDE's features are not very impressive, but the main basics for any IDE. Its power comes from its Extensions. Besides browsing and searching for extensions from inside the IDE (`Shift + CMD + X ` on macOS), [VS Code's Extension Marketplace](https://marketplace.visualstudio.com/VSCode) website have as well the same feature.

To support **go** we will first install the [vscode-go](https://marketplace.visualstudio.com/items/lukehoban.Go) extension. Its source code is hosted on [this GitHub repo](https://github.com/Microsoft/vscode-go). After installation it will require installation of multiple **go** tools. Some of them will require a VPN if you are in a restricted access network:

- gocode: `go get -u -v github.com/nsf/gocode`
- godef: `go get -u -v github.com/rogpeppe/godef`
- gogetdoc: `go get -u -v github.com/zmb3/gogetdoc`
- golint: `go get -u -v github.com/golang/lint/golint`
- go-outline: `go get -u -v github.com/lukehoban/go-outline`
- goreturns: `go get -u -v sourcegraph.com/sqs/goreturns`
- gorename: `go get -u -v golang.org/x/tools/cmd/gorename`
- gopkgs: `go get -u -v github.com/tpng/gopkgs`
- go-symbols: `go get -u -v github.com/newhook/go-symbols`
- guru: `go get -u -v golang.org/x/tools/cmd/guru`
- gotests: `go get -u -v github.com/cweill/gotests/...`

With all the tools installed your VS Code will be ready. By default a few features will be enabled:

###### Autocomplete

 Once you download some library, or even using the standard library, the code will start to display auto-complete options as the code is typed.

###### Auto format

 Go has a very comprehensive, and sometimes hated, code writting rules. There is where `gofmt ` places an important rule. In this Extension the `gofmt` will be automatically executed everytime a file is saved. By default it will: 

- Remove unused imported libraries;
- Spacing code formatting (replacing spaces for tabs when necessary);
- Removing unecessary blank lines;

###### Auto-build and auto-lint

Together with formating the Extension also provides auto-building and linting on save, this makes very quick and simple to see all the possible errors directly inside the IDE and simplifies the coding experience.

There are more functionalities supported by this Extension. Visit its [code repo](https://github.com/Microsoft/vscode-go) for more info.

#### Syntax

For those familiar with the C family of programming languages will feel very comfortable writting **go** code. First, most of it is very similar, and those annoying details, like adding a semicolon to the end of every code line,  are different. Lets go directly to the point. Nothing better than a **Hello World** for a quick glance:

```go
package main // a package name is expected in every go file as the first line

import "fmt" // importing the fmt standard library

// for the main package a main function is necessary
// just like C, this is the entry point for our program
func main() {
  // Print one line to stdout
  fmt.Println("Hello, world")
}
```

#### Basics
There are a few keypoints that, in short, can define the **go** language: 

  - Compiled language
  - Strongly typed
  - Opiniated language
  - No Classes
  - No Generics
  - Concurrency from design

##### Variables
Below are listed the basic variable types:

```go
bool

string

// int is an alias to int32 in 32 bit systems, and int64 for 64 bit
int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr

// uint are unsigned integers


byte // alias for uint8

rune // alias for int32
     // represents a Unicode code point

float32 float64

complex64 complex128
```

To create `custom types` just declare a new type as:

```go
type MyType int

// Declare a list of valid values as constants
const (
  FirstValue MyType = 1
  SecondValue MyType = 2
  LastValue MyType = 99
)
```

There a multiple ways to declare variables in **go**:

```go
package main

import (
    "fmt"
)

func main() {
    // single variable. Variable type comes after the name
    var i int = 0
  
    // multiple variables, single line, j == 1, k == 2
    var j, k int = 1, 2

    // the same as the line above but with implicit type
    // note the colon
    z, x, c := 3, 4, 5

    // multi-line declaration
    var (
      one string
      two string
      three = "three"
    )
}
```

By default each simple type has a "zero-value", which are:

- `0` for `numeric types`
- `""` for `string`
- `false` for `bool`
- `nil` for any `pointer`

As all the code is written inside `packages`, the first letter of a variable name will define it to be `public` or `private`:

```go
package some_package

var PublicVariable string
var privateVariable string
```

This concept can be confusing at the beginning, but it is very useful to avoid extra typing. Global public variables can be accessed by other packages using the following syntax:

```go
package other_package

import "some_package"
import "fmt"

func SomeFunction() {
  fmt.Println(some_package.PublicVariable)
}
```

Another aspect very specific to **go** is that the compiler will not compile code that declares unused variables. Although this feature can seem discomfortable for some, in general it makes the code overall clear.

#### Functions

Public and private functions follow the same rules to variable naming for `public` and `private` access

```go
// this function can be accessed by other packages
func PublicFunction (param string, other int) {

}

func privateFunc() {

}
```

**Go** also supports returning multiple values, and each return value type should be declared as well

```go
func SingleReturn() bool {
  return false
}

func MultipleReturn() (bool, string) {
  return true, "hello"
}

// it is also possible to declare return type as variables without extra declaration
func MultipleReturnExplicit() (correct bool, name string) {
  correct = true
  name = "a name"
  return correct, name
}
```

#### Structs

Besides the basic types `struct` is another very useful type declaration that can be used to compose structure abstractions. 

```go
// declaring the struct
type MyStruct struct {
  PublicVariable string
  privateVariable string
}

func Usage() {
  // constructing a variable of type MyStruct
  myStruct := MyStruct{
    PublicVariable: "public",
    privateVariable: "private",
  }

  fmt.Println(myStruct.PublicVariable)
}
```

Structs can also have functions

```go
// my here is a variable that carries the values of the struct instance
func (my MyStruct) MyMethod() string {
  return my.PublicVariable
}
```

In the example above the `my` variable is passed to the function as a copy. Using a pointer declaration will enable to change the instance's values

```go
func (my *MyStruct) UpdatePrivate(privateValue string) {
  my.privateVariable = privateValue
}
```

#### Next

For a simple introduction this post is already long. Next on we will learn more about the following topics

  - Pointers
  - Collections
  - Flow-control
  - Defer
  - Error handling
  - Concurrency, the cool stuff

#### Further reading

For a more complete understanding of the **go** language, syntax, and usage please refer to the following sources:

- [Effective go](https://golang.org/doc/effective_go.html) for tips on writing clear, idiomatic Go code.
- [An introduction to programming in go](https://www.golang-book.com/books/intro) for a free online e-book.
- [A full list of books about go](https://github.com/dariubs/GoBooks)



For the example codes in this post please refer to [this code repo](https://github.com/danielfbm/go-intro).

[golang]: https://golang.org/
[godownload]: https://golang.org/dl/

