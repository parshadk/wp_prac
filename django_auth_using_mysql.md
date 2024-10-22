To implement a user authentication system in Django with MySQL, follow these steps. The system will include user registration, login, and access to protected pages based on user credentials.

### Step-by-Step Guide:

#### 1. **Set Up a Django Project**

First, install Django and MySQL client dependencies:

```bash
pip install django mysqlclient
```

Next, create a Django project and an app for the authentication system:

```bash
django-admin startproject myproject
cd myproject
django-admin startapp users
```

#### 2. **Configure Django to Use MySQL**

In your `myproject/settings.py`, configure the database settings to use MySQL:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'your_db_name',
        'USER': 'your_db_user',
        'PASSWORD': 'your_db_password',
        'HOST': 'localhost',  # Or other host if it's hosted elsewhere
        'PORT': '3306',       # Default MySQL port
    }
}
```

Make sure you have created the MySQL database and granted access to the user.

#### 3. **Define the User Model (Optional)**

Django comes with a built-in `User` model in `django.contrib.auth`. If the default `User` model suits your needs, you can skip this step. Otherwise, you can create a custom user model.

In `users/models.py`:

```python
from django.contrib.auth.models import AbstractUser

class CustomUser(AbstractUser):
    # Add any additional fields here if needed
    pass
```

Update `settings.py` to tell Django to use the custom user model:

```python
AUTH_USER_MODEL = 'users.CustomUser'
```

#### 4. **Create User Registration Form**

Create a form for user registration using Django's built-in user forms in `users/forms.py`:

```python
from django.contrib.auth.forms import UserCreationForm
from django.contrib.auth import get_user_model

class UserRegisterForm(UserCreationForm):
    class Meta:
        model = get_user_model()
        fields = ['username', 'email', 'password1', 'password2']
```

#### 5. **Create Views for Registration, Login, and Logout**

In `users/views.py`, create the views to handle user registration, login, logout, and access to protected pages:

```python
from django.shortcuts import render, redirect
from django.contrib.auth import login, authenticate, logout
from django.contrib.auth.decorators import login_required
from .forms import UserRegisterForm
from django.contrib import messages

# Register view
def register(request):
    if request.method == 'POST':
        form = UserRegisterForm(request.POST)
        if form.is_valid():
            form.save()
            username = form.cleaned_data.get('username')
            messages.success(request, f'Account created for {username}!')
            return redirect('login')
    else:
        form = UserRegisterForm()
    return render(request, 'users/register.html', {'form': form})

# Login view
def login_view(request):
    if request.method == 'POST':
        username = request.POST['username']
        password = request.POST['password']
        user = authenticate(request, username=username, password=password)
        if user is not None:
            login(request, user)
            return redirect('home')
        else:
            messages.error(request, 'Invalid credentials')
    return render(request, 'users/login.html')

# Logout view
def logout_view(request):
    logout(request)
    return redirect('login')

# Protected view
@login_required
def home(request):
    return render(request, 'users/home.html')
```

#### 6. **Create URL Routing**

In `users/urls.py`, define the URLs for the registration, login, and logout views:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('register/', views.register, name='register'),
    path('login/', views.login_view, name='login'),
    path('logout/', views.logout_view, name='logout'),
    path('', views.home, name='home'),  # Protected page
]
```

In `myproject/urls.py`, include the `users` URLs:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('users/', include('users.urls')),
]
```

#### 7. **Create HTML Templates**

In your `users/templates/users` directory, create the following HTML templates:

- `register.html`:

```html
{% extends "base.html" %}
{% block content %}
  <h2>Register</h2>
  <form method="POST">
    {% csrf_token %}
    {{ form.as_p }}
    <button type="submit">Register</button>
  </form>
{% endblock %}
```

- `login.html`:

```html
{% extends "base.html" %}
{% block content %}
  <h2>Login</h2>
  <form method="POST">
    {% csrf_token %}
    <input type="text" name="username" placeholder="Username">
    <input type="password" name="password" placeholder="Password">
    <button type="submit">Login</button>
  </form>
  <a href="{% url 'register' %}">Don't have an account? Register here.</a>
{% endblock %}
```

- `home.html`:

```html
{% extends "base.html" %}
{% block content %}
  <h2>Welcome, {{ user.username }}!</h2>
  <a href="{% url 'logout' %}">Logout</a>
{% endblock %}
```

#### 8. **Run Migrations and Start the Server**

Run the migrations to apply the database changes:

```bash
python manage.py makemigrations
python manage.py migrate
```

Create a superuser to access the admin panel:

```bash
python manage.py createsuperuser
```

Finally, run the development server:

```bash
python manage.py runserver
```

#### 9. **Access Control: Protect Pages Based on Login Status**

The `@login_required` decorator, already added in the `home` view, ensures that only authenticated users can access this page.

If a user tries to access a protected page without being logged in, they will be redirected to the login page.

### Conclusion

With this setup, you now have a functional authentication system where users can register, log in, and access protected content based on their credentials using Django and MySQL.
