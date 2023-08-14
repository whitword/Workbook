# General enterprise questions

## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?
N-tier (or multi-tier) architecture is a software architecture pattern that divides an application into logical layers or tiers, each responsible for specific functions and having a distinct level of abstraction. Typically, the architecture consists of presentation (user interface), application/business logic, and data storage layers. It promotes modularity, scalability, and separation of concerns by isolating different aspects of the application into separate layers. N-tier architecture enables easier maintenance, flexibility in technology selection, and the ability to distribute components across multiple servers, improving performance and allowing for better resource utilization.
#### What are microservices? Advantages and disadvantages?
Microservices are an architectural approach in which an application is decomposed into small, independent services that communicate with each other through well-defined APIs. Each service focuses on a specific business capability and can be developed, deployed, and scaled independently. 

Advantages of microservices include increased flexibility, scalability, and fault isolation. They allow for technology diversity, easier testing and deployment, and better team autonomy. However, microservices introduce complexities in terms of inter-service communication, distributed system management, and deployment overhead. They require careful design, monitoring, and coordination to ensure the benefits outweigh the challenges and avoid introducing unnecessary complexity to smaller projects.
#### What is Separation of Concerns?
Separation of Concerns (SoC) is a software design principle that advocates dividing a system into distinct modules or components, each addressing a separate concern or responsibility. The idea is to separate different aspects of functionality to make the system more modular, maintainable, and understandable. By isolating concerns, changes or updates to one part of the system have minimal impact on other parts, promoting code reusability and reducing the risk of unintended side effects. SoC improves code organization, readability, and allows for independent development and testing of individual components, leading to more flexible and maintainable software systems.

#### What is a layered design and why is it important in enterprise applications?
A layered design is an architectural pattern where an application is divided into logical layers, each responsible for a specific set of functionalities. Common layers include presentation, business logic, and data access. This design promotes separation of concerns, modularity, and maintainability. It enables the development and maintenance of enterprise applications by providing clear boundaries, facilitating parallel development, and allowing for easier testing, scalability, and extensibility. Layered design enhances code organization, collaboration between teams, and code reuse, making it crucial for building complex and robust enterprise applications.
#### What is Dependency Injection?
Dependency Injection (DI) is a software design pattern and technique where the dependencies of a class or component are provided from the outside, rather than being created or managed internally. It involves injecting the required dependencies through constructor parameters, setter methods, or interfaces. DI promotes loose coupling, modularity, and testability by decoupling classes from specific implementations of their dependencies and allowing for easy substitution or modification of dependencies. It facilitates code reuse, flexibility, and maintainability by externalizing dependencies and promoting a clear separation of concerns.
Benefits of Dependency Injection:

1. Loose Coupling: Dependency Injection promotes loose coupling between components by removing the direct dependency between a class and its dependencies. This makes it easier to replace or modify dependencies without affecting the class's implementation.

2. Modular and Reusable Code: With Dependency Injection, classes become more modular and reusable. They can be developed and tested independently, as dependencies can be easily mocked or replaced with alternative implementations during testing or in different contexts.

3. Testability: Dependency Injection facilitates unit testing by allowing dependencies to be easily replaced with mock objects or test doubles. This enables isolated testing of individual components, improving test coverage and making it easier to identify and fix bugs.

4. Flexibility and Configurability: By externalizing dependencies, Dependency Injection allows for greater flexibility and configurability. Different configurations or implementations of dependencies can be provided at runtime, enabling dynamic behavior and configuration changes without modifying the class's code.

5. Code Maintainability: Dependency Injection reduces code duplication and improves code maintainability. It promotes single responsibility and separation of concerns, making the codebase more modular, readable, and easier to maintain.

Dependency Injection frameworks and containers are often used to automate and simplify the process of injecting dependencies. These frameworks handle the instantiation and management of objects, resolving dependencies, and wiring them together automatically based on configuration or annotations.

