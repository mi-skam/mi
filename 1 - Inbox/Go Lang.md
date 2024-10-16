---
tags:
  - learning
modified: 2024-09-26T15:06:41+02:00
---
To start with [[Go Lang|go]] we need to install go with `homebrew`
```shell
brew install go
```

Go needs a set of environment variables set, to find it's **tools**, **libraries** and **path**
```shell title="Environment variables"
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
```

### Running programs

```shell
go run main.go # compiles and executes code in a temp dir
go build main.go # compiles the program in the current dir
```
### Starting a project (module) und creating packages
We start a go project by `go mod init "project-name"`. This creates a  `go.mod` file where the 
project-name and the go version is pinned. 
In a module there are packages. Every package needs to be in a directory and the first module, the entry point is the so-called `main` package, using `function main()` as first function.

### Getting modules

There is no centrally run service that hosts go modules, but all is run by decentralised git-repositories 👍

We can use **go install** to mainly install binaries and tools or **go get** to install dependencies and libraries to a project, updating `go.mod` and `go.sum`
```shell
go install <path-to-git> # e.G. go install github.com/rakyll/hey@latest
go get <path-to-git>
```

### Makefiles to automate builds

```Makefile
.DEFAULT_GOAL := build
.PHONY : fmt lint vet build

fmt:
	go fmt ./...

lint: fmt
	go lint ./...

vet: fmt
	go vet ./...

build: vet
	go build hello.go
```

### Cross compilation

```shell fold title="GOOS determines the target OS; GOARCH the target architecture"
# build for macos and Apple Sillicon
GOOS=darwin GOARCH=arm64 go build

# build for macos and Intel
GOOS=darwin GOARCH=amd64 go build

# build for Linux and ARM
GOOS=linux GOARCH=arm64 go build

# build for Linux and Intel/AMD
GOOS=linux GOARCH=amd64 go build
```

### Public vs Private
Functions that start with lower case letters are private and upper case are public and meant to be exported, as to be used in other packages.

## Data Types

