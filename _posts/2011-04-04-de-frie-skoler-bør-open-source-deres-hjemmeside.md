---
title: "De frie skoler bør open source deres hjemmeside"
permalink: /content/de-frie-skoler-bør-open-source-deres-hjemmeside
language: da
tags:
  - drupal
  - højskole
  - samarbejde
modified: 2011-04-04T11:03:06Z
---

Det er ingen hemmelighed, at der altid er nok at bruge penge på, når man driver en fri skole, fx højskole og efterskole. Jeg har i en årrække været webmaster for [Vejle Idrætshøjskoles hjemmeside](http://vih.dk), og det koster altid penge, når der skal udvikles noget nyt til hjemmesiden. Vi har bl.a. brugt lidt kræfter på at udvikle noget, der kan håndtere tilmelding til både korte og lange kurser og brochurebestilling. Derudover bruger vi naturligvis mange kræfter på at få netop det design, der appellerer til vores målgruppe, og som helst skal være meget bedre end de andres.

Hvorfor arbejder de frie skoler ikke sammen?
--------------------------------------------

- **Vi har alligevel tilsvarende funktioner.** Hvis jeg ikke tager meget fejl, så har alle andre højskoler udviklet tilsvarende funktioner på deres hjemmesider. Og når de tre år senere skifter hjemmesiden ud, får de et ny firma til at udvikle de samme funktioner igen på en anden måde. Det er spild af penge og tid. Hvis højskolerne i stedet arbejdede sammen om disse basale funktioner, så kunne man i stedet bruge pengene på at kæle endnu mere for designet, bruge tiden på at lave de gode historier osv. Og når man alligevel skal skifte layoutet på hjemmesiden, så det matcher resten af reklamematerialet, så kan man bibeholde de eksisterende funktioner, men blot lægge et nyt layout ovenpå.

Hvordan skal de frie skoler arbejde sammen?
-------------------------------------------

- **Åben kildekode.** På Vejle Idrætshøjskole har vi valgt at [lægge al vores kildekode åbent ud](http://github.com/vih). Det betyder at andre lignende skoler kan kopiere al vores funktionalitet og lægge deres eget design ned over. Det har vi ikke noget imod. Nu er det jo udviklet. Hvorfor skal andre så ikke have gavn af det. Tænk sig, hvis nogen kunne bruge det og skrev tilbage, at de har forbedret funktionerne lidt. Det ville jo være fremragende - og meget billigere for skolerne i det lange løb. Udover os kunne vi kun finde [Den Rymiske Højskole](http://github.com/wulff), som har åbnet deres kildekode. Det undrer at ikke alle gør det, for fordelene er så store!
- **Tilgængelige, almindelige systemer.** Tidligere brugte vi vores eget hjemmestrikkede system, men er for nylig [gået over til at bruge Drupal](http://larsolesen.dk/node/270) (som tilfældigvis også er det system, Den Rytmiske Højskole benytter sig af). Fordelen ved at bruge et open source system er bl.a. at rigtig mange bidrager til udviklingen, og der findes alverdens nyttige moduler, som man kan forbedre sin hjemmeside med, og at systemet er meget mindre personafhængigt. Det er altså meget lettere bare at skifte firma eller udvikler. Højskolerne kunne naturligvis også vælge at lancere deres helt eget system, men så skal man i gang med at udvikle en masse ting, der allerede ligger klar til brug.
- **Projektleder.** Det kræver naturligvis at nogle samler trådene, opretter infrastrukturen til at arbejde sammen og er dygtige til at formidle den nye samlede viden ud til alle de frie skoler. Også de skoler som ikke har ansat IT-kyndige mennesker.

Hvad skal skolerne arbejde sammen om?
-------------------------------------

- **Ikke design, layout og indhold.** Det er jo alt det unikke for den enkelte skole, og det skal skolerne naturligvis have helt for sig selv.
- **Fælles funktioner.** Der er mange områder, men i hvert fald let installation, tilmeldingssystemer til både korte og lange kurser, brochurebestilling, integration med BRUGSEN (eller endnu bedre en open source, netbaseret omskrivning) o.lign., som man ikke allerede kan finde i det meget [omfattende netværk på fx Drupal](http://drupal.org). Og det behøver ikke være systemafhængigt. Nogle højskoler har valgt at bruge Wordpress som deres system, og de højskoler kunne gå sammen om modulerne, mens andre skoler kunne samarbejde med os om at udvikle nogle virkelig gode moduler til vores foretrukne system Drupal.

Hvad nu hvis jeg ikke bryder mig om det, de andre har lavet?
------------------------------------------------------------

Hvis du slet ikke kan lide noget af det, de andre har lavet, så kan du oprette et nyt modul, som andre så kan afprøve. Eller du kan komme med ændrings- og forbedringsforlag til det eksisterende. Og hvis I alligevel skal til at udvikle en ny hjemmeside, så kan det være, at jeres højskole kan sponsorere forbedringerne.

Giv noget og få meget!
----------------------

Ovenstående er skrevet med udgangspunkt i højskolerne, men situationen er nøjagtig den samme for efterskolerne.

Man skal naturligvis _give noget for at få noget_, men niveauet på højskolernes side vil formentlig stige markant, fordi man kan bruge kræfterne, hvor de bør bruges, nemlig på indhold, design og usability. **I melder jer bare ind i kampen næste gang, I skal have en hjemmeside**. I kan overveje, om den ikke skulle laves i Drupal. I kan kigge på, hvordan vi har gjort det, og så kan I måske give os nogle fif til, hvordan vores side bliver bedre? Og så har vi begyndelsen på et økosystem, hvor alle arbejder sammen!
