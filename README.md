# Ferienlager-neureut

Dokumentation zur Lagerseite.

## Wie verbinde ich mich mit der Lagerseite?

Um was an der Lagerseite zu ändern, muss man sich in den Container hängen. Abgesehen von CLI, kann man sich über das Portainer Frontend mit dem Container verbinden. Hierzu unter http://v2202012133723134785.happysrv.de:9000/ einloggen (login wie der VSever login) > local > Container > exec console > unter **user: root** shell öffnen. 

## Wie füge ich statische Files (png, js, img) hinzu?
Um eine Datei in das Python Django/Nginx Backend hinzuzufügen, muss die Datei in das Verzeichnis /home/data/static kopiert werden. Ein Aufruf im HTML Code sieht dann wie folgt aus. 

```

## static files
<script src="{% static 'lagerpage/js/yoxview/yoxview-init.js' %}"></script>

```

## Wie verwalte ich die Mail/Server config?

Unter https://www.customercontrolpanel.de/ mit den Daten aus WhatsApp anmelden. (**SogO groupware = Mailsoftware**)

## Was mache ich nachdem ich Code oder Files hinzugefügt habe?
Nachdem Code oder File Structure Änderungen getätigt wurden, tut es nicht weh einmal das Socket Backend und den Webserver neuzustarten.

```
sudo service uwsgi restart
sudo service nginx restart
```
**HINT:** Uwsgi wird beim restarten failen. Das ist nicht so schlimm, da der Socket trotzdem erstellt und geserved wird. Dieser Fehler behindert nicht die Funktionalität. Er tritt aus irgendeinem bei Containern auf.

**HINT2:** Wenn man ein Update **ERFOLGRREICH** deployed hat, wäre es nett ein Image aus dem Container zu bauen um ein Backup zu haben.
## Was tue ich, wenn ich alles ohne Gnade kaputt gemacht habe?

Sollte man alles zerstört haben, kann man den Container löschen und das Image *ferienlager-neureut-backup:latest* mit den Ports 80:80 443:443 deployen.
