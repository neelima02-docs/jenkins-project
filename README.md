Flask App:
-clone flask app from github 
-python version (3.6 /3.8)
-Create Venv and Run dependencies
-code coverate (Cobertura tool)
-run unit test cases using pytest 



Jenkins CI/CD Execute shell sequence commands:

pyenv versions

echo "#### activating python version 3.8 ####"
pyenv global pypy3.8-7.3.11
pyenv -V

echo "#### Creating flaskapp virtual env ####"
python -m venv flaskapp

echo "#### Activating flaskapp virtual env ####"
source flaskapp/bin/activate

echo "##### Installing required Python Modules ####"
pip install -r requirements.txt

echo "##### Installing code coverage and pytest modules ####"
pip install coverage
pip install pytest-cov

echo '#### Runing tests ####'
pytest --cov=main --cov-report xml
pytest utests --junitxml=./xmlReport/output.xml

echo "##### Deactivating venv and reset python version to system ####"
deactivate# jenkins-project
