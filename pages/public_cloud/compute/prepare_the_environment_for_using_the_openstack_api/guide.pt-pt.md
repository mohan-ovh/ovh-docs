---
title: 'Preparar o ambiente para utilizar a API OpenStack'
excerpt: 'Instale o ambiente OpenStack para controlar as suas instâncias através da API'
legacy_guide_number: g1851
updated: 2022-03-30
---

> [!primary]
> Esta tradução foi automaticamente gerada pelo nosso parceiro SYSTRAN. Em certos casos, poderão ocorrer formulações imprecisas, como por exemplo nomes de botões ou detalhes técnicos. Recomendamos que consulte a versão inglesa ou francesa do manual, caso tenha alguma dúvida. Se nos quiser ajudar a melhorar esta tradução, clique em "Contribuir" nesta página.
>

**Última atualização: 30/03/2022**

## Sumário

É possível administrar os serviços Public Cloud através de comandos provenientes da consola do sistema, após o descarregamento e a instalação das ferramentas OpenStack.

Graças à API OpenStack, pode automatizar esta gestão gerando scripts. O cliente Nova OpenStack permite administrar as instâncias e o espaço em disco. Por outro lado, o cliente Glance OpenStack permite-lhe gerir as imagens e os backups. Quanto ao cliente Swift, permite-lhe gerir o espaço de armazenamento dos objetos.

**Saiba como instalar estas ferramentas OpenStack.**

## Requisitos

- Dispor de um acesso **root** ao ambiente que pretende configurar.

## Instruções

### Em Debian

Abra o terminal ou estabeleça uma ligação em SSH ao ambiente que pretende preparar.

Atualize a cache dos pacotes através do comando `apt update`:

```sh
apt update
```

Utilize o comando abaixo para instalar os clientes OpenStack, Nova (aplicação de cálculo) e Swift:

```sh
apt install python3-pip -y
pip3 install --upgrade pip
pip3 install python-openstackclient python-novaclient python-swiftclient
```

Nesta etapa, recomendamos que crie um utilizador especial para não usar o utilizador root.

Para aceder às ferramentas de ajuda, execute o seguinte comando:

```sh
openstack --help
nova help
```

> [!primary]
> 
> A documentação relativa à API OpenStack está disponível [nesta página](https://docs.openstack.org/python-openstackclient/latest/){.external}.
> 

### Em CentOS

Abra o terminal ou estabeleça uma ligação em SSH ao ambiente que pretende preparar.

Atualize a cache dos pacotes através do seguinte comando:

```sh
yum update -y
```

Utilize o comando abaixo para instalar os clientes OpenStack, Nova (aplicação de cálculo) e Swift:

```sh
apt install python3-pip -y
pip3 install --upgrade pip
pip3 install python-openstackclient python-novaclient python-swiftclient
```

Nesta etapa, recomendamos que crie um utilizador especial para não usar o utilizador root.

Para aceder às ferramentas de ajuda, execute o seguinte comando:

```sh
openstack --help
nova help
```

> [!primary]
> 
> A documentação relativa à API OpenStack está disponível [nesta página](https://docs.openstack.org/python-openstackclient/latest/){.external}.
> 

### Em Windows

Descarregue e instale a versão 2.7.14 de Python. Pode optar por adicionar automaticamente a linguagem de programação Python ao Path, selecionando esta opção na configuração da instalação:

![Instalação automática](images/1_preparation_openstack_environment_windows.png){.thumbnail}

Também pode realizar a instalação. Para isso, siga as instruções descritas abaixo:

#### 1 - Editar as variáveis do ambiente do sistema

Comece por escrever “Editar as variáveis do ambiente do sistema” no campo de busca e selecione o menu que aparece.

![Parâmetros das variáveis do ambiente](images/2_preparation_openstack_environment_windows.png){.thumbnail}

#### 2 - Editar os parâmetros do sistema

Passe para a janela `Opções avançadas`{.action} e clique em `Variáveis do ambiente`{.action} para editar os parâmetros.

![Parâmetros de desempenho](images/3_preparation_openstack_environment_windows.png){.thumbnail}

#### 3 - Configurar as variáveis do ambiente 

Na secção “Variáveis do sistema”, selecione “Novo”, atribua o nome “PYTHON_HOME” e adicione o caminho até Python. Esta última será “C:\\Python27” por predefinição.

![Adicionar o caminho de acesso](images/4_edit_system_variables.png){.thumbnail}

#### 4 - Adicionar o caminho para as variáveis

Depois de adicionar o Python, edite o “Path” (caminho) nas variáveis do sistema e adicione o seguinte no final do caminho:

`...;%PYTHON_HOME%\;%PYTHON_HOME%\Script`

#### 5 - Reiniciar o Windows

É necessário reiniciar o sistema para que as alterações sejam aplicadas.

#### 6 - Instalar o cliente OpenStack

Estando conectado como administrador, escreva “cmd” no campo de busca e selecione o símbolo do sistema quando aparecer. Instale o cliente OpenStack utilizando o seguinte comando:

```sh
# pip install python-openstackclient
```

Se a operação se realizar corretamente, aparecerá um resumo:

![Instalação automática](images/5_preparation_openstack_environment_windows.png){.thumbnail}

No símbolo do sistema, pode verificar a versão instalada introduzindo “python-V” (não é relevante em que diretório se encontra).

![Verificação](images/6_preparation_openstack_environment_windows.png){.thumbnail}

### Em MacOS

Pode utilizar [HomeBrew](https://brew.sh), um gestor de pacotes para MacOS.

Abra o terminal e execute o seguinte comando:

```bash
brew install openstackclient
```

Utilize os comandos abaixo para instalar os clientes Nova (aplicação de cálculo) e Swift:

Para Python2:

```sh
pip install python-novaclient
pip install python-swiftclient
```

Para Python3:

```sh
pip3 install python-novaclient
pip3 install python-swiftclient
```

Para aceder às ferramentas de ajuda, execute o seguinte comando:

```sh
openstack --help
nova help
```

## Quer saber mais?

[Carregar as variáveis de ambiente OpenStack](/pages/public_cloud/compute/loading_openstack_environment_variables).

Fale com a nossa comunidade de utilizadores em <https://community.ovh.com/en/>.
