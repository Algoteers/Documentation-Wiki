As usual, a little planning is in order before starting. What kind of trading strategy do you wish to implement? In what markets? What indicators do you need? Is there any existing AA Trading Bot that is similar to what you envision?

The idea is to start from a solid base: cloning an existing bot and working on top of it is the easiest way to get started.

## Overview

At this early stage, the AA Platform along with existing trading bots templates solve several of the main issues around algorithmic trading:

* Infrastructure to run bots in the cloud;
* Crucial historical and live trades and volumes data;
* Connection with exchanges, placement and handling of orders.

This leaves the Dev Team free to focus in the creative side of things: coming up with and implementing a trading strategy.

In its current version, the AA Platform provides an object (platform) containing several other objects:

* datasource: preloads ready-to-consume data comprised of candlesticks, volumes and stair patterns;
* assistant: opens, closes and moves positions;
* processDatetime: keeps official execution time, to be recorded in logs and used to retrieve stored data.

The overall strategy when working with trading bots can be summarized in the following bullet points:

* Bots are executed every one minute. 
* Each time the bot runs, it first needs to understand the context of the current execution. Does it have any open positions? Have orders placed at an earlier time been filled?
* Then the bot embarks in the calculations required by its trading strategy. At this point in time, there are very few indicators offering processed information. As a consequence, the bot needs to do all calculations internally. Almost all Technical Analysis indicators are calculated from trades and volume data. Their formulas are in the pubic domain and even code is readily available if you search around. You are free to use open source code within your bot's code.
* Once calculations are performed, the bot decides what to do, and uses the platform to place orders on the exchange.

## Particulars of Cloning a Trading Bot

We covered [[elsewhere|Starting out Your Own Bot]] how to clone a bot and set it up to build your own bot on top of it. Please follow the same guidelines when cloning a trading bot. 

In addition, you need to know the following:

### Running Mode

When you run a trading bot in your local environment you can configure the AACloudPlatform to run it either continuously or only once. This is to avoid the consequences of stopping a trading bot forcefully, which may cause the bot to loose sync with the exchange (open positions may not be taken into account in subsequent runs).

By now you should be familiar with the configuration at _this.vm.config.json_:

```
{
  "bot": {
    "path": "../AAName-Trading-Bot"
  },
  "stopGracefully": "false"
}

```

What we haven't discussed so far is the _stopGracefully_ parameter. When the value is _false_ the platform will run the bot continuously. When the value is _true_ the platform runs the bot once and stops it afterwards.

If you ran the bot with _"stopGracefully": "false"_ and need to stop the bot, then simply go back to the config, change the parameter to _true_, save the file and wait. Upon the next run, the bot will be stopped.

## Exchanges API

The AA Platform places orders on exchanges through the use of APIs. You will need to create an API and configure your bot to use it.

### Creating the API Key

Let's take Poloniex as an example. This is how you create an API Key:

Go to the tools menu and select _API KEYS_...

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/Poloniex-API-01.png]]

If you have never used APIs before chances are they are disabled at the exchange. So before actually creating one you will need to enable them...

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/Poloniex-API-02.png]]

You will need to follow the validation process involving checking your email and confirming your choice. Once that is taken care of, go back to the tools menu and click _API KEY_ again. You should now see a screen offering to create a new key...

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/Poloniex-API-03.png]]

Once you create your key, the system will present it as follows...

[[https://github.com/AdvancedAlgos/Documentation/blob/master/Media/Dev-Teams-Getting-Sarted-Guide/Poloniex-API-04.png]]

**Make sure you DO NOT enable withdrawals nor IP access restrictions**.

### Creating an API Key File

Next, you will use the information in the API Key to a create a flat file with the following structure but using your own Key and Secret information:

```
{ "Key" : "6HS4YUEB-865UY9W4-KGHEHHJ-GH72ETG1", "Secret" : "1a3529851a05439asdasdw63426378ggd65701ac4a5d53c4859aa3511a8aa65acbd7e713bba755d0b1591ebe3a7618a71393ef4d3d11310628e1db"}
```

Create a folder named _API-Keys_ at the same level of the platform's repository and save the file using the following naming convention:

"**AA**" + **BotName** + "**.**" + **ExchangeName** + "**.json**"

e.g.: AAMariam.Poloniex.json

> NOTE: Make sure the folder and file doesn't accidentally end up in GitHub! Your API KEYs should be kept secret! 




