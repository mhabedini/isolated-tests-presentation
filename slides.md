---
# You can also start simply with 'default'
theme: bricks

# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
layout: cover
title: SOLID Principles in TypeScript
description: An interactive tutorial on applying SOLID principles with real-world examples and refactoring techniques in TypeScript
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# take snapshot for each slide in the overview
overviewSnapshots: true
---

# Testing Concepts: Stubs, Fakes, Mocks, Spies, Dummies, Emulators, and Simulators

---

# Slide 1: Introduction
## What are we covering today?
- Understanding key testing concepts:
  - Stub
  - Faker
  - Mock
  - Spy
  - Dummy
  - Emulator
  - Simulator
- Examples in:
  - Spring Boot
  - Angular
  - Odoo

---

# Slide 2: Stub
## Definition
- **Stub**: A simple implementation that provides predefined responses.

## Characteristics
- Static behavior.
- Used to isolate the unit under test.
- Returns hardcoded data.

## Example
### Spring Boot:
```java
@Service
public class UserServiceStub implements UserService {
    @Override
    public User getUserById(Long id) {
        return new User(id, "John Doe", "john@example.com");
    }
}
```

---

# Slide 3: Faker
## Definition
- **Faker**: A library that generates random, realistic test data.

## Characteristics
- Produces diverse and dynamic data.
- Useful for load testing and edge cases.

## Example
### Angular:
```typescript
import { faker } from '@faker-js/faker';

const fakeUser = {
    id: faker.datatype.number(),
    name: faker.name.fullName(),
    email: faker.internet.email(),
};
```

---

# Slide 4: Mock
## Definition
- **Mock**: A simulated object that tracks interactions and mimics behavior.

## Characteristics
- Dynamic behavior.
- Validates method calls and arguments.

## Example
### Odoo:
```python
from unittest.mock import Mock

user_service_mock = Mock()
user_service_mock.get_user_by_id.return_value = {
    'id': 1, 'name': 'John Doe', 'email': 'john@example.com'
}
```

---

# Slide 5: Spy
## Definition
- **Spy**: A wrapper around a real implementation that tracks its interactions.

## Characteristics
- Allows partial mocking.
- Verifies behavior without replacing logic.

## Example
### Spring Boot:
```java
UserService realUserService = new UserService();
UserService spyUserService = Mockito.spy(realUserService);
spyUserService.getUserById(1L);
verify(spyUserService, times(1)).getUserById(1L);
```

---

# Slide 6: Dummy
## Definition
- **Dummy**: A placeholder object used to satisfy method signatures.

## Characteristics
- Unused in actual logic.
- Exists only to fulfill parameter requirements.

## Example
### Angular:
```typescript
const dummyUser = { id: null, name: '', email: '' };
service.someMethod(dummyUser);
```

---

# Slide 7: Emulator
## Definition
- **Emulator**: Mimics hardware or software environments for integration/system testing.

## Example
### Spring Boot:
- Running a PostgreSQL emulator using Docker:
```yaml
services:
  postgres:
    image: postgres:latest
```

---

# Slide 8: Simulator
## Definition
- **Simulator**: Reproduces the behavior of a system without full replication.

## Example
### Odoo:
```python
class OdooServerSimulator:
    def simulate_request(self, endpoint, payload):
        return {'status': 'success', 'data': {}}
```

---

# Slide 9: Recap
## Key Takeaways
- **Stub**: Static responses for isolation.
- **Faker**: Generates dynamic test data.
- **Mock**: Simulates behavior and tracks interactions.
- **Spy**: Tracks real implementation behavior.
- **Dummy**: Placeholder objects.
- **Emulator**: Mimics systems for testing.
- **Simulator**: Reproduces system behavior abstractly.

---

# Slide 10: Questions?
## Let’s Discuss!
- Any doubts?
- Real-world use cases?

---