#### What is the DAO pattern? When and how to implement?
The DAO (Data Access Object) pattern is a design pattern that separates the data access logic from the business logic in an application. It provides an abstraction layer between the application and the underlying data storage, such as a database. The DAO pattern helps achieve modularity, code reusability, and maintainability.

The DAO pattern should be implemented when there is a need to decouple the business logic from the details of data storage, and when there is a requirement for flexibility in switching or adapting to different data storage technologies. It is typically implemented by defining a DAO interface that declares the contract for data access operations and providing concrete DAO classes that implement the interface and handle the data access logic.
#### What is SOA? When to use?
SOA (Service-Oriented Architecture) is an architectural style that emphasizes the creation of services as modular, reusable components. It involves designing systems in a way that different services can be accessed and combined to build larger applications. SOA promotes loose coupling, interoperability, and service reusability.

SOA is useful when building complex applications that require flexibility, scalability, and the integration of diverse systems or technologies. It is beneficial in scenarios involving distributed systems, heterogeneous platforms, and the need for business agility. SOA enables organizations to adapt to changing requirements, promote service reusability, and facilitate the integration of various applications and services.

### Testing

#### What are unit test, integration test, system test, regression test, acceptance test? What is the major difference between these?
Unit Test: Unit tests focus on testing individual units or components of code in isolation to ensure they function correctly according to their specifications.

Integration Test: Integration tests verify the interaction and collaboration between different components or modules of a system, ensuring they work together as intended.

System Test: System tests evaluate the complete and integrated system to verify that it meets the specified requirements and functions correctly as a whole.

Regression Test: Regression tests are executed to ensure that changes or updates to the system have not introduced new defects or caused existing functionality to break.

Acceptance Test: Acceptance tests are conducted to determine if a system satisfies the acceptance criteria and meets the needs of the stakeholders or end-users.

The major difference between these types of tests lies in their scope and purpose. Unit tests focus on isolated components, integration tests verify the collaboration between components, system tests evaluate the entire system, regression tests guard against unintended changes, and acceptance tests ensure the system meets user requirements.
#### What is code coverage? Why is it used? How you can measure?
Code coverage refers to the measurement of the proportion of code that is executed by tests. It indicates how thoroughly a set of tests exercises the codebase. Code coverage is used as a metric to assess the quality and effectiveness of testing efforts, helping identify areas of code that lack test coverage. It aids in identifying potential bugs, reducing the risk of undiscovered issues, and increasing confidence in the codebase. Code coverage can be measured using various tools that track which parts of the code are executed during test runs, such as line coverage, branch coverage, or statement coverage.
#### What does mocking mean? How would you do it 'manually' (i. e. without using any fancy framework)?
Mocking is a technique used in software testing to create simulated objects that mimic the behavior of real objects or dependencies. It allows for isolated testing of a specific unit by replacing real dependencies with mock objects that can be controlled and manipulated. Manual mocking involves creating custom implementations of dependencies or interfaces that provide the desired behavior for testing purposes. This can be achieved by creating classes or functions that mimic the expected behavior of the real objects, often using predefined values or hard-coded responses. Manual mocking requires manual setup and maintenance of the mock objects and can be more time-consuming compared to using dedicated mocking frameworks.
#### What is a test case? What is an assertion? Give examples!
In software development, a test case is a specific scenario or condition that is used to verify the correctness of a program or a specific feature. It consists of inputs, execution steps, and expected outcomes. Test cases are designed to ensure that the software functions as intended and to identify any defects or errors.

An assertion, in the context of testing, is a statement or condition that is expected to be true at a specific point in the execution of a program. It acts as a checkpoint to validate whether the program is behaving correctly or not. If an assertion fails, it indicates that there is a bug or an unexpected behavior in the program.

Example:
```csharp
// Test case for a function that calculates the sum of two numbers
public void TestSum()
{
    int result = Sum(2, 3);
    int expected = 5;
    
    // Assertion to verify if the result is equal to the expected value
    Assert.AreEqual(expected, result, "Sum calculation failed!");
}
```

