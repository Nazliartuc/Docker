# Docker #

## Einführung ##
Wir mussten mit Docker einen zweiten Service erstellen. Welher auch wieder über das Netz erreichbar ist. Wichtig war Dabei zu beachten das der Container mit dem "Dockerfile" erstellt wird. Ich habe mich für Einen Webserivce entschieden. 

In diesem Dokument werde ich kurz beschreiben wie ich den Webservice erstellt habe. Die Website ist nur eine Standart seite aber es istersichtlich, dass ich die HTML seite bearbeitet habe.


# Inhhaltsverzeichniss
1. [Dockerfile](#Dockerfile)
    1.1 [Zugriff Webservice](#Zugriff)
2. [Probleme](#Probleme)
3. [Reflexion](#Reflexion)

## Dockerfile <a name="Dockerfile"></a>
Ich habe einen Pfad auf meiner Ubuntu maschine kreeiert um es mir zu vereinfachen. Ich habe den Pfad perklick ersellt und das Dockerfile über das Terminal mit dem Befehl.

		nano Dockerfile

Im Dockerfile habe ich gewisse Konfigurationen angegeben um Apache zu installieren. 

Anfangs gebe ich die Ubuntu Version an und von wem dieses Dockerfile erstellt wurde.

		FROM ubuntu:18.04
		MAINTAINER Nazli Artuc

Es ist wichtig im Dockerfile den befehl "RUN" anzugeben damit dieser als befehl erkannt wird.
Hier wird zuerst ein Update ausgeführt und dannach wir Apache2 installiert.

		RUN apt-get update && apt-get install -y apache2

Mit "ENV" wir die Umgebungs Vaiable ffür Apache angegeben.

		ENV APACHE_RUN_USER www-data
		ENV APACHE_RUN_GROUP www-data
		ENV APACHE_LOG_DIR www-data
		ENV APACHE_RUN_DIR www-data
		
Mit "EXPOSE" wird der port freigegeben.

		EXPOSE 80

Um apache standartmässig zu starten wird der "CMD" befehl benötigt.

		CMD ["/usr/sbin/apache2ctl", "-D" "FOREGROUND"]


### Zugriff Webservice <a name="Zugriff"></a>

Der zugriff auf den Webservice erfolgt über einen Webbrowser.

WICHTIG!

Ich habe auf einer VM gearbeitet und jenach VM einstellung ist der Webservice auf dem Lokalengerät erreichbar oder nur über die VM selbst.

Wenn meine VM auf "NAT" gestellt ist, ist der Webservice nur auf der Ubuntu Maschine im Webbrowser aufrufbar. 

        172.0.0.1:8080

Wenn die VM auf VMnet1 gestellt ist also "Host-Only" kann man die IP-Adresse aufrufen und mit der IP-Adresse auch vom Lokalen Computer darauf zugreifen.

        "IP-Adresse":8080

## Probleme <a name="Probleme"></a>

Ich hatte anfange Probleme, da ich nicht mit dem Dockerfile gearbeitet hatte. Es funktionierte Grundsätzlich alles nur, dass ich nicht die erwartungen erfüllt hatte und noch einmal von vorne beginnen musste. Es war kei grosses Problem, weil wenn man mit dem Dockerfile arbeitet ist vieles vereinfacht bzw. dauert es weniger lang, da es grössten teils Automatisiert ist.

Ein anderes PRoblem war, dass ich vergessen hatte, wenn ich das html file ab ändere ich eine neue Dockermachine erstellen muss. Dank der hilfe von einem Klassenkollege Flavio Paganini konnte ich jedoch dieses Problem lösen.

## Reflexion <a name="Reflexion"></a>

Ich muss sagen das dieses Thema sehr interessant ist genau so wie mit Vagrant und ich hoffe, dass ich dies auch in Zukunft anwenden kann.
Jedoch muss ich mir selber eingestehen das meine abgegebene Arbeit sehr minimalistisch ist. Dies hat auch auf Private Probleme zurrückzuführen.

Ich werde bei der nächsten aufgabe wieder 100% leistung geben um weiterhin am ball zu bleiben.