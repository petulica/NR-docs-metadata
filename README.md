# NR-docs-metadata
 model for metadata of documents in national repository

Reasons for some changes compare to model for data:
* subjectCategories - changed to optional - reason: old data from NUSL
*  dates - added dateIssued for original publication and dateAvailable stays for managing access to files in the repository. Solution is based on use-case of article preprints and postprints
* publisher - for docs is NOT a taxonomy but free text with the value whisperer, because of the variety in publishing, especially articles
* accessibility - přidáno - zejména pro harvest, slovní vyjádření o přístupu (př. volně dostupné v repozitáři Univerzity Karlovy, dostupné z ústavu fyziky AV ČR). u ručně vložených v případě restricted by se dalo asi také využít
* languages - přidáno minItems 1
* relatedItem - změna povinnosti - pro dokumenty nejsou povinní creators, jelikož se většinou bude jednat o vztah část - celek, zejména pak u článků, odkazy na časopis.
* recordIdentifiers - přidána sekce systémových indentifikátorů pro účely harvestu, importu a migrace.
* series - added - works also kind of like tagging similar things, so might be useful also for data. matter of discussion. Title of the series is required if the field is applied
