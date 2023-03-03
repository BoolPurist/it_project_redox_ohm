# Projektantrag
Wir stellen hier unser IT-Projekt "Contributing to the experimental open-source rust operating system + microkernel RedoxOS" (Arbeitstitel) vor und führen die Ziele aus, die wir uns gesteckt haben.

## Florian Naumann

Ich möchte vor allem meinen Teil im Projekt Ion beitragen. 
Link zum Repository: https://gitlab.redox-os.org/bool_purist/ion.

Ansonsten finde ich noch den Bereich Coreutils interessant.
Der ist jedoch optional und nur relevant falls ich alle Ziele im Bezug zu Ion umgesetzt habe. 
Link zu Coreutils https://gitlab.redox-os.org/redox-os/coreutils .

### Warum Ion Shell

- Die Ion Skriptsprache ist stark von Rust inspiriert. 
  Damit lassen sich interessante Beobachtungen zwischen dieser Skriptsprache, Rust und anderen Skriptsprachen wie Bash ziehen.
- Macht als Shell viele Dinge anders als zum Beispiel Bash. Ion ist nicht POSIX compliant als Beispiel.
- Ion selbst ist in Rust geschrieben.
- Ion ist die Default Shell in Redox OS.

Die Untersuchung von dem eingebauten Parser innerhalb der Ion Shell könnte 
auch für den Bericht interessant sein.

#### Was ist Ion 

Ion ist eine Shell, die es erlaubt, Kommandos in der eigenen Ion Skriptsprache auszuführen.
Ion kann nicht nur zum Scripten verwendet werden, sondern 
auch in einer interaktiven Session innerhalb eines Terminal-Emulators genutzt werden.
Es gibt auch ein Online-Manual unter https://doc.redox-os.org/ion-manual/ zu Ion.

#### Konkrete Ziele in Ion Shell

Allgemeinen möchte ich den  Scheme support in Ion auf Redox Os einbringen. 
Beispiel nicht nur "file:" sondern auch Schemes wie "disk:", "acpi:" als Beispiel.
Das ist mein Hauptfokus. 

#### Was sind Schemes in Redox Os

Schemes sind eine eigene Sache aus dem Haus von in Redox Os.
Schemes kann man sich wie URLs vorstellen um Resourcen in Redox Os zu adressieren.

Es gibt zum Beispiel auch das File Scheme welches Dateien adressiert.
Ein Pfad zu einer Datei "/home/user" ist dann gleich "file:home/user" in dem File Scheme.

Jeder Pfad eines Schemes ist mit den Namen des Schemes am Anfange beschrieben "file:...", "acpi:.."
Hier ist die Motivation, dass man zum Beispiel Geräte nicht wie Linux durch eine Datei anspricht 
sondern es über eine URL/Pfad nach einem bestimmten Scheme. Fiktives Beispiel: "driver:keyboard" spricht das 
Keyboard an. 

Interessant hierbei ist, dass auch wenn die URLs eines Schemes wie ein Pfad in einem Baum aussehen mag, 
kann die eigentliche Verwaltung dieser Resourcen unter einen Scheme völlig anderes organisiert sein.
So könnten Resourcen eines fiktiver Scheme wie "list:aa/bb" statt dessen im Hintergrund in einer Liste verwaltet werden.

#### Abseits von der Implementierung von Scheme Support in Ion

Danach/Nebenbei möchte ich versuchen folgende Issues abzuarbeiten.

- "Ion crashes after pressing `enter` key frequently" unter https://gitlab.redox-os.org/redox-os/ion/-/issues/1017 .
- "Ci is broken with current base image redoxos/redoxer from docker hub." unter https://gitlab.redox-os.org/redox-os/ion/-/issues/1020 .
  Continuous Integration schlägt bei jeden Commit/Pull Request fehl. Ich möchte diese Pipelines wieder lauffähig machen.
