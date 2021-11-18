# Dashjoin Translate

For anyone who needs to translate a webpage or application. Dashjoin Translate allows you to leverage sophisticated machine translation, review and change translations, and deploy them to your project in GDPR compliant way in a matter of minutes. Unlike other solutions, Dashjoin Translate cleanly separates translations from your source code and does not rely on 3rd party services at runtime.

Dashjoin Translate is **free** up to a project limit of 20.000 characters and required **no signup**. To get started, you can translate any public website using our [online service](https://dj-translate-srv-dev-qtmq6xeijq-ey.a.run.app/).

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

TODO: placeholders

TODO: arguments

### Rules

### Configuration

### Language Picker

## Use Dashjoin Translate for Your Project

### Adding the Translate Script

### Adding the Translations File
