---
title: "Rotere videoklip"
permalink: /content/rotere-videoklip
language: da
tags:
  - ubuntu
  - linux
modified: 2011-06-25T01:08:46Z
---

Jeg optager sommetider videoer på højkant med mit Canon G10-kamera. Derfor har jeg ofte brug for at rotere videoerne. Jeg arbejder på Ubuntu, og der fandt jeg via [Rotating video clips shot in portrait mode](http://therning.org/niklas/2006/07/rotating-video-clips-shot-in-portrait-mode/) ud af, hvordan jeg kunne bruge mencoder (som er en del af MPlayer) til at rotere videoklippene. Koden i hans artikel er imidlertid lidt forældet, så i virkeligheden skal du bruge følgende: ` `

`>mencoder -ovc lavc -lavcopts vcodec=mjpeg -vf rotate=3 -oac pcm MVI_1093.MOV -o 1093.MOV `Hvis du ikke ønsker at få lyden med, kan du bare tilføje `-nosound` som et ekstra parameter. Skriv hvis du har andre og lettere måder at gøre det på.
