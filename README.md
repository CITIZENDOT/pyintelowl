# pyintelowl

[![PyPI version](https://badge.fury.io/py/pyintelowl.svg)](https://badge.fury.io/py/pyintelowl)
[![Language grade: Python](https://img.shields.io/lgtm/grade/python/g/intelowlproject/pyintelowl.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/mlodic/pyintelowl/context:python)
[![CodeFactor](https://www.codefactor.io/repository/github/intelowlproject/pyintelowl/badge)](https://www.codefactor.io/repository/github/intelowlproject/pyintelowl)

Simple Client for the [Intel Owl Project](https://github.com/intelowlproject/IntelOwl)

2 ways to use it:
* as a library
* as a command line script

You can select which analyzers you want to run for every analysis you perform.

For additional help, we suggest to check the ["How to use pyintelowl" Youtube Video](https://www.youtube.com/watch?v=fpd6Kt9EZdI) by [Kostas](https://github.com/tsale).


## Generate API key
You need a valid API key to interact with the IntelOwl server. 
Keys should be created from the admin interface of [IntelOwl](https://github.com/intelowlproject/intelowl): you have to go in the *Durin* section (click on `Auth tokens`) and generate a key there.

You can use the  with the parameter `-k <api_key>` from CLI

#### (old auth method) JWT Token Authentication
> this auth was available in IntelOwl versions <1.8.0 and pyintelowl versions <2.0.0

From the admin interface of IntelOwl, you have to go in the *Outstanding tokens* section and generate a token there.

You can use it by pasting it into the file [api_token.txt](api_token.txt).

## Library
`pip3 install pyintelowl`

`from pyintelowl.pyintelowl import IntelOwl`

#### Endpoints
`ask_analysis_availability` -> search for already available analysis

`send_file_analysis_request` -> send a file to be analyzed

`send_observable_analysis_request` -> send an observable to be analyzed

`ask_analysis_result` -> request analysis result by job ID

`get_analyzer_configs` -> get the analyzers configuration


## Command line Client

#### Help

`python3 intel_owl_client.py -h`

#### Analyze
2 Submodules: `file` and `observable`

##### Sample
Example:

`python3 intel_owl_client.py -k <api_token> -i <url> -a PE_Info -a File_Info file -f <path_to_file>`

Run all available analyzers (some of them could fail if you did not implemented the required configuration in the IntelOwl server):

`python3 intel_owl_client.py -k <api_token> -i <url> -aa file -f <path_to_file>`

##### Observable
Example:

`python3 intel_owl_client.py -k <api_token> -i <url> -a AbuseIPDB -a OTXQuery observable -v google.com`

#### Get Analyzers Configuration
`python3 intel_owl_client.py -k <api_token> -i <url> -gc`
