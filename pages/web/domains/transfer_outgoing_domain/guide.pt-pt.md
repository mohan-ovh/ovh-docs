---
title: Transferir um domínio para outro agente de registo
excerpt: Saiba como transferir um domínio da OVHcloud para o agente de registo da sua escolha
updated: 2023-03-10
---

> [!primary]
> Esta tradução foi automaticamente gerada pelo nosso parceiro SYSTRAN. Em certos casos, poderão ocorrer formulações imprecisas, como por exemplo nomes de botões ou detalhes técnicos. Recomendamos que consulte a versão inglesa ou francesa do manual, caso tenha alguma dúvida. Se nos quiser ajudar a melhorar esta tradução, clique em "Contribuir" nesta página.
>

**Última atualização: 10/03/2023**

## Objetivo

**Transferência de domínio** refere-se à transferência de um domínio de um agente de registo para outro. Por exemplo, se encomendou um domínio para o nosso website, a OVHcloud é o seu agente de registo atual. O novo agente registador deve iniciar uma transferência de domínio para fora.

De modo a impedir as transferências de domínio não autorizadas, os nomes de domínio são geralmente bloqueados por um estatuto de *clientTransferProhibited*. Esta proteção deve ser levantada na Área de Cliente OVHcloud antes de começar qualquer transferência.

**Este manual explica-lhe como preparar o seu domínio para uma transferência de saída.**

> [!warning]
>
> Se o domínio em questão deve permanecer registado na OVHcloud mas alterado nas suas modalidades de gestão ou de propriedade, uma transferência de domínio não é o procedimento adequado.
>
> Para transferir a gestão do seu domínio para outra conta de cliente OVHcloud, o método adequado é uma alteração de contactos. O procedimento está descrito no [presente guia](/pages/account/customer/managing_contacts).
>
> Se também tem de mudar o **proprietário** do nome de domínio, deve fazê-lo **antes** de alterar os contactos do nome de domínio. Para isso, siga as instruções descritas na nossa documentação sobre a [alteração de proprietário dos nomes de domínio](/pages/web/domains/trade_domain).
>

## Requisitos

