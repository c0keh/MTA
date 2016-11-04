# Uebung 1


## Aufgabe 1 - Audioaufnahme


> Erzeuge  zwei  kurze  Audio-Files  (max.  5  s),  davon  eines  mit  Musik  deiner  Wahl  aus  dem  Internet (wobei sich Musik mit einer relativ hohen Dynamik, d.h. Wechsel zwischen relativ leisen und lauten Abschnitten 
empfiehlt). Wähle eine Abtastrate von 44kHz, 16 Bit Auflösung, mono und achte auf gute Aussteuerung. Das   zweite   Audio-File   soll   eine   Sprachaufnahme   (mit   dem   Headset aufgesprochen)   enthalten (Übersteuerung  vermeiden
!).  Wähle  hier  eineAbtastfrequenz  von  22  kHz,  16  Bit  Auflösung,  mono.  Die Einstellungen wie Abtastrate, Bitzahl und Kanalzahl können im Wavestudio_Samplitude vorgenommen werden. Die Eingangsquelle (wahlweise Audio-CD oder Mikrofon) kann im Windows-Mixer 'Aufnahme' eingestellt werden. Benenne  die  Dateien Musik_[NameArbeitsgruppe].wav und Sprache_[NameArbeitsgruppe].wav. Schick mir  die  beiden  WAV-Dateien  unter  Nennung  deiner  Arbeitsgruppe  per  Mail(ahoenemann@beuth-hochschule.de). Darauf  werde  ich  dir  zwei  WAV
-Dateien  mit  Testsignalen  zusenden,  die  du  bei  den folgenden   Aufgabenpunkten   benötigst,   sine_hiXX.wav   und   sine_loXX.wav. Lies   die   Musik-und   die Sprachdatei mit wave_io ein und erkläre die Angaben im Header! Wie  hoch ist die Bitrate  für die beiden 
Dateien?

### Lösung

filelength: Größe der WAV-Datei in Bit
Samples: erstellte Samples (Proben) insgesamt.
rate: erstellte Samples pro Sekunde
bits: Auflösung der Amplitude je Sample
bytes per Sample: channels * bits in byte
channels: Kanäle (mono/stereo/...)


Bit/s = SamplesProSekunde * bits

![SpracheMetadaten](/Bilder/Aufgabe1_Sprach_Metadaten)
Bit/s = 22050 * 16 = 352800


![SpracheMetadaten](/Bilder/Aufgabe1_Musik_Metadaten)
Bit/s = 44100 * 16 = 705600


## Aufgabe 2 - Aliasing

a
> Modifiziere  wave_io dahingehend,  dass  die  Samples  in  der  WAV-Datei  in  eine  (lesbare)  ASCII-Datei geschrieben  werden.  Lies  die  von  mir  geschickten  Dateien  (Sampling-Frequenz:  16  kHz)  ein  und bestimme   aus   den   resultierenden   Zahlenfolgen   in   der   ASCII-Datei   die Frequenz   der   Sinus-Schwingungen. Erkläre das Ergebnis und speichere jeweils eine Periode für das Protokoll ab. Überprüfe Deine Schätzung mit dem Spektralanalyse-Tool GRAM (Plots ins Protokoll !). Vorgehensweise: Menü Analyze File, Einstellungen: Freq Scale: Linear, FFT Size: 512, Time scale: 1 msec

b
> Bei der zeitlichen Diskretisierung eines Analogsignals muss das sogenannte Abtasttheorem eingehalten werden.  Wie lautet  es  und  wie  lässt  sich  der  Grenzfall,  für  den  es  gerade  noch  gilt,  illustrieren (Zeichnung!)?

c
> Bei  herkömmlichen  Soundkarten  tritt  systembedingt  kein  Aliasing  auf,  weil  das  Audiosignal  stets geeignet vorbehandelt wird (wie?). 

d
> Mit einem kleinen Trick lässt sich Aliasing jedoch nachweisen. Diese auch als Down-Sampling bekannte Methode  besteht  darin,  dass  man  bei  einer  WAV-Datei  z.B.  jeden  zweiten  Abtastwert  wegwirft.  Man erhält  so  eine  Wellenform,  die  genau  die  Hälfte  der  ursprünglichen  Abtastfrequenz  aufweist.  Wenn man das Signal nicht vorher bandbegrenzt hat, können Aliasing-Verzerrungen hörbar werden. Modifiziere  wave_io  dahingehend,  dass  vom  eingelesenen  Signal  jeder  zweite  Abtastwert  verworfen wird  und  das  resultierende  Signal  abgespeichert  wird. Der  Header  muss natürlich  entsprechendverändert  werden!  Wende  das  resultierende  Programm  zunächst  auf  'sine_lo.wav'  und  'sine_hi.wav' an.   Welche   Frequenzen   erscheinen   nach   dem   Down-Sampling   (Spektrogramm   und   WAVs   ins Protokoll!)? 

e
> Was würde passieren, wenn man geeignet bandbegrenzen würde?

### Lösung
xxx


## Aufgabe 3 - Bitreduzierung

a
> Die herkömmlichen PC-Soundkarten arbeiten meist entweder mit 16 oder 8 bit-Auflösung. Wie groß ist die Anzahl der darstellbaren Amplitudenwerte bei diesen beiden Werten?

b
> Wir  wollen  nun  wave_io  so  modifizieren,  dass  wir  die  Bitanzahl  reduzieren  können.  Dazu  können  wir z.B. alle  Samples durch eine  Potenz von 2 teilen (Integer-Division ohne  Rest). Damit das resultierende Signal  nicht  leiser  wird  als  das  Original,  kompensierenwir  die  Operation  durch  Multiplikation  mit derselben  Zweierpotenz. Beachte:  Der  Datentyp  hat  nach  wie  vor  16  Bit!(Denselben  Effekt  erreicht man auch durch einfaches logisches 'Verunden' mit einem entsprechenden HEX-Wert, indem man mit dem LSB beginnend Bits 'ausblendet'.) Mit dem entstandenen Programm verändern wir die in Aufgabe 1   erzeugten   Wave-Dateien.   Ab   welcher   Bitzahl   tritt   bei   Musik/Sprache   eine   hörbare/deutliche Verschlechterung der Qualität ein? Bei wieviel Bit ist dasSprachsignal noch verständlich? (Waves für all diese     Fälle     ins    Protokoll,     Ausschnitte     als    Plots).Was     charakterisiert     das     entstehende Quantisierungsgeräusch und macht es besonders störend?

c
> Modifiziere  dein  Programm  noch  einmal  so,  dass  auch  das  Differenzsignal  zwischen  Original  und bitreduziertem  Signal,  das  heißt,  das  Quantisierungsrauschen  ausgegeben  werden  kann.  Welchen Charakter hat das Rauschen bei einer Reduktion um 1 Bit, wie verändert es sich bei zunehmender Bit-Reduktion? (Waves für all diese Fälle ins Protokoll, Ausschnitteals Plots)

### Lösung
Musik-Störung ab 128

Sprache-Störung 128

Sprache gerade noch verständlich 1024