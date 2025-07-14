

# PrawoAsystent AI

 <!-- Przykładowy obrazek - zalecam podmianę na logo projektu -->

Projekt rozwijany przez grupę **AIprawnikPL**.

**PrawoAsystent AI** to zaawansowana platforma SaaS (Software as a Service) dla branży prawniczej, zaprojektowana w celu radykalnego zwiększenia efektywności i jakości pracy z dokumentami. Naszym celem jest stworzenie centralnego systemu nerwowego dla kancelarii, który automatyzuje powtarzalne zadania i pozwala prawnikom skupić się na pracy strategicznej.

---

## (Kluczowe Funkcjonalności)

*   **Analiza Dokumentów z AI**: Wykorzystanie modeli Google Gemini 1.5 Pro do inteligentnej analizy, redlinowania i streszczania dokumentów prawnych.
*   **Transkrypcja i Analiza Audio**: Automatyczna transkrypcja nagrań audio/wideo z identyfikacją mówców (diarization).
*   **Inteligentna Baza Wiedzy (RAG)**: Błyskawiczne, semantyczne przeszukiwanie wewnętrznej bazy wiedzy kancelarii (dokumentów, snippetów) dzięki integracji z wektorową bazą Pinecone.
*   **Asystent w Edytorze Tekstu**: Integracja z MS Word i Google Docs w celu podpowiadania gotowych klauzul i snippetów w czasie rzeczywistym.
*   **Bezpieczeństwo i Izolacja Danych**: Architektura multi-tenant z rygorystyczną izolacją danych każdej kancelarii na poziomie bazy danych (PostgreSQL RLS).
*   **Zarządzanie Subskrypcjami**: Pełna obsługa płatności i subskrypcji dzięki integracji ze Stripe.

## 🏛️ Architektura Systemu

System jest zbudowany w nowoczesnej, hybrydowej architekturze łączącej **Backend-as-a-Service (BaaS)** z dedykowanymi **mikroserwisami**.

*   **Platforma BaaS (Supabase)**: Służy jako rdzeń systemu, zarządzając bazą danych PostgreSQL, uwierzytelnianiem (Auth), przechowywaniem plików (Storage) oraz funkcjami serverless (Edge Functions).
*   **Mikroserwisy (Python/Flask)**: Dedykowane, skalowalne serwisy w kontenerach Docker do obsługi zadań specjalistycznych:
    *   **Serwis AI**: Odpowiedzialny za komunikację z modelami AI (Gemini), zarządzanie promptami i logikę RAG.
    *   **Serwis Audio**: Asynchroniczne przetwarzanie długotrwałych zadań transkrypcji z użyciem kolejki zadań.

## 🛠️ Stack Technologiczny

### Frontend
*   **Framework**: React 18 + TypeScript
*   **Bundler**: Vite
*   **Styling**: Tailwind CSS + shadcn/ui
*   **Zarządzanie Stanem Serwera**: TanStack Query (React Query)
*   **Integracje z Edytorami**: Office.js (MS Word), Google Apps Script (Google Docs)

### Backend
*   **Platforma BaaS**: Supabase
*   **Baza Danych**: PostgreSQL (z Row Level Security)
*   **Funkcje Serverless**: Deno/TypeScript (Supabase Edge Functions)
*   **Mikroserwisy**: Python 3.11+ / Flask
*   **Kolejka Zadań**: Celery / Redis

### Usługi Zewnętrzne i AI
*   **Modele Językowe**: Google Gemini 1.5 Pro & Flash
*   **Wektorowa Baza Danych**: Pinecone
*   **Płatności**: Stripe & Stripe Connect

## 🚀 Uruchomienie Projektu (Development)

Instrukcje dotyczące lokalnego uruchomienia środowiska deweloperskiego.

### Wymagania Wstępne
*   Node.js (wersja 20.x lub wyższa)
*   Python (wersja 3.11 lub wyższa)
*   Docker i Docker Compose
*   Konto Supabase
*   Klucze API do usług zewnętrznych (Google AI, Pinecone, Stripe)

### 1. Klonowanie Repozytorium
```bash
git clone https://github.com/aiprawnikpl/prawoasystent-ai.git
cd prawoasystent-ai
```

### 2. Konfiguracja Frontend
```bash
cd frontend
npm install
cp .env.example .env.local
```
Uzupełnij plik `.env.local` o klucze publiczne Supabase.

### 3. Konfiguracja Backend (Mikroserwisy)
```bash
cd backend
# Utwórz i aktywuj środowisko wirtualne
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
```Uzupełnij plik `.env` o niezbędne klucze API i dane konfiguracyjne.

### 4. Uruchomienie
```bash
# W osobnym terminalu (w folderze frontend)
npm run dev

# W osobnym terminalu (w folderze backend)
# Uruchomienie serwisu AI
python -m src.services.ai.app

# Uruchomienie serwisu Audio
python -m src.services.audio.app
```

## 🔐 Bezpieczeństwo

Bezpieczeństwo danych jest naszym najwyższym priorytetem. Główne mechanizmy zabezpieczające:

*   **Izolacja Danych**: `Row Level Security` w PostgreSQL zapewnia, że użytkownicy mają dostęp wyłącznie do danych swojej organizacji.
*   **Uwierzytelnianie**: Bezpieczne logowanie oparte o JWT z krótkim czasem życia i mechanizmem odświeżania tokenu. Dostępne 2FA.
*   **Bezpieczeństwo API**: Ograniczanie dostępu (Rate Limiting) i walidacja wszystkich danych wejściowych (Zod).
*   **Ślad Audytowy**: Rejestrowanie kluczowych operacji w systemie w celu zapewnienia zgodności i możliwości audytu.

## 🤝 Kontrybucje

Jesteśmy otwarci na kontrybucje! Jeśli chcesz pomóc w rozwoju projektu, prosimy o przestrzeganie następujących kroków:
1.  Zrób `fork` repozytorium.
2.  Stwórz nowy `branch` dla swojej funkcjonalności (`git checkout -b feature/nazwa-twojej-funkcjonalnosci`).
3.  Zaimplementuj zmiany i stwórz `commit`.
4.  Wypchnij zmiany do swojego forka (`git push origin feature/nazwa-twojej-funkcjonalnosci`).
5.  Stwórz `Pull Request` do głównego repozytorium.

## 📄 Licencja

Ten projekt jest udostępniany na licencji [MIT](LICENSE.md).
-->
