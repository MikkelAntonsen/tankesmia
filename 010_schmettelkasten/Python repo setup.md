
`
Heisann. Det spørs litt hvilke ting du tenker på, men her er ihvertfall et par punkter jeg pleier å forholde meg til:

-   Filstruktur: Prosjektkatalog som inneholder "metafiler" som `README.md` og `pyproject.toml` med venner. All kildekode i en egen katalog, enten `pakkenavn/` eller `src/pakkenavn/`. Fordelen med sistnevnte er hovedsaklig konsistens med `tests/`  og tilsvarende kataloger. Det beskytter også litt mot noen footguns, men jeg har ofte bare brukt den enklere strukturen uten `src/` med hell. Tester i en egen `tests/` katalog rett i prosjektkatalogen - altså utenfor kildekodekatalogen.
-   Lintere, autoformattere, etc: Jeg bruker `black` på all kode uten noen ekstra konfig. Konsistens er fint ![:slightly_smiling_face:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/google-medium/1f642.png) Jeg har også pleid å bruke `flake8` , `isort` og `interrogate` men sikler på å gå over til `ruff` i stedet, så ville nok heller brukt den nå. Om dere bruker type-hints er jo `mypy` kjekt. Evt. noen av de andre type-sjekkerne. Jeg har ikke brukt dem nok til å ha noen mening om forskjeller, fordeler, eller ulemper dem i mellom.
-   Bruk `pyproject.toml` for metadata om prosjektet og installer prosjektet fra begynnelsen av (jeg og kollega Ian har laget en video hvor vi snakker mye om dette: [https://www.youtube.com/watch?v=v6tALyc4C10](https://www.youtube.com/watch?v=v6tALyc4C10)). Jeg pleier å bruke enten `setuptools` eller `flit` som "build-tool", men her tror jeg de fleste funker like bra: `poetry`, `hatch`, `pdm`. Jeg ville valgt det kollegene bruker.
-   Jeg bruker `pip-tools` for å ta vare på dependencies og pinne versjoner. Da vedlikeholder jeg manuelt en `[requirements.in](http://requirements.in/)` fil (og evt `[requirements-dev.in](http://requirements-dev.in/)`  osv) som bare inneholder navnet på mine direkte dependencies og kjører `pip-compile` `[requirements.in](http://requirements.in/)` for å generere en pinned `requirements.txt` fil. Noen verktøy, som `poetry` har egne løsninger som gjør det samme. Jeg liker kontrollen med å gjøre ting selv ![:slightly_smiling_face:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/google-medium/1f642.png)
-   CI: Jeg har brukt GitHub Actions de siste årene og vært fornøyd med det. Ofte har jeg da satt opp `tox` som kjører tester og lintere. Da trenger action'en bare å kalle `tox` så den blir enkel å sette opp.
-   Pre-commit: Jeg liker også `pre-commit` som stopper meg fra å commit'e for mye som blir stoppet i CI likevel. Den har plugins for `black`, `flake8` osv, så jeg setter bare den opp så den ligner det jeg gjør i `tox`.
-   Versjonering: Jeg har brukt `bump2version` lenge. Da kan jeg bare skrive versjonsnummer i kode og dokumentasjon, også vil en kommando a la `bumpversion minor` oppdatere alle versjonsnumre og lage en git tag. Nylig har jeg begynt å bruke [https://github.com/mbarkhau/bumpver](https://github.com/mbarkhau/bumpver) i stedet. Denne fungerer veldig likt men har noen flere muligheter.

Ref: Geir Arne Hjelle



`


