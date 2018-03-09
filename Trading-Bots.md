As usual, a little planning is in order before starting. What kind of trading strategy do you wish to implement? In what markets? What indicators do you need? Is there any existing AA Trading Bot that is similar to what you envision?

The idea is to start from a solid base: cloning an existing bot and working on top of it is the easiest way to get started.

## Overview

At this early stage, the AA Platform along with existing trading bots templates solve several main issues involving algorithmic trading:

* Infrastructure to run bots in the cloud;
* Crucial trades and volumes data;
* Connection with exchanges, placement and handling of orders.

This leaves the Dev Team free to focus in the creative side of things: coming up with and implementing a trading strategy.

In its current version, the AA Platform provides an object (platform) containing several other objects:

* context: keeps historical information about what the bot did on previous executions along with current bot status;
* datasource: preloads ready-to-consume data comprised of candlesticks and stair patterns;
* assistant: opens, closes and moves positions;
* processDatetime: keeps official execution time, to be recorded in logs and used to retrieve stared data.

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



