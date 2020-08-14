## Component Level Architecture

### High Cohesion vs Low Coupling
A feature Module should be highly cohesive and lowly coupled.

**How can we make it highly cohesive ?** 
- Keep the business logic close. 
- Keep the transformation methods close.

**How can we make it low coupled. **
- Keep the state out.
- Compose instead of Inherit


### DRY Principle
- Use Pure Functions
- Extract the commonly used methods. 

### Embrace Types
- Backend doesn't provide you with shape of data your client always needs.
- For example you might have a form implementation which has a Shape X but the backend might be sending you shape Y. 
- Define a separate shape of X and write a mapper (transformation) method to convert Y ↔  X and so on.
- Use this method as a part of pipeline in your observable. 
- Operate you whole UI on the shape X.

API Service 
 - Keep API call
Presenter Service
- Keep logic related to component
Shared Service 
- Keep shared service