# What is LINQ?

LINQ stands for **Language Integrated Query**. It allows you to query data, expressed in simple ways (strings). It allows you to treat in-memory data and databases as a collection, and perform queries on it. (It looks a lot like SQL too).

**When to use?** -> All the time. Ever need to sort a list? LINQ. Ever need to filter a list? LINQ. Ever need to add up all the values in a list? LINQ.

### Imperative vs declarative programming

Most of the coding we've done so far has been **imperative**. What does this mean? We basically kept imperatively telling our computed "do this!" or "do that!": like, "create a `for` loop that does exactly this and that!".

LINQ, however, is **declarative**. We instead just describe **what** we want, but we don't care nor have to tell our computer **how** exactly it has to do what we want. We're not giving a formula or a series of instructions.

### Analogy...

LINQ is like an **assembly line**. The assembly line starts with the raw materials that need to be processed. This is our "**collection**" in LINQ; the **original data source** on which we want to perform our operations.

The assembly line has multiple stops/way stations where it needs to do specific tasks. In LINQ, these 'stops' are our **LINQ-methods**, such as `Where`, `Select`, `OrderBy`, and many more.

At the end of the assembly line, there is the final stop. In LINQ, this final stop are the **LINQ-methods** such as `ToList`, `ToArray`, or other methods to retrieve the result of our query operations.

### The assembly line in code...

***THE SOURCE***
```csharp
List<int> rawMaterials = new List<int> { 5, 12, 8, 15, 20 };
```


***WAY STATIONS***
```csharp
var result = rawMaterials
			.Where(item => item > 10) // Only keep items larger than 10
			.Select(item => item * 2) // Double every item
			.OrderBy(item => item); // Sort the items in ascending order
```


***FINAL STOP***
```csharp
List<int> finishedProducts = result.ToList();
```


### Order of Operations

1. Source =>
2. Filter (`Where`) =>
3. Projection (`Select`) =>
4. Sorting (`OrderBy`) =>
5. Grouping (`GroupBy`) =>
6. Joining (`Join`) =>
7. Aggregation (`Sum Count`) =>

### Important query operators

**WHERE** (filtering)
- is used to filter elements based on a condition/expression (can be either a [[Lambda expressions|Lambda expression]] or [[Delegates|Func delegate]])

ex.
```csharp
List<int> numbers = new List<int> { 5, 12, 8, 15, 20 };
var result = numbers.Where(number => number > 10); // Defines the requirement the number needs to meet in order to be kept
```

--- 

**DISTINCT** (filtering)
- can be used to remove duplicate items from a list

ex.
```csharp
List<int> numbers = new List<int> { 1, 2, 2, 3, 4, 4, 5, 6, 6, 7 };
var uniqueNumbers = numbers.Distinct();
```

---

**SELECT** (projection)
- `Select` is for transforming one kind of collection into another. If i have a collection of `ints`, and i want a collection of `strings`, it can be written like this:

ex.
```csharp
var stringCollection = intCollection.Select(i => i.ToString());
```

- another example: we have a list with names and want to make a new list with the length of every name

ex.
```csharp
List<string> names = new List<string> { "Aerith", "Tifa", "Cloud" };
var result = names.Select(naam => naam.Length);
```


---

**ORDER BY** (sorting)
- is used to sort items based on a certain condition

ex.
```csharp
List<Product> products = new List<Product>
{
	new Product { Name = "Laptop", Price = 800 },
	new Product { Name = "Phone", Price = 500 },
	new Product { Name = "Tablet", Price = 300 }
};

var result = products.OrderBy(product => product.Price); // Sorts the items in ascending order based on their price.
```



---

**THEN BY** (sorting)
- is used in the same way as order by, except it comes after `OrderBy`

ex.
```csharp
var result = products
	.OrderBy(product => product.Category) //First sort on category
	.ThenBy(product => product.Price); // Then on price
```


---
**GROUP BY** (grouping)
- is used to group items based on a certain condition

ex.
```csharp
List<Product> employees = new List<Employee>
{
	new Employee { Name = "Sephiroth", Department = "SOLDIER" },
	new Employee { Name = "Zack", Department = "SOLDIER" },
	new Employee { Name = "Reno", Department = "Public Safety" }
};

var groups = employees.GroupBy(employee => employee.Department);
```


### Chaining

Now you can do something that's called **chaining** query operators.
Think back on **MySQL** queries (which is very similar to **Query Syntax** in LINQ). It'd look something like this:

```sql
IEnumerable<int> scoreQuery =
	from score in scores
	where score > 80
	orderby score descending
	select score;
```


In LINQ's **Method Syntax**, we can chain these all together:

```csharp
var scoreQuesry = scores.Where(s => s > 80).OrderByDescending(s => s);
```


- You might wonder where the `select` is from the **Query Syntax**. Well, in **Method Syntax**, `select` is actually implied! No need to write it!

## Cheatsheet

LINQ (Language Integrated Query) allows you to query collections (like Lists, Arrays) or databases (via Entity Framework) directly within C# code. It provides a consistent, readable way to filter, order, and shape data.

To use LINQ, you must include the namespace at the top of your file:

C#

```csharp
using System.Linq;
```

Here is a breakdown of how to use it, followed by the comprehensive cheatsheet you requested.

---

### 1. The Two Styles of LINQ

There are two ways to write LINQ. Most developers use **Method Syntax**, but **Query Syntax** is useful for complex joins.

#### A. Method Syntax (Fluent API)

