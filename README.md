# team.dysza.app — Zespół

Moduł Dysza.App dla Pracowni Sushi: grafik, zgłoszenia do HR, obecności i wypłaty.

Strona nie zawiera żadnych danych. Po zalogowaniu (login z karty i PIN z manager.dysza.app)
dane przychodzą z funkcji bazy `team_*`, które same pilnują ról: HR Manager i Architekt widzą całość,
Zarząd — podgląd bez zapisu, pracownik — wyłącznie swoje zarobki, grafik i zgłoszenia.

Wersja 1.0 · 8.11.2026

## 1.4.4 · 12.11.2026 — koszt załogi dla w.dysza.app (Wynik)

Po każdym wczytaniu danych (wejście, odświeżenie) przez HR Managera, Zarząd albo Architekta strona zapisuje w bazie
koszt załogi miesięcy z `MIESIACE` — funkcja `team_koszt_zapisz` (tabela `team_koszty`, migracja `wynik_001_podstawy`
w ZDZISŁAWIE). Liczby jak w Koszty (`kosztMies`), ale wszystkie dni miesiąca: `{ dn, F, R, U, dod, bon, osd, do_dnia }`
w złotych — same sumy, bez osób. Zapis tylko po zmianie; błąd (np. brak funkcji w bazie) nie przeszkadza w pracy.
w.dysza.app liczy z tego linię „Załoga” (dniówki + dodatki + bonusy, jak „Zarobione”). Kod: `kosztMiesWynik`,
`publikujKosztyZalogi`, wywołanie w `zaladuj` po `przeliczListopad`.
