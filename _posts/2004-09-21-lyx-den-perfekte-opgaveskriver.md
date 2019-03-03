---
title: "Lyx - den perfekte opgaveskriver"
permalink: /content/lyx-den-perfekte-opgaveskriver
language: da
tags:
  - lyx linux
modified: 2010-11-06T17:00:09Z
---

Det kræver lidt arbejde
-----------------------

Du skal installere et par ting for at få Lyx til at køre. For det første skal du have et Latex-miljø. Lyx er nemlig bare en WYSIWYM-editor til Latex, som er et meget kompliceret sprog, der er meget velegnet til opgaver, bl.a. fordi det har nogle unikke styrker hvad angår fx håndteringen af referencer.

Du kan få hjælp til, hvordan du installerer Lyx på Windows i artiklen [Installing LyX on Windows](https://wiki.lyx.org/Windows/Windows).

Hvordan referencer?
-------------------

Der er stor frihed til at lave referencerne lige som du vil. Det er en god ide at udnytte BibTex-formatet og så importere disse filer i din Lyx-fil. En god editor til BibTex-filer er BibEdit.

Hver reference skal have en referencekode. Det er en god ide at lave et format for disse referencer, du let kan huske. Du må ikke bruge mellemrum eller mærkelige tegn i referencen. Jeg bruger fx Olesen:2004 som referencekode. Hvis forfatteren har skrevet flere artikler på et år, kan du bare tilføje et bogstav bagefter.

`Layout -&gt; Documents -&gt; Bibliography -&gt; click NatBib`

`Insert -&gt; Lists and Toc -&gt; choose BibTex Reference`

Når du vil indsætte en reference bruger du bare:

`Insert -&gt; Citation Reference`

Her kan du, når NatBib er slået til let vælge nøjagtig den måde referencen skal vises på i den tekst du ser på skærmen. Men det er ikke alt. Du skal også lige lave en indstilling, der gør, at den også vises sådan i udskriften.

Det gør du ved at klikke på "BibTex Generated References", hvor end du har sat dem ind i dit dokument. Første gang du klikker på den, vil den gerne tilknytte et program til `.sh`-filer. Her skal du vælge `/lyx/bin/sh.exe`.

Under Style skal du vælge `plainat.bst`. Denne fil kan du finde under `/texmf/bibtex/bst/natbib/plainnat` (engelsk) eller `/texmf/bibtex/bst/natbib/noaps` (norsk eller dansk), hvis du har installeret MikTex i standardbiblioteket.
