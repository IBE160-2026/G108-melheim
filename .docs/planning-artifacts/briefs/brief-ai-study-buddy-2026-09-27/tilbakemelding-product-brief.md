# Tilbakemelding på product brief

| | |
|---|---|
| **Gruppe** | G108 – G108-melheim |
| **Product brief** | `.docs/planning-artifacts/briefs/brief-ai-study-buddy-2026-09-27/brief.md` (commit `dde1a1e`) |
| **Tilbakemelding fra** | Faglærer i IBE160 (utarbeidet med KI-støtte) |
| **Dato** | 2026-10-06 |

Vurdert fil: `brief.md` i mappen `brief-ai-study-buddy-2026-09-27`, som er den eneste briefen. Det finnes ennå ikke PRD, arkitektur eller epics.

## Samlet vurdering

- **Bør revideres før dere går videre.** Rett punktene markert «Endre» før dere lager PRD og arkitektur.

**Det som er bra:**

1. Dere har gjort AI Study Buddy-forslaget til deres eget med en tydelig vri: studiene skal konkurrere med mobilen, ikke med andre studieverktøy. Problemet («Studying loses to the phone») er levende beskrevet, og poenget om at selvtesting virker bedre enn å lese notatene på nytt, gir ideen faglig tyngde.
2. Konkurrentanalysen er ærlig og konkret (Quizlet, NotebookLM, Gizmo, Kahoot), og risikodelen peker på de riktige tingene, særlig at feil i KI-genererte spørsmål både er dårlig for læring og gjør konkurransen urettferdig, og at brukeren bør kunne se hvor i notatene svaret kommer fra.

**De viktigste endringene:**

1. Reduser omfanget av v1 kraftig. V1 inneholder brukerkontoer, venner, opplasting av tekst og PDF, KI-generering av sammendrag, flashcards og quiz, øving alene, quizdueller mot venner, poeng, streaks og ledertavler, og responsivt design. Det er minst fire store funksjonsområder, og flere brukere som påvirker hverandre er blant det mest krevende man kan velge. Start med én bruker: opplasting, KI-genererte flashcards og quiz, og øving med poeng og streak. Legg venner og dueller i neste trinn.
2. Erstatt forretningsmålene med funksjonelle suksesskriterier. «1 av 3 spiller mot en venn hver uke», «1 av 4 bruker fortsatt nettsiden etter en måned» og «5 % betaler for Premium» kan ikke måles i løpet av emnet. Legg til kriterier som kan bli tester, for eksempel «en student kan laste opp en PDF og få minst 10 flashcards med henvisning til side i notatene» eller «en quiz gir riktig poengsum og oppdaterer streaken».
3. Ta forretningsmodellen ut av v1. Gratisgrense og Premium til 79 kr i måneden er fint for visjonen, men betaling er utenfor det appen trenger nå. En daglig grense for KI-generering kan likevel være et nyttig tiltak for å holde kostnadene nede.

## Vanskelighetsgrad og gjennomførbarhet

### Vurdert vanskelighetsgrad

- **Vanskelig**

**Sammenlignbart med:** 1) AI Study Buddy (enkel) som kjerne, men med kontoer, venneliste, dueller mellom brukere og ledertavler blir v1 som beskrevet vanskeligere enn 2) AI CV- og søknadsassistent og 7) Kurs-FAQ-chatbot (middels). Flere brukere som påvirker hverandre er et typisk kjennetegn på et vanskelig prosjekt. Uten den sosiale delen er prosjektet enkelt til middels.

**Begrunnelse:**

| Faktor | Nivå (lav / middels / høy) | Kommentar |
|---|---|---|
| Domenelogikk – hvor mange og hvor kompliserte regler og beregninger må stemme? | Middels | Poeng (XP), streaks, ledertavler per fag og regler for dueller. Hver regel er enkel, men de henger sammen. |
| Datamodell – antall entiteter og relasjoner mellom dem | Høy | Bruker, vennskap, fag, dokument, flashcard, quiz, spørsmål, duell, resultat og poeng. Mange relasjoner mellom brukere. |
| Brukere, roller og innlogging | Høy | Kontoer, venneforespørsler og data som deles mellom brukere. |
| KI-funksjonalitet i appen, f.eks. kall til språkmodell, prompts i koden og håndtering av usikre svar | Middels | Tre typer innhold fra opplastede notater, med kildehenvisning og mulighet til å rapportere feil. |
| Integrasjoner og eksterne tjenester, f.eks. API-er, betaling og e-post | Middels | Språkmodell-API. Betaling (Premium) bør holdes utenfor v1. |
| Sanntid, samtidighet eller flere brukere som påvirker hverandre | Høy | Dueller mellom venner og felles ledertavler. Hvis duellene skjer samtidig (live), blir dette svært krevende. |
| Filhåndtering, f.eks. opplasting, PDF-lesing og eksport | Middels | Opplasting og lesing av PDF og tekst, på både norsk og engelsk. |
| Sikkerhet og personvern | Middels | Kontoer, vennelister og opplastet materiale. Dere nevner selv GDPR og opphavsrett. |

