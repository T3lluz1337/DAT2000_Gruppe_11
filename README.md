# DAT2000_Gruppe_11

Obligatorisk arbeidskrav lenke: https://itfag.usn.no/~kvisli/DAT2000/oblig/DAT2000_oblig_delA.html

Hva som skal gjøres generert av chatGPT:
Oppgave 1: Programmer i databasen
A. Trigger

    Opprette en trigger som reagerer på nye rader i databruk-tabellen.
    Sjekke om DataGjenstårByte er NULL:
        Hvis ja, gjør ingenting (ubegrenset databruk).
    Hvis DataGjenstårByte > 0:
        Reduser DataGjenstårByte med DataBrukByte fra den nye raden.
        Pass på at DataGjenstårByte ikke går under 0.
    Hvis DataGjenstårByte når 0:
        Sett RedusertHastighet til true for abonnementet.

B. Testprogram for trigger

    Skriv en lagret prosedyre som genererer testdata for databruk-tabellen.
    Prosedyren skal ta inn et telefonnummer og en dato som parametere.
    Generer data for hver time på den aktuelle datoen med tilfeldig forbruk (0-20 MB).
    Inkluder transaksjonshåndtering for å sikre korrekt datainnsats i en flerbrukerdatabase.
    Test triggeren ved å kjøre prosedyren med noen telefonnummer og datoer.

C. Lagret funksjon

    Opprett en lagret funksjon som beregner ny gjenstående datamengde ved månedsskifte.
    Funksjonen skal ta inn TlfNr som parameter.
    Beregne ny gjenstående datamengde som sum av månedskvoten og rollover.
    Sørg for korrekt konvertering fra GB til Bytes.
    Håndter abonnementer med ubegrenset datamengde (returner null eller lignende).
    Skriv en SQL-kommando for å oppdatere datamengden for alle abonnementer den 1. i hver måned.

D. Lagret prosedyre

    Skriv en lagret prosedyre for å legge inn en ny rad i datakjøp-tabellen ved kjøp av ekstra datapakke.
    Prosedyren skal ta inn telefonnummer og pakketype som parametere.
    Fyll ut kolonner i datakjøp-tabellen:
        DatoKjøpt settes til dagens dato.
        DatoUtløper beregnes basert på pakketype.
        Pris settes til pakketype pris.
        DataKjøptGB settes til pakketype datamengde.
    Legg til kjøpt datamengde i abonnementets gjenstående datamengde.
    Fjern redusert hastighet hvis abonnementet har dette.
    Inkluder transaksjonshåndtering og feilbehandling:
        Sjekk for gyldige parametere.
        Håndter eventuelle databasefeil.
        Returner informasjon om prosedyren ble gjennomført eller ikke.
    Test prosedyren med SQL-kommandoer.

E. Utfordring: Klientprogram (frivillig)

    Utvikle et Java-program eller webapplikasjon med brukergrensesnitt.
    Koble programmet til databasen for å kunne kjøpe ekstra datapakker.
    Kall den lagrede prosedyren fra oppgave D når kunden kjøper en datapakke.

Oppgave 2: Databaseadministrasjon
A. Sikkerhetskopi

    Utfør logisk sikkerhetskopi av hele PlingMe-databasen med en kommandovindu-kommando.
    Slett alle data i databruk-tabellen med en SQL-kommando.
    Gjenopprett innholdet i databruk-tabellen fra sikkerhetskopien.

B. Fysisk lagring

    Beregn fysisk diskplass som databruk-tabellen vil kreve etter 5 år.
        Ta hensyn til antall kunder og abonnementer.
    Beregn diskplass for indekser på databruk-tabellen.
    Lag en liste over nødvendige tiltak for å sikre tilstrekkelig lagringsplass og ytelse.
