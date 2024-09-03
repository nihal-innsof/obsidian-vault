---
id: Terminologies
aliases: []
tags: []
---

## Beans

Beans are the objects of classes that are managed by spring. The `@Component` annotation is the most common method of defining beans.

## Autowiring

The process of identifying the dependencies of a bean, looking for a match and populating the dependencies is called as autowiring. The `@Autowired` annotation is used to tell spring to find and inject collaborating beans into another. If there are two beans of same type, then spring will throw an error. In the following scenario, two beans of type `Operator` are detected by spring.

```java
@Component
class Arithmetic() {
	@Autowired
	private Operator operator;
	// ...
}

@Component
class Addition implements Operator {

}

@Component
class Subtraction implements Operator {

}
```

Spring will not know which bean to inject into `Arithmetic` bean unless the developer explicitly specifies it.

## Dependency Injection

It is the process by which spring identifies the beans needed for a specific bean to function and injects them as a dependency into it. Spring can perform dependency injection using the constructor or by using a setter method.

## Inversion of Control

Traditionally, the classes which needs the dependency creates the instance of the dependency. Therefore, the class decides when and how to create the dependency. For example, Engine class is a dependency of Vehicle class, which creates its object:

```java
class Vehicle{

    private Engine engine = new Engine();
    //...
}
```

Spring take the responsibility from the class and creates the object itself. The developer simply mentions the dependency and the framework take cares of the rest.

```java
class Vehicle{

    private Engine engine;
    //...
}
```

Thus, control moves from the component that needs the dependency to the framework. The framework takes up the responsibility of finding the dependency of a component, ensuring their availability and injecting them into the component. This process is called as inversion of control.

## IoC Container

IoC container is the framework which provides the inversion of control functionality.

The IoC container manages the beans. For the above example, it creates the instance of the `Engine` class, then creates an instance of `Vehicle` class, and then injects the `Engine` object as a dependency into the `Vehicle` Object.

```java
class Vehicle {
    private Engine engine;
    //...
}
```

IoC Container is a generic term. It is not framework specific. Spring offers two implementation of the IoC container.

- Bean factory
- Application context:
  Both of them are interfaces that have different implementations available. Application context is the typical IoC container in the context of Spring. Spring recommends using it unless there is a memory concern, like in a mobile device. If available memory is low, bean factory should be used.

## Bean factory

The basic version of the Spring IoC container is bean factory. It is the legacy IoC container and provides basic management for beans and wiring of dependencies. In Spring, bean factory still exists to provide backward compatibility.

## Application Context

Application context adds more features to the bean factory that are typically needed by an enterprise application. It is the most important part of the Spring framework. All the core logic of Spring happens here. It includes basic management of beans and wiring of dependencies as provided by the bean factory. Additional features in application context include Spring AOP features, internationalization, web application context, etc.
