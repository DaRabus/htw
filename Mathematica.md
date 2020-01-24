
# Mathematica Cheat Sheet
   ## 0 Konstanten ##
   Lichtgeschwindigkeit im Vakuum
   ```
   c = 299792458;(*m/s*)
   ```
   Boltzmann-Konstante
   ```
   kb = 1.380649*(10^-23);(*J/K*)
   kbeV = 8.617333262145179*(10^-5);(*eV/K*)
   ```
   Planck-Konstante
   ```
   h = 6.62607015*10^-34;(*Js*)
   heV = 4.135667696923859*(10^-15);(*eVs*)
   ```
   Dirac-Konstante
   ```
   \[HBar] = h/(2 Pi);(*Js*)
   \[HBar]eV = 6.582119569509066*10^-16;(*eVs*)
   ```
   Maximale photometrische Strahlungsäquivalent
   ```
   Km = 683;(*lm/W*)
   ```
   
   Universelle Gaskonstante
   ```
   R = 8.314462;(* Universelle Gaskonstante *) 
   ```
   Boltzmann-Konstante
   ```
   k = 1.3806488*10^23;(* Boltzmann-Konstante *)
   ```
   Avogadro-Konstante
   ```
   Na = 6.022140857*10^23;(* Avogadro-Konstante *)
   ```
   
   ## 1 Vektoren ##
   ### Betrag eines Vektors
   Der Betrag eines Vektors entspricht der Länge dieses Vektors.
   ```
   Norm[{x, y, z}]
   ```
   ### Kreuzprodukt
   Bei einem Vektorprodukt zweier Vektoren entsteht ein neuer Vektor. Dieser Vektor steht senkrecht auf den beiden Ausgangsvektoren und ist ein Normalenvektor der von den Ausgangsvektoren aufgespannten Ebene und der Betrag dieses Vektors ist ein Maß für die Fläche des aufgespannten Parallelogramms.
   ```
   Cross[{a, b, c}, {x, y, z}]
   ```
   
   ### Skalarprodukt
   Das Skalarprodukt benötigst du in der analytischen Geometrie sehr häufig. Du kannst es verwenden um den von zwei Vekoten aufgespannten Winkel oder die Fläche des dazugehörigen Parallelogramms zu berechnen. Weiter kannst du mit dem Skalarprodukt einfach Orthogonalität oder Kolliniarität nachweisen.
   ```
   {a, b, c} . {x, y, z}
   ```
   ## 2 Daten ##
   ### List (Array)
   Create Lists
   ```
   l=List[2, 3, 5, 6];
   l[[2]]
   ```
   gibt 3 aus
   
   ### ConstantArray
   Generiert in diesem Fall eine Liste mit 10 c.
   ```
   ConstantArray[c, 10]
   ```
   ### Join
   Fügt Listen zusammen
   ```
   Join[{a, b, r}, {x, y}, {t, u}]
   ```
   gibt {a, b, r, x, y, t, u} zurück.
   
   ## 3 Funktionen ##
   ### Funktion ###
   Auf der linken Seite legen wir den Funktionsnamen fest, hier “f” und wählen einen Namen für das
