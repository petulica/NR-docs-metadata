# NR-docs-metadata
 model for metadata of documents in national repository

názvy polí v množném čísle, pokud typ = array

Reasons for some changes compare to model for data:
* změna přístupu k multilingual - užití pole i18nstr přímo z invenia - bude se čistě používat pro subject, jinak se nad ním bude stavět multilingual
* dates - added dateIssued for original publication (vyplnuje vždy autor) and dateAvailable stays for managing access to files in the repository. Solution is based on use-case of article preprints and postprints
* publishers - for docs is NOT a taxonomy but free text with the value whisperer, because of the variety in publishing, especially articles
* accessibility - přidáno - zejména pro harvest, slovní vyjádření o přístupu (př. volně dostupné v repozitáři Univerzity Karlovy, dostupné z ústavu fyziky AV ČR). u ručně vložených v případě restricted by se dalo také využít
* externalLocation - přidáno - externí umístění souboru/ů (URL odkaz)
  * externalLocationURL - formát URL
  * externalLocationNote - poznámka k souboru nebo jeho umístění
* systemIdentifiers - přidána sekce systémových indentifikátorů pro účely harvestu, importu a migrace.
  * identifier
  * scheme - enum - nusl (PURL nušl), originalRecordOAI (původní OAI adresa z harvestu), catalogueSysNo (katalogové číslo - pokud záznam přichází z katalogu, často exporty), nrOAI (námi přidělované oai ID pro další šíření záznamu)
* originalRecord - původní adresa z domovského systému, jen u harvestu, vyjmutý ze skupiny recordIdentifiers  - chceme ho zobrazovat uživatelům v rozhraní
* series - added - works also kind of like tagging similar things, so might be useful also for data. matter of discussion.
  * seriesTitle - název edice; required
  * seriesVolume - svazek edice
* subjects - řešení jak pro KW tak pro předmětová hesla (subject). v UI nelze vyplnit subject jen KW. Subjects se budou přebírat z harvestu (CZENAS, MeSH...).
* změna názvů po dlouhé diskusi. řešení:
    - title - je string, hlavní název v originálu díla bez kodu jazyka.
      - TO DO P+H - jak zapisovat bilingvní věci formou nápovědy + u MIGRACE, změna v nárvhu rozhraní
      - pravidla řazení výsledků vyhledávání podle jazyka UI uživatele
      - pro vyhledávání a řazení nějaká práce s významnými jazyky.
    - additionalTitles - sekce pro další názvy, která má vždy title multilingual a titleType (subtitle, translatedTitle, alternativeTitle, other)
* rights - licence, data object přes taxonomii, ted array. opakovatelné (do budoucna pro výběr více typů licencí)
* extent - přidáno - rozsah, volný zápis
* events - přidáno - popisné údaje pro související akci (konference, výstava...)
  * eventNameOriginal - volný zápis celého názvu akce
  * eventNameAlternate - zkrácená forma názvu akce nebo překladu. měla by fungovat jako alias pro vyhledávání
  * eventDate - dateORrange
  * eventLocation - def. location, place a country

změny způsobené jiným přístupem k povinnostem:
* definice authority a zrušení authorityBase
  * creators a contributors - povinný pouze fullName
* relatedItem - povinný pouze itemTitle
* abstract - nepovinné
* languages - taxonomie, nebude povinné
* subjectCategories - taxonomie podle klasifikace FRASCATI, nepovinné

Beze změn:
* dateAvailable - datum, kdy bude soubor/y veřejně dostupný/é, řídí se podle něj embargo
* dateModified - datum změny obsahu, ne metadat
* notes - jakákoliv poznámka, opakovatelné, volný zápis, nebudeme příliš povzbuzovat k vyplňování
* methods - multilingual, volný zápis, metody výzkumu
* technicalInfo - multilingual, volný zápis, použitá technika, technologie atd.
* accessRights - taxonomie, podle COAR vocabulary
* resourceType - druh dokumentu, jen jeden per record (neumožní se výběr více typů dok. pro 1 záznam), taxonomie
* fundingReferences - informace o financování
  * projectID - kód projektu - možnost vytěžovat is vavai a openaire
  * projectName - název projektu
  * fundingProgram - název výzkumného programu
  * funder - poskytovatel projektu, taxonomie
* version - verze obsahu, nikoliv záznamu
* geoLocations - zeměpisná poloha
  * geoLocationPlace - lokace, volný zápis
  * geoLocationPoint - další dvě pole
  * pointLongitude - zeměpisná délka
  * pointLatitude - zeměpisná šířka
* persistentIdentifiers - identifikátor objektu, zatím pouze přejímaný z harvestu nebo ručně zapsaný (ISBN, ISSN, DOI...), neřešíme přidělování vlastních PID NR
* relatedItems - pouze změna povinnosti - povinný pouze title.
  * itemTitle - název
  * itemCreator - autor
  * itemContributor - přispěvatel
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


*POVINNOSTI :
  Povinnosti byly nastaveny minimalisticky tak, aby se nevalidní záznamy nemusely ukládat a stačil pouze report/log o chybách.
  Pak jsou údaje, které by měly být povinné, ale není důvod kvůli nim zahazovat záznam. Tzn. pro všechny zdroje by měly být jako základ ve validacích. A to jsou:
- dateIssued, (kvůli datumům jako 199?)
- language (kdyby nebylo, dalo by se doplnit, ale není to důvod zahazovat záznam),
- accessRights (kvůli tomu, že ve starých datech vůbec neexistují a může být složité je dohledat)
- pro vškp:
  - dateDefended
  - defended
  - degreeGrantor