**Hva vanskelighetsgraden betyr for dere:**

- _Vanskelig:_ Et vanskelig prosjekt gir større mulighet for toppkarakter, men også større risiko. Definer en minimal versjon som sikkert kan bli ferdig, og legg resten i tydelige trinn etterpå.

### Gjennomførbarhet med BMAD og Claude Code

| Spørsmål | Vurdering (OK / risiko / stor risiko) | Kommentar |
|---|---|---|
| **Tid og omfang** – kan v1 realistisk bli ferdig og stabil i løpet av semesteret, med tid til flere iterasjoner? | Stor risiko | V1 som beskrevet er for stort for én person i ett semester. Med én bruker og spillifisering uten venner er det realistisk. |
| **BMAD-flyten** – er briefen konkret nok til at PRD, arkitektur og stories kan lages uten store hull, og blir det overkommelig mange stories? | Risiko | Flyten i tre steg er tydelig, men duellreglene (samtidig eller på tur, hvem lager quizen, hva gir poeng) mangler. Dagens omfang gir svært mange stories. |
| **Egnet for Claude Code** – bruker løsningen en vanlig, godt dokumentert teknologistakk som Claude Code håndterer godt, eller krever den nisjeteknologi, spesialmaskinvare eller mye manuell konfigurasjon? | Risiko | Webapp, innlogging og API-kall er godt egnet. Sanntidsdueller og tilgangsstyring mellom venner er vesentlig vanskeligere. |
| **Kontroll på KI-ens arbeid** – kan gruppen selv avgjøre om koden gjør det riktige? Krever domenet kunnskap gruppen ikke har, f.eks. avanserte beregninger eller fagregler, så er det vanskelig å kvalitetssikre. | Risiko | Poeng og streaks er lette å kontrollere. Kvaliteten på KI-spørsmålene krever testmateriale dere kjenner godt, og kildehenvisning. |
| **Testbarhet** – finnes det tydelige regler og forventede resultater som tester kan skrives mot? | Stor risiko | Suksesskriteriene er forretningsmål som ikke kan testes. Poeng- og streakregler kan testes når de er skrevet ned. |
| **Kjørbar for sensor** – kan appen kjøres lokalt etter README, uten gruppens nøkler, betalte kontoer eller egen infrastruktur? | Risiko | Krever språkmodell-nøkkel, og sensor må kunne prøve venner og dueller med flere testbrukere. Planlegg testmodus og ferdige testbrukere. |
| **Avhengigheter og kostnader** – krever løsningen betalte API-er, f.eks. språkmodeller, og finnes det en plan for kostnad, testmodus eller mock-data? | Risiko | Dere nevner at KI koster penger og foreslår gratisgrense, men ikke hvordan appen kjøres uten nøkkel. |

**Konklusjon om gjennomførbarhet:**

- **Lite realistisk uten vesentlige endringer.** Se forslagene under.

**Forslag til justering av omfang eller vanskelighetsgrad:**

1. Minimal v1 for én bruker: opplasting av tekst og PDF, KI-genererte flashcards og quiz med henvisning til notatene, øving alene med XP og daglig streak. Dette er et solid, middels prosjekt som kan bli ferdig og godt testet.
2. Neste trinn, hvis tiden tillater: enkle dueller som ikke skjer samtidig, der to venner tar samme quiz hver for seg og resultatene sammenlignes, og en ledertavle blant venner. Unngå sanntidsdueller, Premium og betaling i dette emnet.

## Hvorfor product brief er viktig for mappen

Product brief er utgangspunktet for PRD, arkitektur, stories og til slutt koden. Del 1 av mappen vurderes blant annet på om sensor kan følge en sporbar vei fra plan til ferdig app. Den vurderes også på om appen gjør det dere har beskrevet, om den er testet, om den er godt designet, og om den kan kjøres etter README. Et uklart, for stort eller for lite brief gjør alt dette vanskeligere senere. Det er mye enklere å rette nå enn sent i semesteret.

## 1. Gjennomgang av briefens deler

