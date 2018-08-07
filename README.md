# simpl-calc-model - example single-player simulation model service.

## Python Setup (assumes Python >= 3.6 and simpl-games-api server running)

    git clone git@github.com:simplworld/simpl-calc-model.git
    cd simpl-calc-model
    mkvirtualenv simpl-calc-model
    add2virtualenv .
    
    PIP_PROCESS_DEPENDENCY_LINKS=1 pip install -r requirements.txt

## Run model service

    export DJANGO_SETTINGS_MODULE=simpl_calc_model.settings
    ./manage.py run_modelservice

If you need some serious debugging help, the model_service includes the ability to do

    ./manage.py run_modelservice --loglevel=debug

Which will turn on verbose debugging of the Autobahn/Crossbar daemon to help debug interactions between the browser and model service backend.

## Run unit tests

    py.test

## Development commands:

### 1 - To setup up database for simpl-calc development use:

1. Creates the simpl-calc game with one phase (Play) and one role (Calculator).
1. Adds a 'default' run..
1. Adds 1 leader ('leader@calc.edu'/'leader') to the run.
1. Adds 2 players to the run ('s#@calc.edu'/'s#' where # is between 1..2. Each player has a private scenario and period 1.
1. The run is set to 'Play' phase

execute:

    ./manage.py create_default_env

To make it easier to recreate the default run you can pass the `--reset` option to delete the
default run and recreate it from scratch like this:

    ./manage.py create_default_env --reset


### 2 - To submit a decision on a scenario:

    ./manage.py submit_decision -s <scenario_id> -d <decision>
