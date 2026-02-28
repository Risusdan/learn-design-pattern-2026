# Design Patterns Learning Schedule

**Scope**: All required topics from the [Learning Path](LearningPath.md) (OPTIONAL topics excluded)

## Progress Tracker

| Week | Topic                                          | Status         |
| ---- | ---------------------------------------------- | -------------- |
| 1    | Introduction, Why, Structure, Classification   | ⬜ Not started |
| 2    | Creational — Factory Method + Abstract Factory | ⬜ Not started |
| 3    | Creational — Builder + Singleton               | ⬜ Not started |
| 4    | Structural — Adapter + Bridge + Composite      | ⬜ Not started |
| 5    | Structural — Decorator + Facade + Proxy        | ⬜ Not started |
| 6    | Behavioral — Chain of Responsibility + Command + Iterator | ⬜ Not started |
| 7    | Behavioral — Observer + State + Strategy       | ⬜ Not started |
| 8    | Behavioral — Template Method + Differentiating All Categories | ⬜ Not started |

---

## Week 1: Introduction, Why, Structure, Classification

*Context-setting week — understand the big picture before diving into individual patterns.*

- [ ] Introduction to Design Patterns — what they are, reusable solutions to common design problems
- [ ] Why Learn Design Patterns — shared vocabulary, proven solutions, avoiding reinventing the wheel
- [ ] Structure of a Design Pattern — intent, motivation, applicability, structure (UML), participants, consequences
- [ ] Classification of Design Patterns — Creational (object creation), Structural (composition), Behavioral (interaction)

**Why It Matters**: Design patterns aren't just "recipes" — they're a shared language that lets engineers communicate complex design ideas in a single word. When someone says "use a Strategy here," the entire team instantly understands the approach: define a family of algorithms, encapsulate each one, and make them interchangeable. Understanding the classification (Creational, Structural, Behavioral) gives you a mental framework for *when* to reach for which category of pattern.

---

## Week 2: Creational — Factory Method + Abstract Factory

- [ ] Factory Method — define an interface for creating objects, let subclasses decide which class to instantiate
- [ ] When to use Factory Method — when a class can't anticipate the type of objects it needs to create
- [ ] Factory Method examples — UI frameworks (create platform-specific buttons), document generators
- [ ] Abstract Factory — provide an interface for creating *families* of related objects
- [ ] When to use Abstract Factory — when a system must work with multiple families of products
- [ ] Abstract Factory examples — cross-platform UI toolkits (Windows vs macOS widgets), database access layers
- [ ] Factory Method vs Abstract Factory — single product vs family of products

**Why It Matters**: Factory patterns solve the problem of *decoupling object creation from object use*. Without them, your code is littered with `if platform == "windows": button = WindowsButton()` conditionals everywhere. With a factory, you centralize that decision in one place, and the rest of your code works with the abstract `Button` interface. This is the foundation of plugin architectures, dependency injection, and cross-platform design — you'll see factories in every major framework.

---

## Week 3: Creational — Builder + Singleton

- [ ] Builder — separate the construction of a complex object from its representation
- [ ] When to use Builder — when an object has many optional parameters or complex construction steps
- [ ] Builder examples — constructing complex queries, building HTTP requests, assembling UI layouts
- [ ] Method chaining and fluent APIs — `builder.setX().setY().build()`
- [ ] Singleton — ensure a class has exactly one instance, provide a global access point
- [ ] When to use Singleton — shared resource (database connection pool, logger, configuration)
- [ ] Singleton pitfalls — hidden dependencies, difficult testing, concurrency issues
- [ ] Differentiating Creational Design Patterns — when to use which pattern and trade-offs

**Why It Matters**: Builder solves the "telescoping constructor" problem — when a class has 10 optional parameters, a constructor with 10 arguments is unreadable and error-prone. Builder lets you set only what you need, with readable method names. Singleton is the most controversial pattern — useful for truly global resources (loggers, config), but often misused as a glorified global variable. Understanding *when* Singleton helps versus when it hides dependencies and breaks testability is a critical design skill.

---

## Week 4: Structural — Adapter + Bridge + Composite

- [ ] Adapter — convert the interface of a class into another interface clients expect
- [ ] When to use Adapter — integrating third-party libraries, legacy code, or incompatible interfaces
- [ ] Adapter examples — wrapping a REST API to match your internal interface, XML-to-JSON conversion
- [ ] Bridge — decouple an abstraction from its implementation so they can vary independently
- [ ] When to use Bridge — when both abstraction and implementation need to be extended independently
- [ ] Bridge examples — shapes with different rendering engines, notifications across different platforms
- [ ] Composite — compose objects into tree structures to treat individual objects and compositions uniformly
- [ ] When to use Composite — when you have part-whole hierarchies (menus, file systems, UI components)

**Why It Matters**: Adapter is the most pragmatic pattern — in real projects, you constantly integrate external systems with incompatible interfaces. Rather than modifying the external code (often impossible) or polluting your code with their interface, an adapter translates between the two. Bridge separates "what it does" from "how it does it" — essential when you need to support multiple platforms or backends. Composite lets you treat `File` and `Directory` with the same interface, which is how every file system, DOM tree, and menu system works.

