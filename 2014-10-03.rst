Stupig Treffen vom 03. Oktober 2014
===================================

Agenda
------

* vor 19Uhr wollen @jarus und @mfa an ihrem osm-cache-api-Projekt weiterarbeiten
* ab 19Uhr wollen @bronsen und @mfa ihr neues Python-Workshop-Wir-Lernen-Zusammen-Django-Und-Django-Rest-Framework-Projekt vorstellen
* Diverse Szenarien des Lernprojektes werden zusammen entworfen
* Das Lernprojekt soll erst ab dem 17.10. starten, damit jeder dafür Werbung machen kann.
* django-dash/wsgi-wrestle: Neue Idee "lendbase" auf http://etherpad.osuosl.org/python-shack-hack
  (Anm: TW kann heute nicht zum Workshop kommen, wenn Fragen sind: email oder irc #shackspace)
* django-dash/wsgi-wrestle: wer hilft bei UI (v.a. CSS/Javascript) und UX? Es wollte evtl. heute
  jmd deswegen zum Workshop kommen.


osm-cache-api
-------------

* nodes importieren klappt.
* würde für den planet nur ca. 6 tage brauchen
* ways und relations werden noch eingebaut; dann erfolgt mal ein testlauf auf einem Hetzner-Server


Python und Django an einem konkreten Projekt lernen
---------------------------------------------------

https://github.com/letusorderit/letusorderit/blob/master/README.md

* Wir wollen heute durchsprechen, welche Schritte (API-Calls) es geben muss damit im readme angesprochenen Szenarien tatsächlich funktionieren.


LetUsOrder.it
-------------

User Story
@Jarus möchte Pizza bestellen und will seine Kollegen fragen ob die auch etwas möchten.

Ablauf:
+++++++

Vorgang: Öffnen einer Bestell-Session
*************************************

Actor: Christoph (Initiator)

Bestell Session wird geöffnet durch:
POST Request <hier URL einsetzen>
Request Body:
* Name der Session (Pizza bestellen)
* URL zum Shop (Addresse des Lieferservice mit Speisekarte)
* Wie lange kann bestellt werden (30min)

Response:
* Öffentlicher Link für die Mitbesteller
* Private URL für Initiator um Bestell-Session zubearbeiten

Christoph (Initiator) teilt die Bestell-Session URL an seine Kollegen (Mitbesteller)

Vorgang: Jemand möchte bei Session mitbestellen
***********************************************

Actor: Andreas (Mitbesteller)

Andreas schaut sich zuerst die Session an, also wo wird z.B. bestellt
GET Request <URL der Bestell-Session>

Response:
Name der Session, URL zum Shop, Dauer der Session

Andreas möchte nun eine Pizza Hawaii bestellen
POST Request <URL der Bestell-Session>
* Produkt als String

Response:
* Private URL für die Teilbestellung von Andreas


Vorgang: Mitbesteller will sein Teilbestellung verändern
********************************************************

Actor: Andreas (Mitbesteller)

Andreas will doch keine Pizza Hawaii sondern eine Pizza Spezial
Komplette Teilbestellung durch neue Teilbestellung ersetzen.

PUT Request <Private URL der Teilbestellung>
Body gleich wie POST für Mitbestellung

Vorgang: Mitbesteller möchte einzusätzliches Produkt bestellen
**************************************************************

Actor: Andreas (Mitbesteller)

Andreas will zusätzlich noch ein "Großer Salat".
=> Teilbestellung wir um Produkt erweitert.

PATCH Request <Private URL der Teilbestellung>
Body gleich wie Post für Mitbestellung

Vorgang: Mitbesteller will seine Teilbestellung löschen
*******************************************************

Actor: Andreas (Mitbesteller)
Andreas will doch keine Pizza mehr und löscht seine Teilbestellung.

DELETE Request <Private URL der Teilbestellung>
Response: Done

Vorgang: Initiator komplettiert Bestellung
******************************************

Actor: Christoph (Initiator)
Christoph hat sehr viel Hunger und möchte die Bestellung los schicken, deshalb macht er die Bestellung zu.

POST Request <Private URL der Bestell-Session>
Response: Done

Vorgang: Initiator möchte wissen wer bestellt hat
*************************************************

Actor: Christoph (Initiator))
Christoph will das Geld einsammeln und möchte wissen wer was Bestellt hat


weiteres
--------

dxheat.com
++++++++++


* Gebaut in Django
* Stack: https://www.dropbox.com/s/iamy56t9jc82ask/Architecture%20DXHeat.com%20v%201.1.pdf?dl=0


logging
+++++++

logmessage nach logstash schicken
