# MacOS Setup

## How to run Apache Airflow in Python Environment (Mac)
1. Check the python version `python --version` [This demo is based on Python 3.10.10]
2. Create the python environment
    ```
    $ python -m venv py_env
    ```
    py_env = name of the environment folder
3. Activate the python environment
    ```
    Windows: $ source py_env/Scripts/activate
    MacOS: $ source py_env/bin/activate
    ```
4. Go to https://github.com/apache/airflow/#installing-from-pypi, click `Installing from PyPI`, and grab this code
    ```
    $ pip install 'apache-airflow==2.5.1' \
    --constraint "https://raw.githubusercontent.com/apache/airflow/constraints-2.5.1/constraints-3.7.txt"
    ```
    Change constraints-3.7.txt to the python version you are using (Example: constraints-3.10.txt)
5. Set up environment variables
    ```
    $ export AIRFLOW_HOME=.
    $ airflow db init
    ```
    This will create SQLite Database, lock folder, and configuration file
6. Start Airflow server
    ```
    $ airflow webserver -p {Port_Number}
    ```
    Check to see if the server is running ok
7. Create credential for Airflow 
    ```
    $ airflow users create --username <USER_NAME> --firstname <FIRST_NAME> --lastname <LAST_NAME> --role Admin --email <EMAIL>
    ```
    Then type password for the new credential twice
8. Start Airflow Scheduler
    ```
    $ export AIRFLOW_HOME=.
    $ airflow scheduler
    ```