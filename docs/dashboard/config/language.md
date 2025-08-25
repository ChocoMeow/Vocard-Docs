# Languages

Vocard Dashboard provides support for multiple languages. Additionally, Vocard Dashboard allows you to easily customize your own language. Simply follow the steps below.

## Language Codes

To find the appropriate `LANGUAGE_CODE`, you can refer to the [IETF Language Tags](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry) or consult resources like:

- [ISO 639 Language Codes](https://www.iso.org/iso-639-language-codes.html)
- [Wikipedia: List of Language Codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)

## Add Translations
1. **Extract Messages**: Initialize the messages by running:
   ```bash
   pybabel extract -F babel.cfg -o messages.pot .
   ```
   
2. **Create Translation Files**: For each new language, run the following command:
   ```bash
   pybabel init -i messages.pot -d translations -l LANGUAGE_CODE
   ```
   Replace `LANGUAGE_CODE` with the appropriate code (e.g., `es` for Spanish).

3. **Add Translations**: Navigate to:
   ```
   translations/LANGUAGE_CODE/LC_MESSAGES/messages.po
   ```
   Open the `.po` file and add your translations:
   ```po
   msgid "Hello, World!"
   msgstr "¡Hola, Mundo!"  # Spanish translation
   ```

4. **Compile Translations**: After adding translations, compile them:
   ```bash
   pybabel compile -d translations
   ```

5. **Test Your Application**: Run your dashboard and verify the new language.