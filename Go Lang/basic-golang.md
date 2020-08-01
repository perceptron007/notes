# Golang

An **interface** doesn't require * to be refrenced, only a **struct** require a * to be refrenced.

```go
func g(g*GoodBye) ServeHTTP(rw http.ResponseWriter, *r http.Request) {
    rw.Write([]byte("Bye"))
}
```

### Types in Go
- Integer
```go
// Types of int in Go
int
int8
int16
int32
int64
uint
uint8
uint16
uint32
uint64

var age int = 21

// Types of float in Go
float32
float64

var gpa float = 4.0

// String type in Go
var dessert string = "Pancake"

// Boolean type in Go
&& // And
|| // or
!  // Not
<  // Greater than
>  // Smaller than 
== // Equal to
!= // Not equal to
<= // Greater than equal to
>= // Smaller than equal to
```

### Documentation to learn
- ServeMux (http.servemux): It's http multiplexer, it acts as route handler for http request deciding based on request path which http handler it needs to map it to.
- HandleFunc: handleFunc is the function which is triggered when a request arrives.
- ResponseWriter: ResponseWriter is an interface which contains necessary method to write response back for a request. It contains method which can be used to update response header as well as response body.
- Request: Request is a struct in go, it acts as an object which carries a lot of params of incoming request. 
   
 ### Questions
 - What is a Package ?
 - What is http.handler ?
     - It's an Interface with a single method ServeHTTP(ResponseWrite, *Request)
 - Why timeout is important for route handlers ? 
 - What is gracefull shutdown ?
 