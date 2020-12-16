# Tracking Biological Weapon Fallout (Bacterial Bomb)
This project was part of the assessment for the Programming for Social Science course of my MSc/PhD at the University of Leeds between September and December.

The main requirements of this particular project were to build a programme which can:
1.	Read in data: Pull in the map data file provided (wind.raster) and find out the bombing point.
2.	Process it: Calculate where 5000 bacteria will end up.
3.	Display the results: Draw a density map of where all the bacteria end up as an image and displays it on the screen.
4.	Write results to a file: Saves the density map to a file as text.

In addition, it was also expected (as additional) to allow the user to adjust the variables (number of bacteria and windspeed-based probabilities) in some way, for example, using scrollbars in Jupyter notebook.

## Brief Project Description
The project states that a bacterial bomb is being set off in a town on top of a building. As part of the government anti-terrorist unit, I am to model where each bacterium in the bomb will spread and land so that the contamination can be dealt with. A map of the town is given with the location of the bomb.

### The Following Default Conditions Are Provided:   
1. Map has north at the top
2. Windspeed probabilities- at a particular moment (iteration), a bacterium will:
    *	Move north (10% probability)
    *	Move south (10% probability)
    *	Move west (5% probability)
    *	Move east (75% probability)
3. One model iteration = one model second
4. Distance that can be moved in one second = one pixel = 1 metre
5. Building height = 75 metres (m)
6. Bacteria vertical movement probabilities:
    *	If bacterium at or above building height:
        *	20% chance of rising by 1 metre/second
        *	10% chance of staying  at the same height
        *	70% chance of falling by 1 metre/second
    * If bacterium below the building height:
        * Drop by 1metre/second

# The Final Programme:
The programme meets the requirements of the project. In addition, it allows users to modify additional parameters (Building height and Headquarter location). Moreover Tabbed Visual Plots are displayed to easily view the plots generated. The user can also choose to enable grids on the scatter plots.

## Requirements to Run the Programmme:
This programmme was coded in Python 3.8.3 using Jupyter Notebook 6.0.3. It required Python 3.6+ to run as f-string are extensively used.

## How to Run the Programme:
You can run the programme by open Jupyter Notebook, browse to the directory of the programme and run the file 'bacterial_bomb.ipynb'. Then click on the first cell and click the 'Run' button in Jupyter Notebook.

You will be displayed with a map of the town with the location of the bacterial bomb. The x and y coordinates of the bomb will be shown as well.

You will see slides to adjust the bacteria number, building height, air speed, windespeed-based probabilities, location of the headquarter. 

You will also see two checkboxes, one to show grids in scatter plots and the other to plot tabbed plots seperately (instead of displayed saved immage output from the first subplots). For details about this, please see 'Project_information.pdf' file.

### To Modify North/South/East/West Probabilities:
Based on the requirements, total probability of moving north or south combined is 0.2 (0.1 each), and that of moving west or east is 0.8. Thus, the user can adjust the probability of moving north or south (pns) and thereby the probability of moving west or east.

The individual probabilities are then based on:

* Random value <= pns (will either move north or south):
    *	Random value <= pn: moves north based on horizontal air speed (hs). Default is 0.5 which is equivalent to original probability of 0.1.
    *	Random value > pn: moves south based on hs. Default is 0.5 which is equivalent to original probability of 0.1.
*	Random value > pns (will either move west or east):
    *	Random value <= pw: moves west based on hs). Default is 0.06 which is equivalent to original probability of 0.05.
    *	Random value > pw: moves east based on hs. Default is 0.94 which is equivalent to original probability of 0.75.

### To Modify Up/Down/Same Probabilities:
If a bacterium is at or above the building height, the probabilities are adjusted as follows:

The total probability of moving up or down (pud) is 0.9 and staying same is 0.1:
* Random value <= pud (will either move up or down):
    * Random value <= pu: moves up by vertical air speed (vs). Default is 0.22, which is equivalent to original probability of 0.2.
    * Random value > pu: moves down by vs. efault is 0.78, which is equivalent to original probability of 0.7.
* Random value > pud: Stays at the same level. Default is 0.1 which is the same as the original probability of 0.1

### Detonate Bomb!
Once the settings are adjusted (or not), and the 'Detonate Bomb!' button is clicked, the model spreads the bacteria till they land on the ground. A visual display of the spread is done by a progress bar. 

Then plots are show in four tabs:
First tab displays four subplots. The second, third and fourth each display a plot. For details about the plots please see 'Project_information.pdf' file.

The programme then saves the density map of the bacteria that landed in the town as a csv file 'bac_den_map.csv'.

# Known issues:
1. The two individual scatter plots in tab 2 and 3, if displayed using the saved image method, lacks legends. Attempt was made to solve by saving the legend from the subplots separately as a figure. But it remains unsolved.
2. (Partially resolved) While the programme does calculate the most concentrated number and location, it only calculates the first instance. If another location has the same number of bacterial deposits as the previously identified most concentrated location, it is ignored.

# Folders/Files in the Repository:
1. Plots: folder contains the saved image and pdf outputs of the plots.
2. bacterial_bomb.ipynb: The main Jupyter Notebook file for the programme
3. bbframwork.py: The agentframework module for the programme.
4. wind.raster: csv file of the map of the town with location of the bomb.
5. bac_den_map: Saved density map of the bacteria after landing in the town.
6. previous_model.ipynb: previous non-oop version of the programme.
7. Project_information.pdf: Document detailing the intention and use of the software, issues during development and how these were overcome (or not), general sources used, the thought processes going into the software design, and the software development process.
8. bacterial_bomb_uml_activity.pdf: The UML activity diagram of the programme.
9. README.md: The readme file of the programme.
9. LISCENSE.md: The liscense file of the programme.