- "Implement set -o pipefail" unter https://gitlab.redox-os.org/redox-os/ion/-/issues/1005 .
- "Is it possible to return arrays from functions?" unter https://gitlab.redox-os.org/redox-os/ion/-/issues/1010 .
- "Parameter Substitution on arrays" unter https://gitlab.redox-os.org/redox-os/ion/-/issues/1001 .
  Vermutlich auch für Strings.
  Scheint so, als wurde es immer noch nicht von der Person, die es vorgeschlagen hat, implementiert. 
- Fehlermeldungen in Ion sollten auch die Zeile mit angeben, wo der Fehler gefunden wurde unter https://gitlab.redox-os.org/redox-os/ion/-/issues/1022

Restliche Dinge, die nicht noch nicht als Issues feststehen

- Umsetzung der Polish Notation und intersect builtin unter https://doc.redox-os.org/ion-manual/control/01-conditionals.html .
- Wenn eine noch nicht deklarierte Variable referenziert wird, 
  sollte auch der Name der nicht vorhandene Variable in der Fehler Meldung angezeigt werden.

### Bisherige Ergebnisse bei der Einarbeitung

Ich habe hauptsächlich die Dokumentation vom Ion Manual und dem Repository von Ion selbst ergänzt.
Auch konnte ich schon meinen 1. Bug Fix im Repository Redoxer verzeichnen.
Link zu Redoxer: https://gitlab.redox-os.org/redox-os/redoxer .

Hier befindet sich eine Liste von meinen bisherigen Errungenschaften: 
https://github.com/BoolPurist/it_project_redox_ohm/blob/main/archievements.md

## Florian Meißner

