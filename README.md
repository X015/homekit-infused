This is beta 10 of HKI 2.0.0

Changes:
- Fixed bug where it would not show the rooms in lights/devices view
- Fixed bug where it would not show the floor selector in lights/devices view 
- Fixed bug that prevented the Romanian language from being selected
- Fixed bug where it would not show thermostats on the climate page for some users
- Fixed bug in the main menu's edit mode, you can no longer select/create columns in the menu
- Fixed bug where the initial onboarding process will take you to the wrong page
- Added Covers view (this might not work as I can't test it personally!), also added are cover view's edit mode and all customizations that other views already can (e.g. change it's header name, hide/show the widgets, user_content)
- Added Covers to the device_counter.yaml file
- Added Covers to the extra_settings.yaml file
- Corrected documentation's indentation
- Removed python_script (this wasn't needed and I had added it by accident, you can safely remove the entire folder if you don't use python_scripts yourself)
- Updated all addons/custom components on the repo (only useful for users that don't use HACS)
- Bugfixes

Unmentioned changes from beta 8/9:
- Thermostat button actions have been reverted to its original behavior. This makes more sense with the rest of the setup.

How to update?
- Step 1: remove the packages and dashboards folder (do NOT overwrite as it might leave deleted files). If you already use packages in your personal setup remove the HKI folders inside that folder instead.
- Step 2: copy the new packages and dashboards folder to the root of your setup
- Step 3: copy the `user_content/views/covers_user_content.yaml` file to your own `user_content/views` folder
- Step 4: add the following line to your `extra_settings.yaml` file, make sure you only add the covers line as the header_secondary line already exists!
```
header_secondary:
  covers:
```
- Step 5: add the following text to your `device_counters.yaml` file:
```
# All Covers
all_covers:
  entities:

# All Garage Doors
all_garage_doors:
  entities:
```
- Step 6: You are done!

NOTE: To make the covers button work in both the menu and frontpage you MUST fill in a sensor badge (this is usually done at onboarding). I assume you have already done the onboarding process, so go to HKI Settings > Button Config > Covers and put either a device_counter entity or `input_number.empty`. THIS IS MANDATORY even if you do not plan to use this!
EXTRA NOTE: Some new text have been added and therefor languages previously translated might be incomplete (e.g. vacuum page is only translated in a few languages). If your language isn't there you can either set it to English once and then back to your own language (this way at least the English titles will be there). Else fill in your own words which can be done in the HKI Settings > Other Translations. If you speak any of the included languages, please be so kind to fill in additional translations and send them back to me. If your language isn't supported, you can always help me translating and it will be added in any of the upcoming versions.

Thanks and Enjoy!
