# Angular Vertical Architecture

This project follows a **feature-based vertical architecture**, ensuring a clear **separation of concerns** while maintaining **scalability and testability**. Each feature is self-contained, including its own data access, business logic, shared utilities, UI components, and state management.

## 📂 Folder Structure

```
/src
├── /app
│   ├── /features # Contains all application features
│   │   ├── /feature-name # A single feature module
│   │   │   ├── /client # Handles API communication & external data sources
│   │   │   │   ├── /dto # Data Transfer Objects (DTOs)
│   │   │   │   ├── /repos # Repository implementations
│   │   │   ├── /domain # Business logic & core entities
│   │   │   │   ├── /models # Defines domain entities
│   │   │   │   ├── /repos # Repository interfaces (abstracts data access)
│   │   │   ├── /shared # Feature-specific utilities, services, guards, assets
│   │   │   ├── /view # UI components for this feature
│   │   │   ├── /store # Manages state for this feature
│   │   │   ├── feature.module.ts # Feature module definition
│   │   │
│   │   ├── /another-feature # Another feature with the same structure
│
│   ├── app.component.ts # Root Angular component
│   ├── app.module.ts # Main application module
│
├── main.ts # Bootstrap Angular application
├── index.html # Root HTML file
```

## 🏗️ Layer Descriptions

### 1️⃣ **Client Layer (Infrastructure Boundary)**
- Handles API requests and external data sources.
- Uses **DTOs** to structure data exchange with the backend.
- Abstracts data retrieval, ensuring backend modifications don't affect other layers.

### 2️⃣ **Domain Layer (Core Business Logic)**
- Contains **business rules and domain models**.
- Uses **repository interfaces** to abstract data access.
- Ensures the business logic is independent of API or UI concerns.

### 3️⃣ **Shared Layer (Feature-Specific Utilities)**
- Contains **guards, interceptors, services, and assets** specific to this feature.
- Prevents unnecessary global dependencies by keeping utilities within the feature scope.

### 4️⃣ **Presentation Layer (View/UI)**
- Responsible for **rendering UI components** and handling user interactions.
- Uses **state management (store)** to synchronize data between UI and business logic.

### 5️⃣ **Store Layer (State Management)**
- Manages application state specific to this feature.
- Uses **NgRx, Signals, or BehaviorSubjects** for reactive data handling.

## 🎯 Key Benefits of This Architecture
✅ **Scalability** – Features can be developed, updated, and tested independently.  
✅ **Maintainability** – Clear separation of concerns makes debugging easier.  
✅ **Testability** – Independent layers enable unit testing without dependencies.  
✅ **Flexibility** – Backend modifications won't impact business logic or UI.  

---

## 📌 Example Analogy: Online Bakery System

- **Client Layer** 🛒: Takes orders and forwards them to the kitchen.  
- **Domain Layer** 🍰: The kitchen follows recipes to prepare cakes.  
- **Shared Layer** 📦: Stores timers, ingredient lists, and baking utilities.  
- **Presentation Layer** 🏪: Displays the cakes in the shop for customers.  
- **Store Layer** 🏷️: Tracks stock levels and orders in real-time.  

---

## 🚀 Getting Started

1️⃣ **Install dependencies**:  
   ```bash
   npm install
   ```  

2️⃣ **Run the project**:  
   ```bash
   ng serve
   ```  