| Data Type      | Hints                                                                                                                                                                                                                                                                                                                                                                                                                            |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Integer        | There are many specific integer types, but as a rule of thumb when to use which:<br>1. working with a protocol or a binary file format defines the integer type<br>2. for a library function which should work with all integers, write a version for `int64` and one for `uint64`<br>3. in all other cases uses `int` (it's size is platform specific)                                                                          |
| Floating point | There is `float32` and `float64`, the lattes is seen as the default.                                                                                                                                                                                                                                                                                                                                                             |
| Strings        | String and runes, runes are used for single characters                                                                                                                                                                                                                                                                                                                                                                           |
| Bools          |                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Arrays         | fixed amount of elements, `myArray := [3]int{2, 3, 5}`<br><br>you can partially update the array by under-providing like that `[3]int{2}` or using indices `[3]int{2: 42}`. The "missing elements" will then bei set to their default values.<br>                                                                                                                                                                                |
| Slices         | dynamic array <br><br>`mySlice = []int{1, 3, 6}`<br>`mySlice2 = make([]int, 5) // [0 0 0 0 0]`<br><br>Slices can be declared by a slice literal (`[]int{}`), nil zero value (`var i []int`) or by the `make()` function.                                                                                                                                                                                                         |
| Maps           | Maps store data in a key-value format, where you can access values by their keys.<br><br>**Dynamic Keys**: Keys can be of any comparable type (like strings, integers, etc.), and the map dynamically grows as more key-value pairs are added.<br><br>unordered<br><br>**Use Case**: Best for scenarios where you need to look up values based on dynamic or external keys.<br><br>*m := make(map[string]int)`<br>m["age"] = 30* |
| Structs        | a collection with a fixed set of named fields with predetermined types.<br><br>statically defined at compile time.  ordered<br><br>**Use Case**: Best for representing complex entities with well-defined properties and behaviors.<br><br>*type Person struct {<br>    Name string<br>    Age  int<br>}<br>p := Person{Name: "John", Age: 30}*                                                                                  |

### Type Conversions

```go
var f = float64(3.14)
```
### Consts and Vars

```go fold title:"There are two ways to declare a variable and assign a value. "
// most verbose way to declare a variable with var and type
// var sum int = left + right 

// the same, but the type is inferred by the type of (sum + right)
// var sum = left + right

// type decleration und value assignment on two lines
// var sum int
// sum = left + right

// short-hand := notation which is only allowed in functions and infers type
sum := left + right 
```

There are some best practices for when to use `:=` vs `var`. By default you take what communicates the intent the best, meaning ":=" within functions by default and "var" as package scope variables.  There are two exceptions:
- inside of functions if the variable should be initialised to its default value, e. G. instead of `x := 0` it's more idiomatic to write`var x int`
- if the derived type is not what you meant and a type casting is needed: instead of `x := byte(20)` `var x byte = 20`

You can group variable declarations like that

```go fold title:"declaration lists"
var (
	X int     = 10
	Y float64 = 30.2
	Z float64 = Y + float64(X)
)
```

#### Typed and untyped Consts

Consts are more less behaving like literals, so we can't use them for composite data types like Arrays, Maps, Slices and Structs. By default they are untyped and adhere to the type they are assigned to, e.G. 
```go fold title:"untyped constant"
const x = 10

var y int = x
var z float64 = x
var d byte = x
```


## Loops

There is only a for-loop, no while or other constructs, but this loop is so versatile that we can emulate all the other types

| loop                           | type                               |
| ------------------------------ | ---------------------------------- |
| `for i := 0; i <= max; i++ {}` | classical c-type for loop          |
| `for sum < max {}`             | while-loop alike (no init, no inc) |
| `for {}`                       | forever-loop                       |

## Conditionals
```go
if value >= 0 {} // basic
else {}
```

There is also a shorthand notation where we move the evaluation and assignment of the value into the scope of the conditional. 
```go
// we start with this
value := someFunc()

if value > 0 {}

// we can use the "if-scoped" variable like this, where value is only accesible in the condition check and the body phase
if value:= someFunc(); value > 0 {}

```

```go
switch value { // basic switch
case "foo":
  //
case "bar":
  //
default:
  //
}
```

And there is also a kind of "anonymous" switch like this, where we evaluate in each case separately.

```go
switch { // basic switch
case value == "foo":
  //
case value == "bar":
  //
default:
  //
}
```

## Structs and Receiver Functions

It's the way to have something like classes in [[OOP]] languages. The method only works for structs that are in the same package (**!**).

```go fold title="Variant without binding between struct and func" hl=10-13 hlalt=16-17
type Point struct {
	X int
	Y int
}

func NewPoint(x, y int) *Point {
	return &Point{x, y}
}

func DistanceFromZero(point *Point) float64 {
	return math.Sqrt(
		math.Pow(float64(point.X), 2) +
			math.Pow(float64(point.Y), 2),
	)
func main() {
	p1 := NewPoint(1, 1)
	fmt.Println(DistanceFromZero(p1))
}
}
```

```go title="Variant using the receiver functions" hl=10-13 hlalt=16-17
type Point struct {
	X int
	Y int
}

func NewPoint(x, y int) *Point {
	return &Point{x, y}
}

func (point *Point) DistanceFromZero() float64 {
	return math.Sqrt(
		math.Pow(float64(point.X), 2) +
			math.Pow(float64(point.Y), 2),
	)
func main() {
	p1 := NewPoint(1, 1)
	fmt.Println(p1.DistanceFromZero())
}
```

## Interfaces

| Interafces |                                     |
| ---------- | ----------------------------------- |
| Anything   |                                     |
| String     | represents a data type as a string  |
| Error      |                                     |

## Go-Routines and Channels