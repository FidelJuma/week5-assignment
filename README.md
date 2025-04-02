# week5-assignment
Assignment 1: Design Your Own Class! 🏗️
Create a class representing anything you like (a Smartphone, Book, or even a Superhero!).
Add attributes and methods to bring the class to life!
Use constructors to initialize each object with unique values.
Add an inheritance layer to explore polymorphism or encapsulation.Let’s design a **Smartphone** class as an example! I will add attributes such as brand, model, and battery life, and then implement methods to interact with the object. I’ll also use inheritance to create a more specific class, like a **SmartphoneWithCamera**, to demonstrate polymorphism and encapsulation.

### Here's the code for the assignment:

```python
# Base class: Smartphone
class Smartphone:
    def __init__(self, brand, model, battery_life):
        self.brand = brand  # Brand of the smartphone
        self.model = model  # Model of the smartphone
        self.battery_life = battery_life  # Battery life in hours
        self._is_on = False  # Private attribute to check if the phone is on

    # Method to turn the phone on
    def turn_on(self):
        if not self._is_on:
            self._is_on = True
            print(f"{self.model} is now ON.")
        else:
            print(f"{self.model} is already ON.")
    
    # Method to turn the phone off
    def turn_off(self):
        if self._is_on:
            self._is_on = False
            print(f"{self.model} is now OFF.")
        else:
            print(f"{self.model} is already OFF.")
    
    # Method to check battery life
    def check_battery(self):
        print(f"{self.model} has {self.battery_life} hours of battery left.")
    
    # Method to display smartphone details
    def display_details(self):
        print(f"Smartphone Details: \nBrand: {self.brand}\nModel: {self.model}\nBattery Life: {self.battery_life} hours")

# Inherited class: SmartphoneWithCamera
class SmartphoneWithCamera(Smartphone):
    def __init__(self, brand, model, battery_life, camera_megapixels):
        super().__init__(brand, model, battery_life)  # Inheriting from Smartphone
        self.camera_megapixels = camera_megapixels  # Additional attribute for camera

    # Overridden method to display details (polymorphism)
    def display_details(self):
        super().display_details()
        print(f"Camera: {self.camera_megapixels} MP")
    
    # New method to capture a photo
    def take_photo(self):
        print(f"Taking a photo with the {self.camera_megapixels} MP camera...")

# Example usage
# Creating an instance of Smartphone
phone1 = Smartphone("Apple", "iPhone 13", 20)
phone1.turn_on()
phone1.check_battery()
phone1.display_details()

# Creating an instance of SmartphoneWithCamera
phone2 = SmartphoneWithCamera("Samsung", "Galaxy S21", 18, 108)
phone2.turn_on()
phone2.check_battery()
phone2.display_details()
phone2.take_photo()
```

### Explanation:

1. **Smartphone Class (Base class)**:
   - **Attributes**: `brand`, `model`, and `battery_life` to store basic information about the smartphone.
   - **Methods**: 
     - `turn_on()` and `turn_off()` control the power state of the phone.
     - `check_battery()` shows the remaining battery life.
     - `display_details()` prints all the phone's information.

2. **SmartphoneWithCamera Class (Inherited class)**:
   - This class inherits from `Smartphone` and adds a new attribute: `camera_megapixels` to represent the phone's camera quality.
   - The `display_details()` method is **overridden** to include camera information (demonstrating **polymorphism**).
   - A new method `take_photo()` simulates the action of taking a photo.

### Output Example:

```text
iPhone 13 is now ON.
iPhone 13 has 20 hours of battery left.
Smartphone Details: 
Brand: Apple
Model: iPhone 13
Battery Life: 20 hours

Galaxy S21 is now ON.
Galaxy S21 has 18 hours of battery left.
Smartphone Details: 
Brand: Samsung
Model: Galaxy S21
Battery Life: 18 hours
Camera: 108 MP
Taking a photo with the 108 MP camera...
```

### Key Concepts:
- **Encapsulation**: The `_is_on` attribute is private (indicated by the underscore) and cannot be directly accessed outside the class. This protects the internal state.
- **Inheritance**: `SmartphoneWithCamera` inherits from `Smartphone`, allowing it to reuse code from the parent class and add additional functionality.
- **Polymorphism**: The `display_details()` method is overridden in the child class to include additional information specific to that class (camera).

Let me know if you’d like any further modifications or explanations!Activity 2: Polymorphism Challenge! 🎭

Create a program that includes animals or vehicles with the same action (like move()). However, make each class define move() differently (for example, Car.move() prints "Driving" 🚗, while Plane.move() prints "Flying" ✈️).Let's create a **Polymorphism Challenge** using animals or vehicles, where each class defines the `move()` method differently, showcasing how polymorphism works in Python.

### Code Example: **Vehicles with Polymorphism**

We'll define three classes: `Car`, `Plane`, and `Boat`, each with its own implementation of the `move()` method.

```python
# Base class: Vehicle
class Vehicle:
    def move(self):
        raise NotImplementedError("Subclass must implement abstract method")

# Car class (inherits from Vehicle)
class Car(Vehicle):
    def move(self):
        print("Driving 🚗")

# Plane class (inherits from Vehicle)
class Plane(Vehicle):
    def move(self):
        print("Flying ✈️")

# Boat class (inherits from Vehicle)
class Boat(Vehicle):
    def move(self):
        print("Sailing ⛵")

# Function to demonstrate polymorphism
def demonstrate_movement(vehicle):
    vehicle.move()

# Example usage
car = Car()
plane = Plane()
boat = Boat()

# Polymorphism in action: Same method name (move), but different behavior
demonstrate_movement(car)   # Outputs: Driving 🚗
demonstrate_movement(plane)  # Outputs: Flying ✈️
demonstrate_movement(boat)   # Outputs: Sailing ⛵
```

### Explanation:

1. **Base Class (Vehicle)**:
   - The `Vehicle` class defines a method `move()` which raises a `NotImplementedError`. This is done to ensure that subclasses must provide their own implementation of the `move()` method (i.e., it acts as an abstract method).
   
2. **Car, Plane, and Boat Classes**:
   - Each of these classes inherits from `Vehicle` and provides its own specific implementation of the `move()` method:
     - `Car.move()` prints "Driving 🚗".
     - `Plane.move()` prints "Flying ✈️".
     - `Boat.move()` prints "Sailing ⛵".

3. **Polymorphism**:
   - The `demonstrate_movement()` function accepts any object of type `Vehicle` and calls the `move()` method on it. Even though the method name (`move()`) is the same, it behaves differently depending on which class the object belongs to. This is **polymorphism** in action.

### Output:
```text
Driving 🚗
Flying ✈️
Sailing ⛵
```

### Key Concepts:
- **Polymorphism**: Different classes (`Car`, `Plane`, `Boat`) have a method with the same name (`move`), but the behavior of that method is different in each class.
- **Inheritance**: `Car`, `Plane`, and `Boat` inherit from the base class `Vehicle` but provide their own specific implementations of the `move()` method.
- **Method Overriding**: Each subclass overrides the `move()` method from the base class to provide its own behavior.

This demonstrates polymorphism because we are able to call the same method (`move()`) on objects of different classes, and each class responds with its unique implementation.

Let me know if you'd like more examples or further explanations!




