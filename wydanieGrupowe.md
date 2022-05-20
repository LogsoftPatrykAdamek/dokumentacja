# wydanie grupowe

## Słownik

**Zlecenie jednosztukowe** - zamówienie zawierajaca jedna sztuke towaru wysylkowego (uwaga zlecenie jednosztukowe może być realizowane jako grupowe jeśli w systemie jest   inne aktywne zamówienie dla tego samego klienta z tym samym adresem wysyłkowym)

**Zlecenie multiadres** -  zlecenia powazane w grupie na podstawie adresu dostawy

**Zlecenie pojedyncze** - zamówienie przekraczające jednym z parametrów graniczne wartości dla zlecenia grupowego lub należące do widoku `v_doorGroupSkipGrouping`

**Zlecenie grupowe** - zamówienie klienta zawierające więcej niż jedną sztukę towaru nie będące zleceniem pojedynczym

## Zasady grupowania

- wyszukujemy zlecenia o najwyższym priorytecie
- spośród zleceń o najwyższym priorytecie sprawdzamy czy jest jakieś do którego możemy dobrać inne pod ten sam adres 
- jeśli tak to tworzymy grupę ze wszystkich zleceń pod dany adres **Zlecenie multiadres**  (wliczając w to zlecenie jednosztukowe pod ww adres) pomijamy zlecnia z widoku `v_doorGroupSkipMultiAddress`
- jeśli wybrano zlecenie nie dające się powiązać z innym adresem dodajemy do niego inne grupowe wg standardowych zasad
- jeśli zlecenie sztukowe dobieramy inne zlecenia sztukowe
- jeśli zlecenie za duże żeby grupować lub zostaja spełnikoen warunki z widoku `v_doorGroupSkipGrouping` puszczamy pojedyncze zlecenie

## Priorytety wysyłek

> ***Priorytet 0 jest priorytetem najwyższym wszelkie operacje powinny być sortowane rosnąco***

Ze względu na sposób obsługi priorytety dzielimy wg zakresu na:

| Priorytet| Planowanie | Uzupełnianie |Uzupełnianie|Grupowanie| Uwagi|
|--|--|--|--|--|--|
|0-89|+|+|+|+| standardowe priorytety 
|97|+|+|+| - |specjalny zlecenia o tym priorytecie nie są grupowane i wyswietlaja sie na terminalu na liście zleceń do wyboru
|99|-|-|-| - |specjalny zlecenia o tym priorytecie są pomijane podczas planowania i uzupełniania zbiórki i grupowania

## Parametry grupowanie

| Parametr| Opis | Użyty w |Od wersji|
|--|--|--|--|
|**groupPicking_autoGroup**|włącza wydruk grupowej listy zbiórki na formatce `doc_autoPrintTaskList`|`doc_autoPrintTaskList`||
|**groupPicking_maxOrderQty**|max ilość zleceń w grupie|||
|**groupPicking_maxWeight**|max waga zleceń w grupie|
|**groupPicking_maxVolume**|max objętość zleceń w grupie



## Parametry proces na terminalu

| Parametr| Opis | Użyty w |Od wersji|
|--|--|--|--|
|**groupPickingTer_listShowAllGroups**|Wyswietla wszytkie aktywne grupy/listy zbiórki lub ogranicza tylko do konkretnego uzytkownika|||
| funkcja `dbo.ter_getOrderlistText(door_id)`|Buduje wyswietlany tekst przy liscie zlceń | ||


TO DO


- [ ] jesli potwerdzmy zbiórke **0** info dla wykonawcy ze potwerdzono z brakien
- [x] jesli potwerdzmy zbiórke **0** blokujemy cały stok tego porduktu

## obiekty do przerzucenia

door_groupInfo
door_groupPlan
door_groupNextOrderPlanNEW



