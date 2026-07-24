# LaTeX Cheat Sheet – DHBW CAS Studienarbeit

Eine umfassende Übersicht über alle verfügbaren Befehle, LaTeX-Umgebungen und Code-Blöcke für das Verfassen der Studienarbeit gemäß DHBW CAS Standards.

---

## 1. Gliederung und Struktur

```tex
\section{Hauptkapitel}                  % Erste Ebene (z.B. 1 Einleitung)
\subsection{Unterkapitel}               % Zweite Ebene (z.B. 1.1 Problemstellung)
\subsubsection{Unter-Unterkapitel}     % Dritte Ebene (z.B. 1.1.1 Ausgangslage)

\label{sec:kapitel_key}                 % Textmarke für Verweise setzen
```

> **DHBW CAS Vorgabe:** Max. 4 Gliederungsebenen. Kein abschließender Punkt hinter der Gliederungsnummer (z. B. `2.1`, nicht `2.1.`). Jeder untergliederte Punkt benötigt mindestens zwei Unterpunkte (z. B. auf `3.1` muss `3.2` folgen).

---

## 2. Literaturverweise und Zitate (biblatex / APA 7th)

### Indirekte Zitate (sinngemäß)
```tex
\parencite[S.~12]{Becker2011}               % Output: (Becker, 2011, S. 12)
\parencite[vgl.][S.~15--18]{Warschat2024}  % Output: (vgl. Warschat, 2024, S. 15–18)
\parencite{Becker2011, Kesten2006}         % Mehrere Quellen in einer Klammer
```

### Direkte Zitate (im Fließtext)
```tex
\textcite[S.~81]{Becker2011}               % Output: Becker (2011, S. 81) betont...
\enquote{Wörtlich zitierter Text.} \parencite[S.~42]{Walter2004}
```

### Längere Zitate (Blockzitat ab 3 Zeilen)
```tex
\begin{quote}
  \singlespacing \small
  Dies ist ein längeres wörtliches Zitat, das vom Haupttext eingerückt und einzeilig formatiert wird. \parencite[S.~99]{Klappert2011}
\end{quote}
```

---

## 3. Textformatierung

```tex
\textbf{Fettgedruckter Text}               % Für wichtige Fachbegriffe
\textit{Kursiver Text}                     % Für Fremdwörter oder Auszeichnungen
\underline{Unterstrichener Text}
\texttt{Monospace Code-Text}

\enquote{Deutsche Anführungszeichen}       % Zitate / Anführungszeichen via csquotes
```

---

## 4. Abkürzungen (`nomencl`)

```tex
% Im Fließtext einmalig ausschreiben und Abkürzung im Verzeichnis registrieren:
Commercial Off-The-Shelf (im Folgenden: COTS)\nomenclature{COTS}{Commercial Off-The-Shelf}
```

> **DHBW CAS Vorgabe:** Im Abkürzungsverzeichnis stehen **nur Fachabkürzungen**, die nicht im aktuellen Duden enthalten sind (kein *z. B.*, *u. a.*, *bzw.*, *PC*).

---

## 5. Abbildungen (Grafiken)

```tex
\begin{figure}[htp]
	\centering
	\includegraphics[width=0.85\textwidth]{chapter/images/mein_diagramm.png}
	\caption{Titel und Beschreibung der Abbildung}
	\vspace{2pt}
	{\small \textbf{Quelle:} Eigene Darstellung nach \textcite[S.~45]{Becker2011}}
	\label{fig:mein_diagramm}
\end{figure}
```

### Verweis im Text:
```tex
Wie in Abbildung~\ref{fig:mein_diagramm} auf Seite~\pageref{fig:mein_diagramm} dargestellt...
```

---

## 6. Tabellen (`tabularx` & `booktabs`)

```tex
\begin{table}[htp]
	\centering
	\caption{Vergleich von Methoden zur COTS-Evaluierung}
	\label{tab:cots_evaluierung}
	\begin{tabularx}{\textwidth}{l X X}
		\toprule
		\textbf{Methode} & \textbf{Vorteile} & \textbf{Nachteile} \\
		\midrule
		Nutzwertanalyse (NWA) & Strukturierte Kriterienbewertung & Subjektive Gewichtung \\
		Wirkungskettenanalyse & Erfasst indirekte Effekte & Aufwändige Monetarisierung \\
		\bottomrule
	\end{tabularx}
	\vspace{2pt}
	{\small \textbf{Quelle:} Eigene Darstellung}
\end{table}
```

### Verweis im Text:
```tex
Tabelle~\ref{tab:cots_evaluierung} gibt eine Übersicht der Methoden...
```

---

## 7. Aufzählungen und Listen

### Stichpunkte (Unnummeriert)
```tex
\begin{itemize}
	\item Erster wesentlicher Aspekt
	\item Zweiter wesentlicher Aspekt
\end{itemize}
```

### Nummerierte Aufzählung
```tex
\begin{enumerate}
	\item Erster Prozessschritt
	\item Zweiter Prozessschritt
\end{enumerate}
```

---

## 8. Quellcode-Listings (`listings`)

```tex
\begin{lstlisting}[language=Python, caption={Evaluierungsfunktion}, label={lst:eval_code}]
def evaluate_cots_score(criteria_weights, scores):
    """Berechnet den gewichteten Gesamtwert für COTS-Software."""
    return sum(w * s for w, s in zip(criteria_weights, scores))
\end{lstlisting}
```

---

## 9. Mathematik und Formeln

### Formel im Fließtext
```tex
Die Berechnung der Gesamtnutzwerts erfolgt über $NWA = \sum_{i=1}^{n} g_i \cdot e_i$.
```

### Zentrierte, nummerierte Formel
```tex
\begin{equation}
	NWA = \sum_{i=1}^{n} g_i \cdot e_i
	\label{eq:nwa_formel}
\end{equation}
```

---

## 10. Querverweise und Referenzen

```tex
\ref{label_key}           % Gibt die Nummer (Kapitel/Abb./Tab./Formel) aus
\pageref{label_key}       % Gibt die Seitenzahl aus
\mypageref{label_key}     % Gibt "Nummer Name auf Seite X" aus
```

---

## 11. Anhang-Befehle

```tex
% Definition eines Anhangs-Abschnitts:
\appsection{Methodenvergleichs-Matrix}{app:matrix}

% Referenzierung im Haupttext:
\appref{app:matrix}        % Gibt "Anhang A" als Klick-Link aus
```

---

## 12. Git Befehle (Terminal)

```bash
git status                                  # Status der Änderungen prüfen
git add .                                   # Alle Änderungen stagen
git commit -m "Neues Kapitel hinzugefügt"   # Commit erstellen
git push origin main                        # Zu GitHub pushen
```
