-   To setup the project

    -   pipenv specific commands:

        ```
        to install all requird packages from Pipfile:
        (on local)$ pipenv install --dev
        (on prod)$ pipenv install

        to activate virtualenv:
        $ pipenv shell
        ```

    -   django specific commands:

        ```
        $ python manage.py makemigrations <app>
        $ python manage.py migrate <app>
        $ python manage.py runserver

        to stop local server:
        $ Control + c

        to exit virtualenv:
        $ exit
        ```
