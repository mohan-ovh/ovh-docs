---
title: 'Konfiguracja konta E-mail Pro w programie Outlook 2016 na systemie Windows'
slug: konfiguracja-outlook-2016
excerpt: 'Dowiedz się, jak skonfigurować konto E-mail Pro w programie Outlook 2016 na urządzeniu z systemem Windows'
section: 'Konfiguracja programu pocztowego'
order: 1
---

**Ostatnia aktualizacja dnia 2018-08-06**

## Wprowadzenie

Konta E-mail Pro mogą być skonfigurowane w jednym z kompatybilnych programów pocztowych. Dzięki temu możesz używać Twojego konta e-mail, korzystając z wybranej przez Ciebie aplikacji.

**Dowiedz się, jak skonfigurować konto E-mail Pro w programie Outlook 2016 na urządzeniu z systemem Windows.**

## Wymagania początkowe

- Wykupienie usługi [E-mail Pro](https://www.ovh.pl/emaile/email-pro/){.external}
- Zainstalowanie programu Microsoft Outlook 2016 na Twoim urządzeniu
- Dane do logowania do konta e-mail, które chcesz skonfigurować

> [!primary]
>
> Używasz programu Outlook 2016 na urządzeniu Mac? Zapoznaj się z naszą dokumentacją: [Konfiguracja konta E-mail Pro w programie Outlook 2016 na urządzeniu Mac](https://docs.ovh.com/pl/emails-pro/konfiguracja-outlook-2016-mac/){.external}.
>

## W praktyce

### Etap 1: dodanie konta

Po uruchomieniu aplikacji Outlook na Twoim urządzeniu możesz dodać konto, korzystając z jednej z dwóch dostępnych metod.

- **Podczas pierwszego uruchomienia aplikacji**: wyświetli się asystent konfiguracji i poprosi o wpisanie adresu e-mail.

- **Jeżeli inne konto zostało wcześniej skonfigurowane**: kliknij `Plik`{.action} na pasku menu na górze Twojego ekranu, a następnie kliknij `Dodaj konto`{.action}.

![emailpro](images/configuration-outlook-2016-windows-step1.png){.thumbnail}

Wpisz hasło dla Twojego konta e-mail, po czym kliknij `Dalej`{.action}. Zaznacz kratkę obok komunikatu `Pozwól mi ręcznie skonfigurować moje konto `{.action}, a następnie kliknij `Połącz`{.action}. Spośród różnych rodzajów kont wybierz **IMAP**.

![emailpro](images/configuration-outlook-2016-windows-step2.png){.thumbnail}

Podaj następnie wymagane informacje.

- **dla poczty przychodzącej:**

|Informacja|Opis |
|---|---|
|Serwer|Wpisz serwer « pro1.mail.ovh.net ».|
|Port|Wskaż port « 993 ».|
|Metoda szyfrowania|Wybierz « SSL/TLS ».|
|Wymaganie uwierzytelnienia|Nie zaznaczaj kratki « Wymagaj logowania przy użyciu bezpiecznego uwierzytelniania hasła » .|

- **dla poczty wychodzącej:**

|Informacja|Opis |
|---|---|
|Serwer|Wpisz serwer « pro1.mail.ovh.net ».|
|Port|Wskaż port « 587 ».|
|Metoda szyfrowania|Wybierz « STARTTLS ».|
|Wymaganie uwierzytelnienia|Nie zaznaczaj kratki « Wymagaj logowania przy użyciu bezpiecznego uwierzytelniania hasła » .|

Po uzupełnieniu informacji kliknij przycisk `Dalej`{.action}, następnie wprowadź **hasło** przypisane do konta e-mail. Jeśli wpisane informacje są poprawne, logowanie zakończy się sukcesem.

Wykonaj test wysyłki e-maili, aby sprawdzić, czy konto zostało poprawnie skonfigurowane.

![emailpro](images/configuration-outlook-2016-windows-step3.png){.thumbnail}

Jeśli wprowadzasz ręcznie dane techniczne w ustawieniach konta, poniżej znajdziesz parametry, których należy użyć w przypadku oferty E-mail Pro:

|Typ serwera|Nazwa serwera|Metoda szyfrowania|Port|
|---|---|---|---|
|Serwer poczty przychodzącej|pro1.mail.ovh.net|SSL/TLS|993|
|Serwer poczty wychodzącej|pro1.mail.ovh.net|STARTTLS|587|

### Etap 2: korzystanie z konta e-mail

Po zakończeniu konfiguracji konto jest gotowe do użytku. Możesz teraz zacząć wysyłać i odbierać wiadomości.

OVH oferuje również aplikację internetową [funkcje do pracy zespołowej](https://www.ovh.pl/emaile/){.external}. Jest ona dostępna pod adresem <https://pro1.mail.ovh.net>. Możesz się do niej zalogować, używając tych samych danych, których używasz do logowania się do konta e-mail.

## Sprawdź również

[Konfiguracja konta e-mail, zawartego w usłudze usłudze MX Plan lub usłudze hostingu, w programie Outlook na urządzeniu z systemem Windows](https://docs.ovh.com/pl/emails/konfiguracja-outlook-2016/){.external}

[Konfiguracja konta Exchange w programie Outlook 2016 na urządzeniu z systemem Windows](https://docs.ovh.com/pl/microsoft-collaborative-solutions/konfiguracja-outlook-2016/){.external}

Przyłącz się do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.