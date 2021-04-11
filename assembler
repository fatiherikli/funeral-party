ASSUME  CS:CODE, DS:DATA        ;- dem Assembler die Zuordnung der Segmentregister zu den Segmenten mitteilen

DATA    SEGMENT                 ;Beginn des Datensegments
Meldung db  "Hallo Welt"        ;- Zeichenkette „Hallo Welt“
        db  13, 10              ;- Neue Zeile
        db  "$"                 ;- Zeichen, das INT 21h, Unterfunktion 09h als Zeichenkettenende verwendet
DATA    ENDS                    ;Ende des Datensegments

CODE    SEGMENT                 ;Beginn des Codesegments
Anfang:                         ;- Einsprung-Label fuer den Anfang des Programms
        mov ax, DATA            ;- Adresse des Datensegments in das Register „AX“ laden
        mov ds, ax              ;  In das Segmentregister „DS“ uebertragen (das DS-Register kann nicht direkt mit einer Konstante beschrieben werden)
        mov dx, OFFSET Meldung  ;- die zum Datensegment relative Adresse des Textes in das „DX“ Datenregister laden
                                ;  die vollstaendige Adresse von „Meldung“ befindet sich nun im Registerpaar DS:DX
        mov ah, 09h             ;- die Unterfunktion 9 des Betriebssysteminterrupts 21h auswaehlen
        int 21h                 ;- den Betriebssysteminterrupt 21h aufrufen (hier erfolgt die Ausgabe des Textes am Schirm)
        mov ax, 4C00h           ;- die Unterfunktion 4Ch (Programmbeendigung) des Betriebssysteminterrupts 21h festlegen
        int 21h                 ;- diesen Befehl ausfuehren, damit wird die Kontrolle wieder an das Betriebssystem zurueckgegeben
CODE    ENDS                    ;Ende des Codesegments

END     Anfang                  ;- dem Assembler- und Linkprogramm den Programm-Einsprunglabel mitteilen
                                ;- dadurch erhaelt der Befehlszaehler beim Aufruf des Programmes diesen Wert
