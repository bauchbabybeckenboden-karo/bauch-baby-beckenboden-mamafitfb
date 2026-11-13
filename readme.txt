Mamafit — Fragebogen Deploy-Paket (eigenstaendig)
==================================================

Zweck
-----
Dieses Paket ist NUR fuer das Netlify-Projekt
"mamafitfragen" gedacht. Die index.html in diesem
Paket ist direkt der Mamafit-Fragebogen, ohne weitere
Fragebogen-Varianten.

Es ist NICHT zu verwechseln mit dem groesseren Paket
"bbb-deploy-v3", das alle drei Fragebogen enthaelt
und fuer das Netlify-Projekt "soyofragebogen" gedacht
ist.


Inhalt
------
- index.html                              → der Mamafit-Fragebogen
- logo.png                                → Logo (Cream auf transparent)
- netlify.toml                            → Netlify-Konfiguration
- netlify/functions/send-notification.js  → Mail-Versand-Function
                                            (erkennt fragebogen_typ "mamafit")


URL nach dem Deploy
-------------------
https://mamafitfragen.netlify.app/


Deploy-Anleitung (Drag & Drop)
------------------------------

1. Den Ordner "bbb-deploy-mamafit" entpackt geoeffnet halten.

2. Netlify-Dashboard oeffnen → Projekt "mamafitfragen" auswaehlen
   → "Deploys".

3. Den GESAMTEN Ordner per Drag & Drop in den Deploy-Bereich ziehen.
   Wichtig: NICHT nur einzelne Dateien, sondern den kompletten Ordner
   mit Unterstruktur (netlify/functions/...).

4. Warten, bis Netlify "Published" anzeigt.

5. RESEND_API_KEY pruefen:
   - Netlify → Site → Site configuration → Environment variables
   - Falls dort nicht vorhanden: hinzufuegen mit dem bestehenden
     Resend-API-Key (denselben wie im Projekt soyofragebogen).
   - Dann unter Deploys "Trigger deploy" → "Deploy site".

6. Aufrufen: https://mamafitfragen.netlify.app/

7. Browser-Cache umgehen mit Strg+F5 (Mac: Cmd+Shift+R), falls nach
   dem Deploy noch die alte Seite zu sehen ist.


Wichtiger Hinweis zu Supabase
-----------------------------
Der Mamafit-Fragebogen schreibt in dieselbe Supabase-Tabelle
"fragebogen_antworten" wie die anderen Fragebogen. Die Mamafit-
spezifischen Felder (schwanger, postnatal, trage, trageberatung,
rueckbildung, lied, aufmerksam_geworden) gehen aktuell NUR in die
Mail, nicht in Supabase, weil die Tabelle dafuer noch keine Spalten
hat.

Falls die Antworten auch in Supabase gespeichert werden sollen,
koennen die entsprechenden Spalten (Typ "text") in der Tabelle
nachtraeglich angelegt werden. Sieh dazu auch das README in
bbb-deploy-v3.
