# wydanie grupowe

### Słownik

**Zlecenie jednosztukowe** - zamówienie zawierajaca jedna sztuke towaru wysylkowego (uwaga zlecenie jednosztukowe może być realizowane jako grupowe jeśli w systemie jest   inne aktywne zamówienie dla tego samego klienta z tym samym adresem wysyłkowym)

**Zlecenie multiadres** -  zlecenia powazane w grupie na podstawie adresu dostawy

**Zlecenie pojedyncze** - zamówienie przekraczające jednym z parametrów graniczne wartości dla zlecenia grupowego lub należące do widoku `v_doorGroupSkipGrouping`

**Zlecenie grupowe** - zamówienie klienta zawierające więcej niż jedną sztukę towaru nie będące zleceniem pojedynczym

### Zasady grupowania

- wyszukujemy zlecenia o najwyższym priorytecie
- spośród zleceń o najwyższym priorytecie sprawdzamy czy jest jakieś do którego możemy dobrać inne pod ten sam adres 
- jeśli tak to tworzymy grupę ze wszystkich zleceń pod dany adres **Zlecenie multiadres**  (wliczając w to zlecenie jednosztukowe pod ww adres) pomijamy zlecnia z widoku `v_doorGroupSkipMultiAddress`
- jeśli wybrano zlecenie nie dające się powiązać z innym adresem dodajemy do niego inne grupowe wg standardowych zasad
- jeśli zlecenie sztukowe dobieramy inne zlecenia sztukowe
- jeśli zlecenie za duże żeby grupować lub zostaja spełnikoen warunki z widoku `v_doorGroupSkipGrouping` puszczamy pojedyncze zlecenie


## Parametry