In this example, the test case tests a function called `Sum` that takes two integers as input and returns their sum. It sets the expected result as 5 and then calls the `Sum` function with inputs 2 and 3. The `Assert.AreEqual` method is used to compare the expected result with the actual result. If they are not equal, an assertion failure will occur.

Note: The example uses the NUnit testing framework, which provides the `Assert.AreEqual` method. If you're using a different testing framework, the assertion syntax may vary.

Test cases and assertions play a crucial role in automated testing, where they are often used in unit tests, integration tests, and other types of tests to ensure the correctness of software systems.
#### What is TDD? What are the benefits?
TDD (Test-Driven Development) is a software development approach in which tests are written before the corresponding code is implemented. The development cycle typically involves writing a failing test, implementing the code to make the test pass, and then refactoring as needed. TDD aims to improve code quality, design, and maintainability by emphasizing test coverage and driving the development process.

The benefits of TDD include improved code quality, faster feedback loops, reduced defect rates, better code maintainability, and increased confidence in the codebase. TDD encourages modular and loosely coupled code, promotes better test coverage, and helps identify issues early in the development process, leading to more robust and reliable software.
#### What are the unit testing best practices? (Eg. how many assertion should a test case contain?)
Unit testing best practices include writing focused and independent tests, adhering to the "Arrange, Act, Assert" structure, ensuring test readability, and aiming for a single assertion per test case. However, the number of assertions in a test case may vary depending on the specific scenario. While it's generally recommended to have a single assertion per test case to keep tests focused and maintainable, there are cases where multiple related assertions may be appropriate, such as testing different aspects of the same method or verifying multiple expected outcomes. It's important to strike a balance between readability, maintainability, and test granularity based on the specific requirements and context.
#### What is arrange/act/assert pattern?
The "Arrange, Act, Assert" (AAA) pattern is a common structure followed in unit testing. It helps in organizing the test code into distinct sections for clarity and readability. 

- Arrange: In this section, the test setup is performed by initializing objects, setting up dependencies, and providing necessary inputs.
- Act: The section where the action or behavior being tested is executed.
- Assert: This section verifies the expected outcomes or conditions by asserting the actual results against the expected values or assertions.

The AAA pattern makes it easier to understand the purpose and flow of the test and separates the setup, execution, and verification steps, promoting a clear structure in unit test code.

### DevOps

#### What is continuous integration? Why is CI important?
Continuous Integration (CI) is a software development practice where developers frequently integrate their code changes into a shared repository, followed by an automated build and testing process. CI aims to detect integration issues and bugs early in the development cycle, ensuring that the codebase remains stable and functional. It promotes collaboration, faster feedback loops, and helps maintain code quality by catching issues early. CI enables teams to identify and fix problems quickly, reduce the risk of integration failures, and facilitate the delivery of reliable software in a more efficient and consistent manner.
#### Why are tests important in the CI workflow?
Tests are crucial in the CI workflow as they enable the early detection of issues, ensuring that bugs or regressions are caught as soon as possible. They provide a means of quality assurance by verifying that the software functions as intended and meets the defined requirements. Tests also validate the integration of code changes, ensuring compatibility and preventing conflicts. By detecting regressions, tests help maintain the stability of the software. Additionally, tests provide a fast feedback loop, allowing developers to address issues promptly and improve the overall development cycle. They instill confidence in code changes, enabling developers to iterate and innovate with assurance.
#### Name some software that help the CI workflow!
Some popular software tools that help facilitate the CI workflow include:

1. Jenkins: An open-source automation server that supports continuous integration and delivery.

2. Travis CI: A cloud-based CI platform that integrates with various version control systems.

3. CircleCI: A cloud-based CI/CD platform with support for parallel and distributed builds.

4. GitLab CI/CD: A built-in CI/CD solution provided by GitLab for seamless integration with Git repositories.

5. TeamCity: A powerful CI/CD server with advanced features and support for different programming languages and platforms.

6. Bamboo: Atlassian's CI/CD server that integrates with other Atlassian tools like Jira and Bitbucket.

