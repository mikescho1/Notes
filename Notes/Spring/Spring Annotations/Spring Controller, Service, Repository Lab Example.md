###### Spring Controller, Service, Repository Lab Example:  

###  Controller Annotations:  
#### @RestController:
A specialized version of the controller which is a convenience annotation that does nothing more than add the @Controller and @ResponseBody annotations above the class declaration.  

By annotating the controller class with @RestController annotation, you no longer need to add @ResponseBody to all the request mapping methods. The @ResponseBody annotation is active by default. 

When set at a class level, all methods annotated with *@RequestMapping* are considered as annotated with *@ResponseBody* as well/

#### @GetMapping, @PostMapping, @PutMapping, @PatchMapping, & @DeleteMapping:
These annotations are shortcuts for *@RequestMapping(method = RequestMethod.GET)* and *@RequestMapping(method = RequestMethod.POST)*  

When combined with the above-mentioned annotations, these methods will be treated as if they were annotated with *@ResponseBody* as well.  


These annotations all take in an optional parameter to specify the path; e.g. @GetMapping("/users").  

#### @PathVariable:  
Values provided as path variables can be captured by addinga @PathVariable parameter to the method.  
![](Images/2019-12-06-12-22-02.png)  

By default, the parameter name must match the variable name in the path; e.g a path of "/users/{id}" must be accompanied by a @PathVariable named id. However, this can be overridden if desired.  

#### @RequestParam:  
Similarly to path parameters, query string parameters can be captured with @RequestParam.  
![](Images/2019-12-06-12-24-51.png)  

The name of the variable must match the name of the query string parameter, unless overridden.  



