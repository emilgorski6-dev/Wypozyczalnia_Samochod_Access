# Wypozyczalnia_Samochodow_Access
🚗 System Zarządzania Wypożyczalnią Samochodów

Projekt bazodanowy realizowany w ramach kierunku Informatyka Ekonomiczna (I stopień, 1 rok)
Wydział Ekonomiczno-Socjologiczny UŁ
Autorzy: Emil Górski, Kacper Bednarek
Data: 23.06.2025


📌 Opis projektu

System zarządzania wypożyczalnią samochodów to relacyjna baza danych zaprojektowana w środowisku Microsoft Access, której celem jest kompleksowa obsługa procesów biznesowych związanych z wynajmem pojazdów.

Projekt obejmuje:

model konceptualny,

model logiczny,

model fizyczny,

implementację integralności danych,

reguły biznesowe,

kwerendy SQL,

formularze i raporty użytkowe.

System umożliwia zarządzanie samochodami, klientami, pracownikami, rezerwacjami oraz transakcjami finansowymi (przelewami), przy zachowaniu pełnej spójności danych.

🎯 Główne cele systemu

Zarządzanie flotą pojazdów

Obsługa procesu rezerwacji

Ewidencjonowanie klientów i pracowników

Rejestracja płatności

Zarządzanie oddziałami i garażami

Analiza danych (raporty i zestawienia finansowe)

Zapewnienie integralności i normalizacji danych

🧱 Struktura bazy danych

System oparty jest na relacyjnej bazie danych składającej się z następujących encji:

Auto

Rezerwacja

Przelew

Klient

Pracownik

Oddział

Garaż

Adres

Relacje między tabelami realizowane są za pomocą kluczy głównych (PRIMARY KEY) oraz kluczy obcych (FOREIGN KEY), z zastosowaniem mechanizmów:

ON DELETE RESTRICT

ON UPDATE CASCADE

🔑 Kluczowe funkcjonalności
🚘 Zarządzanie samochodami

Dodawanie, edycja i usuwanie aut

Zmiana statusu (dostępny, w naprawie, niedostępny)

Przypisanie auta do garażu

Określanie ceny za dzień wynajmu

📅 Zarządzanie rezerwacjami

Tworzenie nowych rezerwacji

Określanie dat wynajmu

Zmiana statusu rezerwacji

Przegląd i filtrowanie rezerwacji

👤 Zarządzanie klientami

Rejestracja danych osobowych

Walidacja wieku (minimum 18 lat)

Weryfikacja posiadania prawa jazdy

👨‍💼 Zarządzanie pracownikami

Rejestracja danych pracowniczych

Przypisanie do oddziału

Kontrola zatrudnienia

💳 Zarządzanie płatnościami

Rejestracja przelewów

Kontrola zgodności płatności z kosztem wynajmu

Filtrowanie przelewów

🏢 Zarządzanie oddziałami i garażami

Przypisanie adresów

Kontrola lokalizacji (wyłącznie Polska)

Zarządzanie pojemnością garaży

📊 Przykładowe kwerendy SQL

Projekt zawiera rozbudowany zestaw kwerend, m.in.:

Dochód miesięczny (sumowanie przelewów według miesiąca)

Liczba rezerwacji klientów

Lista garaży i oddziałów

Sprawdzanie dostępności aut

Filtrowanie przelewów i rezerwacji

Przykład:

SELECT Year(Przelew.Data_przelewu) AS Rok,
       MonthName(Month(Przelew.Data_przelewu)) AS Miesiac,
       Sum(Przelew.Kwota) AS Dochod
FROM Przelew
WHERE Przelew.Status_przelewu = 'Wykonany'
GROUP BY Year(Przelew.Data_przelewu),
         Month(Przelew.Data_przelewu)
ORDER BY Year(Przelew.Data_przelewu),
         Month(Przelew.Data_przelewu);

🛡 Integralność danych

System implementuje cztery poziomy integralności:

✔ Integralność encji

PRIMARY KEY w każdej tabeli

Brak wartości NULL w kluczach głównych

✔ Integralność referencyjna

FOREIGN KEY

ON DELETE RESTRICT

ON UPDATE CASCADE

✔ Integralność domeny

CHECK constraints (np. kraj = "Polska")

Walidacja wieku klienta (18+)

Kontrola dat rezerwacji

Wartości domyślne (np. status auta = "Dostępny")

✔ Integralność zdefiniowana przez użytkownika

Triggery (np. kontrola dostępności auta)

Procedury składowane (proces rezerwacji i kalkulacji kosztów)

📈 Normalizacja

Projekt spełnia założenia:

1NF – dane atomowe, brak powtarzających się grup

2NF – pełna zależność od klucza głównego

3NF – brak zależności przechodnich

Adres został wydzielony jako osobna tabela w celu eliminacji redundancji.

👥 Role użytkowników
🧾 Pracownik obsługi

Tworzenie rezerwacji

Obsługa klientów i przelewów

📊 Menedżer oddziału

Nadzór nad oddziałem

Raportowanie

Zarządzanie garażami

⚙ Administrator

Pełny dostęp do systemu

Zarządzanie wszystkimi encjami

Nadawanie uprawnień

🌐 Możliwości rozbudowy

Integracja z systemami płatności online

Powiadomienia SMS / e-mail

System ról i autoryzacji

Wersja webowa aplikacji

API do integracji z aplikacją mobilną

🧠 Technologie

Microsoft Access

SQL

Relacyjny model danych

Projektowanie baz danych (model konceptualny → logiczny → fizyczny)
