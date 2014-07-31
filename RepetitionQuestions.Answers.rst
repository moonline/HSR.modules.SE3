====================================
FS14 SE3 Repetitionsfragen Antworten
====================================

Dieses Dokument wird vorzu erweitert. Ergänzungen und Antworten sind herzlich willkommen.
Repetitionsfragen: https://github.com/moonline/HSR.modules.SE3/blob/master/RepetitionQuestions.rst


1 Java Advanced
===============

**1.0.1. Generische Schnittstellen bis Java 1.4**

Technische Umsetzung
	Für die Generalisierung wurde Object verwendet. Da alle Klassen implizit von Object ableiten, war die verwendung beliebiger Klassen möglich.
	
Zeitpunkt
	Die Typenprüfung fand zur Laufzeit statt und musste durch den Entwickler umgesetzt werden (typeof).
	
Folgen
	* Laufzeitfehler und eine fehlende Möglichkeit, bereits zur Kompilationszeit auf korrekte Verwendung zu überprüfen (Fehler treten zu spät auf)
	* Notwenigkeit einer aufwendige Dokumentation, da die Schnittstelle selbst nicht dokumentierte, welche Typen erlaubt waren
	

**1.0.2. Vorteil von Generics**

Der Compiler kann die Typensicherheit gewährleisten, sodass entsprechende Fehler nicht erst zur Laufzeit auftreten.


**1.0.3. Kompatibilität von Generics**

Nein. Weil man sonst der Studentenliste Objekte anfügen könnte -> Typensicherheit unterlaufen:

.. code-block:: java

	List<Object> ol = new ArrayList<Object>();
	ol.add(new Object());
	List<String> sl = new ArrayList<String>();
	sl.add(new String("Hallo"));
	
	ol = sl; // NICHT zulässig, da man aufgrund des statischen Types 
		 // "Object" von ol der Studentenliste "Objects" hinzufügen kann!
		 
		 
**1.0.4. Zuweisungen**

Die Variable muss vom gleichen oder einem abgeleiteten Typ sein:

.. code-block:: java

	Object o = new Object();
	String s = new String("Hallo");
	String p = s; // legitim da Type identisch
	Object q = s; // legitim da String von Object erbt
	String z = o; // NICHT legitim da Object kein Subtyp von String!
	
	List<String> ls = new List<String>();
	ls = new ArrayList<string>(); // legitim da ArrayList von List erbt.
	
	
List<Object> und List<String> sind zwei komplett andere Typen, auch wenn String von Object erbt!
Java löst Generics mit Casts, aber in C# wird für jede Generisch benutzte Klasse eine effektive Instanz vom Compiler erstellt.
Aus List<string> und List<Object> werden in C# List_string und List_Object, was eindeutig zeigt, das dies zwei unterschiedliche Klassen sind, die nur ähnlich heissen.


**1.0.5. Konsequenzen**

Weil dann eine mit List<Person> statisch typisierte Liste eine List<Student> enthalten würde, womit der Studentenliste Personen zugewiesen werden könnten!


**1.0.6. Beispiel**

Weil ArrayList ein Subtyp von List ist.
In C# würde die Klasse ArrayList_String von List_String ableiten. Dies zeigt, warum es geht.


1.1 Wildcards
-------------

**1.1.1 Wildcards**

Wildcards sind Platzhalter (?), die dazu dienen generische Klassen mit einem Typ zu generalisieren, der erst zur Compilezeit bekannt ist (z.B. eine Methode, die als Parameter eine Liste mit beliebigem Inhalt annimmt):

.. code-block:: java

	public function Log(List<?> list) {
		for(Object o : list) {
			logger.log(o.toString());
		}
	}


**1.1.2 Einschränkungen mit Wildcards**

Da die Methode mit einem beliebigen Typ verwendet werden kann, kann der Compiler nicht gewährleisten, das bei einer Zuweisung die Typen übereinstimmen:

.. code-block:: java

	public function Log(List<?> list) {
		list.add(new Object()); // NICHT gültig, da die Kompatibilität nicht klar ist
	}
	
	
**1.1.3 Upper/Lower bound Wildcard**

