Once your bot is up and running, generating a specific dataset, you will want to be able to visualize the data in a more friendly manner, probably on top of a typical candlestick chart. To do that, you will need to program a plotter.

Plotters --unlike bots-- run on the Web Platform. Upon execution, the Web Platform loads a web page which, in turn, calls scripts corresponding to bots plotters, among others. The scripts are loaded directly from the corresponding GitHub repository. Thus, every time you wish to see the effect of changes made in plotter’s code you need to commit the changes and push them to the repository. You will use your browser’s debugging tools to debug your scripts directly in-browser.

## Step 1: A Little Planning

Decide on what is the best way to visualize the data your bot is outputting. Is it a curve? Is it a candlestick pattern? Is it a horizontal line?

Are there any existing bots with similar visualization requirements that you can copy as a starter?

## Step 2: Clone Plotter

Clone the existing plotter of your choice and use it as a starting point for your own development.