Argument der Funktion “x”. Beachten Sie das wichtige “x_” auf der linken Seite, das ein sogenanntes
Pattern bezeichnet. Auf der rechten Seite von “:=” steht dann die eigentliche Fuktionsdefinition mit “x” als Argument, ohne dem “_”.<br><br>
   Definition
   ```
   f[x_] := x^2
   ```
   Anwendung
   ```
   f[5]
   ```
   Amplitude
   ```
   MaxValue[3*Cos[4*t - \[Pi]/6], t];
   
   FindMaximum[x Cos[x], {x, 2}]
   FindMaximum[{x Cos[x], 1 <= x <= 15}, {x, 7}]
   ```
   Gibt das Maximum der Funktion an. Mit {x, 2} wird die suche bei x=2 gestartet und nimmt das nächste maximum in der Nähe. Die suche kann noch weiter eingegrenzt werden.    
   
   ## 3 Plot ##
   
   ### 2D Plot ###
   
   ```
   Plot[Sin[x], {x, 0, 6 Pi}]
   ```
   ### Plot in loop ###
   ```
   Do[Print[Plot[x^n, {x, -5, 5}]], {n, 1, 10}]
   ```
   Es muss um Plot ein Print stehen!
   
   ### Plot two lists  ###
   Wenn man zwei Listen plotten möchte, dann fügt man mit `Transpose` die beiden Listen zusammen und gibt sie mit `ListPlot`aus. X und y sind in diesem Beispiel Listen.
   ```
   data = Transpose[{x, y}];
   ListPlot[data, PlotTheme -> "Detailed"]
   ```
   
   ### Plot Optionen ###
   
   #### PlotTheme
   ```
   PlotTheme -> "Detailed"
   ```
  
   #### Frame ####
   Umrandet die Grafik
   ```
   Frame -> True
   FrameLabel -> {{"links", None}, {"unten", "oben"}}
   FrameLabel -> {{"links", None}, {"unten", Style["oben", Black, 18]}},
   FrameTicks -> {{Automatic, None}, {Range[0, 20, 5], None}}
   ```
   
   #### PlotRange ####
   Koordinatenbereich der Grafik (y,x)
   ```
   PlotRange -> {{0, 5}, {0, 20}}
   ```

   #### Grid ####
   Linienfarbe
   ```   
   GridLinesStyle -> LightGray
   GridLines -> {Range[0, 5], Range[0, 20,2]}
   GridLines -> {Automatic, Automatic}
   ```
   
   #### AspectRatio ####
   Hier kann das Seitenverhältnis angegeben werden. 
   ``` 
   AspectRatio -> 0.5
   ``` 
   #### PlotStyle ####
   Mit Directive werden mehrere Styles kombiniert.
   ```
   PlotStyle -> Directive[Dashing[{.01, .01}], Red]
   ```
   
   #### SetOptions ####
   ```
   SetOptions[Plot,
     Frame -> True,
     FrameTicks -> {{Automatic, None}, {Automatic, None}},
     GridLinesStyle -> LightGray
    ];
   ```
   
   ## 5 Import ##
   
   ### Microsoft Excel ###
   Importiert die Excel-Datei in Mathematica.

   ```
   Import["/Users/ms/Desktop/test.xlsx"]
   Import["/Users/ms/Desktop/test.xlsx", {"Data", 1, All, 2}]
   Import["/Users/ms/Desktop/test.xlsx", {"Data", 1, {1,3,66}, 2}]
   Import["/Users/ms/Desktop/test.xlsx", {"Data", 1, Range[1,5], 2}]
   ```
   Syntax:
   ```
   {"Data", # of sheet(s), # of row(s), # of column(s)}
   ```
   
   ### Text
   
   Das gleiche für .txt
   ```
   Import["data.txt", "Table"];
   Import["data.txt", {"Data", All, 2}]
   ```
   Das erste importiert die Tabelle mit Arrays und das zweite speichert nur die zweite Spalte in eine Liste. 
   
   ## 5 Fourier ##
   
   ### Fourier-Transformation
   ```
   FourierTransform[Exp[-t^2/2], t, w, FourierParameters -> {1, -1}]
   FourierTransform[HeavisideTheta[t] Exp[-7*t], t, w, FourierParameters -> {1, -1}]
   ```
   `HeavisideTheta[x]` gibt 0 für alle negativen und 1 für alle positiven Zahlen ausser der Zahl 0.
   ### Fourier-Rücktransformation
   ```
   InverseFourierTransform[Sin[w]*Exp[-Abs[w]], w, t, FourierParameters -> {1, -1}]
   ```
 
 ## Systembegriffe ##
Zuerst sollte man am besten jeweils die Funktionen definieren, da man diese anschliessend einfacher aufrufen kann. Die Eckigen Klammern dabei nicht vergessen, vor allem im Bezug auf die Trigonometrischen Befehle werden diese oftmals vergessen.

### Dirac Delta (Impulsfunktion) ###
Der Dirac Delta oder von uns als Impulsfunktion bezeichnet, ist nur an der Stelle `n = 0 --> 1` ansonsten ist dieser 0. Plot funktioniert bei disen Funktionen am besten mit dem `DiscretePlot[expr,{n,nmax}]`

    DiracDelta[1] = 0
    DiracDelta[0] = DiracDelta[0]
    DiscretePlot[DiracDelta[t], {t, -1, 1}]
