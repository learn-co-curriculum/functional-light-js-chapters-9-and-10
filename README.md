## Chapter 9: List Operations

### Highlights
- Chaining and/or composing list operations together means intermediate results are tracked implicitly and less prone to accidental mutation and hidden side effects.

#### Mapping
- Discusses mapping transformation as projecting a value from one location to another and not as in-place mutation/reassignment. 
- Ideally all functions you pass to `map` would be pure so they could run in a parallelized enviroment without issue

#### Functors
- "A functor is a value that has a utility for using an operator function on that value, which preserves composition."
- A value is compound if it is comprised of individual values (ie. arrays). The functor uses the operator function on each individual value in the compound value and the functor utility creates a new compound value holding the results of all the individual operator function calls -> describes how `map` works
- " You can define a mapping function for any data structure; as long as the utility follows these rules, the data structure is a functor."

#### Filter
- In programming filters are inclusionary and not exclusionary

#### Reduce
- Combines values of a list down to a single value
- Reducing/combining also referred to as "folding"

#### Advanced List Operations
- unique, flatten, zip, merge

#### Methods vs. Standalone
- Standalone functions vs. methods of array prototype
- Array methods receive implicit `this` arg so they aren't actually unary, which makes composition more difficult

#### Fusion
- "Fusion deals with combining adjacent operators to reduce the number of times the list is iterated over" -> better for performance
- Can combine adjacent `map` calls by composing them together, which has performance benefits and also improves declarative nature of your list operations

#### Beyond Lists
- binary tree example used to show that you're able to use so-called "list operations" on any data structure that is an ordered collection of values

### Discussion Topics

1. Simpson believes you shouldn't use `map` in place of `forEach`  where a side effect is performed because you're using a FP operation in a non-FP way. He justifies this with a hilarious metaphor - "A hammer is meant to be held in your hand; if you instead hold it in your mouth and try to hammer the nail, you’re not gonna be very effective. map(..) is intended to map values, not create side effects." Do people agree/disagree with this?
2. For the section on filtering, is the confusion around inclusionary/exclusionary really that great? Is it a big deal one way or the other?
3. How do people feel about the method vs standalone styles?
    
		```js
		[1,2,3,4,5] 
		.filter( isOdd ) 
		.map( double )
		.reduce( sum, 0 );
		```
    
    vs.
    
    ```js
    reduce( 
            map(
                    filter( [1,2,3,4,5], isOdd ),
                    double
            ), 
            sum, 
            0
    );
    ```
    
## Chapter 10: Functional Async

### Highlights

#### Time as State

- Async increases the difficulty of making code more trustable and predictable
- Coordinating responses from async calls requires extra effort

#### Reducing Time

- Promises and callbacks can be used to take care of time normalization
- "A Promise represents a single (future) value in a time-independent manner. More- over, extracting the value from a promise is the asynchronous form of the syn- chronous assignment (via =) of an immediate value. In other words, a promise spreads an = assignment operation out over time, but in a trustable (time-independent) fashion."

#### Eager vs. Lazy

- eager and lazy describe whether operation will finish immediately or progress over time

#### Reactive FP

- Something is reactive if it is set up to react to values as they come in
- Both producer and consumer of values only have to hold on to those values for as long as they're needed, which allows for better memory usage. Similar to how a buffer works
- A normal array is eager because it holds all of its values right now. A "lazy array" allows for values to come in over time
- Can also be referred to as "evented" FP

#### Declarative Time

- Both the producer and consumer should be time-independent. The producer can transmit the values whenever they occur and the consumer can consume values whenever they're ready regardless of when/how they arrive
- The time relationship between producer and consumer is then declarative/implicit and not imperative/explicit
- In imperative code example, it's not obvious where the values/events the consumer is ingesting are coming from. In declarative example, consumer code states that values/events are coming from producer.

#### Observables

- Acts like a "lazy array"
- An Observer ingests events from an event stream

### Discussion Topics

1. What are people's thoughts on Observables? Has anyone used them?
2. Thoughts on chapter as a whole? Was it everything you thought it'd be?
<p class='util--hide'>View <a href='https://learn.co/lessons/functional-light-js-chapters-9-and-10'>Functional Light JS Chapters 9 and 10 </a> on Learn.co and start learning to code for free.</p>

<p class='util--hide'>View <a href='https://learn.co/lessons/functional-light-js-chapters-9-and-10'>Functional Light JS Chapters 9 and 10</a> on Learn.co and start learning to code for free.</p>
