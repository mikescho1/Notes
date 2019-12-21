### Angular Basics:  
###### Uppercase:  
\<h2>{{hero.name | uppercase}} Details\</h2>  
###### Two-Way Binding:  
\<div>
  \<label>name:
    \<input [(ngModel)]="hero.name" placeholder="name"/>
  \</label>
\</div>  
* Although ngModel is a valid Angular directive, it isn't available by default. It belongs to the optional FormsModule and you must opt-in to using it.  
* import { FormsModule } from '@angular/forms' in src-> app-> app.modules.ts


###### Repeater Directive:  

The *ngFor is Angular's repeater directive. It repeats the host element for each element in a list.