---

## Week 5: Structural — Decorator + Facade + Proxy

- [ ] Decorator — attach additional responsibilities to an object dynamically, alternative to subclassing
- [ ] When to use Decorator — adding behavior (logging, caching, encryption) without modifying the original class
- [ ] Decorator examples — Java's I/O streams, Python's `@decorator`, middleware stacks
- [ ] Facade — provide a simplified interface to a complex subsystem
- [ ] When to use Facade — hiding complexity, providing a higher-level API for common use cases
- [ ] Facade examples — database ORM over raw SQL, simplified APIs for complex libraries
- [ ] Proxy — provide a surrogate or placeholder for another object to control access
- [ ] When to use Proxy — lazy loading, access control, remote objects, caching
- [ ] Differentiating Structural Design Patterns — when to use which pattern and trade-offs

**Why It Matters**: Decorator is one of the most widely used patterns — Python's `@decorator` syntax is literally named after it. The key insight is that you can stack behaviors: `LoggingDecorator(CachingDecorator(AuthDecorator(service)))` adds logging, caching, and auth without modifying `service`. Facade is the pattern you use most without realizing it — every time you create a helper function that wraps complex logic into a simple call, that's a facade. Proxy controls access: lazy-loading a large image, rate-limiting API calls, or adding security checks transparently.

---

## Week 6: Behavioral — Chain of Responsibility + Command + Iterator

- [ ] Chain of Responsibility — pass a request along a chain of handlers until one handles it
- [ ] When to use Chain of Responsibility — middleware pipelines, event handling, logging chains
- [ ] Chain of Responsibility examples — HTTP middleware (auth → rate-limit → handler), DOM event bubbling
- [ ] Command — encapsulate a request as an object, enabling undo, queuing, and logging
- [ ] When to use Command — undo/redo functionality, task queues, macro recording
- [ ] Command examples — text editor undo, transaction systems, GUI button actions
- [ ] Iterator — provide a way to access elements of a collection sequentially without exposing internals
- [ ] When to use Iterator — any time you need to traverse a collection uniformly

**Why It Matters**: Chain of Responsibility is the pattern behind every middleware system — Express.js, Django, FastAPI all process HTTP requests through a chain of handlers (authentication, logging, rate limiting, routing). Command turns actions into objects, which is the key to undo/redo (each command stores enough state to reverse itself), task queues (commands can be serialized and executed later), and macro recording. Iterator is so fundamental that most languages built it into the language itself (`for...of` in JS, `for...in` in Python).

---

## Week 7: Behavioral — Observer + State + Strategy

- [ ] Observer — define a one-to-many dependency so that when one object changes state, all dependents are notified
- [ ] When to use Observer — event systems, reactive UIs, pub/sub messaging
- [ ] Observer examples — event listeners in JavaScript, React state changes, message brokers
- [ ] State — allow an object to alter its behavior when its internal state changes (appears to change class)
- [ ] When to use State — objects with complex state-dependent behavior (order processing, media players)
- [ ] State examples — TCP connection states, document workflow (draft → review → published)
- [ ] Strategy — define a family of algorithms, encapsulate each one, and make them interchangeable
- [ ] When to use Strategy — when you need to swap algorithms at runtime
- [ ] Strategy examples — payment processing (credit card, PayPal, crypto), sorting strategies, compression algorithms

**Why It Matters**: Observer is the backbone of reactive programming and event-driven architectures — React's state management, RxJS, and every GUI framework's event system is built on this pattern. State eliminates complex `if/else` chains by representing each state as its own class with its own behavior — a TCP connection in the "Established" state handles data differently than in the "Closing" state. Strategy lets you swap algorithms without changing the code that uses them — essential for payment systems, shipping calculators, and any system with pluggable behavior.

---

## Week 8: Behavioral — Template Method + Differentiating All Categories

- [ ] Template Method — define the skeleton of an algorithm in a base class, let subclasses override specific steps
- [ ] When to use Template Method — when multiple algorithms share the same structure but differ in details
- [ ] Template Method examples — data processing pipelines (read → transform → write), test frameworks (setup → test → teardown)
- [ ] Template Method vs Strategy — inheritance-based (Template) vs composition-based (Strategy)
- [ ] Differentiating Behavioral Design Patterns — when to use which behavioral pattern and trade-offs
- [ ] Differentiating All Categories — Creational vs Structural vs Behavioral, choosing the right pattern for the problem

**Why It Matters**: Template Method is the "Hollywood Principle" — don't call us, we'll call you. The framework defines the workflow, and you fill in the specific steps. Every test framework uses this: `setUp()` → `runTest()` → `tearDown()`. The final differentiation exercise is crucial — in practice, the hardest part of design patterns isn't understanding each one, it's *recognizing which one to apply*. Knowing that "I need to decouple creation" points to Creational patterns, "I need to combine objects" points to Structural, and "I need to manage behavior/communication" points to Behavioral is the real skill.

---
up:: [MOC-Programming](../../../01-index/MOC-Programming.md)
#type/learning #source/self-study #status/seed
