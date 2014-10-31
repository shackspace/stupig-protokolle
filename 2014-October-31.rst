Stupig Treffen vom 31. Oktober 2014
===================================

recap vom letzen mal
++++++++++++++++++++

* Anleitung zum Installieren von Python und Pip auf Windows http://docs.python-guide.org/en/latest/starting/install/win/
* virtualenv / virtualenvwrapper will man
* mehr dazu im Protokoll vom letzen mal: https://github.com/shackspace/stupig-protokolle/blob/master/2014-October-17.rst
(fixes zu virtualenv bitte ins alte Protokoll einpflegen!)

Begriffserklärung:

- python3 ((P)ython >= 3.3)
- python3-pip (pip=Python Package Index)
- python-virtualenv (Python Virtual Environments)
- virtualenvwrapper (set of extensions to Ian Bicking's virtualenv tool)




Einsteigerprojekt LetUsOrder.It startet
---------------------------------------

  * Erklärung der Herangehensweise:
  
    * im Haupt-github-repo wird nur gearbeitet während des Workshops
      https://github.com/letusorderit/letusorderit
    * Jeder darf und soll Forken und mit seinem Fork herumspielen/experimentieren
    * Gerne werden bei jedem Workshop auch Fragen zu vorigen Themen beantwortet 


  * Django für letusorder.it einrichten



  * Modelle erklären und anlegen
  * Admin konfigurieren und zeigen

  * preview:

    * django-rest-framework
    * api design: Versionierung der API, Pagination nicht erst nachreichen
    * Viewsets / Serializers

* DjangoDash/WsgiWrestle-Planungen

  - DjangoDash/WsgiWrestle ist am 29. + 30.11
  - Wer ist dabei? Bei welchem Projekt?

* http://www.reddit.com/r/Python/comments/2kuraa/does_using_django_make_me_less_of_a_programer/ ;-)


----------------------------------------------------------------------

(FIXME ab hier)

# Installation unter Ubuntu 14.04

sudo apt-get install python3 python3-pip python-virtualenv virtualenvwrapper




# source virtualenvwrapper, best included in  ~/.bashrc 
if [ -f /usr/share/virtualenvwrapper/virtualenvwrapper.sh ] ; then
    . /usr/share/virtualenvwrapper/virtualenvwrapper.sh
fi

# define your projektname here
export prjdir="letusorderit"
workon "$prjdir"

# the following does not work, if copied to cmdline?!?
# ! copy from pad inserts weird whitespaces and things fail
if [ ! $? ] ; then
mkvirtualenv "$prjdir" -p /usr/bin/python3
workon "$prjdir"
fi

# *nicht* in das env gehen
# cdvirtualenv "$prjdir"

# leave virtualenv
# deactivate

# install Django in our virtualenv 
pip install Django
# additional Management-commands (shell_plus)
pip install django-extensions
# get ipython
pip install ipython
# other python shell with verbose completion display, ctrl-r, ctrl-s
# pip install bpython
# have browser based scripting
# pip install ipython[notebook]
# debugger tipp: ipdb, pycharm
# getsentry.com for stack trace management
# pip install -r requirements.txt

git clone https://github.com/letusorderit/letusorderit/
cd letusorderit
# create a branch named as your user
git branch $USER
git checkout $USER

# weiter mit "Projekt anfangen" s.u.

Achtung: explizit => Python3

mkvirtualenv letusorderit -p /usr/bin/python3



Projekt anfangen
================
(im aktivierten Virtualenv)
$ django-admin startproject letusorderit
$ cd letusorderit
$ ./manage.py migrate
$ ./manage.py runserver &
$ ./manage.py createsuperuser
# define superuser for administration
# browse to http://127.0.0.1:8000/admin/ and log in

# create an app for the order management, 
# contains database layout for orders
./manage.py startapp ordermgmt


