# Developing the app - the Task model

  Before we get much further with the development of our todo application, we should define what a Task looks like in our application. Create a class for it in the `app/models/Task.java` file:

    package models;

    import java.util.*;

    public class Task {

      public Long id;
      public String label;

      public static List<Task> all() {
        return new ArrayList<Task>();
      }

      public static void create(Task task) {
      }

      public static void delete(Long id) {
      }

    }


  For the Task operations we have created two static methods, *create* and *delete*. For now we wrote dummy implementation for each operation, but later in this tutorial we will write implementations that will store the tasks into a relational database.
    
## The application template

  Our simple application will use a single Web page containing both the tasks list and the task creation form. Modify the `index.scala.html` template as follows:
  

    @(tasks: List[Task], taskForm: Form[Task])

    @import helper._

    @main("Todo list") {

        <h1>@tasks.size() task(s)</h1>

        <ul>
            @for(task <- tasks) {
                <li>
                    @task.label

                    @form(routes.Application.deleteTask(task.id)) {
                        <input type="submit" value="Delete">
                    }
                </li>
            }
        </ul>

        <h2>Add a new task</h2>

        @form(routes.Application.newTask()) {

            @inputText(taskForm("label")) 

            <input type="submit" value="Create">
        }
    }


  We changed the template signature to take 2 parameters:

  * A list of tasks to display
  * A task form

  We also imported helper._ that give us the form creation helpers, typically the form function that creates the HTML <form> with filled action and method attributes, and the inputText function that creates the HTML input given a form field.

  Note: Read more about the [Templating system](http://www.playframework.com/documentation/2.1.0/JavaTemplates) and {Forms](http://www.playframework.com/documentation/2.1.0/JavaFormHelpers) helper.

## The task form

  A Form object encapsulates an HTML form definition, including validation constraints. Let’s create a form for our Task class. Add this to your Application controller:

    static Form<Task> taskForm = Form.form(Task.class);

  The type of taskForm is then Form<Task> since it is a form generating a simple Task.
You also need to import play.data.* and models.* 

  We can add a constraint to the Task type using JSR-303 annotations. Let’s make the label field required:

    package models;

    import java.util.*;

    import play.data.validation.Constraints.*;

    public class Task {

      public Long id;

      @Required
      public String label;
      ...

Note: Read more about the [Form definitions](http://www.playframework.com/documentation/2.1.0/JavaForms) in the Play framework.

## Rendering the first page

  Now we have all elements needed to display the application page. Let’s write the tasks action:

    public static Result tasks() {
      return ok(
        views.html.index.render(Task.all(), taskForm)
      );
    }

  It renders a 200 OK result filled with the HTML rendered by the index.scala.html template called with the tasks list and the task form.

  You can now try to access http://localhost:9000/tasks in your browser:

<a href="images/07x01-play-app-task-form.png"><img src="images/07x01-play-app-task-form.png"></a>


## Handling the form submission

  For now if we submit the task creation form, we still get the TODO page. Let’s write the implementation of the newTask action:

    public static Result newTask() {
      Form<Task> filledForm = taskForm.bindFromRequest();
      if(filledForm.hasErrors()) {
        return badRequest(
          views.html.index.render(Task.all(), filledForm)
        );
      } else {
        Task.create(filledForm.get());
        return redirect(routes.Application.tasks());  
      }
    }

  We use **bindFromRequest** to create a new form filled with the request data. If there are any errors in the form, we redisplay it (here we use 400 Bad Request instead of 200 OK). If there are no errors, we create the task and then redirect to the tasks list.

> Read more about the Form submissions.

## Commit your changes locally and deploy

  Again as we have made a significant change to the web app functionality, even though its not complete, we should commit those changes to Git.
  
  Add these changes to your local git repository as follows:
  
    git add .
    git commit -m "added Task model, forms and page"

  Push this commit to Heroku to deploy the new version of the code using the command
  
    git push heroku master

  Reload your browser to check the live website has been updated, or use the command `heroku open` 

[Back to top...](#top)
[Next...](08-developing-the-app-persisting-data.html)
[Back to Workshop home](index.html)