These tools provide features for building, testing, and deploying software in an automated and continuous manner, helping streamline the CI workflow.
#### What is Continuous Delivery?
Continuous Delivery is a software development practice that aims to enable the frequent and reliable release of software updates to production. It involves automating the entire release process, from building and testing to deployment and release. With Continuous Delivery, teams focus on producing software in small, incremental changes that can be rapidly and safely deployed. By utilizing automated testing, version control, and deployment pipelines, Continuous Delivery ensures that software updates are thoroughly tested and can be released at any time with minimal risk. It promotes faster feedback, shorter release cycles, and greater agility in delivering valuable features and improvements to end-users.
#### What is Continuous Deployment?
Continuous Deployment is a software development practice where changes made to the codebase are automatically and frequently deployed to production environments without human intervention. It extends the concept of Continuous Integration (CI) and Continuous Delivery (CD) by automating the release and deployment process. In a Continuous Deployment workflow, every successful build and passing tests trigger the automatic deployment of the software to production, ensuring that the latest version of the application is continuously available to end-users. This approach aims to minimize lead time, enable faster feedback loops, and improve the speed of delivering new features or bug fixes to production environments.
#### What is DevOps?
DevOps is a collaborative software development and operations approach that emphasizes the integration and cooperation between development teams and operations teams. It combines cultural, organizational, and technical practices to enable faster and more efficient software delivery and deployment. DevOps aims to bridge the gap between development and operations by promoting automation, continuous integration and delivery, infrastructure as code, and a culture of collaboration, communication, and shared responsibility. The goal of DevOps is to achieve higher software quality, faster time to market, improved scalability, and enhanced customer satisfaction by breaking down silos, streamlining processes, and fostering a culture of agility and innovation.

### Software Methodologies

#### What kind of software-lifecycle models do you know?
There are several software lifecycle models, including:

1. Waterfall Model: A sequential, linear approach where each phase (requirements, design, development, testing, deployment) is completed before moving to the next.

2. Agile Model: An iterative and incremental approach that focuses on flexibility, collaboration, and delivering working software in short iterations.

3. Spiral Model: A risk-driven model that combines elements of waterfall and prototyping, emphasizing risk analysis and iterative development.

4. V-Model: A variation of the waterfall model that emphasizes verification and validation activities at each phase.

5. DevOps Model: A collaborative approach that integrates development and operations, focusing on continuous integration, delivery, and deployment.

Each model has its own strengths and weaknesses, and the choice of model depends on project requirements, team dynamics, and the nature of the software being developed.
#### What is a UML diagram? What kind of diagram types do you know?
A UML (Unified Modeling Language) diagram is a visual representation used to model and describe software systems. UML provides a standardized set of symbols and notations to represent various aspects of a system's structure, behavior, and relationships.

Common types of UML diagrams include:

1. Class Diagram: Depicts the static structure of a system, showing classes, attributes, methods, and their relationships.

2. Use Case Diagram: Illustrates the interactions between actors and the system, capturing the system's functionality from a user's perspective.

3. Sequence Diagram: Represents the dynamic behavior of the system by showing the sequence of interactions between objects over time.

4. Activity Diagram: Describes the flow of activities and actions within a system, highlighting the control and data flow.

5. State Machine Diagram: Models the behavior of objects as they transition through states and respond to events.

These are just a few examples of the many UML diagram types available, each serving a specific purpose in visualizing different aspects of software systems.
#### What is a UML class diagram? What are the typical elements?
A UML class diagram is a type of UML diagram that represents the static structure of a system by depicting classes, their attributes, methods, and the relationships between classes. 

Typical elements in a UML class diagram include:

1. Class: Represents a blueprint for creating objects and defines its attributes and methods.

2. Associations: Describes relationships between classes, such as one-to-one, one-to-many, or many-to-many.

3. Attributes: Represents the properties or data associated with a class.

4. Operations: Represents the methods or functions that a class can perform.

5. Inheritance: Indicates the hierarchical relationship between classes, showing inheritance and specialization.

6. Aggregation and Composition: Depicts whole-part relationships between classes.

