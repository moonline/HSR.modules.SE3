==========================
FS14 SE3 Repetitionsfragen
==========================


Antworten zu den Repetitionsfragen
==================================
Falls vorhanden befinden sich diese im GitHub Repository. Ergänzungen oder ganze Antwortensets sind jederzeit herzlich willkommen. https://github.com/moonline/HSR.modules.SE3



Symbolerklärung
===============
**[DP]**
Wissensfragen des Dozenten (Slides) für die Prüfung

**[EW]**
Wissensfrage, die über den Stoff der Vorlesung hinaus geht.



1 Java Advanced
===============

**1.0.1.**
Wie wurden bis Java 1.4 Generische Schnittstellen Typisiert? Zu welchem Zeitpunkt wurde die Typensichereit sichergestellt? Durch wen? Welche negative Konsequenzen zog dies nach sich.

**1.0.2.**
Welchen Vorteil bringen Generics bezüglich Sicherheit?

**1.0.3.**
Sind List<String> und List<Object> kompatibel, sodass einer Liste von Object eine Liste von Strings zugewiesen werden kann?

**1.0.4.**
Allgemein: Welche Bedingungen müssen erfüllt sein, um eine Variable a einer Variable b zuzuweisen zu können?

**1.0.5.**
Warum wäre es extrem gefährlich, wenn einer List<Person> eine List<Student> zugewiesen werden könnte? Welche Konsequenzen würde dies nach sich ziehen?

**1.0.6.**
Warum ist folgende Zuweisung legitim?

.. code-block:: java

	List<String> ls = new ArrayList<String>();


1.1 Wildcards
-------------

**1.1.1**
Was sind Wildcards und wozu dienen sie? Erklären Sie das zugrunde liegende Problem, das Wildcards notwendig macht.

**1.1.2.**
Warum kann trotz Wildcard innerhalb einer Funktion mit Wildcard Parametern auf diesen keine Änderung vorgenommen werden.

**1.1.3.**
Erlären Sie Upper Bound Wildcards und Lower Bound Wildcards. Wozu dienen sie? Machen Sie je ein Beispiel.

**1.1.4.**
Welche Einschränken bringen Upper Bound Wildcards mit? Welche Lower Bound Wildcards?


1.2 Generische Methoden
-----------------------

**1.2.1.**
Was sind generische Methoden? Welches Problem lösen sie?



1.3 Raw-Type
------------

**1.3.1.**
Warum gibt es von einer generischen Klasse nur eine Definition? Warum gibt es keine non-generic Version?


1.4 Erasure
-----------

**1.4.1.**
Was ist ein Erasure? Was macht es?

**1.4.2.**
Was sind Bridge Methoden? Warum braucht es sie?

**1.4.3.**
Erklären Sie Class Sharing. Erklären Sie das Beispiel unten.

.. code-block:: java

	System.out.println(
		(new List<String>()).getClass() == (new List<Integer>().getClass())
	); // true


**1.4.4.**
Warum funktioniert "new T()" nicht? Welche zwei Alternativen gibt es? Nennen Sie Vor- und Nachteile.


2 Referenzen
============

**2.0.1.**
Was passiert mit nicht mehr erreichbaren Objekten?

**2.0.2.**
Erklären Sie die Zustände

a) created
b) in use
c) invisible
d) unreachable
e) collected
f) finalized

**2.0.3.**
Was ist resurection? Was ist zu berücksichtigen?

2.1 Schwache Referenzen
-----------------------

**2.1.1.**
Was sind schwache Referenzen?

**2.1.2.**
Erklären Sie die folgenden Referenz-Typen:

a) Weak-Referenzen
b) Soft-Referenzen
c) Phantom-Referenzen

**2.1.3.**
Erklären Sie die Erreichbarkeiten:

a) strongly reachable
b) softly reachable
c) weakly reachable
d) phantom reachable
e) unreachable

**2.1.4.**
Was sind java.lang.ref.SoftReference's?

**2.1.5.**
Was sind java.lang.ref.WeakReference's?

**2.1.6.**
Wozu dient die ReferenceQueue?

**2.1.7.**
Was sind java.lang.ref.PhantomReference's? Welche Eigenschaften weisst sie auf?

**2.1.8.**
Erklären Sie die folgenden Methoden, die java.lang.Runtime zur Verfügung stellt:

a) gc()
b) runFinalization()
c) freeMemory()
d) totalMemory()
e) maxMemory()
f) addShutdownHook()


3 AOP
=====

**3.0.1.**
Was ist AOP? Welche Vorteile bietet es?

