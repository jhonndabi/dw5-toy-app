### Section 2.2.1

##### 1) (For readers who know CSS) Create a new user, then use your browser’s HTML inspector to determine the CSS id for the text “User was successfully created.” What happens when you refresh your browser?

`notice`. The message disappears

##### 2) What happens if you try to create a user with a name but no email address?

I can usually.

##### 3) What happens if you try create a user with an invalid email address, like “@example.com”?

Nothing wrong happens, there is no validation, the user is created.

##### 4) Destroy each of the users created in the previous exercises. Does Rails display a message by default when a user is destroyed?

Yeah, the following message: `User was successfully destroyed.`

### Section 2.2.2

##### 1) By referring to Figure 2.11, write out the analogous steps for visiting the URL /users/1/edit.


1) The browser issues a request for the /users/1/edit URL.
2) Rails routes /users/1/edit to the edit action in the Users controller.
3) The before_action method asks the User model to retrieve a user with the id on params (User.find).
4) The User model retrieves the user with id equal to 1 from the database.
5) The User model returns the user with id equal to 1 to the controller.
6) The controller captures the user in the @user variable, which is passed to the index view.
7) The view uses embedded Ruby to render the page as HTML.
8) The controller passes the HTML back to the browser.3

##### 2) Find the line in the scaffolding code that retrieves the user from the database in the previous exercise.

```
@user = User.find(params[:id])
```

##### 3) What is the name of the view file for the user edit page?

`edit.html.erb`


### Section 2.3.1

##### 1) (For readers who know CSS) Create a new micropost, then use your browser’s HTML inspector to determine the CSS id for the text “Micropost was successfully created.” What happens when you refresh your browser?

`notice`. The message disappears

##### 2) Try to create a micropost with empty content and no user id.

I can usually.

##### 3) Try to create a micropost with over 140 characters of content (say, the first paragraph from the Wikipedia article on Ruby).

I can usually.

##### 4) Destroy the microposts from the previous exercises.

The following message has appeared: `Micropost was successfully destroyed.`


### Section 2.3.2

##### 1) Try to create a micropost with the same long content used in a previous exercise (Section 2.3.1.1). How has the behavior changed?

The behavior hasn't changed. The message is the same `Content is too long (maximum is 140 characters)`

##### 2) (For readers who know CSS) Use your browser’s HTML inspector to determine the CSS id of the error message produced by the previous exercise.

`error_explanation`


### Section 2.3.3

##### 1) Edit the user show page to display the content of the user’s first micropost. (Use your technical sophistication (Box 1.1) to guess the syntax based on the other content in the file.) Confirm by visiting /users/1 that it worked.

`app/views/users/show.html.erb`

```
...
<p>
  <strong>First Post:</strong>
  <%= @user.microposts.first.content %>
</p>
...
```

##### 2) The code in Listing 2.16 shows how to add a validation for the presence of micropost content in order to ensure that microposts can’t be blank. Verify that you get the behavior shown in Figure 2.16.

The following message has appeared:

```
User must exist
Content can't be blank
```

##### 3) Update Listing 2.17 by replacing FILL_IN with the appropriate code to validate the presence of name and email attributes in the User model (Figure 2.17).

```
class User < ApplicationRecord
  has_many :microposts
  validates :name, presence: true
  validates :email, presence: true
end
```

The following message has appeared:

```

Name can't be blank
Email can't be blank
```


### Section 2.3.4

##### 1) By examining the contents of the Application controller file, find the line that causes ApplicationController to inherit from ActionController::Base.

The first line:

```
class ApplicationController < ActionController::Base
```

##### 2) Is there an analogous file containing a line where ApplicationRecord inherits from ActiveRecord::Base? Hint: It would probably be a file called something like application_record.rb in the app/models directory.


Yes, There is the `app/models/application_record.rb` with the following content on the first line:

```
class ApplicationRecord < ActiveRecord::Base
```
