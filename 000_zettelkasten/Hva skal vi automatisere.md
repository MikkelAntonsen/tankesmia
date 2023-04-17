
###

"Her kan dere komme med innspil!"


Vi vil gi kunder muligheten til å overvåke velferden hos fisken sin in real time.

Er det noen som teller sår bildebasert her? Har du lagt merke til at forskjellige folk teller forskjellig?

## Ide 0: Vi kan ta 100 sekvenser, se hvor mange sår det er og vise resultatet til kunden.

Er dette nyttig for kunden?

## Ide 1: Vi kan ta 100 fisk, se om de har sår eller ikke og vise resultatet til kunden.

#### Hvordan vet vi at en fisk har et sår?

Tidligere detektorer tok alt som sår, også skjelltap. Definer hva et sår faktisk er.

Var dette nyttig for kunden?

## Ide 2: Vi kan ta 100 fisk, score de og vise resultatet til kunden. 

#### Hvordan scorer man en fisk?

Definer en standard som sier nøyaktig hva som teller som et sår. Lag en regel om hvordan scorer hvert sår og bruk sårscoren vetrinærer er vandt med.
Ideelt sett vil alle som følger standaren komme fram til samme resultat.
Det vil være edge-cases hvor forskjellige folk er uenige, det er viktig at alle følger samme standard.
Sår-scoringen har en rekke kriterierer for hva et sår er (må ha en definert sårkant, må se muskel under huden(?)). Dette er grunnen til at sår på hodet/finner ikke blir tatt med, de faller utenfor definisjonen vår [[Spør IH]].
I tillegg må man vite hvor stort såret er. Vi bestemte oss for å sammenligne størrelsen på såret med spordbredden.

