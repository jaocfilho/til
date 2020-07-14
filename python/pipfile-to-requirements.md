<h1>Transforming the dependencies in a Pipfile to requirements.txt</h1>

    pipenv lock -r > requirements.txt

<p>You can use this command to create a new file <code>requirements.txt</code> with all the dependencies from a Pipfile. It is usefull if you want to use another virtual environment.
</p>