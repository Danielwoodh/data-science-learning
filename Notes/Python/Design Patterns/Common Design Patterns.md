---
tags:
  - CodeQuality
  - OOP
  - Python
  - SoftwareDesignPatterns
---
# Common and Best Python Software Design Patterns
<details> <summary>🔍 Summary</summary>
### Summary
This note covers common and best software design patterns in Python, essential for efficient, maintainable, and scalable code. Design patterns provide standardized solutions to frequent software design challenges. Understanding these patterns empowers Python developers to improve code quality and address architectural problems effectively.  </details> 

---
## 🛠️ Singleton Pattern
### Purpose
Ensures a class has only one instance and provides a global point of access to it.
### Use Cases
Logging, database connections, file managers.

<summary> 📄 Code Example </summary>

```python
class Singleton:
	_instance = None
	
	@classmethod
	def getInstance(cls):
		if cls._instance is None:
			cls._instance = Singleton()
		return cls._instance

# Usage
singleton = Singleton.getInstance()
```

---

## 🧱 Factory Method Pattern

### Purpose

Allows a class to defer instantiation to subclasses.

### Use Cases

Frameworks where library code needs to create objects.

<summary>📄 Code Example</summary>

```python
class Creator:
	def factory_method(self):
		raise NotImplementedError("Factory Method not implemented")
		
class ConcreteCreator1(Creator):
	def factory_method(self):
		return ConcreteProduct1()
		
class ConcreteCreator2(Creator):
	def factory_method(self):
		return ConcreteProduct2()
		
# Usage
creator = ConcreteCreator1()
product = creator.factory_method()
```


---

## 🔍 Observer Pattern

### Purpose

Lets one object (the "subject") notify a list of objects (the "observers") about state changes.

### Use Cases

Event handling systems, model-view-controller (MVC) architectures.

<summary>📄 Code Example</summary>

```python
class Subject:
	def __init__(self):         
		self._observers = []      
	
	def attach(self, observer):         
		self._observers.append(observer)      
	
	def notify(self):         
		for observer in self._observers:             
			observer.update(self)  
			
class Observer:     
	def update(self, subject):         
		pass  
		
# Usage 
subject = Subject() 
observer = Observer() 
subject.attach(observer) 
subject.notify()
```

---

## 📦 Composite Pattern

### Purpose

Composes objects into tree structures to represent part-whole hierarchies.

### Use Cases

User interface components, file and directory systems.

<summary>📄 Code Example</summary>

```python
class Component:     
	def operation(self):         
		pass  
		
class Leaf(Component):     
	def operation(self):         
		return "Leaf"  
		
class Composite(Component):     
	def __init__(self):         
		self._children = []      
		
	def operation(self):         
		results = []         
		for child in self._children:             
			results.append(child.operation())         
		return "+".join(results)  
		
# Usage 
leaf = Leaf() 
composite = Composite() 
composite._children.append(leaf) 
print(composite.operation())
```

---
## 📝 Strategy Pattern

### Purpose

Enables selecting an algorithm’s implementation at runtime.

### Use Cases

Sorting algorithms, route calculation.

<summary>📄 Code Example</summary>

```python
class Strategy:     
	def execute(self):         
		pass  
		
class ConcreteStrategyA(Strategy):     
	def execute(self):         
		return "Strategy A"  
		
class ConcreteStrategyB(Strategy):     
	def execute(self):         
		return "Strategy B"  
		
class Context:     
	def __init__(self, strategy):         
		self._strategy = strategy      
	
	def execute_strategy(self):         
		return self._strategy.execute()  
		
# Usage 
strategy = ConcreteStrategyA() 
context = Context(strategy) 
result = context.execute_strategy()
```

---
## 🔌 Adapter Pattern

### Purpose

Allows incompatible interfaces to work together.

### Use Cases

Integrating new components with existing class hierarchies.

<summary>📄 Code Example</summary>

```python
class Target:     
	def request(self):         
		return "Target's default behavior"  
	
class Adaptee:     
	def specific_request(self):         
		return ".eetpadA eht fo roivaheb laiceps"  
		
class Adapter(Target):     
	def __init__(self, adaptee):         
		self._adaptee = adaptee      
		
	def request(self):         
		return self._adaptee.specific_request()[::-1] 

# Usage 
adaptee = Adaptee() 
adapter = Adapter(adaptee) 
print(adapter.request())
```

---

## 📚 Best Practices

- **Right Pattern for Right Problem**: Select a pattern that aligns with the specific problem and context.
- **Avoid Overuse**: Inappropriate use of patterns can complicate code unnecessarily.
- **Understand Before Implementing**: Thoroughly comprehend a pattern before implementing it to ensure its suitability.

---

_Note: These examples provide a basic understanding of design patterns in Python. For complex solutions, deeper exploration and understanding are recommended._