# Projektantrag
Wir stellen hier unser IT-Projekt "Contributing to the experimental open-source rust operating system + microkernel RedoxOS" (Arbeitstitel) vor und führen die Ziele aus, die wir uns gesteckt haben.

## Florian Naumann

Ich möchte vor allem meinen Teil im Projekt Ion beitragen. 
Link zum Repository: https://gitlab.redox-os.org/bool_purist/ion.

Ansonsten finde ich noch den Bereich Coreutils interessant. 
Das ist jedoch optional und nur relevant falls ich alle Ziele im Bezug zu Ion umgesetzt habe. 
Link zu Coreutils https://gitlab.redox-os.org/redox-os/coreutils .

### Was ist Ion 

Ion ist eine Shell, die es erlaubt, Commandos in der eigenen Ion Skriptsprache auszuführen.
Ion kann nicht nur zum Scripting verwendet werden sondern 
auch in einer interaktiven Session innerhalb eines Terminal Emulators genutzt werden.
Es git auch ein online Manual unter https://doc.redox-os.org/ion-manual/ zu Ion.

### Warum Ion Shell

- Die Ion Skriptsprache ist stark von Rust inspiriert. 
  Damit lassen sich interessante Beobachtungen zwischen dieser Skriptsprache, Rust und anderen Skriptsprachen wie bash ziehen.
- Macht als Shell viele Dinge anders als zum Beispiel Bash. Ion ist nicht POSIX compliant als Beispiel.
- Ion selbst ist in Rust geschrieben.
- Ion ist die Default Shell in Redox Os.

Die Untersuchung von dem eingebauten Parser innerhalb der Ion Shell könnte 
auch für den Bericht interessant sein.

### Konkrete Ziele in Ion Shell

- Es gibt folgende Issues, dich ich auf jeden Fall versuchen will, zu lösen.
  - "Ion crashes after pressing `enter` key frequently" unter https://gitlab.redox-os.org/redox-os/ion/-/issues/1017 .
  - "Ci is broken with current base image redoxos/redoxer from docker hub." unter https://gitlab.redox-os.org/redox-os/ion/-/issues/1020 .
    Continuous Integration schlägt bei jeden Commit/Pull Request fehl. Ich möchte diese Pipelines wieder lauffähig machen.
  - "Implement set -o pipefail" unter https://gitlab.redox-os.org/redox-os/ion/-/issues/1005 .
  - "Is it possible to return arrays from functions?" unter https://gitlab.redox-os.org/redox-os/ion/-/issues/1010 .
  - "Parameter Substitution on arrays" unter https://gitlab.redox-os.org/redox-os/ion/-/issues/1001 .
    Vermutlich auch für Strings.
    Scheint so, als wurde es immer noch nicht von der Person, die es vorgeschlagen hat, implementiert 
- Umsetzung der Polish Notation und intersect builtin unter https://doc.redox-os.org/ion-manual/control/01-conditionals.html .

### Was bisher bei der Einarbeitung in Redox Os schon rauskam

Ich ergänzte hauptsächlich die Dokumentation vom Ion Manual und dem Repository von Ion selbst.
Auch konnte ich schon meinen 1. Bug Fix im Repository Redoxer verzeichnen.
Link zu Redoxer: https://gitlab.redox-os.org/redox-os/redoxer .

Hier befindet sich eine Liste von meinen bisherigen Errungenschaften unter: 
https://github.com/BoolPurist/it_project_redox_ohm/blob/main/archievements.md

## Florian Meißner

## Phillip Wagener
