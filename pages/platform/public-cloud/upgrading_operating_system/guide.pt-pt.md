---
title: "Atualizar o sistema operativo"
slug: upgrade-os
excerpt: "Saiba como atualizar um sistema operativo em fim de vida"
section: 'Tutoriais'
order: 14
---

> [!primary]
> Esta tradução foi automaticamente gerada pelo nosso parceiro SYSTRAN. Em certos casos, poderão ocorrer formulações imprecisas, como por exemplo nomes de botões ou detalhes técnicos. Recomendamos que consulte a versão inglesa ou francesa do manual, caso tenha alguma dúvida. Se nos quiser ajudar a melhorar esta tradução, clique em "Contribuir" nesta página.
>

**Última atualização: 09/07/2021**

## Objetivo

Este tutorial descreve os passos a seguir para atualizar um sistema operativo em fim de vida para uma nova versão.

> [!alert]
> Aviso: tal como para qualquer atualização importante de um sistema operativo, existe um risco de falha, de perda de dados ou de falha da configuração de software.
> Assim, antes de seguir este tutorial, a OVHcloud recomenda-lhe vivamente que [guarde a sua instância](../efetuar_backup_de_uma_instancia/) e que efetue testes aprofundados das suas aplicações, de forma a garantir que estas funcionem na nova versão do sistema operativo.
>

> [!primary]
> Para evitar os problemas acima mencionados, recomendamos a instalação de uma nova instância com o novo sistema operativo para o qual efetua a atualização e a subsequente migração dos dados.
> Poderá ainda ser necessário um exame das diferenças na sua aplicação, mas o sistema operativo será provavelmente mais estável.
>

## Requisitos

- Dispor de um [acesso root ao servidor](../tornar-se_root_e_definir_uma_palavra-passe/)
- Ter efetuado [um backup da sua instância](../efetuar_backup_de_uma_instancia/)

## Instruções

### Ubuntu

Antes de atualizar a versão principal do seu SO, certifique-se de que atualiza as versões mais recentes de todos os pacotes instalados na sua versão atual:

```sh
$ sudo apt-get update
```

De seguida, atualize os seus pacotes instalados para as suas últimas versões:

```sh
$ sudo apt-get upgrade -y
```

Terminada esta operação, efetue um *dist-upgrade* que lançará outras atualizações que possam ser necessárias:

```sh
$ sudo apt-get dist-upgrade -y
```

A atualização da versão maior pode então ser efetuada. Ubuntu fornece agora uma ferramenta chamada *do-release-upgrade* que torna a atualização mais segura e mais fácil. Comece a atualização através deste comando:

```sh
$ sudo do-release-upgrade
```

Siga as instruções apresentadas. Estas consistem principalmente em confirmar que deseja continuar a atualização.

Observações:

- A ferramenta pode pedir-lhe que reinicie o seu servidor antes de efetuar a atualização. Para isso, basta que introduza "reboot" (reinicie) e prima a Entrada.
- Atenção: não é recomendado efetuar esta operação através de uma ligação SSH. Como não existe acesso físico ao servidor, a ligação em SSH é a principal forma de aceder ao seu servidor.
O Ubuntu irá iniciar um novo serviço SSH noutra porta para que possa conservar outro acesso em caso de defeito. Além disso, poderá sempre aceder ao servidor através da consola se já não tiver acesso ao servidor através de SSH.
- Durante a atualização, poderá ser-lhe pedido que confirme a eliminação dos pacotes que já não são geridos. Verifique que isto não tem qualquer impacto nas suas aplicações antes de continuar.

Depois de finalizar a atualização, o servidor reiniciará e perderá a ligação até que esta seja reiniciada.
Alguns minutos mais tarde, deverá ser capaz de se ligar e ver uma mensagem semelhante a esta (a versão será a próxima disponível em relação à sua versão anterior):

```sh
$ Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 4.15.0-147-generic x86_64)
```

> [!primary]
> Quando atualiza o sistema operativo em vez de o reinstalar, a nova versão do seu SO não está indicada na Área de Cliente, na API OVHcloud, nem na API Horizon / OpenStack.
>

Verifique que as suas aplicações funcionam como previsto. Em caso de problema, recomendamos que [restaure o backup](../criar_restaurar_um_servidor_virtual_a_partir_de_um_backup/) efetuado antes da atualização.

### Fedora

Antes de começar a atualização da versão principal do SO, certifique-se de que atualiza as versões mais recentes de todos os pacotes instalados na sua versão atual. Introduza esta encomenda:

```sh
$ sudo dnf upgrade —refresh
```

A seguir, reinicie o servidor:

```sh
$ reboot
```

Depois de reiniciar o servidor, instale o pacote de atualização:

```sh
$ sudo dnf install dnf-plugin-system-upgrade
```

Agora que dispõe do pacote necessário, pode efetuar a atualização. As atualizações do sistema só são oficialmente aceites e testadas em 2 versões no máximo (por exemplo, de 32 a 34).
Neste exemplo, vamos passar de Fedora 32 para 33:

```sh
$ sudo dnf system-upgrade download --releasever=33
$ sudo dnf system-upgrade reboot
```

Uma vez a versão descarregada e o processo de atualização lançado, o servidor reinicia-se para terminar a atualização.
<br>Pode demorar algum tempo até voltar a ligar-se ao servidor, pois a atualização leva tempo.

Verifique que as suas aplicações funcionam como previsto. Em caso de problema, recomendamos que [restaure o backup](../criar_restaurar_um_servidor_virtual_a_partir_de_um_backup/) efetuado antes da atualização.

> [!primary]
> Se encontrar dificuldades, encontrará respostas às suas questões no website [Fedora Docs](https://docs.fedoraproject.org/en-US/quick-docs/dnf-system-upgrade/) {.external}.
>

## Quer saber mais?

Fale com a nossa comunidade de utilizadores em <https://community.ovh.com/en/>.
