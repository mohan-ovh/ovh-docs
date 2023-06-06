---
title: Configure o seu NAS-HA no Windows Server através do CIFS
slug: nas/cifs
excerpt: Saiba como montar um NAS-HA no Windows Server através do CIFS.
section: NAS-HA
order: 04
updated: 2021-11-22
---

> [!primary]
> Esta tradução foi automaticamente gerada pelo nosso parceiro SYSTRAN. Em certos casos, poderão ocorrer formulações imprecisas, como por exemplo nomes de botões ou detalhes técnicos. Recomendamos que consulte a versão inglesa ou francesa do manual, caso tenha alguma dúvida. Se nos quiser ajudar a melhorar esta tradução, clique em "Contribuir" nesta página.
>

**Última atualização: 08/12/2021**

## Objetivo

Configure e monte o seu espaço de armazenamento NAS-HA OVHcloud no Windows Server através de CIFS.

## Requisitos

- Um [servidor dedicado](https://www.ovhcloud.com/pt/bare-metal/) **ou** um [VPS]https://www.ovhcloud.com/pt/vps/) **ou** uma [instância Public Cloud](https://www.ovhcloud.com/pt/public-cloud/) com uma distribuição Windows.
- Uma oferta [NAS-HA](https://www.ovh.pt/nas/).

### Configuração

- **Windows Server 2008** : clique no menu `Start`{.action} > `All the programs`{.action} > `Accessories`{.action} > `Command prompt`{.action}.
- **Windows Server 2012** : clique no ícone `Windows PowerShell`{.action} na barra de tarefas.
- **Windows Server 2016** : clique no menu `Start`{.action} e, a seguir, no ícone do `Windows PowerShell`{.action}.
- **Windows Server 2019** : clique no menu `Start`{.action} e, a seguir, no ícone do `Windows PowerShell`{.action}.

De seguida, execute o seguinte comando:

```bash
net use z: \\CIFS_SERVER_IP\CIFS_PATH
```

### Exemplo

- Montagem CIFS para um NAS-HA:

```bash
net use z: \\10.16.101.8\zpool-000206_PARTITION_NAME_1
```

> [!alert]
>
> O utilizador SMB/CIFS é `nobody`, qualquer modificação de direitos efetuada por este utilizador pode gerar conflitos com direitos NFS existentes.
> 

## Quer saber mais?

[NAS - Perguntas Frequentes](https://docs.ovh.com/pt/storage/file-storage/nas/faq/)

Se precisar de formação ou de assistência técnica para implementar as nossas soluções, contacte o seu representante comercial ou clique em [esta ligação](https://www.ovhcloud.com/pt/professional-services/) para obter um orçamento e solicitar uma análise personalizada do seu projecto aos nossos especialistas da equipa de Serviços Profissionais.

Fale com a nossa comunidade de utilizadores: <https://community.ovh.com/en/>.