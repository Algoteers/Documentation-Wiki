## Step 1: A Bit of Planning

First thing to do is understanding what you wish to do and deciding which of the existing bots resembles the most to what your own bot should end up looking like. 

Are you doing an indicator bot? A trading bot? What kind of process will your bot involve? What kind of data output should your bot have? Which of the existing bots is the most similar to your requirements?

## Step 2: Using an Existing Bot as a Starting Point

### Copy and Rename Bot

Once you have identified the bot that is the most similar to yours, clone the corresponding repository and --once in your local machine-- copy and paste the repository’s root folder, renaming it with the name of your new bot. 

Make sure you follow the naming convention using the following string:

“**AA**”+”**BotName**”+”**-Indicator-Bot**” _or_ “**-Trading-Bot**”

e.g.: _AAOlivia-Indicator-Bot_

> NOTE: Make sure the bot name is unique. That is, no other bot by any other Dev Team can have the same name.

### Rename Solution

Now rename the solution using the following syntax: “**AA**”+“**BotName**”+“**-TypeOfBot-**”+“**Bot**”+“**.sln**”

e.g.: _AAOlivia-Indicator-Bot.sln_

### Remove .git Folder

Next, delete the hidden _.git_ folder to eliminate the relation to the original GitHub repository.

### Add GitHub Repository

Now is a good time to go to GitHub and add a new local repository within your own organization. Make sure you include a concise description of what the bot does.

### Configure Solution

Next, open the recently renamed solution in Visual Studio and make the following changes:

* In the Solution Explorer window:
  - Change the name of the project.
  - You may want to rename one of the existing processes (the one you are planning to use).
  - Delete the remaining original unused processes, if any.
* Open _this.bot.config.json_ and update:
  - The bot’s name.
  - The process name, deleting config for unused processes.

## Step 3: Start Coding

Now you are good to go. We’ve found the following workflow is quite practical:

* Code directly in the bot’s solution until the code is fully implemented.
* Close the bot’s module and go to the cloud platform solution to debug (as explained here). While debugging, the bot’s files will pop up in separate tabs, so that you can edit the code in the process.

> NOTE: Please, bear in mind that the data produced by other bots available in the testnet storage may be inconsistent, incomplete or even faulty. If you are using other bot's dataset as input for your own bots, it might be a good idea to isolate portions of the data and even move it to your local environment to work in isolation temporarily.

## Step 4: Configure Dev Team and Bots to Run in Production

Now that your bots are ready and you are happy with the datasets they produce, it is time to register your Dev Team and bots in the AA Platform so that they can run in the production environment using complete input datasets and produce complete outputs. Running in production is not that different from running in the development environment. You can even finish and fine-tune your development while running your bots production.

### Configuration File

Clone the [[AAPlatform|https://github.com/AdvancedAlgos/AAPlatform]] repository and open _ecosystem.json_. You will need to locate the following piece of code:

```
    {
      "codeName": "AAMasters",
      "displayName": "AA Masters",
      "bots": [
        {
          "repo": "AAOlivia-Indicator-Bot",
          "configFile": "this.bot.config.json"
        },
        {
          "repo": "AATom-Indicator-Bot",
          "configFile": "this.bot.config.json"
        },
        {
          "repo": "AAMariam-Trading-Bot",
          "configFile": "this.bot.config.json"
        }
```

Copy the piece of code and replicate it immediately below the closing key. Modify the pasted code to incorporate the details of your own GitHub organization and your own bots. Once you are finished, commit the changes and submit a pull request. Someone in the AdvancedAlgos Organization will analyze your request and pull it into the main branch's code if everything looks right.


