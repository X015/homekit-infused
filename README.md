# Home Assistant 0.94.1 compatible Lovelace setup.
My current Home Assistant install (current running version 0.94.2)

## Lovelace setup by jimzz011 May 2019 (*updated: 03/06/2019)
#### WARNING NOTE: This lovelace setup is mainly created for smaller sized smartphones like an iPhone X. It will work perfectly fine on larger displays but spacing on the right side might be off a bit (This work has been completed as of 12/06/2019, you can expect a new release within a few days). 

### Changes (03/06/2019): 
Added missing files like configuration.yaml etc.

## Introduction
Hello fellow home assistant users, I have started using Home Assistant almost a year ago and I absolutely love it. It is very addictive (as I think many of the people viewing this will know that feeling). Anyways I had done some basic HTML in the early 2000's but that was basically it. So I went into this software and this is what I have got to share. Bare in mind that I am just an amateur hobbyist that has no clue of what he's writing but I just try to read up on the community forums. It is not always as easy as it sounds knowing that Home Assistant changes fast, and I mean really fast. Things written down 2 months ago might already be outdated. So this is the code I came up with messing around with it and it works pretty good :P, ofcourse this is a work in progress and I will try to better the code, make it cleaner and look for details. For now I hope someone can make use of this.

### Screenshots and Video

Screenshot Summary (find more screenshots in the screenshots folder with the rest of the files):

<img src="https://github.com/jimz011/homeassistant/blob/master/screenshots/1.jpg" width="300" height="650">
<img src="https://github.com/jimz011/homeassistant/blob/master/screenshots/2.jpg" width="300" height="650">
<img src="https://github.com/jimz011/homeassistant/blob/master/screenshots/3.jpg" width="300" height="650">
<img src="https://github.com/jimz011/homeassistant/blob/master/screenshots/4.jpg" width="300" height="650">
<img src="https://github.com/jimz011/homeassistant/blob/master/screenshots/5.jpg" width="300" height="650">

<img src="https://github.com/jimz011/homeassistant/blob/master/screenshots/red1.jpg" width="300" height="650">
<img src="https://github.com/jimz011/homeassistant/blob/master/screenshots/red2.jpg" width="300" height="650">

#### Don't stop here! Watch the video!
There is SOO much going on in just 5 views that I can't possibly throw all the screenshots here without making this document unreadable. Please refer to the screenshots folder for more screenshots OR watch the video below which will give you the grand tour into this setup!

Video: CLICK ON THE IMAGE TO START VIDEO

