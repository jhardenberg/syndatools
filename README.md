[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)
![stand with Ukraine](https://badgen.net/badge/stand%20with/UKRAINE/?color=0057B8&labelColor=FFD700)

# syndatools
## Simple script tools to list and extract data in a synda archive

These scripts allow to quickly browse the contents of a local ESGF mirror created by [synda](https://github.com/Prodiguer/synda) and to copy the data to your local directory in a convenient format and with some postprocessing.

There are only two commands for now:

* **syndalist** helps to browse the archive
* **syndaget** uses the same syntax and can be used to retrieve the data

## Examples 

List all CMIP6 dataset for variable `tas` in experiment `historical` at frequency (table) `Amon`
````
syndalist var=tas exp=historical freq=Amon
````

The same data could then be copied to the current directory with 
````
syndaget var=tas exp=historical freq=Amon
````

`syndaget` allows also to postprocess the data with cdo:
````
syndaget var=tas exp=historical freq=Amon post='-zonmean -timmean -selyear,1990/2005'
````

Just enter the commands to get a full list of options.

## Configuration

1. The tools try to guess the location of your synda archive from the `$ST_HOME` environment variable, so no configuration may be necessary. In case this does not work, please open both commands with a text editor and change the variable `INDIR` to point to the location of your synda ESGF archive. Example: `INDIR=/work/datasets/synda/data` 

2. Place them as executables in a directory in your path.

## Dependencies

The only dependence is [cdo](https://code.mpimet.mpg.de/projects/cdo/).