These elements collectively provide a visual representation of the structure of a system, the relationships between classes, and the behavior of the objects within the system.
#### What kind of design patterns do you know? Bring at least 3 examples.
There are several design patterns commonly used in software development, including:

1. Creational Patterns: These patterns focus on object creation mechanisms. Examples include Singleton (ensures only one instance of a class is created), Factory Method (provides an interface for creating objects without specifying their concrete classes), and Builder (separates the construction of complex objects from their representation).

2. Structural Patterns: These patterns deal with the composition of classes and objects. Examples include Adapter (adapts the interface of one class to another), Decorator (adds additional functionality to an object dynamically), and Composite (treats individual objects and compositions of objects uniformly).

3. Behavioral Patterns: These patterns are concerned with communication and interaction between objects. Examples include Observer (defines a one-to-many dependency between objects), Strategy (enables selecting algorithms at runtime), and Command (encapsulates a request as an object, allowing parameterization and queuing of requests).

These are just a few examples of the many design patterns available, each addressing specific software design problems and promoting best practices in structuring and organizing code.
#### What is the purpose of the Iterator Pattern?
The purpose of the Iterator Pattern is to provide a way to access elements of a collection sequentially without exposing its underlying structure. It decouples the traversal logic from the collection, allowing clients to iterate over the collection's elements using a common interface. The Iterator Pattern promotes separation of concerns by encapsulating the iteration logic within the iterator object, simplifying the collection interface. It also enables the use of multiple simultaneous iterations on the same collection and provides a standardized way to iterate over various types of collections, enhancing code flexibility and maintainability.
#### What do you know about the SOLID principles?
The SOLID principles are a set of five design principles that promote software design that is modular, maintainable, and extensible. 

1. Single Responsibility Principle (SRP): A class should have only one reason to change.
2. Open-Closed Principle (OCP): Software entities should be open for extension but closed for modification.
3. Liskov Substitution Principle (LSP): Subtypes must be substitutable for their base types without affecting program correctness.
4. Interface Segregation Principle (ISP): Clients should not be forced to depend on interfaces they don't use.
5. Dependency Inversion Principle (DIP): High-level modules should not depend on low-level modules; both should depend on abstractions.

These principles help guide the design and architecture of software systems, promoting loose coupling, modularity, and maintainability. They enhance code flexibility, extensibility, and facilitate easier testing and refactoring.
#### How would you separate data storage code and business logic code (which uses stored data) in an application?
To separate data storage code from business logic code, you can apply the Repository pattern. The business logic code should define interfaces representing the required operations on the data, while the data storage code implements these interfaces. The business logic code interacts with the data storage code through these interfaces without directly accessing the underlying data storage implementation details. This separation allows for flexibility and modularity, enabling easy replacement or change of the data storage implementation without affecting the business logic. It promotes a clean separation of concerns, improves testability, and facilitates maintainability and scalability of the application.

## Computer science

### Data Structures
#### What is the difference between Stack and Queue data structure?
The main difference between a Stack and a Queue data structure lies in the order in which elements are accessed and removed. 

A Stack follows the Last-In-First-Out (LIFO) principle, where the last element added is the first one to be removed. It resembles a stack of items, where new items are placed on top, and the topmost item is the one accessed or removed.

On the other hand, a Queue follows the First-In-First-Out (FIFO) principle, where the first element added is the first one to be removed. It resembles a queue or line, where new items are added at the end, and removal happens from the front.

In summary, a Stack operates on a "last in, first out" basis, while a Queue operates on a "first in, first out" basis.
#### What is a graph? What are simple graphs? What are directed graphs? What are weighted graphs?
A graph is a mathematical structure composed of vertices (also known as nodes) and edges that connect these vertices. It represents relationships or connections between elements. 

A simple graph is an undirected graph without any self-loops or multiple edges between the same pair of vertices.

A directed graph (or digraph) is a graph where each edge has a specific direction, indicating a one-way relationship between vertices.