- Ter um [domínio](https://www.ovhcloud.com/pt/domains/) registado na OVHcloud
- Ter o direito de solicitar a transferência do nome de domínio: o proprietário e/ou os administradores devem ser informados do pedido de transferência.
- Ter acesso à secção de gestão do domínio na Área de [Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt){.external}.
- O registo do nome de domínio em questão data de há pelo menos 60 dias e não foi transferido ou trocado (ou seja, a mudança de proprietário) durante os últimos 60 dias

> [!primary]
>
> Se é o **proprietário** do domínio mas a sua gestão na Área de Cliente OVHcloud está indisponível, seja através do seu próprio acesso ou através do contacto administrativo do domínio, consulte [este guia](/pages/account/customer/managing_contacts#caso-especifico-de-um-proprietario-de-dominio) antes de continuar.
>

## Instruções

> [!warning]
>
> As instruções que se seguem descrevem a forma mais comum de transferir um nome de domínio, válido para a maioria dos domínios de primeiro nível (top-level domain, ou TLD). No entanto, as regras específicas de procedimentos aplicáveis aos TLD são definidas apenas pela autoridade competente, ou seja, pelo **registo**. Os agentes de registo, como a OVHcloud, devem respeitar estas regras e não têm qualquer influência sobre as decisões dos registos.
>
> Assim, o procedimento exato para as transferências de domínio pode variar, em particular no caso de certos TLD de código de país (ccTLD, tais como .lu, .uk, .hk, .ro) e de alguns TLD especiais (.am, .fm, etc..). As transferências podem igualmente ser proibidas por diversas razões, por exemplo, em caso de pagamento pendente, de abuso ou de bloqueio do registo.
>
> Em caso de dúvida, recomendamos que consulte os seguintes recursos:
>
> - O sítio Web do registo TLD correspondente;
> - a [lista dos TLD disponíveis na OVHcloud](https://www.ovhcloud.com/pt/domains/tld/);
> - [Explicações do ICANN sobre os códigos de estado EPP](https://www.icann.org/resources/pages/epp-status-codes-2014-06-16-en) (para saber que códigos de estado se aplicam atualmente ao seu nome de domínio, efetue uma pesquisa *Whois*, utilizando de preferência o website do registo TLD correspondente);
> - o website e a interface de gestão do seu novo agente de registo, especialmente para as questões relativas a um processo de transferência pendente.
>

### Etapa 1: eliminar a proteção contra a transferência do nome de domínio

Ligue-se à sua [Área de Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt) e selecione a `Web Cloud`{.action}. Clique em `Nomes de domínio`{.action} e selecione o domínio correspondente.

No separador `Informações gerais`{.action}, encontrará o cursor `Proteção contra a transferência` sob **Segurança**. Por predefinição, esta proteção está `Ativada`{.action}.

![proteção ativada](images/outgoing-transfer-step1.png){.thumbnail}

Clique no cursor e confirme, na nova janela, que pretende eliminar esta proteção. Aguarde alguns minutos para que o estado passe para `Desativado`{.action}.

![desativação proteção](images/outgoing-transfer-step2.png){.thumbnail}

> [!primary]
>
> Uma vez levantada a proteção, o domínio ficará desbloqueado durante sete dias. Após este período, a proteção será automaticamente reativada. Se não solicitar a transferência de domínio para o novo agente de registo durante este período, será necessário levantar novamente a proteção do domínio.
>

### Etapa 2: recuperar o código de transferência

> [!warning]
>
> Observe que sempre é possível desbloquear e recuperar o código de transferência do seu nome de domínio após a expiração. De acordo com as regras de registro, um domínio em [redemptionPeriod](https://www.icann.org/resources/pages/epp-status-codes-2014-06-16-en) pode precisar ser restaurado para ser transferido. Entre em contato com seu novo registrador para obter os detalhes da transferência.
>

Uma vez levantada a proteção contra a transferência, pode recuperar o código de transferência do seu nome de domínio. Para isso, ainda no separador `Informações gerais`{.action}, clique em `AUTH/INFO`{.action} situado ao lado de `Proteção contra a transferência`. Não hesite em atualizar a página caso seja necessário.

Aparecerá uma janela com o seu código AUTH/INFO (também conhecido como código de transferência, palavra-passe de domínio, AUTH-CODE ou EPP-Code).

![outgoingtransfer](images/outgoing-transfer-step3.png){.thumbnail}

O código será pedido pelo seu novo agente de registo para concluir o processo de transferência. Pode verificar os detalhes junto do seu novo agente de registo.

Em vez de introduzir manualmente o código, recomendamos que o copie/cole, uma vez que alguns caracteres podem ser facilmente confundidos.

Uma vez o código de transferência recuperado, **não bloqueie de novo o seu domínio a menos que já não queira transferi-lo**.


### Etapa 3: iniciar a transferência para o novo agente de registo

Depois de realizar os passos anteriores, pode lançar o processo de transferência, geralmente através de uma encomenda. A transferência pode demorar até 10 dias. 

Para mais informações contacte o seu novo agente de registo.

> [!warning]
>
> Se o seu novo agente de registo pedir um novo código de transferência, reative a `Proteção contra a transferência` para o seu domínio e desative-a novamente alguns minutos depois. Assim, poderá recuperar um novo código de transferência.
>

## Quer saber mais?

[Transferência de domínio .co.uk de saída](/pages/web/domains/transfer_outgoing_couk)

Para serviços especializados (referenciamento, desenvolvimento, etc), contacte os [parceiros OVHcloud](https://partner.ovhcloud.com/pt/).

Se pretender usufruir de uma assistência na utilização e na configuração das suas soluções OVHcloud, consulte as nossas diferentes [ofertas de suporte](https://www.ovhcloud.com/pt/support-levels/).

Fale com nossa comunidade de utilizadores: <https://community.ovh.com/en/>. 