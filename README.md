# Functional-core-imperative-shell


# 1. Separation of immutable and mutable logic
Quite a lot of different people have been on the same trail of thought. Gary Bernhardt's formulation of a *"functional core, imperative shell"* seems to be the most voiced. 



### "Boundaries" - Gary Bernhardt  
*"Imperative shell" that wraps and uses your "functional core".. The result of this is that the shell has fewer paths, but more dependencies. The core contains no dependencies, but encapsulates the different logic paths. So we’re encapsulating dependencies on one side, and business logic on the other side. Or put another way, the way to figure out the separation is by doing as much as you can without mutation, and then encapsulating the mutation separately. Functional core — Many fast unit tests. Imperative shell — Few integration tests*  

https://www.youtube.com/watch?v=yTkzNHF6rMs  
https://www.destroyallsoftware.com/talks/boundaries  
https://www.destroyallsoftware.com/screencasts/catalog/functional-core-imperative-shell  

### There are only two roles of code - John Sonmez  
*All code can be classified into two distinct roles; code that does work (algorithms) and code that coordinates work (coordinators).*  
https://simpleprogrammer.com/2012/10/21/there-are-only-two-roles-of-code/

### Object layer, valuelayer - Andy Matuschak 
*Great talk, but specifically on the separation of side-effects at the at the 27 minutes 53 seconds mark.*  
https://realm.io/news/andy-matuschak-controlling-complexity/


### A Modern Architecture for FP - John A De Goes  
*Interpreters of the functional core*  
http://degoes.net/articles/modern-fp
http://degoes.net/articles/modern-fp-part-2


### Hexagonal architecture - Alistair Cockburn  
*Hexagonal Architecture is an architecture defined by establishing a perimeter around the domain of your application and establishing adapters for input/output interactions. By establishing this isolation layer, the application becomes unaware of the nature of the things it's interacting with.*

*Create your application to work without either a UI or a database so you can run automated regression-tests against the application, work when the database becomes unavailable, and link applications together without any user involvement.*

http://alistair.cockburn.us/Hexagonal+architecture  
https://github.com/jschairb/sandbox/wiki/HexagonalArchitecture   



# 2. Test isolation - nomock
Growing Object-Oriented Software, Guided by Tests Without Mocks - Vladimir Khorikov  
http://enterprisecraftsmanship.com/2016/07/05/growing-object-oriented-software-guided-by-tests-without-mocks/

Test Isolation Is About Avoiding Mocks - Gary Bernhardt   
https://www.destroyallsoftware.com/blog/2014/test-isolation-is-about-avoiding-mocks

To Kill a Mockingtest - Ken Scambler  
http://rea.tech/to-kill-a-mockingtest/

Mocking is Tautological - Mark Sands  
http://marksands.github.io/2014/05/14/mocking-is-tautological.html  



# 3. Blogs on Functional core, Imperative shell  
"Functional core & Imperative shell" : OO design, and isolated tests without mocks  
http://blogs.perl.org/users/mascip/2014/06/functional-core-imperative-shell-oo-design-and-isolated-tests-without-mocks.html  
http://blogs.perl.org/users/mascip/2014/06/functional-core-imperative-shell-explanation-with-code.html  


Business-Friendly Functional Programming, Part 2: Testability - Yang Bo  
http://rea.tech/business-friendly-functional-programming-part-2-testability/

mokacoding - unit and acceptance testing, automation, productivity  
http://www.mokacoding.com/blog/functional-core-reactive-shell/

Functional Core, Imperative Shell - Sean Hammond  
http://www.seanh.cc/posts/functional-core-imperative-shell

BoochTek, LLC  
http://blog.boochtek.com/category/programming/architecture

DoorDash Engineering
https://doordash.engineering/2022/07/26/functional-core-imperative-shell-using-structured-concurrency-to-write-maintainable-grpc-endpoints-in-kotlin/


# 4. Reality...
Conceptually, these are nice ideas. But how well do they ride in reality? Here are some of my experiences from C#.

## Frameworks
To my knowledge, there are no frameworks readily available in which one can program. Also I would be hard pressed to figure out what such framework offer, given that the notion of purity (especially in the light of inheritance and polymorphism and partial compilation) make the problem a deeply rooted in the language, the type checker and the compiler as a whole. 

## Separation
Separating the core from the shell by means of namespaces is too brittle, especially with modern IDE's make it too easy for you to cross the boundaries. A better approach, perhaps, is to separate the core and the shell into different projects under the same solution. That way the code is more segregated.

## Purity
Not much native support is offered from the language in term of keeping the core pure - free from side effects. Perhaps a simple method at startup could via reflection ensure that no usage of file I/O, Console I/O etc is used. The tricky part, though, is realizing just how much code we take for granted that is impure. For example `DateTime.Now` or `Guid.NewGuid()`.

Resharper has introduced a `[pure]` attribute (https://www.jetbrains.com/help/resharper/Reference__Code_Annotation_Attributes.html#PureAttribute) but I have too little experience with it to jot anything down.

# 5. Slides/books
Functional Programming in Ruby - Vitor Capela  
https://speakerdeck.com/dodecaphonic/functional-programming-in-ruby

Enemy of the State by Justin Spahr-Summers  
https://speakerdeck.com/jspahrsummers/enemy-of-the-state

Functional Programming in Swift - slide 55+  
http://www.slideshare.net/SaugatGautam2/functional-programming-in-swift

Test-Driven Development with Python - Harry Percival  
https://books.google.dk/books?id=fTLJAwAAQBAJ&pg=PA403&lpg=PA403&dq=%22functional+core%22+%22imperative+shell%22&source=bl&ots=A4g25w7wWY&sig=x0bu4NZWiXrpzWPziAH7Y78AKgM&hl=en&sa=X&ved=0ahUKEwi0jq3em-zPAhUqG5oKHYNJBIE4ChDoAQhRMAk#v=onepage&q=%22functional%20core%22%20%22imperative%20shell%22&f=false


# Quotes...

>  programming, when stripped of all its circumstantial irrelevancies,   
> boils down to no more and no less than very effective thinking so as to avoid unmastered complexity,  
> to very vigorous separation of your many different concerns.  
> -- Dijkstra EDW512  
> https://www.cs.utexas.edu/users/EWD/transcriptions/EWD05xx/EWD512.html  