Upper Bound
	* "Oben gebunden"
	* ermöglichen das eingrenzen auf Subtypen
	* Nur lesenden Zugriff auf generische Klasse wie bei <?>
	* <?> = <extends Object>
	
	.. code-block:: java
	
		// Nur Strings oder subklassen erlaubt
		public function log(List<? extends String> list) {
			for(String s : list) { // gültig da eine Subklasse auch ein String ist
				logger.log(o.toString());
			}
		}
		
Lower Bound
	* "Unten gebunden"
	* ermöglichen das eingrenzen auf Elterntypen
	* Nur schreiben Zugriff auf generische Klasse, bei lesendem Zugriff nicht gewährleistet werden kann, das die Parent Klasse die verwendeten Methoden unterstützt.
	* Methoden, die nicht lesen nicht mit dem generischen Parameter parametrisieren, da sie sonst bei einem Lower Bound Wildcard nicht aufgerufen werden können
		
	  .. code-block:: java
	
		public boolean contains(Object c) {} // statt E
		
	
	.. code-block:: java
	
		public function log(List<? super String> list) {
			list.add(new String()); // gültig, da String garantiert eine 
			                        // Subklasse vom der Klasse des Genericparameters ist.
		} 
		

**1.1.4. Einschränkungen Wildcards**

Upper Bound
	Nur lesenden Zugriff auf generische Klasse
Lower Bound
	Nur schreibenden Zugriff auf generische Klasse
	
Erklärung siehe vorherige Frage.


1.2 Generische Methoden
-----------------------

**1.2.1. Generische Methoden**

Anstatt dem generalisieren von ganzen Klassen kann eine einzelne Methode einer nicht generischen Klasse typisiert werden:

.. code-block:: java

	class Logger {
		// ...
		public <T> void log(T element) {
			this.writeToLogFile(element.toString);
		}
		// ...
	}
	
Der Kompiler stellt aufgrund der aktuellen Parameter die Typensicherheit sicher!
Gäbe es generische Methoden nicht, müsste jeweils die ganze Klasse generalisiert werden und die gleiche Instanz könnte nicht mehr von verschiedenen Klassen genutzt werden.



1.3 Raw Types
-------------

**1.3.1. Raw Type**

Zur Abwärtskompatibilität entschieden sich die Java Entwickler, Generics mit Casts und nicht wie in C# mit einzel kompilierten Klassen zu lösen. Damit Generic Klassen weiterhin mit altem Code kompatibel waren, verwenden alle die gleiche Klasse.

Damit muss der Code auch ohne Angabe der <> kompilierbar sein, was zur Notwendigkeit von Raw Types führt.


1.4 Erasure
-----------

**1.4.1. Erasure**

Erasure bedeutet, das zur Compilezeit der generische Parameter entfernt und mit dem Upper Bound Typ ersetzt wird:

.. code-block:: java

	class Test<T> {
		T attr;
		public T getAttr() { .. }
		public void setAttr(T p) {.. };
	}

	// wird zu
	
	class Test {
		Object attr;
		public Object getAttr() { .. }
		public void setAttr(Object p) { .. }
	}
	
	
Wo notwendig, ergänzt der Compiler casts.


**1.4.2. Bridge Methoden**

Bridge Methoden verhindern eine "noSuchMethod" Exception mit falsch verwendetem Legacy Code:
Dazu wird eine generische Methode, die mit einem bestimmten Parameter typisiert wurde, zusätzlich mit einer Object-parametrisierten Methode überladen. So findet der Compiler in jedem Fall die Methode und wirft anschliessend eine Class Cast Exception.

.. image:: img/1.13.jpg
   :width: 75 %
   
.. image:: img/1.14.jpg
   :width: 75 %

   
**1.4.3. Class Sharing**

Da immer nur eine Klasse existiert liefert getClass immer den Raw-Type. Entsprechend ist folgender Code lauffähig:

.. code-block:: java

	// gäbe true zurück
	new List<String>()).getClass() == (new List<Integer>().getClass(); 
	  
	  
**1.4.4. new T()**

Der Compiler weiss nicht, ob der übergebene Typ einen Defaultkonstruktor besitzt da die formalen Parameter ja durch das Erasure entfernt wurden.

Alternativen:

* Objekt injecten (von aussen übergeben)
* Classtype übergeben und über Reflection instanziieren