A weighted graph assigns a numerical value (weight) to each edge, representing a measure of distance, cost, or any other relevant attribute associated with the edge. Weighted graphs are often used to model scenarios where the connections have varying degrees of significance.
#### What are trees? What are binary trees? What are binary search trees?
A tree is a hierarchical data structure consisting of nodes connected by edges, with a single node designated as the root. Each node can have child nodes, forming a branching structure. Trees are used to represent hierarchical relationships or organized data.

A binary tree is a type of tree where each node has at most two child nodes, commonly referred to as the left child and right child. It provides a simple and efficient way to organize and search data.

A binary search tree (BST) is a binary tree that satisfies the binary search property, where the value of each node in the left subtree is less than the value of the node, and the value of each node in the right subtree is greater. BSTs enable efficient searching, insertion, and deletion operations, making them useful for applications where ordered data is required.
#### How can you store graphs in programs? What are the advantages/disadvantages per each?
There are several ways to store graphs in programs, each with its own advantages and disadvantages. 

1. Adjacency Matrix: A 2D matrix where rows and columns represent vertices, and matrix cells indicate the presence or absence of edges between vertices. It allows constant time access to check edge existence but consumes more space for sparse graphs.

2. Adjacency List: Each vertex maintains a list of its adjacent vertices. It requires less space for sparse graphs but requires traversing lists for edge existence checks.

3. Edge List: A list of all edges in the graph, usually represented as pairs of vertices. It is memory-efficient for sparse graphs but lacks direct vertex connectivity information.

The choice depends on factors such as graph density, memory constraints, required operations (access, traversal, modification), and computational efficiency considerations.
#### What are graph traversal algorithms? What is BFS, how does it work? What is DFS, how does it work?
Graph traversal algorithms are used to visit and explore all the vertices or nodes in a graph. They determine the order in which the vertices are visited and can be used to solve various graph-related problems.

Breadth-First Search (BFS) is a traversal algorithm that explores all the vertices at the same level before moving to the next level. It starts at a chosen vertex and visits its adjacent vertices before moving to the next level of vertices. BFS uses a queue data structure to maintain the order of vertex exploration, ensuring that closer vertices are visited first.

Depth-First Search (DFS) is another traversal algorithm that explores as far as possible along each branch before backtracking. It starts at a chosen vertex and visits one of its adjacent vertices, recursively applying the same process until there are no more unvisited vertices. DFS uses a stack data structure to keep track of the visited vertices.

Both BFS and DFS are widely used for various graph-related tasks such as finding connected components, determining reachability, and solving maze or puzzle problems.
#### How does dictionary work?
A dictionary, also known as a hashmap or associative array, is a data structure that stores key-value pairs. It uses a hash function to compute an index, called a hash code, for each key. The hash code determines the position of the corresponding value in an array or bucket. During insertion or retrieval, the hash code is used to quickly locate the desired value. Dictionaries provide efficient lookup, insertion, and deletion operations, with an average constant time complexity. However, collisions may occur when different keys produce the same hash code, requiring additional handling mechanisms such as chaining or open addressing to resolve conflicts.
#### Why is it important for keys in a hashmap to have an immutable type? (Consider string for example.)
It is important for keys in a hashmap to have an immutable type because the hash code of an object is typically computed based on its internal state. If a key's state is mutable and can be changed after being inserted into the hashmap, it may result in a different hash code. As a consequence, the key would no longer be located in the correct position within the hashmap, leading to incorrect lookup or retrieval operations. By using immutable keys, their hash code remains consistent, ensuring the integrity of the hashmap's internal structure and preserving the expected behavior of key-based operations.
### Algorithms
#### What is QuickSort? Describe the main logic of this sorting algorithm.
QuickSort is a widely used sorting algorithm that follows the divide-and-conquer approach. The main logic of QuickSort involves selecting a pivot element from the array and partitioning the remaining elements into two sub-arrays based on whether they are smaller or larger than the pivot. This process is repeated recursively on the sub-arrays until the entire array is sorted. The pivot element is effectively placed in its correct position, and the sub-arrays on either side of the pivot are sorted independently. QuickSort is efficient due to its average-case time complexity of O(n log n), but it can degrade to O(n^2) in the worst-case scenario.
## Software design

