-   **pipenv related info**:

    -   `pip3 install pipenv`
    -   `pipenv shell` (to activate virtualenv)
    -   `pipenv install django==3.0` (optional)

    -   `pipenv install pytest --dev` (since, we don’t need pytest in production so you can specify that this dependency is only for development with the --dev argument. Providing the --dev argument will put the dependency in a special [dev-packages] location in the Pipfile. These development packages only get installed if you specify the --dev argument with pipenv install)

    -   `pipenv install --dev` (to install all the dependencies needed for development, which includes both the regular dependencies and those you specified with the --dev argument during install)

    -   `pipenv install --ignore-pipfile` (it tells Pipenv to ignore the Pipfile for installation and use what’s in the Pipfile.lock)

    -   `pipenv install` (to install all requird packages from Pipfile)

---

-   **django related info**:

    -   `django-admin startproject <project_name> .`
    -   `python manage.py startapp <app_name>`
    -   `python manage.py makemigrations <app_name>` (optional)
    -   `python manage.py migrate <app_name>` (optional)
    -   `python manage.py createsuperuser` (to create admin)

---

-   **start/stop server**:
    -   `python manage.py runserver`
    -   `Control + c` (to stop local server)
    -   `python manage.py test` (optional)
    -   `exit` (to exit our virtualenv)

---
