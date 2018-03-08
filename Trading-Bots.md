AA Trading Bots have a lot in common with Indicator Bots. They consume indicator's datasets in the quest to implement specific trading strategies and signal the AA Platform for it to place orders with exchanges.

## Step 1: Planning

As usual, a little planning is in order before starting. What kind of trading strategy do you wish to implement? In what markets? What indicators do you need? Is there any existing AA Trading Bot that is similar to what you envision?

Truth be told, there are very few bots in offer at this early stage, but more and more are coming. The idea is to start from a good base, so cloning an existing bot and working on top of it may be a good idea.

## Step 2: Exchanges API

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

Next, you will use the information in the API Key to a create a file with the following structure:

```
{ "Key" : "6HS4YUEB-865UY9W4-KGHEHHJ-GH72ETG1", "Secret" : "1a3529851a05439asdasdw63426378ggd65701ac4a5d53c4859aa3511a8aa65acbd7e713bba755d0b1591ebe3a7618a71393ef4d3d11310628e1db"}
```

Save the file in your local environment. Make sure you place it somewhere outside the folder structure you are using for your repositories to make sure the file doesn't accidentally end up in GitHub. Use the following naming convention:

"**AA**" + **BotName** + "**.**" + **ExchangeName** + "**.json**"

e.g.: AAMariam.Poloniex.json