This uses lambda expressions and method chaining. It is generally preferred for most standard operations.

C#

```csharp
var numbers = new List<int> { 1, 2, 3, 4, 5 };

// "Give me numbers greater than 2"
var result = numbers.Where(n => n > 2).ToList();
```

#### B. Query Syntax (SQL-like)

This looks like SQL but works on C# objects. It always starts with `from` and ends with `select` or `group`.

C#

```csharp
var result = from n in numbers
             where n > 2
             select n;
```

---

### 2. The LINQ Cheatsheet

Here are the most common operations grouped by category.

#### 🔍 Filtering & Projection

|**Operation**|**Method Syntax Example**|**Description**|
|---|---|---|
|**Where**|`.Where(x => x.Age > 18)`|Filters elements based on a condition.|
|**Select**|`.Select(x => x.Name)`|Projects/transforms data (e.g., gets just the names).|
|**SelectMany**|`.SelectMany(x => x.Orders)`|Flattens a list of lists (e.g., get all orders from all users).|
|**Distinct**|`.Select(x => x.Name).Distinct()`|Removes duplicate values.|
|**OfType**|`.OfType<string>()`|Filters a collection to only include items of a specific type.|

#### 🔢 Sorting

|**Operation**|**Method Syntax Example**|**Description**|
|---|---|---|
|**OrderBy**|`.OrderBy(x => x.Name)`|Sorts in ascending order.|
|**OrderByDescending**|`.OrderByDescending(x => x.Age)`|Sorts in descending order.|
|**ThenBy**|`.OrderBy(x => x.Name).ThenBy(x => x.Age)`|Secondary sort (must follow an OrderBy).|
|**Reverse**|`.Reverse()`|Reverses the order of the list.|

#### 📊 Aggregation (Math)

|**Operation**|**Method Syntax Example**|**Description**|
|---|---|---|
|**Count**|`.Count()` or `.Count(x => x.Active)`|Returns the number of items.|
|**Sum**|`.Sum(x => x.Salary)`|Adds up numerical values.|
|**Average**|`.Average(x => x.Rating)`|Calculates the average.|
|**Min / Max**|`.Min(x => x.Price)`|Finds the lowest or highest value.|

#### 🎯 Element Selection (Getting specific items)

_Note: Methods ending in `OrDefault` return `null` (or default value) if not found, preventing crashes._

|**Operation**|**Method Syntax Example**|**Description**|
|---|---|---|
|**First**|`.First(x => x.ID == 1)`|Gets the first match. Throws exception if none found.|
|**FirstOrDefault**|`.FirstOrDefault(x => x.ID == 1)`|Gets first match or returns `null`/default. **(Safer)**|
|**Single**|`.Single(x => x.ID == 1)`|Expects **exactly one** match. Throws if 0 or >1 found.|
|**SingleOrDefault**|`.SingleOrDefault(x => x.ID == 1)`|Expects 0 or 1 match. Throws if >1 found.|
|**Last**|`.Last()`|Gets the last element.|

#### ✅ Quantifiers (True/False Checks)

|**Operation**|**Method Syntax Example**|**Description**|
|---|---|---|
|**Any**|`.Any(x => x.Failed)`|Returns `true` if **at least one** element matches.|
|**All**|`.All(x => x.Passed)`|Returns `true` if **every** element matches.|
|**Contains**|`.Contains(5)`|Returns `true` if the collection contains the specific object.|

#### ✂️ Partitioning (Pagination)

|**Operation**|**Method Syntax Example**|**Description**|
|---|---|---|
|**Take**|`.Take(10)`|Selects the first 10 items.|
|**Skip**|`.Skip(10)`|Skips the first 10 items (often used with Take for paging).|
|**TakeWhile**|`.TakeWhile(x => x.Active)`|Takes items until the condition becomes false.|

#### 📦 Grouping & Joining

|**Operation**|**Method Syntax Example**|**Description**|
|---|---|---|
|**GroupBy**|`.GroupBy(x => x.Department)`|Groups data by a key. Returns a collection of groups.|
|**Join**|`.Join(target, x=>x.Id, y=>y.Id, (x,y) => new {...})`|Inner join two collections based on matching keys.|

---

### 3. Vital Concept: Deferred vs. Immediate Execution

This is the most common "gotcha" in LINQ.

Deferred Execution (Lazy):

Most LINQ operators (like Where, Select) do not actually run the query when you write them. They only construct the query. The code runs only when you iterate over the variable.

C#

```csharp
var query = numbers.Where(n => n > 5); // Query defined, NOT executed yet
// ... later in code ...
foreach (var n in query) { ... } // NOW it executes
```

Immediate Execution:

Methods that return a single value or a concrete collection execute immediately.

C#

```csharp
var count = numbers.Count(); // Executes immediately
var list = numbers.ToList(); // Executes immediately
var array = numbers.ToArray(); // Executes immediately
```

> **Pro Tip:** If you are debugging and want to see your results, add `.ToList()` to the end of your query to force it to run immediately.

---

### 4. Real-World Example

Here is how you might combine these in a real application (e.g., getting a list of email addresses for active users, sorted by name):

C#

```csharp
List<User> users = GetUsers();

var emailList = users
    .Where(u => u.IsActive && u.Email != null)  // 1. Filter
    .OrderBy(u => u.LastName)                   // 2. Sort
    .Select(u => u.Email)                       // 3. Project (flatten to just strings)
    .ToList();                                  // 4. Execute and store in List
```
