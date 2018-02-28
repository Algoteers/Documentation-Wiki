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

Click **Next** and **Connect **in the following screen.

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

## Step 3: Clone the Platform

Clone the [[AACloudPlatform|https://github.com/AdvancedAlgos/AACloudPlatform]] repository in your local machine.

### Using GitHub Desktop

If you are an advanced GitHub user you are probably using Git via the command-line. If you are not, we recommend [[downloading and installing the GitHub Desktop|https://desktop.github.com/]] application.

If you are not familiar at all with GitHub, we highly recommend you invest the time in learning it, as it is the most popular collaboration and version control system. For further information on how to use GitHub Desktop, please refer to the [[Getting Started with GitHub Desktop guide|https://help.github.com/desktop/guides/getting-started-with-github-desktop/]] or [[watch this video tutorial|https://www.youtube.com/watch?v=GqNAD4XoZ6k]].

Once you have launched GitHub Desktop and logged in with your GitHub credentials, this is what you need to do to clone the platform’s repository:

Go to _File > Clone Repository_

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/GitHub-Desktop-01.png]]

Click on the URL tab and paste the repository URL in corresponding field: https://github.com/AdvancedAlgos/AACloudPlatform. Choose where in your local machine GitHub should copy the files.

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/GitHub-Desktop-02.png]]

Once you clone the repository, GitHub desktop keeps track of the changes that may occur in the files in your local machine and helps synchronize the changes with the online repository via commits and pushes. 
