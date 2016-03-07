Firewatch Community Localization
==============================

Hello! This is Patrick from Campo Santo. At present, we've contracted professional translators to create full-text localizations of Firewatch in five languages: Spanish, French, Russian, German and Simplified Chinese. We love seeing non-english speakers play our game, but as a small team we have limited resources and aren't able to localize it for everyone. 

That's why we've posted our full text-string database here: *localization by and for fans*. If you love Firewatch and want to make it more accessible to others, feel free to download the data, test it out, and contribute your translations back to this repository for others to download and use. 

Firewatch is currently subtitled in English and Russian on Steam. Our professional localizations in German, Spanish, French and Simplified Chinese are coming soon for Steam and PS4. We'll update this README as this patch arrives, as well as if we add any more official localizations.

Worth noting: a [community-run Firewatch project](https://www.transifex.com/firewatch/firewatch-localization) has also sprung up on Transifex, using the data found here. If you're interested in contributing, take a look!

Important note: at present, Firewatch's included fonts and layouts do not support characters outside the ISO Latin-1 set. We apologize for this limitation and hope that we will be able to remove it at some point.

All English game content provided here is copyright 2016, Campo Santo. All rights reserved.


Where to find the data
-----------
Here on our Github page, you’ll find complete text dumps of every string in the game— from menu choices, to spoken dialog captions, to UI and note text. You can download the entire repository as a Zip file or as a full Git repo. 

The Zip file contains everything you need and is the simpletst for most people. Git is somewhat complicated to learn, but makes it possible to track your changes and merge in updated versions of our English source strings. If you're serious about doing a full fan loc, we recommend making a Github account and learning how to [pull down a git repo](https://help.github.com/articles/set-up-git/). 


Project Organization
-----------
Each language is in its own top-level directory, named by the language code. We include two languages for you to base yours off of: `en_us` (English) and `vg_mt` (Mëtal). Mëtal is a fake language we made up to test our localization system; it mimics English but uses random Unicode characters to make it clear what parts of the UI are being localized properly.

At the top level of the project, open the file `SupportLanguages.loc`. Inside you'll see the languages contained in our repo and their short language codes. When copied into the proper directory on your computer, this file tells the Firewatch app which language options to display in the Settings menu.

Also note the file `localization.en_us`, which is by far the largest in the project. This contains every string in the game that's NOT a conversation between Henry and Delilah, which leaves a lot of strings, including in-game notes, menus and all other UI text.

Now open the `vg_mt` folder. All the strings in the game are here as a series of files. The filename is a "section", which is a bunch of lines organized around concept or a conversation topic. The files are in _JSON format_ using _Unicode (UTF-8) encoding_. We recommend using a text editor that understands Unicode automatically and can use JSON syntax highlighting, such as Sublime Text.


Playing Firewatch with fan localizations
------------

First, find your Localization folder inside your computer's "persistant data path". This path is located on different places according to your OS. 

    Mac: `/Users/<YourUserName>/Library/Application Support/CampoSanto/Firewatch/Localization`

    Windows: `C:\Users\<YourUserName>\AppData\LocalLow\CampoSanto\Firewatch/Localization`

Download this repo onto your computer. Then, copy the *contents* of all of the localization folders into the path above. Not the folders themselves, just the contents. When you're done, all of the language files, plus the SupportedLanguages.loc file, shoudl all be in one directory together.

Start Firewatch and you should now see a language dropdown with all these new language options included.


JSON Syntax
------------

Each file is structued as a "JSON Object", which is a series of _key:value pairs_.

These pairs have the original English string on the left and the localized string on the right, with a ":" or "colon" in between. Each pair will be on its own line, and lines are separated with a comma. 

For example, here is a very short example file, selected from `About Brian Goodwin - General - Dialog.vg_mt`: 

```json
{
  "Couldn't handle your charms?": "Çóùldñ't häñdlë ÿóùr çhärms?¿?",
  "Not many can.": "Ñót máñÿ çáñ.",
  "Unsurprising.": "Üñsúrprîsîñg.",
  "Huh.": "Hùh."
}
```

We have an English string on the left, and then our fake "Mëtal" language string on the right. The strings are enclosed in "straight quotes" and separated by a colon, and at the end of each line _except for the last one_, we have a comma. Also notice that the entire file is enclosed in curly braces, which look like this {}.

The entire file must be valid JSON in order to work in the game. There are great online tools available for validating / formatting your JSON, here is one you can cut and paste your text into to test it: https://jsonformatter.curiousconcept.com

The example above is very simple and doesn't include some issues you will encounter, like the need to *escape newlines* and other special characters within your strings. If you have any questions don't hesitate to open a Github issue for help. There's more info on JSON format here: http://www.w3schools.com/json/json_syntax.asp

Also, remember to save your file as UTF-8 so that non-western characters will be displayed properly.


Creating your own localization
-----------
Your localization should have a unique file extension at the end of every file. Country codes work great for this: `.en_uk` specified "English, United Kingdom" and you are welcome to mirror that style for your own locale. Make sure every file has this unique extension and that you organize your files into a subdirectory the same way.

To test your localization locally, first make sure that _every file in it is valid JSON_ (see above). Then, add a new line to the `SupportedLanguages.loc` file at the root of this project, with the name of your language, a pipe, and the file extension you used. See the next section for how to move these files into a place where Firewatch can use them.

Before you test your own, let's first test Mëtal, our psuedolanguage we at Campo Santo use to test loc. Copy all of the files inside of the vg_mt directory into the Localization folder, along with `SupportedLanguages.loc`. Restart Firewatch and you should now see a languages dropdown in the settings menu; changing the language to Metal should immediately translate all menus into our weird fake language.

Now try doing the same with your own localization. Make sure `SupportedLanguages.loc` is updated with your new info, and then copy it and the contents of your localization's subdirectory into the persistent data path's Localization directory. When you're done, that directory should contain the Metal files AND your own loc files, all in the same folder. Restart Firewatch and see if your language works!

When Firewatch can't find a localized version of a string in the selected language, it will always fall back to English and display that. If you're seeing English strings which you think you've translated, several things might be wrong. Before you open a Github issue and write to us, first test that same string, in game, in Mëtal. If it works in that localization, but not in your own, something is wrong with your files! Some things to check for: filename typos, missing strings, unclosed or unescaped quotation marks, or other issues that would invalidate your JSON.

If you're still stuck, try opening a Github issue so that we or another member of the localization community can help.


Contributing back to the community
-----------
You may find in-progress localizations to contribute to over at [Transifex](https://www.transifex.com/firewatch/firewatch-localization). This is a community-run project (unaffiliated with Campo Santo) but it's the most active fan localization community at present.

If you have a complete localization of your own you'd like to share, contribute it back to this repository so others can benefit from it. To do so, the best way is to fork the repo and send us a pull request: https://help.github.com/articles/fork-a-repo/

If this is too complicated, no worries! I'm happy to help. Just create a new archive or zipfile of your project structure and email patrick@camposanto.com. I'll add your work (with proper credit) to this repository so others can find it more easily.


Licensing
-----------
All English text content provided in this repository is Copyright 2016, Campo Santo, all rights reserved. 

However, you are permitted a use these strings as a reference for creating a "community localization", meaning a complete, line-for-line translation of the English text to another language.


Community localization licensing
-----------
We ask that, in creating a localization, you contribute it back to the community. If you do so, we ask that you send a copy to us (see below) and release it with the following license text included in the repository: 

All Firewatch community-contributed localizations are licensed under the [Creative Commons "BY-NC 4.0" License](http://creativecommons.org/licenses/by-nc/4.0/), visible here: http://creativecommons.org/licenses/by-nc/4.0/

Others players are free to access, play, and remix your localization strings so long as they, too, contribute them back to this repository free of charge. In this way, people will be able to improve upon the work of others and offer the widest variety of high-quality translations of this game.
