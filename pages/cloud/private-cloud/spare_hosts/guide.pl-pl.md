---
title: 'Hosty zapasowe'
excerpt: 'Zarządzanie hostami zapasowymi w usłudze Dedicated Cloud'
slug: hosty_zapasowe
section: 'Funkcjonalności OVH'
legacy_guide_number: g860
---

## Wprowadzenie

Otrzymałeś e-mail informujący o utworzeniu zgłoszenia awarii związanego z dodaniem hosta zapasowego do usługi Dedicated Cloud.

Host zapasowy jest dostarczany do twojej infrastruktury w przypadku uszkodzenia hosta wchodzącego w skład infrastruktury. Host ten jest darmowy. W zgłoszeniu awarii określone jest IP hosta, którego dotyczy przerwa w usłudze. 
Możesz się zalogować do vSphere Client, aby sprawdzić alert związany z uszkodzonym hostem. 
Jeśli prawidłowo skonfigurowałeś funkcje HA i DRS VMware, wirtualne maszyny automatycznie przeniosą się na host zapasowy. 
Jeśli nie włączyłeś tych funkcji, będziesz musiał ręcznie przenieść swoje wirtualne maszyny.


## 

## Uwaga!!!
OVH dostarcza host zapasowy, aby uniknąć utraty zasobów. Po przywróceniu hosta do prawidłowego działania, OVH odbiera host zapasowy.


## 
Należy oddać host zapasowy. Nie ma możliwości zachowania hosta zapasowego, ani przekształcenia go w host odpłatny. Jeśli chcesz wymienić uszkodzony hosta, zapoznaj się z tym przewodnikiem: url=GUIDE#861]Wymiana uszkodzonego hosta[/url]


## 
Po przywróceniu prawidłowego działania hosta i zniknięciu alertów, możesz zwrócić host zapasowy. Wystarczy postępować zgodnie z procedurą opisaną w sekcji "usuwanie hosta" w przewodniku [Jak dodać hosta?]({legacy}605)

