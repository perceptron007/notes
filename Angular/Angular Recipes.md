#### Modules in Angular


#### Dependency Injection

<details> 
	<summary>What is a NodeInjector ? </summary>
    
- A Node Injector is a an Element Level Injector Provided by Angular.
- Typically Element Level Injector is created for each directive.    
- You define a node injector by providing values in providers array of Angular Component.
</details>

<details>
	<summary>What are different dependency Injection decorators and when to use them ?</summary>
    
- @Self: Will restrict dependency injector to look for it's own Node Injector dependencies
- @Optional: Will not cause an error during dependency injection if node injector is not provided with a reference to the Service being used in the Component
- @Host: Restrict the dependency injection process to only look at the immediate parent for a given service instance and stop right there. It will throw an error if a service is not provided either in the component itself or the parent component. 
- @SkipSelf : Will skip it's own node injector
 </details>

<details> 
	<summary>Explain viewProviders ? How is it different from providers  </summary>
    
**viewProviders:** When you provide a service in viewProviders array the instance of those service is scoped to only the Components View.
- Say for example you have a <ng-content> </ng-content>
- Any Components being projected inside <ng-content> will not get reference to the service instance which are declared in viewProviders
    
**providers:** When you provide a service providers array the instance of those service is scoped to All Children of that component.
</details>

What is R3 Injector and where is it provided ?