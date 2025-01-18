# Testing Concepts: Stubs, Fakes, Mocks, Spies, Dummies, Emulators, and Simulators

## Introduction
### What are we covering today?
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

## Stub
### Definition
- **Stub**: A simple implementation that provides predefined responses.

### Characteristics
- Static behavior.
- Used to isolate the unit under test.
- Returns hardcoded data.

### Example
#### Spring Boot:
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

## Faker
### Definition
- **Faker**: A library that generates random, realistic test data.

### Characteristics
- Produces diverse and dynamic data.
- Useful for load testing and edge cases.

### Example
#### Angular:
```typescript
import { faker } from '@faker-js/faker';

const fakeUser = {
    id: faker.datatype.number(),
    name: faker.name.fullName(),
    email: faker.internet.email(),
};
```

---

## Mock
### Definition
- **Mock**: A simulated object that tracks interactions and mimics behavior.

### Characteristics
- Dynamic behavior.
- Validates method calls and arguments.

### Example
#### Odoo:
```python
from unittest.mock import Mock

user_service_mock = Mock()
user_service_mock.get_user_by_id.return_value = {
    'id': 1, 'name': 'John Doe', 'email': 'john@example.com'
}
```

---

## Spy
### Definition
- **Spy**: A wrapper around a real implementation that tracks its interactions.

### Characteristics
- Allows partial mocking.
- Verifies behavior without replacing logic.

### Example
#### Spring Boot:
```java
UserService realUserService = new UserService();
UserService spyUserService = Mockito.spy(realUserService);
spyUserService.getUserById(1L);
verify(spyUserService, times(1)).getUserById(1L);
```

---

## Dummy
### Definition
- **Dummy**: A placeholder object used to satisfy method signatures.

### Characteristics
- Unused in actual logic.
- Exists only to fulfill parameter requirements.

### Example
#### Angular:
```typescript
const dummyUser = { id: null, name: '', email: '' };
service.someMethod(dummyUser);
```

---

## Emulator
### Definition
- **Emulator**: Mimics hardware or software environments for integration/system testing.

### Example
#### Spring Boot:
- Running a PostgreSQL emulator using Docker:
```yaml
services:
  postgres:
    image: postgres:latest
```

---

## Simulator
### Definition
- **Simulator**: Reproduces the behavior of a system without full replication.

### Example
#### Odoo:
```python
class OdooServerSimulator:
    def simulate_request(self, endpoint, payload):
        return {'status': 'success', 'data': {}}
```

---

## Recap
### Key Takeaways
- **Stub**: Static responses for isolation.
- **Faker**: Generates dynamic test data.
- **Mock**: Simulates behavior and tracks interactions.
- **Spy**: Tracks real implementation behavior.
- **Dummy**: Placeholder objects.
- **Emulator**: Mimics systems for testing.
- **Simulator**: Reproduces system behavior abstractly.
