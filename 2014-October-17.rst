Stupig Treffen vom 17. Oktober 2014
=====================================

Agenda
------

* Virtualenv/Django Einführung (als Vorbereitung für LetUsOrder.it-Projekt)

  - Virtualenv / Virtualenv-wrapper-Einführung
  - Aufsetzen eines Django-Projektes (mit und ohne Template)
  - Django konfigurieren

* DjangoDash/WsgiWrestle-Plaunungen

  - Wer ist dabei? Bei welchem Projekt?


***************************************

Empfehlungen:
- Film: Who Am I - Kein System ist sicher
  "weniger Bullshit als erwartet" - bronsen


djangodash-ideen:
-----------------

Hier brauchts noch Ideen! Und Mitmachende: am besten bei TW melden :)

- Verleihsystemdings, Codename *Lendbase*: http://etherpad.osuosl.org/python-shack-hack


Stupig-Projekt: Letusorderit
----------------------------

- Kurzes Recap zum gedachten Projekt-Ablauf:
  - Mob-Programming
  - Szenario: https://github.com/shackspace/stupig-protokolle/blob/master/2014-October-03.rst#letusorderit
  - Backend: REST-Api mit Django Rest Framework (DRF)
  - Frontends sollen explizit separate, eigenständige Projekte werden

- Bedarfsermittung: Wer weiß am wenigsten, m.a.W.: wo müssen wir anfangen?
  1) kann PHP
  2) kann Pascal, ganz wenig Python

Buchempfehlung für Einsteiger: Head First Python: http://www.amazon.de/dp/1449358756/?tag=nrrdde-21


Einführung in Django mit Virtualenv
-----------------------------------

Virtualenv
~~~~~~~~~~

Venv dient der Kapselung von Bibliotheken; zum einen können Pakete von Systempaketen abgekapselt werden, zum anderen kann man in unterschiedlichen Projekten verschiedene Versionen der Pakete verwendet.

Es gibt helferscripte für verschiedene Shells (bash, zsh, fish).

'pip' ist DER Paketmanager für virtualenvs.
Unter Debian/Ubuntu einfach mit python-pip bzw. python3-pip

'pip search' sucht in pypi nach Paketen.

Virtualenv kann auch mittels python-virtualenv installiert werden.
Virtualenv-Wrapper kann als Paket 'virtualenvwrapper' installiert werden.

virtualenv
https://virtualenv.pypa.io/en/latest/
Virtualenv anlegen mit 'virtualenv <folder>'.
Aktivieren mit '. <folder>/bin/activate'
'which python' zeigt, dass Python von dem virtualenv verwendet wird.
'pip freeze' zeigt die installierten Pakete.
'pip install <paket>' installiert das Paket.
'deactivate' verlässt das virtualenv


virtualenvwrapper:

http://virtualenvwrapper.readthedocs.org/en/latest/index.html
'mkvirtualenv <envname>' legt das env.
'workon <envname>' aktiviert das env.

spezifische Version eines Paketes installieren:
'pip install Django==1.5.10'

die requirements.txt von einem Projekt installieren mit
'pip install -r requirements.txt'

eine neue requirements.txt erstellen mit
'pip freeze > requirements.txt'

virtualenvs listen
'lsvirtualenv'

virtualenv löschen
'rmvirtualenv <name>'


Django
~~~~~~

http://www.djangoproject.com/
https://docs.djangoproject.com/en/1.7/intro/tutorial01/
Buchempfehlung: http://www.amazon.de/dp/098146730X/?tag=nrrdde-21


neues Env mit name dj-shack und Python3
'mkvirtualenv dj-shack -p /usr/bin/python3'
Django installieren in der aktuellsten Version
'pip install Django'

einen Ordner für das Projekt anlegen
'mkdir hello-django'
'cd hello-django'

ein neues django-projekt
'django-admin startproject hello'

in das Projektverzeichnis von Django wechseln:
'cd hello'

den runserver starten
'python manage.py runserver'

nun auf http://localhost:8000 surfen

eine neue App anlegen mit dem namen 'ola'
'./manage.py startapp ola'



Sonstiges
---------

Emberjs hat ein wesentlich süßeres Logo als Angularjs.

-> mpathy schuldet TW 10 Euro <-

Mehr Strom!

* FIXME (weitere Punkte hinzufügen, oder bestehende Agenda-Punkte verbessern)
