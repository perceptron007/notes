# Fucking Fuck functional Programming
### Basic Principle 

#### What is functional programming 
Functional programming is a computer programming paradigm that relies on functions modeled on mathematical functions.
The model look like as below

															Input -> Computation -> Output
Functions are first class. 
- Can be used as values
- Can be passed as params in another functions
- Functions are pure

Purity is often time associated with refrential transparency.
- Referential Transparency means that a function given a same input will always produce a same output no matter how many times the function is called.


In lambda calculus or mathematics, a function is just a relation between an Input and Output. 
- Function maps Input to Output
- So, in case of a pure function and when we have an Input and we know the definition of function we can easily predict the output.
- Understanding functions as a mapping between Input and Output is crucial in order to think about Functional Programming.

#### Lets learn a bit about Lambda Calculus

Lambda Calculus has three basic components. 
- Expressions
- Variables 
- Abstractions

###### Expression
An expression is a superset of {Variable and Abstractions}
An expression is something which needs to be evaluated.

f (x) => x * 2;

The right hand side of => above is an example of expression.
It itself has no value, but once it's evaluated it gives us a value. 


######  Abstraction
 An abstraction is just another name for a function.
 It is an lambda term which has a head (denoted by lamda symbol λ) and a body and is applied to an arguement (Arguement is an input value)
 
 - So from the definition we can infer abstraction is made up of two parts 
     - Head and Body
     - λ (lambda) : This is often times used to denote the head
     - Body : This is often time an expression

Example of a simple function written in lambda calculus
```haskell
											λx.x
```

The way to think about a function in functional programming is simple. 
- You will have a function which will have a head and a body.
- Body of the function will contain some variable.
- Now you need to apply this function to arguements. 
    - Apply function to arguements is same as calling a function with parameters. (In non functional programming language)
- So now all the variables in the expression will be replaced by values of arguements.

The above given example (λx.x) is a lamda function and it doesn't have a name. 
It's an example of _anonymous function_ 

(λ)x : This denots head of the lamda 
λ ( x ) : The x part is the single parameter of this function
λ x(.)x : The ' . ' seperates the paramater and the body.
λ x. (x) : The last x is the body, which in case of this function is just returning the value. 

Which implies it's an Identity function.

##### Beta Reduction
Beta reduction is this process of applying a lambda term to an argument, replacing the bound variables with the value
of the argument, and eliminating the head.

Applications in lambda functions are left associative.
**Example**
```haskell
((λx.x)(λy.y))z
[x ∶= (λy.y)]
(λy.y)z
[y ∶= z]
z
```
The process of beta reduction stops when there are either no more heads or lambda remaining to reduce.

Now we can come up with a definition of **computation** 
> A computation therefore consists of an  initial lambda expression (or two, if you want to separate the function and its input) plus a finite sequence of lambda terms, each deduced from the preceding term by one application of beta reduction.

**Free variables ?**
The variables which are not bound in the head of the lambda but still are present in the body. 

**Alpha equivalence**
When two or more lamba expression when applied an arguement results in same values after reduction those lambda expressions are called Alpha equivalent

**Multiple Arguements in Lambda**
Each lamda can only bind to one parameter and can only accept one arguement.
But we might have functions which might require multiple arguements. For such kind of functions we have nested heads.

So you apply the leftmost head first and reduce it, then this head is elimenated and you move on to another head. 

This process was discovered by scientist called Haskell Curry and is called Currying. 




### Basic Commands

Input  :

Output

### Questions
- What is an Abstraction
- What is a bound variable in a Body of Abstraction. 