## Step 1: Node.js

Before we start, make sure you have Node.js installed. If you don’t, please [[download and install Node.js|https://nodejs.org/en/download/]].

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/Node-js-01.png]]

## Step 2: Azure Storage Explorer

Bots consume and store data in the Microsoft Azure cloud. This tool will allow you to browse and manage data.

### Download, Install, Run

Download and install the [[Azure Storage Explorer|https://azure.microsoft.com/en-us/features/storage-explorer/]].

The following screen should pop up when you launch Azure Storage Explorer:

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/Azure-Storage-Explorer-02.png]]

Select _Use a connection string or a shared access signature URI_ and click **Next**.

Select _Use a connection string_ and paste the following connection string in the corresponding field to connect to the testnet storage:

```
DefaultEndpointsProtocol=https;AccountName=aatestnet;AccountKey=rQRuD8KeD0upqcN9532zqZTknKwkYJDpGzkATGptk9lIEovkLchdOGOJVld26cUjpzTA4enxsxpCB33B0pOZRg==;EndpointSuffix=core.windows.net
```

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/Azure-Storage-Explorer-03.png]]

Click **Next** and **Connect** in the following screen.

> **NOTE**: Please bear in mind that this connection method is provisional and will soon be changed for a secure one.

Storage Explorer will load on the following screen:

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/Azure-Storage-Explorer-01.png]]

### Data Structure

Spend some time exploring and getting familiar with the data structure under the _File Shares_ folder.

The data is stored under the following folder tree structure:

- ExchangeName
  - BotName
    - dataSet.V1
      - Output
        - This is the folder where bots store their data outputs.
      - Processes
        - This folder holds one child folder per each process by each bot.
        - Each child folder holds a control checkpoint file named _Status.Report.”MARKETPAIR”.json_ (e.g.: _Status.Report.USDT_BTC.json_). This checkpoint helps the process restart from a certain point in the event of an unexpected interruption. Bots are free to store data in any way developers see fit. We have found in some cases it is best to organize data in the following format: YEAR > MONTH > DAY > HOUR > MINUTE.

> **NOTE**: Please be mindful of the way you use storage space. While using the AA Platform is currently free of charge for you, there are expenses related to storage volumes that the project needs to pay for.

## Step 3: Clone the Cloud Platform

Clone the [[AACloudPlatform|https://github.com/AdvancedAlgos/AACloudPlatform]] repository in your local machine.

### Using GitHub Desktop

If you are an advanced GitHub user you are probably using Git via the command-line. If you are not, we recommend [[downloading and installing the GitHub Desktop|https://desktop.github.com/]] application.

If you are not familiar with GitHub at all, we highly recommend you invest the time in learning it, as it is the most popular collaboration and version control system. For further information on how to use GitHub Desktop, please refer to the [[Getting Started with GitHub Desktop guide|https://help.github.com/desktop/guides/getting-started-with-github-desktop/]] or [[watch this video tutorial|https://www.youtube.com/watch?v=GqNAD4XoZ6k]].

Once you have launched GitHub Desktop and logged in with your GitHub credentials, this is what you need to do to clone the platform’s repository:

Go to _File > Clone Repository_

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/GitHub-Desktop-01.png]]

Click on the URL tab and paste the repository URL in corresponding field: 

```
https://github.com/AdvancedAlgos/AACloudPlatform
```

Choose where in your local machine GitHub should copy the files.

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/GitHub-Desktop-02.png]]

Once you clone the repository, GitHub desktop keeps track of the changes that may occur in the files in your local machine and helps synchronize the changes with the online repository via commits and pushes. 

## Step 4: Clone Bot Examples

There are several bots to play with and many more will be available soon from Dev Teams under their own organizations. In the meantime, the ones in [[AAMaster|https://github.com/AAMasters]] should suffice. Clone them in your local machine.

## Step 5: Test Run

### Request Connection String

Send us an email to feedback@advancedalgos.org to request connection strings for existing bots. You will receive an instructional email explaining how to use them.

### Configure Which Bot to Run

> NOTE: For the sake of this guide, we will use Microsoft Visual Studio as the IDE of choice. However, the platform is IDE-agnostic, thus you should be able to use your preferred IDE, as usual. If that is the case, we would be thrilled if you could share screen shots of your own set up so that we can add them here. Send any contributions to feedback@advancedalgos.com or submit a pull request with a new version of this page incorporating them.

We will first configure which bot to run. Open _AACloudPlatform.sln_. In the Solution Explorer window, scroll down and open _this.vm.config.json_. Enter one of the example bot’s name and path in the config file as shown below:

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/Visual-Studio-01.png]]

### Configure Process

Now we need to tell the platform which process to run. Bots may have multiple process. Each of them is defined in a file named _Interval.js_, located inside a folder in the root of the bot’s repository, as shown below:

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/Local-Files-01.png]]

In the example above, the bot has two processes: _Multi-Period-Daily_ and _Multi-Period-Market_. Choose either and copy the exact folder name. Back in your preferred IDE, click on the Project node and paste the process name as the value for the Script arguments field:

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/Visual-Studio-02.png]]

### Execute

Once running, the process should call the command prompt and start showing some activity:

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/Command-Prompt-01.png]]

### Debugging

By now you should be able to run any bot in your local environment and use typical debugging tools and procedures should anything go wrong.

Open the _IntervalExecutor.js_ module and place a breakpoint in the following line:

```
fileProcessingInterval.start(loopControl);
```

Now, run the IDE. When execution halts, press F11 to step into the module _Interval.js_ that will be loaded from the configured bot process folder. Once there you can set more breakpoints or debug the module step by step.

## Step 6: What to Expect After Execution

Remember bots' main activity is producing datasets. That is, once you run the AACloudPlatform and the platform calls the bot and process you just configured, you will not “see” much more than the command prompt popping up, as described earlier. Do not expect any graphics, browser windows or candlestick charts to pop up. The visualization of bots activity over a candlestick chart happens at a different moment. We will get there later. In the meantime, what you can actually see is the dataset generated by the bot in the form of _.json_ files stored in the cloud and the logs stored locally.

### Check Output

As stated above, you should be able to browse the output of the bot using the Azure Storage Explorer (_aatestnet > File Shares_). Check the bot’s code at _Interval.js_ to find out where the bot is storing its output. In the case of AAOlivia, search for the following string for the code building the path string:

```
let filePath
```

### Logs

Upon execution, the platform creates a folder named _Logs_ right outside the repository. Thus, you will find the Logs folder in the same directory as the AACloudPlatform. Each bot stores logs in its own sub-folders.