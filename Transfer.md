# Lite WMS Orange wersja 4.5


# Transfer


## Transfer palety terminal  
Proces w repoizytorium `TRASFERLU`

## Parametry grupowanie

| Parametr| Opis | Użyty w |Od wersji|
|--|--|--|--|
|**transferTer_InfoShowProductName**|włącza wydruk grupowej listy zbiórki na formatce `doc_autoPrintTaskList`|`doc_autoPrintTaskList`||



exec   [ter_LoadUnitINFOtransferPROC]   'ZS00021_p6' 




select [dbo].[ter_LoadUnitINFOshort] ( 'ZS00021_p6' ) as PALINFO
 EXEC dbo.stk_findBestLocationForLU_multi 394199 , null, null, 3,0, 3
