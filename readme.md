2 Jebao Wavemaker (SW-4) Pumpen selbst steuern
=======
Da das Str�mungsbild trotz der vielen M�glichkeiten die die Controller von Hause aus bieten, nicht meinen W�nschen entsprach, habe ich dieses kleine Projekt auf die Beine gestellt.
�ber die PWM Pins des Arduino wird ein Signal erzeugt und mit einem RC-Glied in eine Gleichspannung umgewandelt.
Die Gleichspannung wird �ber den OP verst�rkt und liefert am OP Ausgang 0-9V (oder 0-10V wenn man eine 10V Spannungsquelle hat).
Im Programm wird Pump1 als Master betrachtet und Pumpe 2 ist Slave. Wenn Pump1 auf 100% l�uft, l�uft Pumpe2 mit 0%.
Es gibt 4 Timings (siehe Bild) die man frei definieren kann. Auch sind 0% und 100% Leistung frei einstellbar (PWM Rate 0-255).
0% bedeutet bei mir, dass die Pumpe mit minimaler Leistung l�uft, so dass diese gerade nicht stehen bleibt.
Den Arduino Sketch also einfach im Kopfteil an die eigenen Bed�rfnisse anpassen.

![Timing Diagramm](https://github.com/sruttloff/arduino-wavemaker-controller/blob/master/timing.jpg?raw=true)

Zur Umsetzung ben�tigt wird:
1. Arduino Mega 2560 (eine kleinere Version des Arduino tut's auch, dann muss allerdings die Pinbelegung angepasst werden)
2. 1 x OP Verst�rker LM358
3. 6 x 10kOhm Widerst�nde
4. 2 x 22uF Elko's
5. Netzteil mit 9-12V DC
6. Ein paar Meter 2 Adriges Kabel + Hohlstecker (3,5mm / 1,45mm) um die Controller der Pumpen anzuschliessen.

Hier der Schaltplan:
![Schaltplan](https://github.com/sruttloff/arduino-wavemaker-controller/blob/master/circuit-breadboard_Schaltplan.png?raw=true)

Hier der Aufbau auf einer Steckplatine (Breadboard):
![Schaltplan](https://github.com/sruttloff/arduino-wavemaker-controller/blob/master/circuit-breadboard_Steckplatine.png?raw=true)

Die Pin 1 und 2 von J1 liefern dann die Spannung von 0-9V f�r die beiden Controller.
Ich selbst habe die SW-4 Controller mit Hohlsteckern angeschlossen.
Hat man die Version der Controller ohne die Steckanschl�sse, muss man das Geh�use �ffnen. Einfach die 4 Schrauben auf der R�ckseite entfernen.
Dann den Deckel abnehmen. Nun muss die Platine gel�st werden. An der Stelle wo eigentlich die Buchse sitzen sollte, wurde vom Hersteller der Ground-Pin mit dem Kontaktpin der Buchse verl�tet.
Entweder ist da nur sehr viel L�tzinn drauf oder ein Draht wurde zwischengel�tet. Das muss man entfernen.
Der Nachteil ist hierbei, dass der Controller nun nichts mehr tut, da er auf ein Signal von aussen wartet. 
Einen Kippschalter aufzul�ten, bringt die L�sung. So kann man zwischen normalem und externem Modus umschalten.

Hier ein Foto wo man den Draht anl�tet:
![Timing Diagramm](https://github.com/sruttloff/arduino-wavemaker-controller/blob/master/jebao-board.jpg?raw=true)

Markierung 1 zeigt, wo die Br�cke auf der Vorderseite der Platine zu entfernen ist. Statt der Br�cke einen Schalter zwischen setzen.
An den - kommt dann der Minus von der Schaltung und an + der Ausgang von der Schaltung.

Optionaler Schalter zur F�tterung
Bei Dr�cken des Schalters wird der F�tterungsmodus aktiviert. Die Pumpen stehen f�r 10 Sekunden still.
Erneutes Dr�cken, bricht den Modus ab.
Hier der Schaltplan und der Aufbau auf einer Steckplatine (Breadboard)::
![Schaltplan](https://github.com/sruttloff/arduino-wavemaker-controller/blob/master/circuit-breadboard-food-switch_Schaltplan.png?raw=true)

![Schaltplan](https://github.com/sruttloff/arduino-wavemaker-controller/blob/master/circuit-breadboard-food-switch_Steckplatine.png?raw=true)