3.1 AspectJ
-----------

**3.1.1.**
Was sind Pointcut, Advice und Aspect? Was sind JoinPoints?

**3.1.2.**
Was ist der Unterschied zwischen execute() und call()?

**3.1.3.**
Wie kann in einem around() auf die Parameter zugegriffen werden?

**3.1.4.**
Wozu dient thisJoinPoint? Warum kann dies nicht über this erreicht werden?

**3.1.5.**
Wozu dienen target() und args()? Machen Sie ein Beispiel.

**3.1.6.**
Wie kombinieren Sie Pointcuts?

**3.1.7.**
Welche Zugriffsrechte haben Sie auf die Felder der gewavten Klasse? Wie können Sie auf private member zugreifen?


4 Agile Programmierung
======================

**4.0.1.**
Erklären Sie die Begriffe "Prinzip", "Methode" und "Prozess".

**4.0.2.**
Wie ist der RUP aufgebaut? Welche Dokumente werden üblicherweise erstellt?


4.1 Scrum
---------

**4.1.1.**
Was ist Scrum?

**4.1.2.**
Wie ist Scrum aufgebaut? Machen Sie eine Skizze.

**4.1.3.**
Wozu dient das Backlog? Was sind Product- und Release Backlog?

**4.1.4.**
Welche Aufgabe hat der Product Owner?

**4.1.5.**
Wozu dienen die "Sprint Planning Meetings"?

**4.1.6.**
Wer ist der ScrumMaster? Was ist seine Aufgabe?

**4.1.7.**
Was ist ein Sprint?

**4.1.8.**
Wozu dienen "Daily Scrum Meetings" und was wird diskutiert?

**4.1.9.**
Was ist das "Executable Increment"?

**4.1.10.**
Welche Rollen gibt es bei Scrum?


4.2 Agile Prinzipien
---------------------

**4.2.1.**
Fassen sie die agilen Prinzipien kurz zusammen.

**4.2.2.**
Nennen Sie die drei Prämissen agiler Software Entwicklung.

**4.2.3.**
Wie funktioniert Agile Planung?

**4.2.4.**
Was ist das Ziel jeder Iteration?

**4.2.5.**
Wie wird der Fortschritt gemessen?


4.3 Agile Teams
---------------

**4.3.1.**
Welche Rolen gibt es? Wie werden die Rollen wahrgenommen? Wer ist verantwortlich?

**4.3.2.**
Nennen Sie einige Erfolgsfaktoren für Agile Teams.


4.4 Agile Projekte
------------------

**4.4.1.**
Was ist der "Inception Desk"?


4.5 User Stories
----------------

**4.5.1.**
Was sind User Stories? Wie werden sie notiert (Format)?

**4.5.2.**
Nennen Sie einige Eigenschaften guter User Stories.

**4.5.3.**
Erklären Sie den Unterschied zwischen User Storie und Use Case.


4.6 Aufwandschätzung
--------------------

**4.6.1.**
Wie soll zu Projektbegin geschätzt werden?

**4.6.2.**
Wie funktioniert agiles schätzen?

**4.6.3.**
Was ist Punkte basiertes schätzen und wie funktioniert es?

**4.6.4.**
Wann sollte neu geschätzt werden und wann nicht?


4.7 Agile Planung
-----------------

**4.7.1.**
Wie unterscheidet sich agile von statischer Planung?

**4.7.2.**
Wie funktioniert agile Planung?

**4.7.3.**
Wie flexibel ist der Projektumfang? Was ist zu tun, wenn neue User Stories hinzukommen?

**4.7.4.**
Listen Sie auf, aus welchen Schritten ein agiler Plan besteht.

**4.7.5.**
Zeichnen Sie eine Burn-Down Chart, bei der in Iteration 2 und 5 je 5 Punkte neue Features hinzukommen. Nehmen Sie alle andern notwendigen Annahmen an.


4.8 Agile Methoden & Management
-------------------------------

**4.8.1.**
Erklären Sie die folgenden Methoden:

a) TDD
b) Refactoring
c) Continious Integration

**4.8.2.**
Was ist Just-In-Time Analysis?

**4.8.3.**
Was ist ein Iteration Planning Meeting und wie ist es aufgebaut?

**4.8.4.**
Welche Vorarbeiten müssen geleistet sein, um beim IPM die nächste Iteration planen zu können und was wird konkret mit wem geplant?

**4.8.5.**
Wozu dient die Mini Retrospektive?

**4.8.6.**
Wozu dienen die Daily Stand-up Meetings und was wird besprochen?









