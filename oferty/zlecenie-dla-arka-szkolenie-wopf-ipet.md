# Nowe szkolenie dla przedszkola z podstroną i ofertą do pobrania w PDF

**Zgłosiła:** Ewa · **Data:** 2026-10-28 · **Powstało przy:** jednostronicowej ofercie szkolenia
„Wielospecjalistyczna Ocena Poziomu Funkcjonowania i Konstrukcja Indywidualnego Programu
Edukacyjno-Terapeutycznego w oparciu o wybrane narzędzia obserwacji funkcjonalnej” (PDF A4, gotowy u Ewy).

## Co Ewa chciała

1. Dodać na stronie `eduplaner2026.pl` nowe szkolenie dla przedszkola o tym tytule.
2. Po kliknięciu w kartę szkolenia ma się otwierać jego podstrona — i tak ma być przy każdym szkoleniu.
3. Na podstronie szkolenia ma być możliwość pobrania i wydrukowania oferty w PDF.

## Dlaczego front tego nie załatwia

- Szkolenia są produktami w bazie sklepu i dodaje się je w panelu (Materiały → Szkolenia).
  Panel sam włącza podstronę każdemu materiałowi (`ma_strone` ustawiane na `true` przy zapisie),
  więc punkt 2 jest już spełniony dla każdego dodanego szkolenia. Treść do wklejenia w panel
  Ewa dostała gotową.
- **Szkolenia nie są dziś widoczne publicznie.** `eps_mvp_publiczna_oferta()` w
  `eduplaner-sklep/includes/mvp.php` przepuszcza wyłącznie produkty z grupy „Broszury”,
  a `eps_mvp_blokuj_stary_produkt()` blokuje bezpośredni adres podstrony szkolenia. Nowe szkolenie
  po dodaniu w panelu nie pokaże się więc klientom, dopóki sprzedaż szkoleń nie zostanie włączona.
- **Panel nie ma pola na PDF z ofertą szkolenia.** Pole pliku PDF (`epp_pdf`) jest w
  `eduplaner-panel/includes/materialy.php` tylko dla broszur i służy jako plik dla kupującego,
  chroniony przed publicznym pobieraniem. Szablon `template-parts/strona-produktu.php` nie ma
  przycisku pobrania oferty. To zmiana w kodzie sklepu i wdrożenie paczką różnic — poza zakresem
  pracy z Ewą.

## Co powinno się stać z jej punktu widzenia

- Dodaje szkolenie w panelu, tak jak dziś broszurę, i po kliknięciu „Opublikuj” widzi je na stronie
  z własną podstroną.
- Przy każdym szkoleniu może w panelu wybrać plik PDF z ofertą. Na podstronie szkolenia pojawia się
  wtedy wyraźny przycisk „Pobierz ofertę (PDF)”, a plik jest dostępny publicznie, bez logowania —
  to materiał reklamowy, nie towar.
- Szkolenie bez wgranego PDF wygląda tak jak dziś, bez pustego przycisku.
- Decyzja, kiedy szkolenia stają się widoczne publicznie, należy do Arka i Ewy.
