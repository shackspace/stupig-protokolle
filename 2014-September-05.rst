Stupig Treffen vom 05. September 2014
=====================================

moin2
-----

TW erzählt was über moin2. Er ist Code-Dev von moinmoin und moinmoin-2.0.

Kompletter Rewrite, weil Flask/Werkzeug und so viel besser als alles selbst schreiben.

test.moinmo.in ist eine 2er version. aber ca. 1 jahr alt. TW will bald eine neue Version installieren.

Verbesserungen:
~~~~~~~~~~~~~~~

* Abstraktion der Daten, nicht nur der Text ist versioniert, sondern auch die Uploads.
* Metadaten jetzt als json. durch whoosh https://pypi.python.org/pypi/Whoosh alles indexiert und schnell durchsuchbar
* Eigenes Ticket System
* Blog System
* Moar Performance
* Bot-Schutz

Release Blocker:
~~~~~~~~~~~~~~~~

* User Interface / UX

Kritik an unterbliebenem Release:

Wenn nichts released wird => Niemand verwendet es => Leute sind weniger motiviert mitzuarbeiten bzw. es gibt keine Nutzer die sich aufreden
Bräuchte einen guten Frontendler, der das mal ein wenig voranbringt.
Hat gerade ca. 1.5 aktive Entwickler.

Tests sind teilweise viel zu kompliziert.

Alle 1344 Tests von moin2 laufen in codeship durch. :)


Devops
------

* https://codeship.io/

Ähnlich Travis-CI nur besser.
Free für Open-Source.

* https://www.rainforestqa.com/

Frontendtesting ohne sich mit Selenium usw. rumzuschlagen.


Kirchenreich
------------

http://kirchenreich.org

Kirchendaten aus OpenStreeetMap, genauso wie die Map tiles von MapBox gerendert.
DjangoDash Projekt 2012.
Eigentliche Idee wir wollen OpenStreetMap Daten mit Wikipedia Daten zusammenführen.
Andreas hat die Domain bereits gehabt, also war das Thema bereits vorbestimmt.
Projekt ist wenig eingeschlafen.

Siehe auch happyhourmap.de, Code ist ähnlich wie Kirchenreich aber eigentlich komplett anders.

HappyHourMap verwendet leveldb zum prozessieren der Nodes, weil das weniger RAM verbraucht.


Personal API-Projekt
--------------------

mfa baut was ähnliches wie:
https://speakerdeck.com/eay/personal-api-zur-abbildung-des-digitalen-ichs-im-social-web

in Python ... Name des projektes ist gefunden. aktuell privates Repo. public folgt, wenn etwas aufgeräumter.


OSM full vs. daily import
-------------------------

Wir (kirchenreich und happyhourmap) brauchen einen Node/Way/Rel-Cache, um die daily changeset von OpenStreetmap zu verarbeiten.
Die Daily-Files gehen davon aus, dass man eine fullimport-Datenbank hat.
wir haben aber nur Teilausschnitte (Kirchen, bzw. Bars).

Caches:
~~~~~~~

 - Node Cache (zum Bauen von Ways, Rels)
 - Way Cache (zum Bauen von Rels)
 - Relation Cache (zum Bauen von Rels)

Das ganze sollte nicht zuviel RAM verbrauchen, deshalb kein Redis.
Postgres bietet sich wegen der schnellen Indexe auf die osm-ids an (Hauptzugriffspfad auf die Daten).

Toolchain:
~~~~~~~~~~

* PostgreSQL
* sqlalchemy (weil ohne ORM macht es keinen Spaß)
* gevent (wir haben noch kein projekt mit gevent)
* Flask (die API benötigt vorauss. nur eine sehr minimal Web-API, falls überhaupt)
* lxml (xml in schnell) -- http://pranavk.github.io/python/parsing-xml-efficiently-with-python/
* click (commandline in gut)

Was soll es können:
~~~~~~~~~~~~~~~~~~~

* Anwärmen des Caches via Change Files oder full imports.

``python osm-cache.py apply-changes 365.osc``

* Anwärmen aus osm File

``python osm-cache.py load-data filtered.osm``

* Internal API

::

  from osm_cache import Nodes

  >>> node_1234 = Nodes[1234]
  >>> type(node_1234)
  <osm_cache.types.Node>

  >>> len(Nodes)
  1320123

* external (web) API

::

  GET /nodes/1234
  JSON Response

  GET /way/12345
  JSON Response, mit allen Nodes für diesen Way


Notfall Strategien für fehlende Daten:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 * http://wiki.openstreetmap.org/wiki/API_v0.6#Read:_GET_.2Fapi.2F0.6.2F.5Bnode.7Cway.7Crelation.5D.2F.23id
 * planet osm dump
 * local (deskop pc) gehostete postgres mit fullimport (ca. 600G postgres-db)