Da diese Funktion aber bei `DiracDelta[0]` von Mathematica unenvoled bleibt müssen wir für die Darstellung des Dirac Impulses auf eine andere Funktion zugreifen.

    Table[DiscreteDelta[n], {n, -2, 2}] = {0, 0, 1, 0, 0}
    DiscretePlot[DiscreteDelta[n], {n, -1, 1}]
![Discrete Delta](http://rabus.ddns.net/bilder/Markdown/DiscreteDelta.jpg)
### UnitStep (Schrittfunktion) ###
Die Schrittfunktion ist wie die Impulsfunktion ein Spezialfall, diese Funktion verhält sich jedoch so, dass sie bis 0, 0 ist und anschliessend immer 1.

    Plot[UnitStep[x], {x, -3, 3}, PlotStyle -> Thick]
![Unitstep](http://rabus.ddns.net/bilder/Markdown/unitstep.jpg)
### Unit-Box (Rechteck Funktion) ###
Die Rechteck Funktion wird in Mathematica mit der Unit Box Funktion dargestellt. Diese geht von `-0.5` bis `0.5` . Verschiebungen funktionieren wie gewohnt. Negativ nach Rechts und positiv nach links.

    Plot[UnitBox[x], {x, -1, 1}]
![Rechteckfunktion](http://rabus.ddns.net/bilder/Markdown/box.jpg)
### Unit-Triangle (Dreieck Funktion) ###
Die Dreieck Funktion wird ähnlich wie die Rechteck Funktion dargestellt und verhält sich gleich. Verschiebungen funktionieren wie gewohnt. Negativ nach Rechts und positiv nach links.

    Plot[UnitTriangle[x], {x, -2, 2}]

![enter image description here](http://rabus.ddns.net/bilder/Markdown/dreie.jpg)
### Signale darstellen ###
Ein kleines Beispiel wie man nun Signale darstellen kann die z.B aus mehreren Deltas bestehen.

    DiscretePlot[DiscreteDelta[-2 + n] - 2 DiscreteDelta[-1 + n] - DiscreteDelta[n] +DiscreteDelta[1 + n] + UnitStep[n - 1] - UnitStep[1], {n, -5, 5}]
![Discret Signal Example](http://rabus.ddns.net/bilder/Markdown/signaldiscret.jpg)
### Periodizität von Signalen ###
Es gibt einen sehr nützlichen Befehl in Mathematica um die kleinste Periode einer Funktion herauszufinden.

    FunctionPeriod[Sin[x], x] = 2 \[Pi]   
### Faltung von Signalen (Convolve) ###
Die Faltung in Mathematica funktioniert mi dem Englischem Begriff `Convolve`

    Convolve[DiracDelta[x], f[x], x, y] = f[y]
Die Faltung funktioniert Graphisch sowie auch rechnerisch.

    Plot[Convolve[UnitBox[x], UnitTriangle[x], x, t], {t, -2, 2}]
![Faltung Graphisch](http://rabus.ddns.net/bilder/Markdown/faltgr.jpg)
## Komplexe Zahlen ##
Für die Komplexen Zahlen ist Mathematica das NonPlusUltra. Wir werden hier alle nötigen oder möglichen Funktionen Auflisten.

### Argument bzw Winkel ###
Um eine Komplexe Zahl in Polarkoordinaten darzustellen benötigt man den Phasenwinkel .

    Arg[1 + I] = \[Pi]/4
### Real/Imanigär Teil berechnen ###
Den Real/Im Teil kann man mit folgendem Befehl zeigen.

    ReIm[5 + 12 I] = {5, 12}

 ### Betrag einer Zahl ###
 Den Betrag einer Zahl kann mit folgendem Befehl zeigen. Die normale Formel wäre ja:
 |x| = sqrt(x^2 + y^2)

    Abs[5 + 12 I] = 13

 ### Der Komplex Konjugierte Wert ###
 Den Komplex Konjugierten Wert einer Komplexen Zahl erhält man wie folgt.
 

    Conjugate[1 + I] = 1 - I
### Komplex Expand für Komplexe Umwandlung ###
Den folgenden Befehl nutzen wir für die Umwandlung in die Euler Formeln.

    ComplexExpand[Sin[x + I y]] = Cosh[y] Sin[x] + I Cos[x] Sinh[y]