### Security

#### What is OAuth2?
OAuth2 is an open standard protocol that enables secure authorization and delegation of user authentication between different applications. It allows users to grant limited access to their protected resources (such as personal information or online accounts) to third-party applications, without revealing their login credentials. OAuth2 operates by issuing access tokens to authorized applications, which can then be used to access the protected resources on behalf of the user. It is widely used for authentication and authorization in web and mobile applications, providing a secure and standardized mechanism for user consent and access control.
#### What is Basic Authentication?
Basic Authentication is a simple authentication scheme used in web protocols, where the user's credentials are sent in plaintext format over the network. It involves including a username and password combination in the HTTP headers of a request. The server validates the credentials and grants access if they are correct. However, Basic Authentication lacks robust security measures and is vulnerable to eavesdropping and credential interception. To enhance security, it is recommended to use protocols like HTTPS in conjunction with Basic Authentication to encrypt the communication channel and protect the user's credentials from unauthorized access.
#### What is CORS, why it’s needed in browsers?
Cross-Origin Resource Sharing (CORS) is a mechanism that allows web browsers to securely make cross-origin HTTP requests. It is needed in browsers to enforce the same-origin policy, which restricts web pages from accessing resources from different origins (domains). CORS defines a set of headers that the server can use to grant or deny access to resources based on the origin of the requesting domain. It provides a way for servers to control which origins are allowed to access their resources, mitigating security risks and protecting user data. CORS enables safe communication between different origins while maintaining the security of web applications.
#### How can you initialize a CSRF attack?
Cross-site request forgery (also known as CSRF) is a web security vulnerability that allows an attacker to induce users to perform actions that they do not intend to perform. It allows an attacker to partly circumvent the same origin policy, which is designed to prevent different websites from interfering with each other.
CSRF attacks exploit a mechanism that makes the sign-in process more convenient. Browsers often automatically include credentials in the request when a user tries to access a site. These credentials can include the user’s session cookies, basic authentication credentials, IP address, and Windows domain credentials.

If there is no protection against CSRF attacks, it can be easy for an attacker to hijack the session and impersonate the user. Once a user is authenticated on the site, the site cannot differentiate between a legitimate user request and a fake request sent by the attacker.

#### What is JWT used for? Where to store it on client side?
JWT (JSON Web Token) is used for secure authentication and authorization in web applications. It is a compact, self-contained token that contains claims or information about the user. JWTs are often used for single sign-on (SSO) scenarios, where a user authenticates with one application and can access other protected resources without re-authentication. On the client side, JWTs are typically stored in the browser's storage, such as localStorage or sessionStorage. They can also be stored in cookies with the "httpOnly" and "secure" attributes for additional security. The client can then include the JWT in subsequent requests to access protected resources on the server.
### Threaded programming

#### When do you need to use threads in an application?
Threads are used in applications to handle concurrent or parallel tasks. They are beneficial when an application needs to perform multiple operations simultaneously, such as handling multiple user requests, processing background tasks, or utilizing multiple CPU cores effectively. Threads allow for the execution of tasks in parallel, improving performance and responsiveness. They are particularly useful for tasks involving I/O (input/output) operations, network requests, or heavy computation. However, it's important to note that thread usage should be carefully managed to avoid issues like race conditions, deadlocks, and resource contention.

#### *When race conditions occur?
A race condition occurs when two threads access a shared variable at the same time. The first thread reads the variable, and the second thread reads the same value from the variable. Then the first thread and second thread perform their operations on the value, and they race to see which thread can write the value last to the shared variable. The value of the thread that writes its value last is preserved, because the thread is writing over the value that the previous thread wrote.

#### *When deadlocks occur?
A deadlock occurs when two threads each lock a different variable at the same time and then try to lock the variable that the other thread already locked. As a result, each thread stops executing and waits for the other thread to release the variable. Because each thread is holding the variable that the other thread wants, nothing occurs, and the threads remain deadlocked.

