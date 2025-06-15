---
title: "Creating a Custom Authentication Backend in Django"
seoTitle: "Custom Authentication Backend in Django"
datePublished: Fri Jul 18 2022 07:02:34 GMT+0000 (Coordinated Universal Time)
slug: custom-authentication-backend-in-django
cover: https://res.cloudinary.com/practicaldev/image/fetch/s--jBFjsQ3E--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/y79h0v6wtipnu4xdcciu.jpg
tags: tutorial, django, python, webdev

---

You may have noticed that the built in authentication system in Django has quite some few limitations. For example, it only allows your website's users to only log in using their username and password. But in modern day websites, you might want to enable your users to be able to log in to your site using either their username or email address. If your website is for a company, you can even implement an authentication backend to make users log in using lets say a secret key.

>> What is an authentication backend in django?
An authentication backend is a python class which provides two methods for authenticating a user and also retrieving a user.

To implement a custom authentication backend, you need to define a python class with two(2) methods. One for retrieving a user and the other for authenticating a user. The two methods are, `get_user()` and `authenticate()` respectively.

The `authenticate()` method takes in a request object and the user credentials as parameters. It then returns a user object that matches the given credentials, if they are valid. It returns None if the credentials are not valid.
`get_user()` method takes a user ID as a parameter and has to return a user.


In this tutorial, we are going to create a new authentication backend to allow users login using their email addresses also.

**NOTE: THIS TUTORIAL ASSUMES YOU HAVE ALREADY CONFIGURED A VIRTUAL ENVIRONMENT AND ALSO CREATED A NEW DJANGO PROJECT.**

Let's create a new django application called `account` by running the command in your project root directory.:
```bash
python manage.py startapp account
```
Add `account` to your installed applications.

The account app should have the following directory structure.

![The green dots there just mean they are untracked by git](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/w3qgdtcr8dbn608d15h4.png)
Next, create a new file called `authentication.py` in the account app.
In `authentication.py`, we add the following code:
```python
from django.contrib.auth.models import User
class EmailAuthBackend:
    """
    Custom authentication backend.

    Allows users to log in using their email address.
    """

    def authenticate(self, request, username=None, password=None):
        """
        Overrides the authenticate method to allow users to log in using their email address.
        """
        try:
            user = User.objects.get(email=username)
            if user.check_password(password):
                return user
            return None
        except User.DoesNotExist:
            return None

    def get_user(self, user_id):
        """
        Overrides the get_user method to allow users to log in using their email address.
        """
        try:
            return User.objects.get(pk=user_id)
        except User.DoesNotExist:
            return None
```
Remember, the authenticate() method will be used to authenticate your users, and will be called when you call the authenticate() method in your view.
In the `authenticate()` method above, we are having the parameters request, username and password. The entered email address will be found in the username parameter and the password in the password parameter.

We are using a try, except block because, fetching a user that does not exist will raise a `DoesNotExist` error.
We retrieve a user with the incoming email address, note that the email address must be set to `unique=True` otherwise a `MultipleObjectsReturned` error will be raised if more than one user has the same email address. This can be done by creating a custom user model. If you're not familier with a custom user model, let me know in the comments.

Next, we're using the method, user.check_password(). This will take the password argument, hash it and then compare it with the hashed password in the database. If there is a match, it will return `True`, else `False`.
In our case, if the result is True, we return the user, else we return None.
Also, if there is no user in the database with that email address, in that case a user.DoesNotExist error will be raised. If there's no user, we return None.

The get_user() method takes a user_id as an argument. It returns the user if it exists or else it returns None.

Thats it, we are done with our custom authentication backend. Phew.
But now, users will still not be able to log in using their email address. This is because, we have not told django to add our authentication backend to the list of authentication backends available. To do that we need to edit our `settings.py` file.
Add the following to it.

```python
AUTHENTICATION_BACKENDS = [
    'django.contrib.auth.backends.ModelBackend', # This is the default that allows us to log in via username
    'account.authentication.EmailAuthBackend'
]
```

Now, django is aware of our authentication backend.

But how does django apply our authentication backend?
When we call the `authenticate()` method from django.contrib.auth in our view, django authenticates the user agains each of the authentication backend specified in the `AUTHENTICATION_BACKENDS `setting. In other words, it calls the authenticate method of each of the authentication backends specified. 
Django will stop at the first backend that authenticates successfully.

Go ahead and run your development server and try out your new authentication method. 
You can extend this to authenticate against whatever you wish.


Thanks for reading. If you have any questions, please let me know in the comments section. And also, dont forget to follow for more tutorials.
If you would like to request for a tutorial, let me know. Thanks and **happy coding.**