### Motivation
Ich möchte auf der [relibc](https://gitlab.redox-os.org/redox-os/relibc), der `libc`-Implementierung in Redox arbeiten. Dort habe ich mir vor allem das Testen ins Auge gefasst.

Weiterhin möchte ich kleinere Verbesserungen an [core](https://gitlab.redox-os.org/redox-os/coreutils)/[extrautils](https://gitlab.redox-os.org/redox-os/extrautils) vornehmen. Auch halte ich eine spätere Kollaboration mit Florian Naumann an Ion für größere Features nicht für ausgeschlossen.

#### Was ist relibc
`relibc` hat es sich als Ziel gesetzt, eine portable POSIX C standard library in Rust zu sein. (https://gitlab.redox-os.org/redox-os/relibc/-/blob/master/README.md) Die Implementierung in Rust sorgt in der Theorie für eine deutlich höhere Typ- und Speichersicherheit. Bindings (= C-Header) werden dann über das Rust-Crate [cbindgen](https://github.com/eqrion/cbindgen) automatisch aus der Rust-API generiert.

#### Warum relibc
Ich habe Vorerfahrung in C- und C++-Entwicklung und möchte diese im Rahmen des Projekts einbringen. Außerdem interessiert mich die Möglichkeit einer robusteren libc und die Schnittstelle Rust <-> C.

Das Testing möchte ich mir vornehmen, da ich leider noch nicht viel Unit Testing-Erfahrung gesammelt habe, aber (in Rücksprache mit meinen Kollegen) die vorhandene Testsuite für eher dürftig halte und die Verbesserung dieser für das Projekt als sehr sinnvoll erachte. 

#### Was sind core/extrautils

### Konkrete Ziele

#### relibc

- **Erweiterungen der aktuellen Unit Tests direkt im Repo**
  Leider werden die fehlenden Tests noch nicht ausführlich als Issue getrackt. Ich werde daher die generierten C-Header mit den vorhandenen Test Cases abgleichen (`grep`) und Mängel notieren.
- **Fuzzing der Library auf Rust-Ebene (und evtl. auch auf C-Ebene)**
  Fuzzing stellt eine gute Addition zu Tests da, um Bugs zu finden, und ist auch von Seiten des Project Owners gewünscht. (https://gitlab.redox-os.org/redox-os/relibc/-/issues/79)
- **Betrachten der Möglichkeit, eine existierende `libc`-Testsuite zu adaptieren**
  `glibc`, `musl libc`, `LLVM libc` haben alle schon das Problem einer Testsuite gelöst. Die Frage bleibt, ob diese sich sauber adaptieren lassen, und ob dadurch, dass `relibc` durch seine Minimalistik viele POSIX-Erweiterungen wohl nicht implementieren wird, nicht zu viele False Negatives auftreten. Auch für dieses Projekt gab es Zuspruch im offiziellen Chat.

##### Mutigeres Ziel
- **Memory safety in classic non-checking c functions like gets, strcmp… via communication with the allocator**
  Ich weiß nicht, ob das im Endeffekt technisch möglich ist, aber da wir in relibc (bei den meisten Programmen) auch den Memory Allocator kontrollieren, könnte theoretisch auch bei den unchecked C-Funtionen - im Fall, dass Heap-allokierte Pointer verwendet werden - die Bounds aus der Heap-Struktur des Allocators gelesen und damit durch die Hintertür Bounds Checking eingeführt werden. Dies schließt bei Legacy-Code ganze Fehlerklassen aus.


## Phillip Wagener

### Motivation

Vor allem möchte ich im RedoxOS Book meinen Teil zum Projekt beitragen. 
Dieses wird aus Markdown-Dateien mittels [mdBook](https://gitlab.redox-os.org/redox-os/mdBook)
Link zum Repository: (https://gitlab.redox-os.org/redox-os/book)

Zudem finde ich das Repository von coreutils/extrautils sehr interessant.
Links zum Repository: (https://gitlab.redox-os.org/redox-os/coreutils) (https://gitlab.redox-os.org/redox-os/extrautils)
Hier werde ich mir einige ToDos raussuchen, um diese umzusetzen.

#### Was ist mdBook

mdBook ist ein Tool von Rust, um aus Markdown-Files eine Dokumentationen zu generieren.

#### Warum RedoxOS Book

- Hier befindet sich die Dokumentation von Redox Os, welche sehr wichtig für das Verständnis und die Weiterarbeit am Projekt ist.
- Gerade an dieser Stelle wird in vielen Open Source-Projekten gerne Zeit gespart. Dies rächt sich aber zuverlässig mit steigendem Projektalter (siehe https://en.wikipedia.org/wiki/Technical_debt).

Daher werde ich meine initialen Anstrengungen darauf konzentrieren, am Buch nachzubessern.

#### Was sind extra/coreutils

- https://www.gnu.org/software/coreutils/
- GNU coreutils sind eine Sammlung an Kommandozeilen-Helfern
- RedoxOS orientiert sich allerdings eher an den BSD coreutils, welche als Paradigma BSD-typisch deutlich minimaler entwickelt werden
- RedoxOS extrautils stellen eine Erweiterung der Utilities-Sammlung durch beliebte und nützliche Tools, die allerdings nicht zu den coreutils gehören, dar.

#### Warum extra/coreutils

- extra/coreutils sind nützliche Helfer, welche meiner Meinung nach mit eingebunden werden sollten.

### Konkrete Ziele
#### RedoxOS Book

Aufgrund der Vielfältigkeit an Aufgaben werde ich mich
1. Auf die Übersetzung der bisherigen Kapitel spezialisieren, und
2. Mich auf neue Kapitel wie zum Beispiel das Filesystem und Speicherverwaltung in Redox konzentrieren

#### extra/coreutils

1. Für den Anfang werde ich mir diverse man-Pages ansehen und schauen wie die Kommandos funktionieren.
2. Zudem werde ich diese Kommandos unter Linux testen und die Unterschiede herausarbeiten.
3. Hierdurch können neue Aufgaben wie zum Beispiel Verbesserungen entstehen, welche ich dann umsetzen werde.

### Aktuelle Ergebnisse

Zurzeit sind noch keine Ergebnisse vorzuweisen. Dies geschah aufgrund eines Todesfalls in der Familie und wird gebeten, zu entschuldigen.
