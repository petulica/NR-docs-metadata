# NR-docs-metadata
 model for metadata of documents in national repository

Reasons for some changes compare to model for data:
*  dates - added dateIssued for original publication and dateAvailable stays for managing access to files in the repository. Solution is based on use-case of article preprints and postprints
* publisher - for docs is NOT a taxonomy but free text with the value whisperer, because of the variety in publishing, especially articles; not mandatory!
* accessibility - přidáno - zejména pro harvest, slovní vyjádření o přístupu (př. volně dostupné v repozitáři Univerzity Karlovy, dostupné z ústavu fyziky AV ČR). u ručně vložených v případě restricted by se dalo asi také využít
* relatedItem - změna povinnosti - pro dokumenty nejsou povinní creators, jelikož se většinou bude jednat o vztah část - celek, zejména pak u článků, odkazy na časopis.
* recordIdentifiers - přidána sekce systémových indentifikátorů pro účely harvestu, importu a migrace.
* series - added - works also kind of like tagging similar things, so might be useful also for data. matter of discussion. Title of the series is required if the field is applied
* abstract - not mandatory for docs, because of GL and current content
* provider - original from NUSL nahrazen komunitami, resp. primární komunita, která vždy plní funkcí providera a tudíž je odpovědná za obsah a zveřejnění
* dateIssued - added - povinné, vždy vyplní autor, pokud by nestahoval celý záznam


* povinnosti:
 komenty k povinnosti vždy na konci pole
  * typology
    - requirmentsM for manual submissions
    - oai_R = requirments for harvest in general
- dateIssued, (kvůli datumům jako 199?)
- language (kdyby nebylo, dalo by se doplnit, ale není to důvod zahazovat záznam),
- accessRights (kvůli tomu, že ve starých datech vůbec neexistují a může být složité je dohledat)
- subjectCategories (ve starých datech není vůbec a je otázka, zda vynucovat u nových ručních)


LEGENDA:

comment_RFC - měla by prodiskutovat celá skupina
oai - týká se specifik, které jsou odlišné od modelu, ale mělo by platit pro všechny harvesty
oai_R - rozšiřuje oai a týká se pouze povinností pro harvest obecný/čistě nušl
requirments - obecný komentář k povinnostem
