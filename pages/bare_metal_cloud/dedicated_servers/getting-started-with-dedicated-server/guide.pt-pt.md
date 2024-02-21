---
title: 'Primeiros passos com um servidor dedicado'
excerpt: 'Saiba como utilizar o seu novo servidor dedicado'
updated: 2024-02-19
---

> [!primary]
> Esta tradução foi automaticamente gerada pelo nosso parceiro SYSTRAN. Em certos casos, poderão ocorrer formulações imprecisas, como por exemplo nomes de botões ou detalhes técnicos. Recomendamos que consulte a versão inglesa ou francesa do manual, caso tenha alguma dúvida. Se nos quiser ajudar a melhorar esta tradução, clique em “Contribuir” nesta página.
>

## Objetivo

Um servidor dedicado é um servidor físico situado num dos nossos datacenters. Ao contrário das soluções de alojamento web (descritas como "partilhadas"), que são geridas tecnicamente pela OVHcloud, é totalmente responsável pela administração no seu servidor dedicado.

**Saiba como utilizar o seu novo servidor dedicado.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/I2G6TkKg0gQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Requisitos

- Ter um [servidor dedicado](https://www.ovhcloud.com/pt/bare-metal/).
- Estar conectado em SSH (acesso root) em Linux ou enquanto administrador em Windows.
- Ter acesso à [Área de Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt).

> [!primary]
>
> Se o seu servidor pertence à linha de produtos **Eco**, consulte [este guia](/pages/bare_metal_cloud/dedicated_servers/getting-started-with-dedicated-server-eco).

## Instruções

Quando o seu servidor dedicado for configurado pela primeira vez durante o processo de encomenda, pode selecionar o sistema operativo a instalar.

### Instalação ou reinstalação do servidor dedicado

Pode facilmente reinstalar o seu servidor e escolher outra imagem de OS na sua [Área de Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt). No separador `Informações gerais`{.action}, clique em `...`{.action} em frente do sistema operativo e, a seguir, em `Instalar`{.action}.

![Botão Reinstalar](images/reinstalling-your-server-01.png){.thumbnail}

Na nova janela, selecione uma das opções de instalação:

- `Instalar a partir de um template OVHcloud`{.action}: pode selecionar o sistema operativo e personalizar a configuração do seu servidor.
- `Instalar um dos seus templates`{.action}: para poder aplicar um template personalizado, deve ter previamente registado, pelo menos, uma configuração de servidor. Para isso, é necessário selecionar a opção "Registar esta instalação" na etapa 4 do processo de instalação.
- `Instalar a partir de uma imagem personalizada`{.action}: esta opção permite-lhe instalar uma imagem externa no servidor. Para mais informações, consulte o [guia sobre a funcionalidade Bring Your Own Image](/pages/bare_metal_cloud/dedicated_servers/bring-your-own-image).

> [!primary]
>
> Certos sistemas operativos ou plataformas proprietárias, como o Plesk ou o Windows, requerem licenças que geram custos suplementares. Pode comprar licenças [junto da OVHcloud](https://www.ovhcloud.com/pt/bare-metal/os/) ou junto de um revendedor externo. De seguida, deverá aplicar a sua licença no sistema operativo ou através da Área de [Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt).
>
> Pode gerir todas as licenças na secção `Bare Metal Cloud`{.action} sob `Licenças`{.action}. Nesta secção, também pode encomendar licenças ou adicionar licenças existentes através do botão `Ações`{.action}.
>

Clique em `Seguinte`{.action} para continuar.

![Seleção de templates](images/reinstalling-your-server-02.png){.thumbnail}

Depois de escolher `Instalar a partir de um template OVHcloud`{.action}, pode selecionar o sistema operativo nos menus pendentes.

![Seleção operacional](images/reinstalling-your-server-03.png){.thumbnail}

Se tiver de alterar o esquema de particionamento do seu sistema operativo, selecione a opção "Personalizar a configuração das partições" antes de clicar em `Seguinte`{.action}.

![Personalizar a configuração das partições](images/reinstalling-your-server-04.png){.thumbnail}

Depois de finalizar os ajustamentos, clique em `Seguinte`{.action} para aceder à página de resumo.

#### Adicionar uma chave SSH (facultativo)

Se instalar um sistema operativo GNU/Linux, pode adicionar a sua chave SSH à última etapa do processo de instalação.

![Personalizar SSH](images/SSH_01.png){.thumbnail}

Se uma chave SSH já estiver registada, aparecerá no menu pendente em "Chaves SSH" na parte inferior. Caso contrário, terá de adicionar uma na secção "Serviços".

Para isso, abra a barra lateral ao clicar no canto superior direito e utilize o atalho `Produtos e serviços`{.action}.

![Personalizar SSH](images/SSH_02.png){.thumbnail}

Em "Os meus serviços", passe para o separador `Chaves SSH`{.action} e clique em `Adicionar uma chave SSH`{.action}.

![Personalizar SSH](images/SSH_03.png){.thumbnail}

Uma vez que se trata da instalação de um servidor dedicado, tenha o cuidado de selecionar "Dedicado" no menu pendente (compatível com um VPS também).

Na nova janela, introduza um ID (nome da sua escolha) e a própria chave (do tipo RSA, ECDSA ou Ed25519) nos campos correspondentes.

![Personalizar SSH](images/SSH_04.png){.thumbnail}

Para obter uma explicação detalhada sobre a geração de chaves SSH, consulte o nosso [guia](/pages/bare_metal_cloud/dedicated_servers/creating-ssh-keys-dedicated).

> [!warning]
>A OVHcloud fornece-lhe serviços pelos quais é responsável em termos de configuração e gestão. Assim, é responsável pelo seu bom funcionamento.
>
>Este guia foi concebido para o ajudar o mais possível nas tarefas mais comuns. No entanto, se encontrar dificuldades ou dúvidas relativamente à administração, utilização ou implementação dos serviços num servidor, recomendamos que contacte um fornecedor especializado.
>

### Ligação ao seu servidor

#### Linux

Uma vez terminada a instalação, receberá um e-mail com as instruções de acesso administrativo. Pode ligar-se ao seu servidor através de um terminal de comando ou com um cliente terceiro utilizando SSH, que é um protocolo de comunicação segura.

Para se ligar ao servidor, utilize os exemplos abaixo e substitua as informações de identificação pelos seus próprios identificadores (o endereço IP e o nome de referência do servidor são permutáveis).

```bash
ssh username@IPv4
```

**Exemplo:**

```bash
ssh ubuntu@169.254.10.250
```

Para saber mais sobre SSH, consulte o nosso guia [Introdução ao SSH](/pages/bare_metal_cloud/dedicated_servers/ssh_introduction).

#### Windows

Uma vez terminada a instalação, receberá um e-mail com a sua palavra-passe de acesso administrador (root). Deve utilizar estas informações de identificação para se ligar ao servidor através de RDP (**R**emote **D**esktop **P**rotocol). Uma vez ligado, o Windows irá guiá-lo durante a instalação inicial.

Consulte também o nosso guia [Configurar uma nova instalação do Windows Server](/pages/bare_metal_cloud/dedicated_servers/windows_first_config).

### Reinicialização do seu servidor dedicado <a name="reboot"></a>

Pode ser necessário um reboot para aplicar configurações atualizadas ou para resolver um problema. Na medida do possível, faça o "soft reboot" do servidor através da seguinte linha de comando:

```bash
reboot
```

No entanto, pode efetuar um "hard reboot" a qualquer momento na sua [Área de Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt). No separador `Informações gerais`{.action}, clique em `...`{.action} em face de "Estado" na zona **Estado dos serviços** e, a seguir, em `Reiniciar`{.action} e `Validar`{.action} na janela contextual.

![Reiniciar](images/rebooting-your-server.png){.thumbnail}

### Segurança do seu servidor dedicado

Como explicado acima, o cliente é o administrador do seu servidor dedicado. Enquanto tal, é responsável pelos seus dados e pela sua segurança. Para saber mais sobre a segurança do seu servidor, consulte o nosso guia [Proteger um servidor dedicado](/pages/bare_metal_cloud/dedicated_servers/securing-a-dedicated-server).

Se utilizar um servidor Windows, consulte [este guia](/pages/bare_metal_cloud/dedicated_servers/activate-port-firewall-soft-win).

### Monitorização OVHcloud <a name="monitoring-server"></a>

Pode ativar ou desativar o monitoring de um servidor dedicado a partir do separador `Informações gerais`{.action} da sua [Área de Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt). A opção situa - se na secção `Estado dos serviços`.

![Monitoring](images/monitoring-your-server.png){.thumbnail}

Clique no botão `Configurar`{.action}. Na janela que aparece, tem três opções para o comportamento de vigilância:

- **Desativado**: Esta opção interrompe as mensagens de alerta e as intervenções da OVHcloud. Escolha esta opção se executar ações de administração pertinentes no servidor que impedem uma resposta ICMP.
- **Ativado com intervenção proactiva**: Se o servidor deixar de responder, ser-lhe-á enviado um e-mail de alerta e o servidor será verificado por um técnico.
- **Ativado sem intervenção proactiva**: No caso de o servidor deixar de responder, receberá uma mensagem de alerta por e-mail. Para dar início a uma intervenção, é necessário ativar a opção com intervenção proactiva.

![Monitoring](images/monitoring-your-server2.png){.thumbnail}

Clique em `Confirmar`{.action} para atualizar a sua configuração de vigilância.

Para mais informações sobre o sistema de monitorização, consulte [este manual](/pages/bare_metal_cloud/dedicated_servers/network_ip_monitoring).

### Configuração de rede

#### Modo bridge IP

O modo bridge é a ação empreendida pelo equipamento de rede para criar uma rede agregada a partir de várias redes de comunicação ou de vários segmentos de rede. O modo bridge é distinto do roteamento, que permite que as redes comuniquem de forma independente, mantendo-se separadas.

Trata-se de uma configuração frequentemente utilizada no contexto da virtualização, para permitir que cada máquina virtual tenha o seu próprio endereço IP público.

Para mais informações sobre o modo bridge, consulte o nosso manual: [Modo bridge IP](/pages/bare_metal_cloud/dedicated_servers/network_bridging).

#### Alias IP

O modo alias IP associa dois endereços IP ou mais a uma interface de rede. Isto permite que o seu servidor estabeleça várias ligações a uma rede, cada uma delas com um objetivo diferente.

Para obter instruções detalhadas sobre a configuração do alias IP, consulte o manual [Configurar o endereço IP em alias](/pages/bare_metal_cloud/dedicated_servers/network_ipaliasing).

#### Configuração IPv6

Todos os servidores dedicados OVHcloud são entregues com um bloco /64 IPv6. Para utilizar os endereços deste bloco, deve introduzir modificações na configuração da rede. Consulte o nosso guia [Configuração IPv6](/pages/bare_metal_cloud/dedicated_servers/network_ipv6).

### Modo rescue

Para todo o tipo de problema, a primeira etapa de reparação consiste em reiniciar o seu servidor em modo de rescue a partir da sua [Área de Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt). É importante identificar os problemas do servidor neste modo, de forma a excluir os problemas relacionados com os softwares antes de contactar as nossas equipas de suporte.

Consulte o manual "[Ativar e utilizar o modo rescue](/pages/bare_metal_cloud/dedicated_servers/rescue_mode)".

### Acesso à ajuda do IPMI

A OVHcloud implementa todos os servidores dedicados com uma consola IPMI (Intelligent Platform Management Interface) que é executada no seu browser ou a partir de uma applet Java, e permite-lhe aceder diretamente ao seu servidor, mesmo que não tenha uma ligação de rede. Isto faz dele uma ferramenta útil para resolver problemas que possam ter colocado o seu servidor fora da linha.

Para mais informações, consulte o nosso manual "[Utilização do IPMI com servidores dedicados](/pages/bare_metal_cloud/dedicated_servers/using_ipmi_on_dedicated_servers)".

### Backup Storage

Os servidores dedicados da OVHcloud incluem um espaço de armazenamento com controlo de acesso e fornecido como opção gratuita. É preferível utilizá-la como opção de backup complementar se o próprio servidor sofrer uma perda de dados.

Para ativar e utilizar a opção Backup Storage, consulte [este guia](/pages/bare_metal_cloud/dedicated_servers/services_backup_storage).

## Quer saber mais?

[Configuração das contas de utilizadores e acesso root num servidor](/pages/bare_metal_cloud/dedicated_servers/changing_root_password_linux_ds)

[Proteger um servidor dedicado](/pages/bare_metal_cloud/dedicated_servers/securing-a-dedicated-server)

[Ativar e utilizar o modo rescue](/pages/bare_metal_cloud/dedicated_servers/rescue_mode)

Se precisar de formação ou de assistência técnica para implementar as nossas soluções, contacte o seu representante comercial ou clique em [esta ligação](https://www.ovhcloud.com/pt/professional-services/) para obter um orçamento e solicitar uma análise personalizada do seu projecto aos nossos especialistas da equipa de Serviços Profissionais.

Junte-se à nossa comunidade de utilizadores em <https://community.ovh.com/en/>.
