# TextBar Live

_Date: 2016.12.26_

## Introduction
TextBar Live is a cloud-hosted service from which you can see all your TextBar items on a single web page. If you have, or manage, multiple Macs this is invaluable, especially if those Macs are remotely located (perhaps somewhere like [Macminicolo](https://macminicolo.net)).

TextBar Live is a paid subscription service.

## Pricing
* 1 device = $1 per month
* 3 devices = $2 per month

You can purchase multiple subscriptions; if you purchase a ‘3 device’ subscription and a ‘1 device' subscription, you will have a subscription for 4 devices.

## Getting Started
* Go to: [https://app.textbar.co](https://app.textbar.co)
* Click on the ‘Login’ section and log in
	* This will create an account linked to your Google email
		> * Note: TextBar Live currently only supports Google authentication
* Click on the ‘Accounts’ section
* Purchase a subscription
* Download TextBar Mac app, from:
 [http://www.richsomerfield.com/apps/textbar/TextBar.app-2.0.241.zip](http://www.richsomerfield.com/apps/textbar/TextBar.app-2.0.241.zip)
* Install and start the new TextBar Mac app
* Go to the TextBar / Preferences / Live
* Enter your API token, from: [https://app.textbar.co/#/account](https://app.textbar.co/#/account)
* Click 'Enable' to register this device
	* When registered, it'll be listed here: [https://app.textbar.co/#/devices](https://app.textbar.co/#/devices)
* You should see your TextBar items here: [https://app.textbar.co/#/items](https://app.textbar.co/#/items)
	* Note: For the first time, you may need to restart the TextBar Mac app, or, click 'Submit all items'

## The API

TextBar Live has an API that is convenient for managing headless servers. It allows for registering devices and items from the command line.

### Registering and Activating Devices

-   Generate a new GUID for your device identifier, then submit it:

	`'curl -XPOST -u richs\@gmail.com:00000000-f206-0000-8ef1-000000000000
    https://app.textbar.co/api/devices/00000000-cbb1-0000-b2db-000000000000 -H
    "Content-Type: application/json" -d '{"name":"my temperature sensor"}'`

	* 'richs@gmail.com:00000000-f206-0000-8ef1-000000000000' is your API Token
	* '00000000-cbb1-0000-b2db-000000000000' is your Device GUID (required to submit data)


### Submitting and Updating TextBar Items

-   Generate a new GUID for your item identifier, then submit it:

	`curl -XPOST -u richs\@gmail.com:00000000-f206-0000-8ef1-000000000000
    https://app.textbar.co/api/devices/00000000-cbb1-0000-b2db-000000000000/items/6b996108-0000-4331-0000-000000000000
    -H "Content-Type: application/json" -d '{"text":"hello\\nworld"}'"`

	* 'richs@gmail.com:00000000-f206-0000-8ef1-000000000000' is your API Token
	* '00000000-cbb1-0000-b2db-000000000000' is your Device GUID (required to submit data)


> Notice the '\\\\n' for a newline.

Once the device has been registered, you don't need to register it again unless you delete it. Creating and updating a TextBar item use the same API.