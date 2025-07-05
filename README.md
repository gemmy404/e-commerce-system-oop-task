#  E-commerce System - Fawry Rise Journey Challenge

---
A comprehensive Java-based e-commerce system implementing product, cart functionality, and checkout process.

## Features

### Product Management
- View all available products in the inventory.
- Check if a product is **expired**.
- Check **availability** of required quantity before purchase.
- **Update inventory** after product is purchased.

### Cart Operations
- Add items to cart with validation for quantity and availability.
- Track **total weight** of cart items.

### Customer Services
- Check customer's **remaining balance** after calculating total cost.
- Ensure the customer has sufficient funds before checkout.

### Checkout Process
- Finalize the purchase of items in the cart.
- Validate cart contents, and customer balance before completing the transaction.


## Project Structure

---
- `Service`
- `Entity`
- `Util`
- `Custom Exceptions & Global Exception Handler`

## SOLID Principles Implementation Like:

---
##### **Single Responsibility Principle (SRP)**
Each class has one reason to change:
- `Product`: Manages product data only
- `Customer`: Manages customer information only
- `Cart`: Manages cart operations only
- Service classes: Each handles one specific business domain

##### **Interface Segregation Principle (ISP)** 

**Benefits of ISP Implementation:**
-  **Focused Interfaces**: Each service interface focuses on specific functionality
-  **No Forced Dependencies**: Classes implement only required methods
-  **Easy Testing**: Mock specific interfaces without unused methods
-  **Flexible Implementation**: Different implementations can focus on their domain
-  **Maintainability**: Changes to one service don't affect others

##### **Dependency Inversion Principle (DIP)**
- High-level modules depend on abstractions (interfaces)
- Concrete implementations depend on abstractions
- Dependency injection through constructor injection
### Sample Products

---
The system comes with pre-configured sample products:

| Product | Price | Stock | Expirable | Shippable | Weight  |
|---------|-------|-------|-----------|-----------|---------|
| Cheese | 100.0 | 8 | Yes       | Yes | 400.0g  |
| TV | 350.0 | 7 | No        | Yes | 1250.0g |
| Biscuits | 75.0  | 6 | Yes       | Yes | 200.0g  |
| ScratchCard | 50.0  | 5 | No        | No | -       |


## Exception Handling

---
### Custom Exceptions
```java
public class ProductNotFoundException extends RuntimeException
public class InsufficientQuantityException extends RuntimeException
public class ProductExpiredException extends RuntimeException
public class CartEmptyException extends RuntimeException
public class InsufficientBalanceException extends RuntimeException
public class CustomerNotMatchException extends RuntimeException
public class DuplicateProductException extends RuntimeException
```

### Global Exception Handler
```java
public class GlobalExceptionHandler {

    public static void handle(Exception e) {
        Logger logger = Logger.getLogger(GlobalExceptionHandler.class.getName());

        if (e instanceof CustomerNotMatchException) {
            logger.log(Level.SEVERE, e.getMessage());
        } else if (e instanceof ProductNotFoundException) {
            logger.log(Level.WARNING, e.getMessage());
        }                       .
                                .
                                .
                                .
        else {
            logger.log(Level.WARNING, "An unexpected exception occurred", e);
        }
    }
}
```

##  Performance & Quality

---
### Performance Optimizations
- Stream API for efficient collection processing
- Minimal object creation through proper design
- Efficient exception handling

### Development Guidelines
- **Follow SOLID principles** especially ISP in service layer
- **Use meaningful exception types** for error handling

### Future Development & Enhancement
- **Unit Testing Framework**
    - Implement unit testing
    - Use Mockito for mocking dependencies and external services
    - Achieve minimum 80% code coverage for critical business logic

- **Maven Build Management**
    - Structure project with multi-module Maven architecture
    - Implement Maven profiles for different environments (dev, test, prod)


## Finally

---
**I** want to express my sincere gratitude to **Fawry** for this amazing challenge - it was truly an enjoyable and enriching experience.