[![Watch Video](https://img.youtube.com/vi/NFj7gwNAYPg/0.jpg)](https://youtu.be/NFj7gwNAYPg) 

sorry for the bad filming, I had to use accessibility tools to show you where I am actually pressing or it might get really confusing. This also meant it really limited my way of interacting with the device and thus making some errors sometimes. You will have to forgive me on that.

### How to use

Prerequisites:
- Home Assistant 0.93.x or 0.94.x
- A bunch of custom-cards, see below for links
- Patience
- Some more patience
- Have lovelace set in `yaml` mode, it has `!includes` which are NOT supported by the UI editor. To set lovelace to use the yaml mode put the following line into your `configuration.yaml`:
```
lovelace:
  mode: yaml
```
To use this Lovelace setup I highly recommend it that you only try this on a test environment or have at least basic knowledge of how to use Lovelace and custom cards. If you don't know how to work in Lovelace you could seriously hurt your setup to the point it will no longer render the page until you fix the error.
```
ALWAYS MAKE BACKUPS!!!!!!!!!
```
Make sure you always make a backup of your `ui-lovelace.yaml` file and other files if needed. I can not give guarantees that the setup works for anyone but myself. Everyone has different entities and more or less switches/sensors/camera's etc. If you happen to have a quite similar setup like I have you might get away with just changing the entity ID's but I highly recommend you to only use snippets of the setup and not just blatantly copy the entire thing and complain that it doesn't work. Because trust me, it isn't going to work :D.

Try to use RAW versions of the text to avoid any kind of wrongful spaces. Remember that I warned you :D!

Now lets get into the custom-cards and components you will need (components are optional as they might not apply to you).
Cards:
* [Bar-Card](https://github.com/custom-cards/bar-card) - This one is optional, as I don't use this (yet)
* [Button-Card](https://github.com/custom-cards/button-card) - The MOST IMPORTANT card of my setup, you will need this!!
* [Card-Modder](https://github.com/thomasloven/lovelace-card-modder) WILL PROBABLY NO LONGER BE USED IN THE NEXT RELEASE, DO NOT USE THIS ANYMORE!
* [Card-Tools](https://github.com/thomasloven/lovelace-card-tools) - ESSENTIAL many custom-cards depend on this, including Card-Modder
* [Compact-Custom-Header](https://github.com/maykar/compact-custom-header) - Not essential, however one of my most favorite cards, it makes swipe navigation possible in lovelace as well as the ability to tweak the header just the way you want! I recommend to install this.
* [Popup-Card](https://github.com/thomasloven/lovelace-popup-card) - ESSENTIAL this card is essential for my setup to work, without it the buttons on the front page will become useless.
* [State-Switch](https://github.com/thomasloven/lovelace-state-switch) - ESSENTIAL this card is used within the Popup cards.
* [Thermostat-Card](https://github.com/ciotlosm/custom-lovelace/tree/master/thermostat-card) - Not Essential you will not need this card to use this setup, you can replace this with a thermostat card of your choice.
* [Tracker-Card](https://github.com/custom-cards/tracker-card) - Not Essential, but handy for updates.
* [Upcoming-Media-Card](https://github.com/custom-cards/upcoming-media-card) - Required if you want the upcoming media card. You will require a custom component for Sonarr and Radarr as well. If you do not run something like Kodi/Plex and get the films/series yourself you will have no use for this.
* [Lovelace-Useful-Markdown-Card] WILL NO LONGER BE USED IN THE NEXT RELEASE, DO NOT USE THIS ANYMORE!
* [Vertical-Stack-In-Card](https://github.com/custom-cards/vertical-stack-in-card) - You do not need this and I would not recommend using it on this setup. I have modified the js to have a transparent background as this card enforces a background. I'd recommend using a regular vertical-stack for this. I only use this for my custom:check-marker-cards
* [Mini-Media-Player](https://github.com/kalkih/mini-media-player) - Beautiful replacement for the standard media player. I'd recommend this. The border-radius can not be set for iOS with a card-modder card on this. You will have to change the border radius in the js file of the card. Don't know what you are doing? Don't worry you can always redownload the file. Or just leave it as is.
* [Swipe-Card](https://github.com/bramkragten/custom-ui) - A card that makes use of swiper giving you endless swipe possibilities. For example you could make horizontal-stacks scroll horizontally and basically have an endless stack on the same space as you normally would have for 3 or 4 buttons (or maybe more depending on the size). Recommended! 
* [Calendar-Card](https://github.com/ljmerza/calendar-card) - This is the card I use to show our calendars. Recommended!
* [Simple-Weather-Card](https://github.com/kalkih/simple-weather-card) - This is the beautiful minimalistic weather card which is seen on the top of my home screen. I like it a lot as it takes so much less space than most weather cards and it is imo one of the least important data to know. All I need to know is, what is the Temperature and "Is it going to rain?".
* [Lovelace-PostNL](https://github.com/peternijssen/lovelace-postnl) - Highly recommended if you are a Dutch citizen (all Dutch citizens use this postal service). If you are not Dutch it is no use to install this. Get a card that does fit your needs! (if there is one ofcourse)
* [Mini-Graph-Card](https://github.com/kalkih/mini-graph-card) - The best card for making graphs by a long shot! Highly recommended!
* [Light-Entity-Card](https://github.com/ljmerza/light-entity-card) - A beautiful replacement for a color wheel. Can be used as a card or as seen in my setup (see video) with a popup card.

Custom Components:
* [RDW-Sensor](https://github.com/eelcohn/home-assistant-rdw) - Only useful for Dutch citizens. Used for car license plates, APK and Insurrance tracking.
* [Sonarr-Upcoming-Media](https://github.com/custom-components/sensor.sonarr_upcoming_media) - Required to use with Upcoming Media Card.
* [Radarr-Upcoming-Media](https://github.com/custom-components/sensor.radarr_upcoming_media) - Required to use with Upcoming Media Card.
* [XboxOne](https://github.com/hunterjm/hassio-addons/tree/master/xboxone) - Xbox One Component to control you Xbox one from Home Assistant

### TO DO (*updated: 12/06/2019) *Some categories have a work completed sign, expect this to be uploaded soon!
- Global theming to have the ability to have themes change dynamically, in automations and per user. This will include a day and night theme ###in Progress
- Cleaning up and converting card-modder to card-mod and useful-markdown-card to markdown-mod ###Currently in progress
- Scenes (continue the testing of my automations and where needed change) ###Postponed for later evaluation
- Birthdays ###Work Completed
- Xiaomi Roborock s55 Vacuum ###Work Completed
- Xiaomi Plantsensor Cards ###Waiting for Sensors to Arrive
- Energy Consumption Graphs ###Postponed to a future release
- Correct spacing for larger phone screens ###Work Completed
- Other graphs related to servers/computers etc. ###Postponed to a future release
- Rework climate view to accomodate more information ###in Progress
- And many more, which I can't think of at the moment ###Always in Progress

### Questions?

Please ask any question you have on the Home Assistant community forums.
https://community.home-assistant.io/t/homekit-inspired-lovelace-by-jimzz011-may-2019-ha-0-93-x-0-94-x-compatible/117086

## Thank you

Thank you for taking your time reading all this mess, I hope you have great fun with Home Assistant as I have and I will always try to help people out where I can, but as I said I am only an amateur so do not expect miracles :P.
Anyways have fun and see you next time!

## A very special thanks to
@ciotlosm

@thomasloven

@balloob

@gluwc

@maykar

@robbiet480

@ljmerza

@iantrich

@kalkih

@bramkragten

@peternijssen

@eelcohn

@hunterjm

@jc2k

@kuuji

@romrider

@everyone I forgot to mention

I am really sorry, I have tried to get you all. But also a very big thank you to all of the ones not mentioned here. And ofcourse the Home Assistant community which helped me out a lot.

## Author

Jimz011
