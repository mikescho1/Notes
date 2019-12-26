# Angular 4 Java Developers Task Application Notes:  
<br>  

## Setting Up H2 Console For Browser Access:  
1. ### In applications.property file, enter:   
   * spring.datasource.name=tasks
   * spring.jpa.show-sql=true
   * spring.h2.console.enabled=true
   * spring.h2.console.path=/h2-console  

2. ### Run Server:    
   * Go to browser and enter localhost:8080/h2-console  

3. ### Change JDBC URL:    
   * In window displayed in browser, change JDBC URL to jdbc:h2:mem:tasks (plural version of entity name) 

<br>   


___  
## Angular CLI (Command Line Interface):  
1. ### Install Angular CLI  
   * Enter "npm install -g @angular/cli" in terminal.  
2. ### Enter "ng new frontend" to create Angular project folders and files.  
  
## Create Angular Components:  
The main app.component files that are automatically installed when the Angular project is created are used for sections like navigation bar, footer, side bars, etc.  

We will create nested components inside the apps folder to hold our task application.  

1. ### Create tasks component:  
     * cd into the 'app folder'.
     * enter 'ng generate component tasks' or shorthand version 'ng g c tasks'  
2. ### Create tasks-add component subfolder inside tasks:  
     * enter 'ng g c /tasks/ tasks-add'.  
3. ### Create tasks-list component subfolder inside tasks:  
     * enter 'ng g c /tasks/ tasks-list'.  

![](Images/2019-12-26-09-56-52.png)  
<br>    
![](Images/2019-12-26-09-49-07.png)  

## Add Bootstrap To Project:  
1. ### Install Bootstrap:  
   * cd into frontend folder.
   * enter 'npm install --save bootstrap' to save it locally.  
2. ### Tell Angular that we want to use bootstrap:  
   * Got to angular.json folder.  
   * In "styles" array, reference the new bootstrap file.  
     * /node_modules/bootstrap/dist/css/bootstrap.min.css"  
![](Images/2019-12-26-10-04-44.png)  
<br>  

## Buildout Components:  
1. ### Create container in main app.component.html to hold tasks.component:  
![](Images/2019-12-26-10-07-39.png)  
<br>  

2. ### Create containers in tasks.component to hold add-tasks and list-tasks component:  

![](2019-12-26-10-11-01.png)  

3. ### Add starter input.form-control to tasks-add component:  
   * input.form-control is a bootstrap feature that will allow a user to input new tasks in the app. 
   * This feature will updated later in the tutorial.  
 
![](Images/2019-12-26-10-16-32.png)  
<br>  

4. ### Setup tasks-list.component.html:  
   * li.list-group-item is a bootstrap feature will create the list of tasks for the app.  
     * The list below is in place to show that the layout is formatted correctly. This page will be updated once we create our task model in the next section.  

![](Images/2019-12-26-10-30-25.png)  
<br>  



## Create Angular MVC Pattern:  
<br> 

### Create Model Component:  

1. ###  Create a task.model.ts file for your entity.  
   * add fields and constructor to match your Spring entity class.  

![](Images/2019-12-24-14-45-57.png)     
<br>  

2. ### Import task.model.ts to tasks.list.component.ts.    
     * Import file.  
    * Initialize an array of tasks.  
    * Optionally set some tasks up to test by creating new tasks in the ngOnInit() method. 
    * Add a method to getDueDate
    * Add method onTaskChange($event, task)  
      * The logic for this method will be added when we complete the task.service.ts.    

![](Images/2019-12-24-15-14-56.png)      
<br>  


3. ### Update tasks-list.component.html to dispaly the tasks using Bootstrap.    
   * Create *ngFor to loop through list of tasks. 
   * Add checkboxes and setup input so that checkboxes can be checked off as completed.  
   * Add a class block to display whether or not task is completed.  
   * Add a class block to display the due date using the getDueDateLable(task) method.    

![](Images/2019-12-24-15-10-03.png)   
<br>  


Display in brower is updated.  

![](Images/2019-12-24-15-20-05.png)      

Next we will create the service class so that we can remove the status data we entered in the *ngOnInit()* method to temporarily populate our checklist.  
<br>   


___   
## Create Service Component:  
The service class will reach out to the Spring Boot Application to get the data.  

1. ### Create task.service.ts file to hold CRUD Operations.    
   * Export class.
   * Insert dependency injection by creating a constructor that takes takes an Http component as a parameter.  
     * Must add @Injectable decorator anytime a dependency is injected.  
     * Create a *getTasks()* method that reaches out to our API endpoint.  
       * Pull in map from rxjs library that excepts a response as an objservable for the *getTasks()* method. 
     * Create a *saveTask(task: Task, checked: boolean)* method.  
       * set task completed based on the value of the check box (whether checked or not).  
       * Similar to the *getTasks()* method, we are going to use our http component to call out to our Spring Boot end point that takes in a body of 'task'.
       * We pass the task object we receive in our tasklist.component.html (step 3 above) as the body of our post method.  
![](Images/2019-12-26-09-03-31.png)  
<br>  

   
2. ### Go to tasks-list.component.ts file.   
   * Import TaskService file.  
   * Create a constructor that takes TaskService in its parameter.  
   * Remove temporary data from *ngOnInit()* method and replace with *taskService.getTasks()*  
     * Chain *.subscribe()* to the get method, which will take an array of tasks that it receives from the server in it's paramater.
     * Finally, log any errors to the console.  
   * Write logic for *onTaskChange Method()* to call *saveTask()* method in TaskService component when checkbox is checked as 'task completed'.  
     * You can now run the frontend and complete some tasks, thencheck the H2 console on localhost:8080 to confirm that the tasks are being completed on the server end as well.

![](Images/2019-12-26-09-14-09.png)   
<br>  


1. ### Go to app.module.ts file.     
   * Import TaskService.
   * Add TaskService as a provider. 
   
![](Images/2019-12-24-15-41-58.png) 
<br>  


4. ### Create a () proxy-conf.json file:    
   * Set API to http://localhost:8080 so that the application can reach Spring Boot's endpoints.  

![](Images/2019-12-24-16-43-02.png)    
<br>  


5. ### Change the "start" line in the package.json file:    
   * Pass in the newly created proxy.conf file to "ng serve".
   * *Going forward, start the frontend server by calling "npm start", instead of "ng serve".*  

![](Images/2019-12-24-16-47-45.png)     
<br>  


Any time you are working with two local hosts like we are here, we need to add the above proxy.conf to proxy all requests over to Spring Boot. 

Adding localhost:8080 directly to the get task method instead of completing steps 4 & 5 will result in a "cross origin resource sharing" (CORS) issues.  


 