#### *What is Resource Contention?
In multi-threaded code, contention occurs when two or more threads are attempting to access the same resource simultaneously (in other words, they are contending for access to the resource). In incorrectly-written code, this usually results in errors.

#### What is a daemon thread?
A daemon thread, also known as a background thread, is a type of thread in a program that runs in the background and does not prevent the program from terminating. Unlike regular threads, daemon threads do not keep the program running if all other non-daemon threads have finished execution. Once all non-daemon threads have completed, the JVM terminates, regardless of whether daemon threads are still running. Daemon threads are commonly used for tasks such as garbage collection, log maintenance, or background services that should not prevent the program from exiting.
#### What is the difference between concurrent and parallel execution of code?
Concurrent execution refers to the ability of a system to handle multiple tasks or processes at the same time, regardless of whether they are actually running simultaneously. It involves interleaving the execution of tasks, allowing progress on multiple tasks in an overlapping manner. Concurrent execution can be achieved using techniques such as multitasking, multithreading, or asynchronous programming.

Parallel execution, on the other hand, involves the actual simultaneous execution of multiple tasks or processes across multiple physical or logical processors. It utilizes the available resources to perform tasks concurrently and can result in improved performance by taking advantage of parallel processing capabilities.

In summary, concurrent execution focuses on managing multiple tasks effectively, while parallel execution is about simultaneously executing tasks to leverage available resources and achieve faster execution.
#### What is the most important problem developers are faced when using threads?
One of the most important problems developers face when using threads is ensuring thread safety. Thread safety refers to the ability of a program or system to perform correctly and predictably in a multithreaded environment. Concurrent access to shared resources can lead to issues like race conditions, deadlocks, and data corruption. Developers need to carefully synchronize access to shared data, use locking mechanisms, and employ thread-safe data structures to prevent such problems. Failure to handle thread safety properly can result in bugs, unpredictable behavior, and difficult-to-reproduce issues, making it a critical concern in multithreaded programming.
#### In what kind of situations can deadlocks occur?
Deadlocks can occur in situations involving multiple threads or processes, where each thread holds a resource and waits for another resource that is held by another thread, resulting in a circular dependency. Deadlocks commonly occur when there is a combination of four conditions: mutual exclusion (resources cannot be simultaneously shared), hold and wait (threads hold resources while waiting for others), no preemption (resources cannot be forcibly taken from threads), and circular wait (a circular chain of threads waiting for resources). Deadlocks can happen when locking mechanisms, synchronization primitives, or resource allocation strategies are not appropriately managed, leading to threads getting stuck indefinitely.
#### What are possible ways to prevent deadlocks from occurring?
Several strategies can help prevent deadlocks:

1. Avoidance: Use a resource allocation strategy that ensures the system will never enter an unsafe state, where a deadlock could occur. This can involve using techniques like resource ordering or resource-request graphs.

2. Prevention: Eliminate one or more of the four conditions (mutual exclusion, hold and wait, no preemption, circular wait) that can lead to deadlocks. For example, by allowing preemption of resources or using timeouts for waiting.

3. Detection and recovery: Implement algorithms to detect and resolve deadlocks if they occur, such as resource scheduling or process termination.

4. Good design practices: Employ proper locking and synchronization techniques, minimize resource contention, and avoid unnecessary resource dependencies to reduce the likelihood of deadlocks.

Applying a combination of these approaches can help mitigate the risk of deadlocks in systems and ensure smoother operation.
#### What does critical section or critical region mean in the context of concurrent programming?
In concurrent programming, a critical section or critical region refers to a portion of code that accesses shared resources or variables that should not be concurrently accessed by multiple threads. It is a section of code where data consistency needs to be maintained to avoid race conditions and ensure the correctness of the program. To prevent concurrent access, synchronization mechanisms such as locks, mutexes, or semaphores are used to enforce mutual exclusion, allowing only one thread at a time to execute the critical section. Properly managing critical sections is crucial for maintaining data integrity and avoiding concurrency-related issues.
