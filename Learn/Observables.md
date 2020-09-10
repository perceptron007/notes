# Observables

## Iterators and Observables ?

### What is the difference between Events and Array ?
- Events and Array are both collections. 

Iterators and Observer are related.

**Iterator**
- Producer
- Consumer

You can ask for an iterator object from an Array in JS.

And in the object you call next to get a value from the prodcucer. 
> In JS "for … of" loop uses iterator pattern behind the scence and let user use for … of in order to work with a nice syntax.

Iterator is done once you have reached one of the two condition.
- Done 
- Error
Either the producer is done with producing value, or producer has faced an error.

**Observer Pattern**

In Observer Pattern you can define a Observer which acts like a producer, you can pass a function to this producer and now if anything happens inside the observer. 
You don't have to manual ask(pull) for the new value, instead the observer will send you (push) the new value.

```js
document.addEventListener(
 "mousemove",
    function next(e) {
        console.log(e)
    },
);

// Will print all the grid point when you will move your mouse.
```
So in a way the iterator and observer pattern are both of similar pattern where one works with synchronous values and other one works with Asynchronous values.

Both patterns are symmetrical

#### Differences
**Iterator and Observer** both are patterns designed to progressively send information to consumer.

The **difference** between the two arised when handling the cases of completion and error. 
In iterator, the author have came up with a way of defining a complete and error state. 
But in case of Observer pattern there were no way to define a completion state and Error state. 

The reason for was because, in UI it was thought the UI Events will always keep happening and the events were mostly thought as UI events. But nowadays events are part of different paradigm such as Streams in Node (I/O Stream), API calls and such. 

Both of them can complete. 

**Example of Push based API**
- DOM Events:
- Websockets
- Server-sent Events
- Node Stream
- Service Workers
- XMLHttpRequest
- jQuery Events
- setInterval

**Observable = Collection + Time**
We can say an Observable is Collection which arrives over time.

> An array is an Collection which gives you an iterator. 

> Generator => Something you can push information in as well as pull information out. 
Iterator => You can only pull information out of it.

 
**Why Observable are important ?**
Let's think about a simple UI workflow.
- A user will create an event on the UI.
- Based on that event you have to make a Async Server Request
- After the data is fetched you might have to display the data along with few animations for the transition

Well, the good thing is Observables can model
- Events
- Async Server Requests
- Animations

If you model all these three things with Observables you can compose them together seamlessly. 

So what our adapted push based interface might look like 

**Adapted Push based API**
- DOM Events :: Observable
- Websockets :: Observable
- Server-sent Events :: Observable
- Node Stream :: Observable
- Service Workers :: Observable
- jQuery Events :: Observable
- XMLHttpRequest :: Observable
- setInterval :: Observable

All the push based API's now would be exposed as Observables.

#### How to handle Events in traditional Event based API
```js
var logger = (e) => console.log(e);
document.addEventListener("mousemove", logger);

document.removeEventListener("mousemove", logger);
```

**Observable API**
```js
var mouseMoves = Observable.fromEvent(element, "mousemve")
var subscription = mouseMoves.forEach(console.log);

subscription.dispose();
```
> Mental model for an Observable is to think Observable similar to Event Handler, where in Event Handler you can only pass one handler for value, in Observable you can pass three different handler. 

Observable accepts an Object with three different handlers
- onNext: What to on value, similar to Event Handler
- onError: You can tell what to do in case Error happened
- onCompleted: You can tell what to do in case the Event is completed

> This object is called an Observer object.

### Implementing Observable "fromEvent" method

```js
Observable.fromEvent => (dom, eventName) {
	// return Observable Object
    return {
		forEach: function(observer) {
			let handler = (e) => observer.onNext(e);
    	    dom.addEventListener(eventName, handler);
        
        	// return Subsciption Object
        return {
            dispose: () => 		dom.removeEventListener(eventName, handler);
        }   
    };
  };
}
``` 

### How to Flatten Async Calls ?
- Three basic Flattening Async Strategies

**concatAll (Top to Bottom and Left To Right)**
When you use concatAll, it doesn't matter in which order the observable are completing or emiiting, the concatAll will flatten the values in the same order the observables are passed inside the concatAll. 

```js
{
 ..{1}
 ....{2 ..........3}
 ........{}
 ............{4}
}.concatAll()

{..1.2.............3.4}

// It wouldnt matter if 4 is emmitted before 3 the order is important Stream 2 will be completed first only then
// next observable is picked up.
```

Lets imagine it this way

Say you are creating a dish and you need certain ingredients
Lets divide these ingredients into few categories

```js
Category1: Fats
Category2: Veggies
Category3: Sauces
Category4: Protien
Category5: Garnish



concatAll([
    Category1
    Category2
    Category3
    Category4
    Category5
])


//Now when you pass an observer to this concatAll we want the result in the same order as we have passed the observables in, we can't do anything with Garnishing items until we have completed the remaining steps above. 

// In UI we run into such concurrency problems more than ever where you are waiting for one datasource to arrive before you can make use of another data-source, thus we can use such a strategy to work for us.

```
But as we can see from the use cases of the concatAll, it would be a bad idea to pass an infinite stream in concatAll because it will never end and the streams after them will never be called. 

**MergeAll (First Come First Serve)**
TODO: Add Explaination Here

**SwitchLatest (Whenever a new Observable comes along dispose the old one)**
TODO: Add Explanation here

#### What is an Hot Observable ?
Some observable will only emit values, when you apply on observer to them like API call. But few of them will keep emitting value and doesn't depend on the consumer of the observable. For example a mouse-move event is a **hot-observable**. 
You will be able to listen to the values which it will emit after subscribing but not the value it has already emitted and the source will not wait for you either, it will emit the event as soon as an event has happened.

#### Explain TakeUntil.
```js
Observable({.....1.....2.............3}).takeUntil(
	Observable({................4}) <- Stop Observable
)
// As soon as you have an event emitted in the stop observable, it will stop listening to the source observable.
// Result {.....1......2......}  You can see 4 is emitted before 3 therefore the resulting observable doesn't have 3 as the source breaks as soon as 4 has arrived
```

#### What is the difference between Promise and Observable ?
Promise are not suitable for modelling async operations on the UI. 
- You can't cancel a promise, a promise is always hot.
- When you create on Observable it doesn't start calling an API, it's cold. It will only call the API only when it's subscribed to.
- Promise 