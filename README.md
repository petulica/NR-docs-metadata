# NR-docs-metadata
 model for metadata of documents in national repository

názvy polí v množném čísle

Reasons for some changes compare to model for data:
*  dates - added dateIssued for original publication and dateAvailable stays for managing access to files in the repository. Solution is based on use-case of article preprints and postprints
* publishers - for docs is NOT a taxonomy but free text with the value whisperer, because of the variety in publishing, especially articles; not mandatory!
* accessibility - přidáno - zejména pro harvest, slovní vyjádření o přístupu (př. volně dostupné v repozitáři Univerzity Karlovy, dostupné z ústavu fyziky AV ČR). u ručně vložených v případě restricted by se dalo asi také využít
* relatedItems - změna povinnosti - pro dokumenty nejsou povinní creators, jelikož se většinou bude jednat o vztah část - celek, zejména pak u článků, odkazy na časopis. 
  * itemTitle - název, TO DO - dořešit absenci nameType z dat v NUŠL 
  * itemCreator - autor
  * itemContributor - přispěvate
  * role - taxonomie contributorType
  * itemPIDs - identifikátor/y
  * itemURL 
  * itemYear - rok vydání, POUZE ROK, integer
  * itemVolume - svazek
  * itemIssue - číslo
  * itemStartPage - první stránka části
  * itemEndPage - poslední stránka části
  * itemPublisher - nakladatel
  * itemRelationType - typ vztahu k původnímu popisovanému dokumentu, taxonomie
  * itemResourceType - typ dokumentu, taxonomie resourceType
* recordIdentifiers - přidána sekce systémových indentifikátorů pro účely harvestu, importu a migrace.
  * identifier
  * scheme - enum - nusl (perzistentní adresa z nušl), originalRecordOAI (původní OAI adresa z harvestu), catalogueSysNo (katalogové číslo - pokud záznam přichází z katalogu), nrOAI (???)
* originalRecord - původní adresa z domovského systému, jen u harvestu, vyjmutý ze skupiny recordIdentifiers  - chceme ho zobrazovat uživatelům v rozhraní 
* series - added - works also kind of like tagging similar things, so might be useful also for data. matter of discussion. Title of the series is required if the field is applied
  * seriesTitle - název edice
  * seriesVolume - svazek edice
* abstract - not mandatory for docs, because of GL and current content
* provider - original from NUSL nahrazen komunitami, resp. primární komunita, která vždy plní funkcí providera a tudíž je odpovědná za obsah a zveřejnění
* dateIssued - added - povinné, vždy vyplní autor, pokud by nestahoval celý záznam
* subjects - nebude taxonomie. Subjects se budou přebírat z harvestu (CZENAS, MeSH...). Schéma se bude rozlišovat podle identifikátoru (URI nebo kód). Ručně vkládané???
* languages - taxonomie, nebude povinné
* titles - TO DO: nutné dořešit titleType (main, subtitle, alternativeTitle, other) vs multilingual
* creators - autoři, bez povinné afiliace, 
* contributors - přispěvatelé, bez povinné afiliace, povinná role contributorType (taxonomie), v datovém modelu byly nějaké zmatky
* keywords - TO DO: nutné dořešit problém s multilingual, párování překladů

Beze změn:
* dateAvailable - datum, kdy bude soubor/y veřejně dostupný/é, řídí se podle něj embargo
* dateModified - datum změny obsahu, ne metadat
* notes - jakákoliv poznámka, opakovatelné, volný zápis, nebudeme příliš povzbuzovat k vyplňování
* subjectCategories - taxonomie podle klasifikace FRASCATI, nepovinné
* methods - multilingual, volný zápis, metody výzkumu
* technicalInfo - multilingual, volný zápis, použitá technika, technologie atd.
* accessRights - taxonomie, podle COAR vocabulary 
* resourceType - druh dokumentu, jen jeden per record (neumožní se výběr více typů dok. pro 1 záznam), taxonomie
* rights - licence, bude opakovatelné (do budoucna pro výběr více typů licencí), taxonomie - bez hlášky o autorském zákonu
* fundingReferences - informace o financování 
  * projectID - kód projektu, validace???
  * projectName - název projektu
  * fundingProgram - název výzkumného programu
  * funder - poskytovatel projektu, taxonomie
* version - verze obsahu, nikoliv záznamu, bude zapisovatené???
* geoLocations - zeměpisná poloha
  * geoLocationPlace - lokace, volný zápis
  * geoLocationPoint - další dvě pole
  * pointLongitude - zeměpisná délka
  * pointLatitude - zeměpisná šířka
* externalLocation - externí umístění souboru/ů (URL odkaz)
  * externalLocationURL - formát URL
  * externalLocationNote - poznámka k souboru nebo jeho umístění
* extent - rozsah, volný zápis
* persistentIdentifiers - identifikátor objektu, zatím pouze přejímaný z harvestu nebo ručně zapsaný (ISBN, ISSN, DOI...), neřešíme přidělování vlastních PID NR
* events - popisné údaje pro související akci (konference, výstava...)
  * eventNameOriginal - volný zápis celého názvu akce
  * eventNameAlternate - zkrácená forma názvu akce nebo překladu. měla by fungovat jako alias pro vyhledávání
  * eventDate - datum, ve formě dateORrange
  * eventLocation - def. location, place a country  

* VSKP
* dateDefended - datum obhajoby, formát date, pokud záznam neosahuje samostatné pole dateIssued, tak se přebírá toto datum do pole dateIssued
* defended - informace o obhájení ano/ne, boolean
* degreeGrantor - univerzita, na které byla práce obhájena, taxonomie Institutions
* studyField - studijní obor, NEBUDE TAXONOMIE, nevalidované příbírání z harvestu, nepovinnné pole



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
