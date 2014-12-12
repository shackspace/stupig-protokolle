Stupig Treffen vom 12. Dezember 2014
====================================

Misc
----

* krass, stack-exchange nutzt .net auf 9 Servern. aber viel Elasticsearch/Redis!
http://www.slideshare.net/GABeech/stack-exchange-infra-41714842

* docker ist cool
* bepasty ist verdockert: https://registry.hub.docker.com/u/asmaps/bepasty/dockerfile/


kurzer Abriss DRF2.4 vs DRF3.0
------------------------------

* http://www.django-rest-framework.org/
* (Serializer-)Validierung ist besser
* Features umhacken scheint schwieriger geworden zu sein
* Metadata nun als Klasse. Viel besser.
* Upgrade-Path nicht dokumentiert
* letusorder it wurde gleich auf DRF3 migriert


pull request mergen
-------------------

* done


devpi als lokaler cache für pip
-------------------------------

* http://doc.devpi.net/latest/
* bringt erhebliche Geschwindigkeitsvorteile
* noch ungelöst: wie bringt man Docker container dazu, dass sie den devpi (in einem anderen Docker container) verwenden können?


bronsen hält Kurzvortrag zu git, git-flow, (no)feature branches
---------------------------------------------------------------

* findet git-flow übertrieben
* rebase kann zu Problemem führen wenn man zu früh pusht
* seine Historie so hinzuschummeln, dass der git-graph "schön" aussieht ist evtl falsch optimiert
* vorteil rebase: weniger kreuzungen
* nachteil rebase: riskanter!
* nachteil merge: diese merge-commits sind nicht schön in der historie


wo kommen die templates her
---------------------------

::

  # See: https://docs.djangoproject.com/en/dev/ref/settings/#template-loaders
  TEMPLATE_LOADERS = (
    'django.template.loaders.filesystem.Loader',
    'django.template.loaders.app_directories.Loader',
  )

  # See: https://docs.djangoproject.com/en/dev/ref/settings/#template-dirs

  TEMPLATE_DIRS = (
    normpath(join(SITE_ROOT, 'templates')),
  )#
  ######### END TEMPLATE CONFIGURATION


letusorderit-revue
------------------

* how-to-serialize
* how-to-paginate: Django settings und Möglichkeiten wie man es in einem View überschreibt
* howto stream: https://github.com/tomchristie/django-rest-framework/issues/939


Lizenzdiskussion
----------------

letusorderit als GPLv2, MIT oder BSD lizensieren?
Entscheidung auf nächsten Termin vertagt. Vote needed.


letusorderit-client
-------------------

https://github.com/letusorderit/letusorderit-client

Ausblick:

- Python-Client (für IRC, Twitter, Jabber, cli,. ...) mit requests /
  Gute Beispiele: tweepy, python-fitbit, python-intercom, ...


NEXT
----

* nächster Termin ist 9. Januar 2015! (am 26.12.2014 sind alle auf dem Weg nach Hamburg)
