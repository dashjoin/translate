# Dashjoin Translate

For anyone who needs to translate a webpage or application. Dashjoin Translate allows you to leverage sophisticated machine translation, review and change translations, and deploy them to your project in GDPR compliant way in a matter of minutes. Unlike other solutions, Dashjoin Translate cleanly separates translations from your source code and does not rely on 3rd party services at runtime.

Dashjoin Translate is **free** up to a project limit of 20.000 characters and requires **no signup**. To get started, you can translate any public website using our [online service](https://dj-translate-srv-dev-qtmq6xeijq-ey.a.run.app/).

## Activating Translation Mode

When using Dashjoin Translate, there are two modes:

* Production mode: this is the mode that visitors and users of your website or application see. Dashjoin Translate is active in the background and replaces texts on the page depending on which display language is chosen. Users can switch the display language using a language picker widget. Note that in production mode no calls to the translation API are made. All texts are served from the translation file you create.
* Translation mode: in this mode, the translation screens are active and calls to the translation API are being made. When using the online service, the translation mode is activated by default. Once you added translations to your project, the translation mode can be activated via the browser console (see the deployment section below).

## Translation Menus

This section documents the functionality you use to translate your project.

### Welcome Screen

The welcome screen only requires you to pick one target language. Once you confirm this selection, your project is initialized and the page you are currently on is translated into the language you selected. Note that the free version of Dashjoin Translate uses the Google translation service and that the contents of the page will be sent to it.

### WYSIWYG Editor

Once you confirm your target language choice in the welcome screen, you enter the WYSIWYG editor. Your website's or application's page is displayed and functions as usual. The following Dashjoin Translate elements are available:

* Context menu: you find the context menu in the lower left corner of the screen. Click it to open the main menu
* Language picker: the language picker in the lower right corner of the screen allows you to switch the display language on the page. By default, this element is also visible in production mode
* Hover menu: when you hover over any text, a green or red background indicates whether the text is being translated (green) or not (red). If you remain over the text for three seconds, a menu appears that lets you change the existing translation, mark the text not to be translated, or include it back into the set of translated texts. For more information on excluding texts, see the section on rules below.

### Main Menu

The main menu provides you with a quick summary about your current translation project. Use the combo box to change the display language or navigate to either the translations, rules, or configuration pages.

### Translations

The translations menu provides you with an overview table. Each row represents a page in your website or application and indicates the number of translated texts are well as the translation coverage for each language. You can machine translate all missing texts right here or click the table cells to get to the translation summary for a given page and language.

The translation summary page shows you the original text, its translation, and whether the machine translation was modified by you or another user. Simply click the target column to add or edit the translation.

#### Placeholders

Sometimes the texts contain hyperlinks or boldface passages. Of course, in the translations, these elements must be in the correct places. The translations dialog displays these elements via placeholders that are shown as oval numbered elements at the respective position in the original text and its translation. When you edit the translation, these placeholders are shown as XML elements:

```
<ph id="1"/>
```
You can move and edit these placeholders, in case the machine translation did not place them at the right position.

#### Arguments

There are cases, where dynamic content is embedded in text. Consider the following example sentence: "You uploaded 15 images to this site", where the number 15 is obviously a dynamic element. The system marks 15 as an argument. An argument is shown as a numbered green rectangle. When editing, it is shown as an XML element. The sentence above is shown as: "You uploaded <x id="1"/> images to this site".

When you are happy with the translations, you can download the text bundle from this page. See the section below on how to add this file to your project for production.

### Rules

Any website or application contains parts that must not be translated, for instance a table displaying dynamic results from a database. Dashjoin Translate uses [CSS selectors](https://www.w3schools.com/cssref/css_selectors.asp) to identify these elements. The rules dialog shows an editable overview table with each row representing one rule. A text is not translated if its HTML element does not match any of the rules.

Note that it is best practise to make the rules as general as possible in order for them to be immune to layout changes performed on your website or application later on. There's also a name and description field that allows you to document the reason why a given element is to be excluded. Rules can also be activated and deactivated.

New rules applying to specific texts can also be added using the WYSIWYG editor. Likewise, a rule causing a text to be excluded can be deactivated in the WYSIWYG editor.

### Configuration

The configuration screen allows you to specify more language option. Dashjoin Translate guesses the original language used by your website or application. The configuration screen allows you to override this value. Correctly setting this parameter helps the translation API to generate better translations. The second option allows you to specify which languages you would like your project to be translated into. Note that you can always add new languages later on. 

### Language Picker

The language picker is a small widget that provides a default functionality for your users to pick their preferred display language. For information on the available parameters and how to customize this component, please see the translation file format section below.

## Use Dashjoin Translate for Your Project

This section describes how you can deploy the translations to your project.

### Adding the Translate Script

Dashjoin Translate requires you to add the following files to your website or application:

* browser.js: this script contains the Dashjoin Translate runtime
* dji18n.json: this is the file you downloaded from the translations page

The browser.js file must be added via an HTML script element. You may have the script src attribute point to an external URL or download the script and host if locally.

By default, the script looks for the translation files at the URL /dji18n.json. You may also specify the URL via the dji18nurl attribute:

```
<script src="..." dji18nurl="..."></script>
```

Finally, there's the option to copy and paste the file contents directly into a script tag which saves the HTTP round trip:

```
<script src="..."></script>
<script id='dji18n'>
  contents of the file dji18n.json
</script>
```

The following sections shows examples of how to do this for different platforms.

#### Static HTML

```
<html>
  <head>
    <!-- insert this script tag and make sure the translations are available at /dji18n.json -->
    <script src="https://github.com/dashjoin/translate/blob/main/browser.js"></script>
  <head>
  ...
```

#### Wordpress

There are several options you can use to add a script to your wordpress site. The most convenient is by using the [Insert Headers and Footers Plugin](https://wordpress.org/plugins/insert-headers-and-footers/).

* Upload the translation to the media library (by default Wordpress disallows .json files - please rename the file to dji18n.txt in this case)
* Install the "Insert Headers and Footers" plugin
* Go to Settings > Header and Footer Scripts
* Enter the script tag shown above to "Scripts in header" and save the settings

```
<script 
  src="https://github.com/dashjoin/translate/blob/main/browser.js"
  dji18nurl="/wp-content/uploads/YEAR/MONTH/dji18n.txt"
></script>
```

### Updating Translations

This section describes how you can add or update translations:

* Visit your website or application
* Open the browser console (CTRL + SHIFT + I in most browsers)
* In the script console, enter: dashjoin.i18n.enableDevMode()
* This re-activates the translation mode
* Perform your changes
* Download the new version of the dji18n.json file and add it to your site as described in the section above

### Translations File Format

This section describes the translation file format. The file must have a valid JSON structure. Note that you can edit this file and put it under version control.

* id: domain name of the project to be translated
* language: the source language
* targets: array of target languages
* rules: array of rules with
  * name: rule name used in the WYSIWYG editor
  * rule: the CSS selector to determine which HTML elements exclude
  * description: rule documentation
  * disabled: flag indicating whether the rule is disabled
* resources: map with the languages as keys
  * namespaces: array of pages
    * id: page path
    * resource: map with the original text as the map key
      * text
      * ctime
      * status
      * mtime

TODO: language picker options

