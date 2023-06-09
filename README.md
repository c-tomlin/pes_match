# ONS PES Matching Pipeline Scripts
A python pipeline for matching census and post-enumeration survey (PES) data deterministically.

For additional information consider reading:
* [ONS data linkage working paper](https://www.ons.gov.uk/methodology/methodologicalpublications/generalmethodology/onsworkingpaperseries/developingstandardtoolsfordatalinkagefebruary2021)
* [Census 2021 to Census Coverage Survey matching methods, England & Wales](https://www.ons.gov.uk/peoplepopulationandcommunity/populationandmigration/populationestimates/methodologies/linkagemethodsforcensus2021inenglandandwales)

## Setup instructions

### Installing Python and an IDE
We recommend using the IDE Spyder which is available through the anaconda navigator. This can be installed [here](https://www.anaconda.com/products/distribution) and further instructions on installing Spyder can be found [here](https://docs.spyder-ide.org/current/installation.html).

## Using this code
Once Python is installed, download this repository and execute the command `pip install -r requirements.txt` to install/update the required packages for this repository.

The aim of this repository is to provide a set of functions for cleaning and then matching census and PES data. PES_MATCH gives matchers the tools to automatically match records 
at the chosen level of geography and then resolve conflicts/difficult cases using the Clerical Resolution Online Widget. Associative matching can also be implemented to
assist in finding all possible matches between census and PES households. Once all methods have been applied at a single level of geography, matches can be combined and 
residuals collected for the next stage of matching.

An example of a typical matching pipeline is provided in the `pipeline/` repository, however users may wish to apply matching methods in their own chosen order.
Files can be executed in the command line using `python file_name.py` or within Spyder using the inbuilt run function.

## Pipeline running order
* Step 1: Run scripts in `pipeline/processing/` to clean raw files
* Step 2: Update matchkeys in `pipeline/X_Stage_X/` before running the scripts in order. 2 stages are included but more can be run if needed
* Step 3 (Optional): Run clerical search (`pipeline/Clerical_Search/`) to find the remaining matches within chosen level of geography e.g., postcode or enumeration area

## Directories and files of note

Descriptions of project directories and other significant files:
* `CROW/` - contains the code and config files for the [Clerical Resolution Online Widget](https://github.com/Data-Linkage/Clerical_Resolution_Online_Widget)
* `Data/` - contains mock data and stores cleaned data, clerical inputs/outputs, checkpoint files and final outputs
* `library/` - contains functions and a configurable parameter file
* `pipeline/` - scripts forming the record matching pipeline. Matchkeys can be updated within the scripts