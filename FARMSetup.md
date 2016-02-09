# Setting up the FARM #

## Pre-Requisites ##
  * Java 1.6
  * Eclipse 3.4
  * Copy of FARM version 2.0

## Create new Java project: **generic** ##
### Import files ###
  * Right click project name, choose import
  * General -> File System, click next
  * Browse to the `generic` folder inside `farm`
  * Check `lib` and `src` directories, click finish

### Set Build Path ###
  * Open `lib` folder inside package explorer
  * Right click `farmsimulator.jar`, choose Build Path -> Add to build path
  * Right click `utilities.zip`, choose Build Path -> Add to build path


**Should be no compilation errors (assuming Java 1.6 is the JRE)**


## Create new Java project: simulator ##
  * Import files:  `lib` and `src` directories from simulator folder
  * Set Build Path: add `farmgeneric.jar` and `utilities.zip` to build path
  * Should be no compilation errors

## Create new Java project: graphcolor ##
  * Import files: `lib` and `src` directories from `graphcolor` folder as well as any scripts you want to add
  * Set Build Path:  add `farmgeneric.jar`, `farmsimulator.jar`, `utilities.zip`, `security.txt` to build path


**Should be no compilation errors**


## Setting up to Run the RMI Registry ##
  * Click Run -> External Tools -> External Tools Configurations…
  * Double-click program, should create a new configuration
  * Set the following variables:
    * Name:  RMI Registry
    * Main Tab
      * Location:  (should be path to rmiregistry.exe) `C:\Program Files\Java\jre1.6.0_07\bin\rmiregistry.exe`
      * Working Directory: `${workspace_loc:/graphcolor}`
    * Environment Tab
      * Add new Variable: `CLASSPATH`
      * with Value: `${workspace_loc:/graphcolor/lib/farmsimulator.jar}`
  * Click Apply, then Close


## Setting up to Run Graphcolor ##
(via farm.graphcolor.Main and/or farm.graphcolor.OriginalMain)
  * Click Run -> Run Configurations…
  * Double-click Java Application, should create a new configuration
  * Set the following variables:
    * Name:  gc main (or original main)
    * Project: graphcolor
    * Main class: farm.graphcolor.Main (farm.graphcolor.OriginalMain)

## Running the FARM on Graphcoloring ##
### Inside eclipse: ###
  * Run RMI Registry:
    * Click Run -> External Tools -> RMI Registry
    * Should get empty console window
  * Run Graphcolor.Main (OriginalMain)
    * Click Run -> gc main (or original main)

### Outside eclipse: (Windows) ###
  * Edit `SetJava.bat` and `SetClassPath.bat` to reflect your machine’s settings
  * Double click `runRMI.bat`
  * Double click `runMain.bat`, `runMainInteractive.bat`, or `runOriginalMain.bat`

### Outside eclipse: (Mac) ###
  * Edit `runRMI.command`, `RunOriginalMain.command`, and `RunMain.command` to reflect the right classpath
  * Double click `RunRMI.command`
  * Double click `RunMain.command` or `RunOriginalMain.command`

**NOTE:**  Be sure to shut down the RMI Registry (ctrl+c) correctly each time or you will have to restart your computer because the port doesn’t reset and it won’t start up properly the next time.