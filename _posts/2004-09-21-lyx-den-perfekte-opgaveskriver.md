---
title: "Lyx - den perfekte opgaveskriver"
permalink: /content/lyx-den-perfekte-opgaveskriver
language: da
tags:
  - lyx
  - linux
last_modified_at: 2019-12-02T16:00:09Z
---

## Installere Lyx

Lyx kræver et Latex-miljø for at køre. Lyx er nemlig bare en WYSIWYM-editor til Latex.

Du skal installere et par ting for at få Lyx til at køre. For det første skal du have et Latex-miljø. Lyx er nemlig bare en WYSIWYM-editor til Latex, som er et meget kompliceret sprog, der er meget velegnet til opgaver, bl.a. fordi det har nogle unikke styrker hvad angår fx håndteringen af referencer.

Jeg installerede først [MikTex 2.9](https://miktex.org/download). Jeg valgte `Net Installer`-versionen.

Derefter installerede jeg [Lyx](https://www.lyx.org/).

## Hvordan referencer?

Der er stor frihed til at lave referencerne lige som du vil. Det er en god ide at udnytte BibTex-formatet og så importere disse filer i din Lyx-fil. En god editor til BibTex-filer er BibEdit.

Hver reference skal have en referencekode. Det er en god ide at lave et format for disse referencer, du let kan huske. Du må ikke bruge mellemrum eller mærkelige tegn i referencen. Jeg bruger fx Olesen:2004 som referencekode. Hvis forfatteren har skrevet flere artikler på et år, kan du bare tilføje et bogstav bagefter.

`Layout --> Documents --> Bibliography --> click NatBib`

`Insert --> Lists and Toc --> choose BibTex Reference`

Når du vil indsætte en reference bruger du bare:

`Insert --> Citation Reference`

Her kan du, når NatBib er slået til let vælge nøjagtig den måde referencen skal vises på i den tekst du ser på skærmen. Men det er ikke alt. Du skal også lige lave en indstilling, der gør, at den også vises sådan i udskriften.

Det gør du ved at klikke på "BibTex Generated References", hvor end du har sat dem ind i dit dokument. Første gang du klikker på den, vil den gerne tilknytte et program til `.sh`-filer. Her skal du vælge `/lyx/bin/sh.exe`.

Under Style skal du vælge `plainat.bst`. Denne fil kan du finde under `/texmf/bibtex/bst/natbib/plainnat` (engelsk) eller `/texmf/bibtex/bst/natbib/noaps` (norsk eller dansk), hvis du har installeret MikTex i standardbiblioteket.
