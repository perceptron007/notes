## Best Practices

### High Level Design
In high level design we are going to talk about architecture of a Monorepo application. 
- Talking about architecture is hard, the fundamental problem when architecture is discussed is that you need to cross a given threshold in order to really see the benefits of architecture otherwise everything seems overkill. 
- Matrices for a Good Architecture
    - Maintainability
    - Readability
    - Code Sharing
    - Extendability
    - Ease of access to Onboard new developers to the projects
    - Ability to swap some pieces of the application with different ( technology, library )

#### Architecture of The Project
- Generally we are concerned mostly about two parts of the project (Apps and Libs)
- In Angular our apps are mostly a collection of modules rather than a collection of Components
- 

#### Architecture at Module Level 
Modules are the basic building blocks of Angular application. 
But that's not it, you have to understand that each modules need a different behavior depending on the use case. 
And we can summarize different type of modules into the following category.
- App Module
    - Role: Initialise application
    - Signature: Bootstrap Component
    - Deps: RoutingModule, Core Module
    - Exports: None
- Routing Module
    - Role: Manage Module Routing
    - Signature: No Declaration, Only Guard Services
    - Deps: Routing Module
    - Exports: Routing Module
- Feature Module
    - Role: Business Logic and UI
    - Signature: No Exports
    - Deps: Shared Module, Routing Module
    - Exports: None
- Shared Module
	- Role: Reusable, Shared UI Widgets 
    - Signature: Declaration
    - Deps: Common Module
    - Exports: Declarations
- Core Module
    - Role: Contains Shared Application Logic
    - Signature: Providers Only, No Declaration
    - Deps: None
    - Exports: None

##### Solid Principles For Modules
S : Single Responsibility Principle (A modules should have only one reason to change)
O: A module should be open for extension but closed for modification.


 

### Low Level Structure
#### Architecture at Component Level
- Container / Presenter / Presentation Component

#### What do we have in our components ?
- We have ngrx dispatch and action calls. 
- We have FormGroup create and Data Transformation method calls. 
    - We transfer data from shape of DTO to FormGroup while recieving data.
    - We transfe data from shape of FormGroup to DTO while sending the data.
- We have conditional presentation logic. (Can be extracted to Presenter Service) 