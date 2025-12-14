The three-tier model is an architectural pattern that helps clearly separate responsibilities within an application. By dividing the application into three layers—the **presentation layer**, the **domain layer**, and the **persistence layer**—we ensure that each layer has only one specific task. This not only makes the code clearer but also easier to maintain and extend.

The idea to build projects in multiple layers is based off the "**Single Responsibility**" principle; which means that each component in your program should be responsible for only one thing. You can view this per [[Methods|method]], [[Class|class]], module, etc. In other words, a piece of code, a class, or a layer in your software **should have only one task and should not be overloaded with multiple responsibilities**. This prevents them from turning into "*God classes*" or containing "*Spaghetti code*".

### Analogy...

Imagine you're a chef in a kitchen. If you were to apply the principle of **Single Responsibility** to kitchen tools, a knife should be meant for cutting, not for prying open a lid. Each tool has its own specific function. If we want to change the way we cut, we need to adjust the knife and not worry about accidentally changing something else (since we only use the knife for cutting).

# The three tiers

### Presentation Tier (User Interface Layer)

For classes responsible for the presentation of data.

**RESPONSIBILITY:**
- interaction with the user

**EXAMPLE APPLICATION OF SINGLE RESPONSIBILITY:**
- shows data to the user, accepts user input

**FORBIDDEN:**
- not allowed to implement business logic and cannot communicate with the database layer

### **Application/Domain Tier (Business Logic Layer)**

For classes responsible for data processing.

**RESPONSIBILITY:**
- core logic of the application

**EXAMPLE APPLICATION OF SINGLE RESPONSIBILITY:**
- contains logic specific to the domain of the application, such as validating data, applying business rules, or coordinating actions

**FORBIDDEN:**
- not allowed to communicate with the user, so this layer cannot print anything on screen!
- not allowed to communicate with database layer, it doesn't want to know *how* or *where* data gets stored

### **Data Management Tier (Database Layer)**

For classes responsible for data storage.

**RESPONSIBILITY:**
- data storage and access to a database (which is somewhere else)

**EXAMPLE APPLICATION OF SINGLE RESPONSIBILITY:**
- retrieving and storing data from said database. its responsibility is to focus on effectively communicating with the database and transforming data between the domain and the database

**FORBIDDEN:**
- not allowed to communicate with user nor implement business logic

### Loose Coupling

Loose coupling is a design principle in which components in a system are made as independent as possible. This means that changes to one component have minimal impact on other components. Notice how [[Encapsulation]] gets used here.

In 3-tier architecture, the communication would look something like this:

**PRESENTATION TIER - DOMAIN TIER**
- the UI layer does not know how the business logic layer or its methods work
- their communication works through clearly defined [[Interfaces]]
- edits to the UI layer does not impact the underlying business logic

**DOMAIN TIER -  DATA TIER**
- the business logic isn't directly dependent on the specific database implementation
- abstractions such as repositories or data access objects (DAO's) get used
- the business logic layer works with models/entities without having to know how these get stored

!!! The **presentation tier** does NOT directly communicate with the **data tier**! All communication between these two tiers always go through the **domain tier** as well!

**example:**
A webshop application has a product overview. 
The **presentation layer** only shows the products and calls a `getProducts()` method. 
The **domain layer** retrieves the data via a Product Repository, without knowing whether it comes from an SQL database, NoSQL database, or web service. If the database is later replaced, the application will continue to work without any changes in the other layers.

### Solution & Project step-by-step guide

**Startup Project:**

You're gonna wanna make your Startup Project a `Console App`, and your 3 layer projects a  `Class Library`.

**Dependencies**:

We've talked about how the UI layer is connected to the domain layer and the domain layer is connected to the data layer. We're gonna have to link these layers together in our project via **dependencies**.

- right-click `Dependencies` under each of your (3) projects
- `Add Project Reference...`
- tick the boxes of the Project(s) you want to link with the one you're currently at

### Public & Internal access modifiers

From now on, you'll need to be careful using the keyword `internal` as an **access modifier**. These have been identical up until now; our projects almost exclusively consisted of one project within one solution. If you use this access modifier instead of `public`, you won't be able to use that [[Class]], [[Properties|property]], or [[Methods|method]] outside the project it's in. 

Therefore, definitely don't set everything to `public` by default; it's still best to keep the **access scope** as small as possible. This means that everything that can be set to `internal` should remain internal; only what needs to be accessible outside the project (or your application layer) should be set to `public`.

### Namespaces

Make sure the namespaces of all classes are correct. A namespace must consist of the name of your solution + the name of your project + any subfolders.

**Persistence**
Make that each repository class implements its respective [[Interfaces|interface]] from the Domain layer. Note that methods to access the data are defined here and in the implemented IRepository interface.

**Domain**
The constructor of the `DomainController` expects an instance of each IRepository interface to be provided through its constructor. These instances are maintained in private (read-only) fields.

**Presentation**
The constructor of the `{app_name}Application` expects an instance of the `DomainController` to be provided through its constructor. This instance is maintained in a private field. 

**Startup**
The Startup class builds our application layer by layer in its Main method: 
the three-layer model is configured:
- In the Persistence layer, each IRepository interface is implemented using a
corresponding repository class that implements the respective interface. Objects are instantiated here.
- The Domain layer is created by instantiating the `DomainController` and applying dependency injection for each IRepository interface in its constructor.
- The Presentation layer is created by creating the `{app_name}Application` class and passing the `DomainController` instance in its constructor.