| Del av brief | Status | Kommentar |
|---|---|---|
| Executive Summary – er det klart hva appen er, og hvilket problem den løser? | OK | Svært tydelig: studier som føles som et spill, basert på egne notater. |
| The Problem – er problemet konkret, med reelle situasjoner og brukere? | OK | Konkret og godt begrunnet, med tre tydelige delproblemer. |
| The Solution – beskriver løsningen brukeropplevelsen, ikke bare teknologi? | OK | Tre enkle steg (Upload, Practise, Compete) beskriver opplevelsen godt. |
| What Makes This Different – er vurderingen ærlig og realistisk? | OK | Ærlig om sterke konkurrenter, med en tydelig vinkel. |
| Who This Serves – er primærbrukerne tydelige, og vet vi hva de trenger? | Juster | Studenter i Norge er tydelig, men bredt. Beskriv gjerne én konkret student og situasjon, for eksempel ti ledige minutter på bussen før en forelesning. |
| Success Criteria – kan kriteriene faktisk sjekkes eller testes? | Endre | Alle kriteriene er forretnings- eller bruksmål som ikke kan måles i emnet. Legg til funksjonelle kriterier. |
| Scope – er det klart hva som er med i første versjon, og hva som ikke er det? | Endre | Tydelig liste, men for stor. Flytt venner, dueller og ledertavler til neste trinn. |
| Vision – henger visjonen sammen med resten uten å blåse opp omfanget? | Juster | Visjonen er fin, men forretningsmodellen bør flyttes hit, slik at den ikke påvirker v1. |

## 2. Utgangspunkt for del 1 av mappen

Punktene følger kriteriene i sensorveiledningen for del 1. Vektene i parentes viser hvor mye hvert kriterium teller i del 1.

| Kriterium i del 1 | Hva briefen bør legge til rette for | Status | Kommentar |
|---|---|---|---|
| **1. Prosess og KI-styring** (30 %) | Brief som er presis nok til at PRD og stories kan bygges direkte på den, slik at krav kan spores fra brief til kode. | Juster | Godt skrevet, men repoet har bare én commit med innhold. Bruk BMAD videre, commit jevnlig og lagre promptene. Dokumenter beslutningen om å redusere omfanget. |
| **2. Funksjonalitet og omfang** (20 %) | Realistisk omfang for gruppen og semesteret: en tydelig kjerneflyt som kan bli ferdig og stabil, og nok innhold til å vise reell funksjonalitet. | Endre | For stort for én person. En redusert v1 med spillifisering for én bruker gir fortsatt mye funksjonalitet. |
| **3. Kvalitetssikring og testing** (15 %) | Suksesskriterier og funksjoner som er konkrete nok til å bli testtilfeller. | Endre | Forretningsmål gir ikke testtilfeller. Skriv regler for poeng og streak, og lag testnotater med forventede spørsmål. |
| **4. Design og brukeropplevelse** (10 %) | Tydelige brukere og brukssituasjoner som designet kan bygges rundt, gjerne med de viktigste skjermbildene eller flytene skissert. | OK | Mobilbruk og spillfølelse gir et tydelig designgrunnlag. Skisser øving med flashcards og quiz på mobil. |
| **5. Kodekvalitet og arkitektur** (10 %) | Teknologivalg som er begrunnet og ikke mer komplekse enn appen trenger. | Juster | Teknologi er ikke valgt. Unngå sanntidsteknologi og betalingsløsning i v1, og velg én enkel webstakk. |
| **6. README og kjørbarhet** (10 %) | Løsning som andre kan kjøre lokalt uten betalte kontoer, og uten tilgang til gruppens egne tjenester og nøkler. | Juster | Planlegg testmodus for KI og ferdige testbrukere, slik at sensor kan prøve appen. |
| **7. Ryddighet i repoet** (5 %) | En plan for hvor hemmeligheter, testdata og dokumentasjon skal ligge. | Juster | `.docs/planning-artifacts` er en god struktur. Legg testnotater i en egen mappe, og hold API-nøkler i `.env` utenfor Git. |

## 3. Neste steg for gruppen

1. Del Scope i v1 (én bruker, opplasting, flashcards, quiz, XP og streak) og senere trinn (venner, dueller, ledertavler, Premium).
2. Skriv om suksesskriteriene til funksjonelle, testbare kriterier, og skriv ned reglene for poeng og streak.
3. Velg KI-tjeneste med plan for testmodus, og lag deretter PRD med BMAD.

Oppdater product brief i repoet når dere har gjort endringene, slik at historikken viser hvordan planen utviklet seg. Det er en del av prosessen sensor ser etter.
