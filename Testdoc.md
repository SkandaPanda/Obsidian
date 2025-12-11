\begin{tikzpicture}
\begin{axis}[
    title={Översikt över blodtrycket i systemkretsloppet},
    xlabel={Kärlsegment},
    ylabel={Blodtryck (mm Hg)},
    width=12cm, height=8cm,
    ymin=0, ymax=140,
    xmin=0, xmax=7,
    xtick={0.5, 1.5, 2.5, 3.5, 4.5, 5.5, 6.5},
    xticklabels={Vä. Kam., Artärer, Arterioler, Kapillärer, Venoler, Vener, Hö. För.},
    x tick label style={rotate=45, anchor=east},
    grid=major,
    legend pos=north east
]

% Systoliskt tryck (Övre kurva)
\addplot[color=red, smooth, thick] coordinates {
    (0.1, 120) (0.9, 120)  % Vänster kammare (Systole)
    (1.1, 120) (1.9, 110)  % Artärer
    (2.1, 100) (2.9, 40)   % Arterioler (Stort tryckfall)
    (3.1, 35)  (3.9, 15)   % Kapillärer
    (4.1, 15)  (4.9, 10)   % Venoler
    (5.1, 10)  (5.9, 5)    % Vener
    (6.1, 5)   (6.9, 2)    % Höger förmak
};
\addlegendentry{Systoliskt tryck}

% Diastoliskt tryck (Nedre kurva)
\addplot[color=blue, smooth, thick] coordinates {
    (0.1, 5)   (0.9, 5)    % Vänster kammare (Diastole, nära 0)
    (1.1, 80)  (1.9, 75)   % Artärer (Hoppar upp till ~80)
    (2.1, 70)  (2.9, 40)   % Arterioler
    (3.1, 35)  (3.9, 15)   % Kapillärer (Pulsen försvinner, samma som sys)
    (4.1, 15)  (4.9, 10)   % Venoler
    (5.1, 10)  (5.9, 5)    % Vener
    (6.1, 5)   (6.9, 2)    % Höger förmak
};
\addlegendentry{Diastoliskt tryck}

% Fyllnad mellan kurvorna (Pulstryck)
\addplot[name path=A, draw=none] coordinates {
    (1.1, 120) (1.9, 110) (2.1, 100) (2.9, 40)
};
\addplot[name path=B, draw=none] coordinates {
    (1.1, 80) (1.9, 75) (2.1, 70) (2.9, 40)
};
\addplot[red!10] fill between[of=A and B];

\end{axis}
\end{tikzpicture}