# NR-docs-metadata
 model for metadata of documents in national repository

Reasons for some changes:
* subjectCategories - changed to optional - reason: old data from NUSL
*  dates - added dateIssued for original publication and dateAvailable stays for managing access to files in the repository. Solution is based on use-case of article preprints and postprints
* publisher - for docs is NOT a taxonomy but free text with the value whisperer, because of the variety in publishing, especially articles
* accessibility - přidáno - zejména pro harvest, slovní vyjádření o přístupu (př. volně dostupné v repozitáři Univerzity Karlovy, dostupné z ústavu fyziky AV ČR). u ručně vložených v případě restricted by se dalo asi také využít
* languages - přidáno minItems 1
