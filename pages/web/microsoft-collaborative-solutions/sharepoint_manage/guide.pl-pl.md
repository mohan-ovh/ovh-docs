---
title: Aktywacja i zarządzanie usługą SharePoint OVHcloud
slug: aktywacja-kont-email-zawartych-w-hostingu
excerpt: Dowiedz się, jak zamówić i skonfigurować usługę SharePoint
section: SharePoint
order: 01
updated: 2020-08-11
---

**Ostatnia aktualizacja z dnia 11-08-2020**

## Wprowadzenie

Oferty SharePoint pozwalają wykorzystać współdzieloną przestrzeń dyskową do wspólnej pracy.

**Dowiedz się, jak zamówić i skonfigurować usługę SharePoint.**

## Wymagania początkowe

- Dostęp do [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl).
- Wykupienie usługi [Hosted Exchange](https://www.ovhcloud.com/pl/emails/hosted-exchange/){.external} w celu zamówienia przypisanej usługi SharePoint.

## W praktyce

### Etap 1: zamówienie usługi SharePoint

Zaloguj się do swojego [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl) i przejdź do sekcji `Webcloud`{.action}, aby rozpocząć zamawianie usługi SharePoint.

Istnieją dwa rodzaje usług do wyboru:

| Przypisana usługa SharePoint                                                                                                                      	| Samodzielna usługa SharePoint                                                                                                                                                                       	|
|-----------------------------------------------------------------------------------------------------------------------------------------	|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| ![sharepoint](images/order-manage-sharepoint-02.png){.thumbnail}                                                                        	| ![sharepoint](images/order-manage-sharepoint-03.png){.thumbnail}                                                                                                                            	|
| Jeśli dysponujesz usługą Hosted Exchange w Panelu klienta, możesz powiązać konta użytkowników z platformą SharePoint. Zaznacz konto lub konta, które chcesz powiązać z licencją SharePoint. 	| Jeśli nie masz usługi Hosted Exchange OVHcloud lub też potrzebujesz niezależnej usługi SharePoint, zamów usługę SharePoint Standalone. <br>Określ liczbę licencji, których potrzebujesz, w zależności od liczby użytkowników.	|

Po dokonaniu wyboru kliknij `Zamów usługę`{.action}, aby sfinalizować zamówienie.

### Etap 2: aktywacja usługi SharePoint

Po zatwierdzeniu i opłaceniu zamówienia otrzymasz na adres e-mail podany w Twoim Panelu klienta wiadomość z informacją, że usługa jest gotowa do konfiguracji.

Aby przeczytać ten e-mail, zaloguj się do Twojego [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl), kliknij Twój profil w prawym górnym rogu, a następnie wybierz Twoje inicjały. Przejdź do karty `Wiadomości odebrane`{.action} i wyszukaj e-mail z następującym tematem:

> **\[xx-11111-ovh] Skonfiguruj usługę Microsoft SharePoint!**

Aby rozpocząć tę konfigurację, przejdź do sekcji `Web` w Twoim Panelu klienta. Kliknij `Microsoft`{.action}, następnie `Sharepoint`{.action}, po czym wybierz odpowiednią usługę SharePoint.

Nazwij usługę w polu „Adres URL SharePoint” i kliknij przycisk `Zatwierdź URL`{.action}

![sharepoint](images/order-manage-sharepoint-04.png){.thumbnail}  

> [!warning]
>
> Po zatwierdzeniu nie można będzie już zmienić nazwy usługi.

### Etap 3: konfiguracja usługi SharePoint

Zaloguj się do Twojego [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl) i przejdź do sekcji `Web`. Kliknij `Microsoft`{.action}, następnie `Sharepoint`{.action}, po czym wybierz odpowiednią usługę SharePoint.

#### **Samodzielna usługa SharePoint**

Ta usługa jest niezależna, więc należy najpierw przypisać do niej domenę, aby móc skonfigurować użytkowników.

##### ***Dodanie domeny***

Przejdź do karty `Domeny` i kliknij `Dodaj domenę`{.action}. Wybierz domenę posiadaną w Panelu klienta lub podaj nazwę domeny zewnętrznej, którą zarządzasz. 

- Jeśli wybierzesz domenę znajdującą się w Twoim Panelu klienta, zostanie ona automatycznie zatwierdzona. Można więc przejść od razu do konfiguracji użytkowników.
 
- Jeśli wybierzesz domenę zewnętrzną, konieczne będzie dodanie rekordu CNAME do strefy DNS domeny, aby zatwierdzić ją w usłudze SharePoint. Jeśli chcesz sprawdzić rekord CNAME, który należy tu podać, kliknij ikonę informacji obok frazy „Weryfikacja domeny w toku”, jak pokazano poniżej.


![sharepoint](images/order-manage-sharepoint-05.png){.thumbnail}

##### ***Konfiguracja użytkownika***

Przejdź do karty `Użytkownik`, kliknij `...`{.action} po prawej stronie konta, a następnie wybierz `Edycja konta`{.action}

![sharepoint](images/order-manage-sharepoint-06.png){.thumbnail} 

Wprowadź dane użytkownika w oknie, które się pojawi, a następnie kliknij `Zatwierdź`{.action}

Aby uzyskać uprawnienia administratora w platformie SharePoint, kliknij ponownie`...`{.action} z prawej strony konta, a następnie `Aktywuj uprawnienia administratora`{.action}

#### **Przypisana usługa SharePoint**

Jaka sama nazwa wskazuje, usługa ta jest przypisana do usługi Exchange wybranej przez Ciebie podczas składania zamówienia. Nie ma więc potrzeby przypisywania domeny.

##### ***Konfiguracja użytkownika***

Przejdź do karty `Użytkownicy` w Twojej usłudze, aby wyświetlić wszystkie konta Exchange, które mogą korzystać z licencji SharePoint.

![sharepoint](images/order-manage-sharepoint-07.png){.thumbnail} 

Kolumna `Konto aktywne` wskazuje, czy konto w usłudze Exchange korzysta z licencji SharePoint. 

> [!primary]
>
> Jeśli chcesz aktywować licencję dla konta, które nie ma do niej dostępu, kliknij `...`{.action} z prawej strony konta, a następnie `Aktywuj SharePoint`{.action}.

Domyślnie konto korzystające z licencji nie ma uprawnień administratora. Aby je przyznać, kliknij `...`{.action} z prawej strony konta, a następnie `Aktywuj uprawnienia administratora`{.action}.

![sharepoint](images/order-manage-sharepoint-08.png){.thumbnail} 

#### **Przywrócenie uprawnień administratora**

W obu rodzajach usługi SharePoint dostępny jest przycisk `Przywróć uprawnienia administratora`{.action} w karcie `Użytkownik`. Umożliwia on przywrócenie uprawnień administratora usługi w razie błędnej operacji w interfejsie SharePoint.

![sharepoint](images/order-manage-sharepoint-09.png){.thumbnail}

#### **Edycja plików Office 365 online**

Pliki Office 365, takie jak plik *.docx* lub *.xls* można edytować bezpośrednio online.

Potrzebna jest do tego ważna licencja Office 365 i potwierdzenie tego faktu w Panelu klienta OVHcloud.

Przejdź do zakładki `Użytkownicy` na Twojej platformie i kliknij `...`{.action} po prawej stronie konta, a następnie kliknij `Dodaj licencję Office`{.action}.

![sharepoint](images/order-manage-sharepoint-10.png){.thumbnail}

Po potwierdzeniu, że posiadasz licencję Office 365, kliknij przycisk `validate`{.action}.

![sharepoint](images/order-manage-sharepoint-11.png){.thumbnail}

Teraz możesz już edytować pliki Office 365 bezpośrednio w interfejsie WWW Twojego sharepointa.

## Sprawdź również

Dołącz do społeczności naszych użytkowników na stronie<https://community.ovh.com/en/>.

