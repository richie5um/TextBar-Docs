# TextBar Live - Alpha

_Date: 2016.12.26_

## Introduction to TextBar Live
TextBar Live is a cloud-hosted service from which you can see all your TextBar items on a single web page. If you have, or manage. multiple Macs this is invaluable, especially if those Macs are remotely located (perhaps somewhere like [Macminicolo](https://macminicolo.net)).

## Getting Started
* Go to: [https://app.textbar.co](https://app.textbar.co)
* Click on the ‘Login’ section and log in.
	* This will create an account linked to your Google email.
		> * Note: TextBar Live only supports Google authentication at the moment.
* Click on the ‘Accounts’ section.
* Purchase a 3 device subscription. Use a Coupon Code, if you have one, to get a discount.
	> * Note that you need to provide credit card or Paypal details even though it is free.
* Save the ‘API Token’ by copying it to your clipboard or otherwise preserving it.
* Download the Mac alpha version of TextBar from here:
 [http://www.richsomerfield.com/apps/textbar/TextBar.app-2.0.241.zip](http://www.richsomerfield.com/apps/textbar/TextBar.app-2.0.241.zip)
 
	{>> I don't have a plist file currently. I'm assuming this was eliminated in the 2.0.241 release? <<}
	{-- * Note: This replaces your existing TextBar app. The format of the TextBar items is the same, so it should be a seamless experience. However, you should backup your TextBar items by making a copy of this file:
		* /Library/Preferences/com.RichSomerfield.TextBar.plist--}
{--* To configure the Mac client you need to run these commands:
	* Configure the Service
			`defaults write com.RichSomerfield.TextBar CloudURL -string 'https://app.textbar.co'`
	* Configure the API Token using the API Token you saved previously
			`defaults write com.RichSomerfield.TextBar CloudToken -string 'richs@gmail.com:12345678-1234-1234-1234-123412341234’`--}
			
* Start the new TextBar app
* Go to the Textbar Live Pane: TextBar / Preferences / Live
* Enter the API token you saved previously
* Restart TextBar app
* Hopefully it should now be working and you should see your TextBar items on the web page.

## The API

TextBar Live has an API that is convenient for managing headless servers. It allows for registering devices and items from the command line.

### Registering and Activating Devices

-   Generate a new GUID for your device identifier, then submit it:

	`'curl -XPOST -u richs\@gmail.com:00000000-f206-0000-8ef1-000000000000
    https://app.textbar.co/api/devices/00000000-cbb1-0000-b2db-000000000000 -H
    "Content-Type: application/json" -d '{"name":"my temperature sensor"}'`

### Submitting and Updating TextBar Items

-   Generate a new GUID for your item identifier, then submit it:

	`curl -XPOST -u richs\@gmail.com:00000000-f206-0000-8ef1-000000000000
    https://app.textbar.co/api/devices/00000000-cbb1-0000-b2db-000000000000/items/6b996108-0000-4331-0000-000000000000
    -H "Content-Type: application/json" -d '{"text":"hello\\nworld"}'"`

Notice the '\\\\n' for a newline.

Once the device has been registered, you don't need to register it again unless
you delete it. Creating and updating a TextBar item use the same API.

## Pricing
TextBar Live is a paid subscription service. Current fees are:

* 1 device = $1 per month
* 5 devices = $2 per month

The system is configured to allow you to purchase multiple subscriptions, and it will total your allowed devices. So if you purchased a ‘3 device’ subscription and a ‘1 device subscription’, you would have a subscription for 4 devices.

The pricing is subject to change, which is why the subscriptions are on a monthly basis. Any price changes will be based on the hosting and support costs. Ideally, they will be reduced, but I can’t afford to run this service at a loss. And, at this stage, I have no idea how much it will cost to run.


